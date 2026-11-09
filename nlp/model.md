---
title: model
status: draft
updated: 2026-10-16
---

[[小模型]]

n-gram models		
markov models			马尔科夫模型
recurrent neural networks	循环神经网络






马尔可夫模型（Markov Model）是一种统计模型，
广泛应用在语音识别，词性自动标注，音字转换，概率文法等各个自然语言处理等应用领域。
经过长期发展，尤其是在语音识别中的成功应用，使它成为一种通用的统计工具。
到目前为止，它一直被认为是实现快速精确的语音识别系统的最成功的方法。
复杂的语音识别问题通过隐含马尔可夫模型能非常简单地被表述、解决




N-Gram模型
N-Gram是一种基于统计语言模型的算法。它的基本思想是将文本里面的内容按照字节进行大小为N的滑动窗口操作，
形成了长度是N的字节片段序列。
每一个字节片段称为gram，对所有gram的出现频度进行统计，并且按照事先设定好的阈值进行过滤，形成关键gram列表，
也就是这个文本的向量特征空间，列表中的每一种gram就是一个特征向量维度。

[[大模型]]
[RLHF]
(Reinforcement Learning from Human Feedback)



[BERT] 
(Bidirectional Encoder Representations from Transformers) 
is a deep learning model developed by Google in 2018 for natural language processing (NLP) tasks 
such as text classification, question answering, and language understanding. 
It is based on a transformer architecture 
and is trained using a combination of masked language modeling and next sentence prediction tasks.




[GPT-3]
GPT-3 is an autoregressive language model that uses deep learning to produce human-like text. It was developed by OpenAI, a research laboratory based in San Francisco, California. GPT-3 is the third generation of the Generative Pre-trained Transformer (GPT) model and is the largest language model ever created. It is trained on a dataset of 45TB of text, including books, articles, and websites. GPT-3 is capable of generating human-like text, completing tasks like question answering, summarization, and translation.


[XLNet]
XLNet is a deep learning model developed by Google AI Language that is designed to improve the performance of natural language processing tasks such as question answering, natural language inference, and text classification. It is based on the Transformer architecture and uses a combination of self-attention and recurrence to better capture long-term dependencies in text.

[RoBERTa]
RoBERTa is a deep learning model developed by Facebook AI that is based on the BERT model. It is designed to improve the performance of natural language processing tasks by leveraging unsupervised data in a self-supervised manner. RoBERTa is an optimized version of BERT that is designed to be more robust to hyperparameter tuning and better at handling longer sequences.
