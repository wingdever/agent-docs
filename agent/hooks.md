# Hooks 
在Agent生命周期关键节点上的可注册回调；
实现上常借助事件机制，但重点不是发事件，
而是在特定时机插入逻辑，
可以修改输入输出、阻止执行、改变下一步走向，
即生命周期拦截器+回调，能够干预流程。

## 事件类型体系

### 工作流生命周期
StreamEventWorkflowStarted   = "WORKFLOW_STARTED"
StreamEventWorkflowCompleted = "WORKFLOW_COMPLETED"
StreamEventAgentStarted      = "AGENT_STARTED"
StreamEventAgentCompleted    = "AGENT_COMPLETED"
### 执行状态
StreamEventToolInvoked    = "TOOL_INVOKED"     // 工具调用
StreamEventToolObs        = "TOOL_OBSERVATION" // 工具返回
StreamEventAgentThinking  = "AGENT_THINKING"   // 思考中
StreamEventErrorOccurred  = "ERROR_OCCURRED"   // 出错了
### 工作流控制
StreamEventWorkflowPaused     = "WORKFLOW_PAUSED"     // 暂停
StreamEventWorkflowResumed    = "WORKFLOW_RESUMED"    // 恢复
StreamEventWorkflowCancelled  = "WORKFLOW_CANCELLED"  // 取消
StreamEventApprovalRequested  = "APPROVAL_REQUESTED"  // 请求审批
StreamEventApprovalDecision   = "APPROVAL_DECISION"   // 审批结果
### LLM 事件
StreamEventLLMPrompt  = "LLM_PROMPT"  // 发给 LLM 的内容
StreamEventLLMPartial = "LLM_PARTIAL" // LLM 增量输出
StreamEventLLMOutput  = "LLM_OUTPUT"  // LLM 最终输出