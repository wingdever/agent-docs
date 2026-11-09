# codebuddy

## install
npm install -g @tencent-ai/codebuddy-code

## 可拓展能力
### Agent(智能体编排)
 - 主会话可 spawn 子 agent（Agent 工具），并行/后台执行，自动组队（TeamCreate）
 - 配套的任务管理（TaskCreate/Update/List）、跨会话记忆（Memory）、定时调度（Cron）、动态工
  作流（Workflow）
### Skill(技能)
 - 内置技能（如 loop）+ 自定义技能（按目录加载的 SKILL.md）+ 斜杠命令
 - 通过 Skill 工具或 /<command> 触发
### MCP(外部工具协议)
 - 连接外部 MCP server 扩展工具/资源，WaitForMcpServers 等待握手，DelegateTool 处理外部委托