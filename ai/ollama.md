---
title: 文件目录路径
status: draft
updated: 2026-10-16
---

ollama
https://ollama.com/
https://github.com/ollama/ollama
https://ollama.com/library

下载和安装
curl -fsSL https://ollama.com/install.sh | sh

# install
sudo pacman -S ollama
sudo systemctl enable --now ollama
curl http://127.0.0.1:11434/api/tags

# pull models
## embedding:embed_model
ollama pull bge-m3
## generation:llm_model
ollama pull qwen2.5:7b
ollama pull qwen2.5:3b

# list models
ollama list

装载模型
运行模型
导入自定义模型



# 文件目录路径
/usr/local/lib/ollama
Created symlink /etc/systemd/system/default.target.wants/ollama.service → /etc/systemd/system/ollama.service.
~/.ollama
    history


文档对话

文档加工
读取向量存储
执行问答

命令行

\$ollama
ollama run llama2

# RAG with Ollama
## 1
pip install chromadb
pip install unstructured langchain langchain-text-splitters
pip install "unstructured[all-docs]"
pip install flask
## ragflow
## LangChain
## LlamaIndex
## XRAG
安装：
pip install examinationrag
\# Install 'jury' without dependencies to avoid conflicts
pip install jury --no-deps
启动：
xrag-cli webui
