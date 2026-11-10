# Context 上下文

## context-window:
    1. system instructions  | 系统指令
    2. user prompt          | 用户当前请求
    3. conversation history | 对话历史
    4. long-term memory     | 跨会话持久记忆
    5. retrived info (rag)  | 实时检索的外部知识
    6. available tools      | 可用工具定义与schema
    7. output format        | 输出格式要求


## 结构化信息
可以在对话中让智能生成结构化的具有会话语义的信息，
这些结构化信息可以跨轮次乃至跨会话生效。
比如关于goal、todo等的信息。
那么对信息结构化存储正是通过压缩信息来增强智能的一个路径。

## 目录
整体设计：类型、生命周期、模块构成、数据结构
分层上下文与统一抽象
上下文窗口的动态编排
摘要、压缩与细节召回
指代消解与关键事实管理
用户画像：最近状况、总览状况和阶段状况
长任务与上下文漂移

