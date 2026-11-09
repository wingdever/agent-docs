---
title: AI Model
status: draft
updated: 2026-10-16
---

# AI Model
deploy tool entity: {
    <llama.cpp>,
    <ollama>,
    <LM_studio>
};
model fileformat entity: {
    <gguf>,
    <transformers>,
    <gptq>,
    <awq>,
    <onnx>
};
model provide type: {
    [open-source],
    [proprietary]
};
model provider entity: {
    <Meta LLama>,
    <Mistral_AI Mistral>,
    <Microsoft Phi>,
    <DeepSeek DeepSeek>,
    <Google Gemma>,
    <Alibaba Qwen>
};
model file platform entity: {
    <huggingface>,
    <modelscope>,
    <ollama>,
    <github>
};
model api platform entity: {
    <openrouter>,
};
api provider entity: {
    <Google Gemini>,
    <OpenAI GPT>,
    <Anthropic Claude>,
    <Cohere Command>,
};


AI模型部署显存要求：
Note: 
You should have at least 
8 GB of RAM available to run the 7B models, 
16 GB to run the 13B models, 
and 32 GB to run the 33B models.



# LLM for 6GB of VRAM
smaller to medium-sized models, 
primarily in 4-bit (Q4) or possibly 5-bit (Q5) quantization.
## 1.5B - 7B parameter models (4-bit or 5-bit quantized)
Examples include:
Mistral-7B(Various fine-tunes)
    Mistral-7B-Instruct-v0.2
    OpenHermes-2.5-Mistral-7B

3.6GB     deepcoder:1.5b-preview-fp16
4.6GB     phi4-mini-reasoning:3.8b-q8_0
4.9GB     deepseek-r1:8b
4.9GB     granite3.3:8b
4.9GB     cogito:8b-v1-preview-llama-q4_K_M
5.0GB pic gemma3:4b-it-q8_0
5.2GB     qwen3:8b-q4_K_M
5.3GB     exaone-deep:2.4b-fp16


Llama 3(8B)
DeepSeek-Coder-6.7B
## 10B - 13B parameter models (heavily quantized, Q4_K_S or Q3_K_M)
5.7GB llama2:13b-chat-q3_K_S
5.7GB codellama:13b-code-q3_K_S
5.7GB codellama:13b-instruct-q3_K_S
5.7GB codellama:13b-python-q3_K_S


# GGUF (GPT-Generated Unified Format)
for local inference on typical consumer hardware,
GGUF as most recommended and best-supported format

# transformers
PyTorch .pt/.pth, TensorFlow Checkpoints
Original Training Format

