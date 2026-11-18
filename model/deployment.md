# 模型部署

## AI hardware
GPU: H100, A100, L40S, 4090
CPU: 
Network: RoCE (RDMA) vs. TCP/IP
## deploy framwork
Ollama vLLM SGLang



## SGLang
SGLang深度优化：Radix缓存与复杂任务的极致吞吐
1. SGLang 的缓存优化及 Radix Tree 原理及运行时高级抽象
- Radix Tree (基数树) 原理
- SGLang 的 RadixAttention
- 运行时高级抽象 (Frontend/Backend)
- SGLang IR (中间表示)
2. SGLang 对于复杂AI任务中的极致延迟及吞吐优化
- Token Healing 技术
- 复杂控制流优化
- 多租户与智能调度
- SGLang 与 vLLM 在执行中的差异