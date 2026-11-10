# pipeline rag workflow
## 1. prepare phase
store knowledge documents into database.
### 1.1 Chunking
split document into small parts.
0. naive chunk:
chunk by a fixed character count
1. Semantic Chunking
2. Proposition Chunking
### 1.2 Embedding
tranfer small document part into vector. 
0. Common embedding models
  1. text-embedding-3
  2. BGE
  3. Qwen3-Embedding
1. Domain-Specific Embeddings
### 1.3 Indexing
save vector and link to document parts into database.
1. database
  1. vector-database
    1. SQLite + sqlite-vec
    2. Postgres + pgvector
    3. milvus
    4. chromadb
  2. graph-rag
    entity and relation
2. schema
  1. vector linked with document parts
  2. metadata
## 2. retrieve phase
find documents about need knowledge.
### 2.1 Query-Processing
process query input from user for better match.
1. Query Transformation
use llm to generate specific general decomposed query.
  1. 指代消解
  2. 省略句补全
  3. 同义词和术语规范化
  4. 查询条件提取
  5. 关键词提取
2. HyDE
use llm to generate posiable answer to match.
### 2.2 Retrieval
select matched content from database.
1. Recall 
  1. semantic: compare query embedding with document parts embedding.
  2. keyword: bm25
  3. hybrid search
2. Rerank candidate documents by relevance.
## 3. Compose
### 3.1 Agentic RAG
workflow use loop instead of pipeline.
### 3.2 Adaptive Routing
lightweight classifier estimates the difficulty of a question.
