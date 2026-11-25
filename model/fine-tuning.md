# fine-tuning 微调

## 微调准备：数据
- 数据增强
- 数据清洗
- 数据去重

## 微调技术选型
### 全参数微调
### PEFT 参数高效微调
1. 技术
- Adapter Tuning
- Prompt Tuning
- Prefix Tuning
### LoRA 低秩适配
1. 变体
- QLoRA
- AdaLoRA
- LongLoRA
- SLoRA
### SFT 监督微调 supervised 
### 指令微调


## 框架
- unsloth
- [Transformers](https://github.com/huggingface/transformers)
- [PyTorch](https://github.com/pytorch/pytorch)
- [DeepSpeed](https://github.com/deepspeedai/DeepSpeed)

## 原理
SVD矩阵分解