# 向量存储
llama-index 内置 SimpleVectorStore + 本地 JSON 持久化；
刻意不装 chromadb：
其依赖需在本机编译，且本项目规模用内置 SimpleVectorStore 足够