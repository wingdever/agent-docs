---
title: 本地STT
status: draft
updated: 2026-10-16
---

# 本地STT


# vosk
[text](https://alphacephei.com/vosk/index.zh.html)
pip install vosk
下载语音识别模型

vosk-model-small-zh-cn-0.22
vosk-model-zh-cn-0.22



Vosk-Server
将vosk模型放到服务器上



## 安装

```
mkdir vosk
cd vosk
# 创建虚拟环境（例如命名为vosk-env）
python3 -m venv vosk-env
# 激活虚拟环境
source vosk-env/bin/activate
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
pip install --upgrade pip
pip install vosk
mkdir vosk_models
cd vosk_models
wget https://alphacephei.com/vosk/models/vosk-model-cn-0.22.zip
unzip vosk-model-cn-0.22.zip


# 安装pyaudio（需在虚拟环境中）
pip install pyaudio


```

# whisper