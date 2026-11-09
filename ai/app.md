---
title: model_manager
status: draft
updated: 2026-10-16
---

# model_manager
entities: {
    <ollama>,
    <LM_studio>,
    ...
}

# RAG_app
entities: {
    <ragflow>,
    <dify>,
    <cherry_studio>,
    <anythingllm>,
    <fastgpt>,
    <langchain>,
    <flowgpt>,
    <maxkb>,
    <llamaindex>,
    ...
}
## ragflow
install:
git clone https://github.com/infiniflow/ragflow.git
cd ragflow
git checkout -f v0.16.0
cd docker
run:
docker compose -f docker-compose.yml up -d
docker compose -f docker-compose-gpu.yml up -d
check:
docker logs -f ragflow-server
docker ps
docker ps -a
docker images
stop:
docker-compose -f docker-compose.yml stop
docker-compose -f docker-compose.yml start
docker-compose -f docker-compose.yml down
link:
https://github.com/infiniflow/ragflow


# MCP_app
entities: {
    <xxx>,
    ...
}