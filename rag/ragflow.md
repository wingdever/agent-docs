---
title: install
status: draft
updated: 2026-10-16
---

企业级的开源RAG（检索增强生成）引擎

# install
## 依赖docker
sudo pacman -S docker docker-compose
sudo systemctl start docker.service
sudo systemctl enable docker.service
sudo usermod -aG docker $USER ## 请重新登录生效
docker --version
docker-compose --version
## 配置docker
sudo sysctl -w vm.max_map_count=262144
echo 'vm.max_map_count=262144' | sudo tee -a /etc/sysctl.conf
sudo sysctl -p
## 部署ragflow
git clone https://github.com/infiniflow/ragflow.git
cd ragflow/docker
git tag
git checkout -f v0.26.4 ## 最新稳定版本
docker compose -f docker-compose.yml up -d
docker logs -f docker-ragflow-cpu-1
## 配置ragflow
1. 使用API
2. LocalModel(Ollama)
在 ragflow/docker 目录下执行:
docker compose -f docker-ollama.yml up -d
docker exec -it ollama ollama pull llama3

# features
Extract knowledge from complex unstructured documents, 
compile it into reusable structured knowledge artifacts, 
and enable agentic multi-step retrieval with traceable citations 
for automated, low-hallucination RAG workflows.
## 1. Deep Document Understanding & Long-Context Extraction
Extracts knowledge from unstructured data with complex formats.
Finds the small target in a data haystack from unlimited tokens.
## 2. Template-Based Chunking
Intelligent and explainable chunking.
Multiple selectable templates.
## 3. Knowledge Compilation
Compiles document and dataset into structured knowledge artifacts.
Generates Wikis, Graphs, Trees, PageIndex, Mind Maps, Timelines, and Skills.
Supports configurable compilation models and processing rules.
Allows viewing, updating, and regenerating artifacts.
## 4. Agentic Retrieval
Performs multi-step retrieval for complex questions.
Analyzes, decomposes, retrieves, and verifies evidence when needed.
Uses multiple retrieval and reasoning rounds for well-grounded answers.
Offers Low / Medium / High / Ultra thinking modes to control depth.
## 5. Grounded Citations & Reduced Hallucinations
Visualizes text chunking for human intervention.
Provides key references and traceable citations to support grounded answers.
## 6. Heterogeneous Data Compatibility
[Word,PowerPoint,Excel,TXT,image,PDF,scancopy,structdata,webpage]
## 7. Automated, Effortless RAG Workflow
Streamlined RAG orchestration for individuals and large businesses.
Configurable LLMs and embedding models.
Multiple recall with fused re-ranking.
Intuitive APIs for seamless business integration.