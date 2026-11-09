---
title: transformer
status: draft
updated: 2026-10-16
---

# transformer
transformer neural network
Some key elements of the model such as:
	Number of layers in transformer blocks
	Number of attention heads
	Loss function
	Hyperparameters
	


# BERT
Question Answering




# torchtext
```
import torch
from torchtext.datasets import AG_NEWS
train_iter = iter(AG_NEWS(split='train'))
next(train_iter)
```

```
from torchtext.data.utils import get_tokenizer
from torchtext.vocab import build_vocab_from_iterator

tokenizer = get_tokenizer('basic_english')
train_iter = AG_NEWS(split='train')

def yield_tokens(data_iter):
    for _, text in data_iter:
        yield tokenizer(text)

vocab = build_vocab_from_iterator(yield_tokens(train_iter), specials=["<unk>"])
vocab.set_default_index(vocab["<unk>"])
```

将单词转化为整数数字
vocab(['here', 'is', 'an', 'example'])
>>> [475, 21, 30, 5297]




## Transformer Input
representation: Token = 
	embedding_word : Vector 
	+ 
	embedding_position : Vector 
### embedding_word
way_from pre-train:
	Word2Vec
	Glove
	Transformer
### embedding_position
PE(pos,2i) = sin(pos/10000^(2i/d_model))
PE(pos,2i+1) = cos(pos/10000^((2i+1)/d_model))
pos: position of the token in the sentence
d_model: dimension of the embedding vector

## Self-Attention 自注意力机制
every token have Q(query),K(key),V(value)
about this token:
	Q:waht want to know the context of the sentence
	K:waht kind of things are related
	V:the information you want to get
Attention(Q,K,V) = softmax(Q*K^T/d_k^0.5) * V
	d_k: dimension of the Q,K vector, as column number

## Multi-Head Attention


# token
1. transform的token的包含上下文的语义的生成，只和其以及之前的token相关。
2. 每次计算包括缓存输入、新输入和输出3部分。
3. Prefill 阶段并行处理整段输入；Decode 阶段每步包括读取历史 K/V Cache、计算当前 token 的 Q/K/V 并追加 K/V、输出当前 token 的表示并采样下一个 token。
4. Prefill 对新输入的整段词向量做并行运算，得出各个token。
这里并行运算在数学上通过因果掩码等效于逐个token串行运算。
Prefill 一次性计算整段 prompt 的 Q/K/V，并把每层 K/V 存入 KV Cache。
5. 然后逐个token生成输出。
6. 这里包括新的输出成为新的缓存。
7. Decode 阶段当前 token 的 K/V 被追加到 KV Cache，作为下一步的历史缓存；Q 不缓存。

# 矩阵乘法 of 注意力
Cᵢⱼ = ∑ₖ Aᵢₖ Bₖⱼ
## 定义: X 输入
Xnm : n行 m列 矩阵
X_ij : 矩阵 i行 j列 的元素
Xi[] : 矩阵 i行 的向量
Cnm == Ank x Bkm
C_ij == Ai[] · B[]j
补充：
d维表示语义的表示空间的自由度。
## 逐行投影: Q,K,V 投影
1. math level
tokens: Xnd : n tokens d dimision
weight: WQdq: from d dimision to q dimision
Qnq = Xnd x WQdq <==> qi == xi x WQ
2. tranformer level
Q = X x WQ <==> token_i -> q_i
K = X x WK <==> token_i -> k_i
V = X x Wv <==> token_i -> v_i
## 内积与分块: S = Q Kᵀ 分数
S = Q Kᵀ 
Sᵢⱼ = qᵢ · kⱼ = ∑ₔ Qᵢ,ₔ Kⱼ,ₔ
Sᵢ,: = [Sᵢ₁, Sᵢ₂, ..., Sᵢₘ]
矩阵 S  表示: 未归一化的注意力分数矩阵(logits矩阵)
元素 Sᵢⱼ 表示: 第i个 query 与第j个 key 的相似度或匹配程度。
向量 Sᵢ, 表示: 一个 query 对所有 key 的分数
## 加权累加: softmax 缩放与掩码
A = softmax(S / √d_k) = softmax(QKᵀ / √d_k)
S / √d_k：缩放后的注意力 logits；
A：注意力权重矩阵；
Aᵢⱼ：第 i 个 query 分配给第 j 个 key 的注意力权重；
softmax 通常按行进行，因此每个 query 对所有 key 的权重和为 1
补充：
在单头注意力中，注意力权重是一个标量矩阵，
因此每个维度共享同一组权重，
因此单头注意力决定“从哪些 token 聚合信息”，
但对被聚合 value 向量的所有维度使用相同权重。
## 外积之和: AV 聚合
Attention(Q,K,V) = A V = softmax(QKᵀ / √d_k) V
矩阵形状: n × d_v token数量 v维度
oᵢ = ∑ⱼ Aᵢⱼ vⱼ
第 i 个位置根据它与所有 key 的匹配程度，
对所有 value 做加权平均，得到新的表示。
## 多头注意力
headₕ = Attention(QWₕQ, KWₕK, VWₕV)
每个头有自己的一组投影和注意力权重 A⁽ʰ⁾，
因此不同头可以关注不同关系、不同子空间或不同模式。


# Process 处理流程
## Prefill 预填充编码输入
并行处理整个输入 prompt，计算密集，
主要目标是高效地建立 KV Cache 并产出第一个 token。

### Prefill 的 KV Cache 数学定义
设某一层 Transformer 的输入为：
X ∈ R^(n × d)
其中 n 是输入 prompt 的 token 数，d 是模型隐藏维度。
该层的投影矩阵为：
W_Q ∈ R^(d × d_k)
W_K ∈ R^(d × d_k)
W_V ∈ R^(d × d_v)
Prefill 阶段一次性计算整段输入：
Q = XW_Q
K = XW_K
V = XW_V
形状分别为：
Q, K ∈ R^(n × d_k)
V ∈ R^(n × d_v)
因果自注意力为：
Attention(Q,K,V) = softmax(QKᵀ / √d_k + M) V
其中 M 是因果掩码，M_ij = 0 当 j ≤ i，否则 M_ij = -∞。
Prefill 结束时，每层保留：
C_K^(l) = K^(l)
C_V^(l) = V^(l)
这就是该层的 KV Cache。注意：
- 只缓存 K 和 V，不缓存 Q；
- 每层都有自己的 C_K^(l), C_V^(l)；
- 多头注意力中，每个头也分别缓存自己的 K/V；
- Prefill 的并行计算通过因果掩码，在数学上等价于每个位置只能看到自己和之前的 token。
Prefill 最后用最后一个位置的输出得到 logits，并采样出第一个输出 token y_1。
- Prefill 的 KV Cache 就是 Prefill 这次 Attention 用到的 K 和 V 的全量副本。

## Decode 自回归解码生成
顺序地逐个生成 token，通常受内存带宽限制，
每一步都依赖于之前所有 token 的 KV Cache。
X⁽ˡ⁺¹⁾ = FFN( LayerNorm( X⁽ˡ⁾ + O⁽ˡ⁾ W_O⁽ˡ⁾ ) )
X⁽ᴸ⁺¹⁾ = H
→ h_last（Prefill 取最后一行；Decode 只有一行）
→ logits = h_last W_LM
→ p = softmax(logits)
→ y_next ~ p

### Decode 的单步数学过程
假设当前已经生成了 t-1 个 token，KV Cache 中保存了：
C_K ∈ R^((n+t-1) × d_k)
C_V ∈ R^((n+t-1) × d_v)
现在输入上一个 token y_(t-1) 的表示，记为：
x_t ∈ R^(1 × d)
x_t = Embed(y_(t-1)) + PE(t)
	Embed(y_(t-1)) ：token embedding
	PE(t)：位置 t 的位置编码
注意 Decode 每步只处理一个 token，所以 x_t 是单行向量。
该层计算当前 token 的 Q/K/V：
q_t = x_t W_Q
k_t = x_t W_K
v_t = x_t W_V
形状为：
q_t, k_t ∈ R^(1 × d_k)
v_t ∈ R^(1 × d_v)
然后先更新 KV Cache：
C_K ← [C_K; k_t]
C_V ← [C_V; v_t]
更新后：
C_K ∈ R^((n+t) × d_k)
C_V ∈ R^((n+t) × d_v)
当前 token 的 query 与所有历史 key 做注意力打分：
s_t = q_t C_Kᵀ / √d_k
s_t ∈ R^(1 × (n+t))
得到注意力权重：
a_t = softmax(s_t)
a_t ∈ R^(1 × (n+t))
加权聚合所有缓存的 value：
o_t = a_t C_V
o_t ∈ R^(1 × d_v)
最后经过输出投影、残差、LayerNorm、FFN 等，得到当前步输出，并采样出下一个 token：
y_t ~ softmax(LMHead(o_t'))
其中 o_t' 是该层/整个模型处理后的表示。

关键点：
1. Decode 每步只计算当前 token 的 q_t,k_t,v_t；
2. 历史 token 的 K/V 不再重新计算，直接从 KV Cache 读取；
3. 当前步的 k_t,v_t 追加进 cache；
4. Decode 阶段单 query 对全部历史 key 做注意力，因此不需要因果掩码，因为它本来就只能看到历史；
5. 位置编码使用当前位置 pos = n+t。

### 多头注意力下的 Decode
对每个头 h：

q_t^(h) = x_t W_Q^(h)
k_t^(h) = x_t W_K^(h)
v_t^(h) = x_t W_V^(h)

分别更新每个头的 cache：

C_K^(h) ← [C_K^(h); k_t^(h)]
C_V^(h) ← [C_V^(h); v_t^(h)]

每个头独立计算：

o_t^(h)
= softmax(q_t^(h) (C_K^(h))ᵀ / √d_k) C_V^(h)

然后拼接所有头：

o_t = Concat(o_t^(1), ..., o_t^(H)) W_O

### 复杂度对比
Prefill：

O(n² d_k)

因为 n 个 query 要和 n 个 key 做注意力。

Decode 单步：

O((n+t) d_k)

因为只有 1 个 query，但要和 n+t 个历史 key 做注意力。生成 T 个 token 的总注意力成本约为：

O(∑_(t=1)^T (n+t) d_k)
= O(T(n+T)d_k)

KV Cache 显存占用大致为：

O(L · (n+T) · d_k · 2)

其中 L 是层数，系数 2 表示 K 和 V；多头、batch 再乘相应维度。