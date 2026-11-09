# deepseek-harness
## agent-loop
struct: 会话(Session) -> 轮次(Turn) -> 步骤(Step)
用户输入 - 理解意图 - 结构化执行
1. 意图理解
Inbox-quene =: next-turn-quene + next-step-quene => Driver
复合意图 = n*问答意图 + n*执行意图
2. 任务编排
将大目标拆解为可执行的步骤序列：
宏观编排（轮次内自主规划）：
    将任务拆解成小目标，自主规划多个步骤，直到认为任务完成。
微观编排（子代理subagent委派）：
    除了拆解任务、接收结果和汇总之外，
    将独立子任务委派给专门的 subagent 并行执行。
3. 步骤执行
每个步骤对应一次模型请求以及这次请求触发的工具调用。
循环的核心链路是：组装提示词 → 调用 LLM → 执行工具 → 将结果写回日志。
(1)组装提示词：
通过 system-prompt 服务组装请求前缀，并从会话日志中派生历史上下文。
(2)调用 LLM：
经 LLM 接口流式获取模型响应。
(3)执行工具：
经工具注册表分发并执行模型请求的工具调用。
(4)写回日志：
每个模型可见的事实（包括工具结果）追加回会话日志，供下一步派生使用。
4. 轮次衔接
(1)Goal Round:继续当前会话，保留上下文。
(2)Ralph Run:共享工作区并传递交接报告。


## system-prompt
通过动态组装在每个步骤中与提示词的其余部分一同提供给模型。
### tools registry-table
struct tool {
    name
    desc
    parameter-struct
}
ctx.tools.register(definition)
ctx.systemPrompt.tools(provider)
### dynamic-assemble service
