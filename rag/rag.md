---
title: RAG 检索增强生成 Retrive Augmented Generation
status: draft
updated: 2026-10-16
---

# RAG 检索增强生成 Retrive Augmented Generation
## paradigm 范式
Naive RAG
	索引
	检索
	生成
Advanced RAG
	预检索
	检索增强
	后检索
Modular RAG
	混合检索
	智能编排
	技术融合
## variant 变体
	T-RAG 时序感知
	CRAG 纠错增强
	Self-RAG 自反思
	RAG-Fusion 多查询融合
	Rewrite-Retrieve-Read RAG 查询重写
## component 部件
检索器 Retriever
生成器 Generator
增强方法 Augmentation Method
## Naive RAG Pipeline 朴素检索增强生成流程
知识库构建
	文档加载和分块
	分块方案详解
Embeddings向量化
	向量化意义
	向量化实践
	向量相似度算法
		余弦距离Cosine
		点积IP
		欧式距离L2
	向量数据库
		向量数据库作用
		向量数据库类型
		主流向量数据库和功能对比
Prompt上下文增强设计





 1. Embedding 与 LLM 用哪种服务？ 这是 RAG 的核心依赖。选项：
    - 云端 API（OpenAI / DeepSeek / 智谱 / DashScope 等）——效果最好，需要你提供 key 和厂商
    - 本地 Ollama（如 bge-m3 + qwen）——全离线、隐私最好，但要装 Ollama 和下载模型
    - 本地 HuggingFace sentence-transformers 做 embedding + 云端 LLM 做生成
  2. 暴露给 agent 的工具形式？ 选项：
    - MCP Server（stdio / SSE）——现在 agent（CodeBuddy、Claude Desktop 等）的通用标准，推荐
    - HTTP REST API（FastAPI）——通用但要 agent 自己写客户端
    - 两者都做（MCP 为主，HTTP 备用）

llama-index 的部分依赖（尤其是 pydantic、numpy、torch
   生态）

llama-index 核心与 Ollama 集成包都是纯 Python（py3-none-any）

chromadb 需要编译，避开它——我们直接用 llama-index 自带的简单向量存储 +
  本地持久化（或轻量 faiss 替代），减少依赖风险。

  我的方案要点：
  - 不引入 chromadb / torch，用 Ollama 做 embedding + LLM，向量索引用 llama-index 内置
  SimpleVectorStore 落盘，依赖最小。
  - 分块策略针对 MD 的 frontmatter 和 [[双链]] 做专门处理：把 frontmatter 的 title/status
  注入到 chunk 文本，提升检索命中。
  - 增量索引：基于文件 mtime/hash 做缓存，避免 5704 个文件每次全量重嵌。
  - MCP Server 暴露 search_docs（检索）、ask_docs（带生成回答）、reindex（重建）三个工具。
  - 学习资料放在 ~/Projects/wiki/docs/，每步一篇，讲清「为什么这么设计」而不只是贴代码。


1. ~/Projects/wiki/ 下新建项目文件（代码、配置、README、docs/
  学习资料）——全部在你指定的空工作目录内。
  2. 在 ~/Projects/wiki/.venv/ 创建 Python 虚拟环境并安装包。
  3. 用 pacman/yay 系统级安装 Ollama（写 /usr、注册 systemd 服务），并下载模型到
  ~/.ollama（约 1–3 GB）。这是唯一影响工作目录之外的操作，需要你点头。
  4. 生成 MCP 配置示例文本给你，但不会擅自改 ~/.codebuddy/mcp.json 等你的 agent
  配置（那属于共享配置，按 Commons 规则应由你本人或 agent-sync 流程处理）。

分块粒度。你的文档是个人笔记，很多很短（如 model.md 才 10 行），也有长文。我倾向：
  - 固定 chunk_size ≈ 512 token、overlap 64；
  - 短文档不切分，整篇一个 chunk（避免语义被切断）；
  - 每个 chunk 头部注入 来源路径 + title + 目录主题，让检索能命中「哪个领域」而不只是词面。


