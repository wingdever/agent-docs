---
title: 安装工具
status: draft
updated: 2026-10-16
---

# 安装工具
1. 依赖PortAudio（PyAudio 的依赖）
sudo pacman -S portaudio cmake
2. cpu版本
pip install sherpa-onnx
3. nvidia gpu cuda版本
pip install sherpa-onnx==1.11.1+cuda -f https://k2-fsa.github.io/sherpa/onnx/cuda.html
4. 预训练模型
# 下载组件
## 中文模型压缩包
wget https://github.com/k2-fsa/sherpa-onnx/releases/download/kws-models/sherpa-onnx-kws-zipformer-wenetspeech-3.3M-2024-01-01.tar.bz2
## 解压模型
tar xf sherpa-onnx-kws-zipformer-wenetspeech-3.3M-2024-01-01.tar.bz2