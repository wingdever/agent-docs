# Agent Docs

## About
docs about agent which help human request relevant job.

## AI应用的生态结构
### 1. 底层：模型与基础设施层 (The Foundation)
    大模型基座：如GPT-4、Claude 3.5、Gemini等，提供核心的推理能力。
    算力与平台：由云服务商（如华为云、字节跳动）提供底层算力支撑。
## 2. 中间层：框架与协议层 (The Orchestration)
    开发框架：这是Hermes Agent、OpenClaw、LangGraph等框架所处的主要层级。它们为开发者提供构建智能体所需的各种“零部件”和“蓝图”。
    互操作协议：为解决不同智能体、工具间的通信问题，行业正在推进标准化协议，如MCP（模型上下文协议）和A2A（智能体间协议）。Hermes Agent和OpenClaw等主流框架都已原生支持MCP。
## 3. 上层：应用与平台层 (The Application)
    平台型：构建通用智能体中台，实现跨行业部署，如迈富时。
    内嵌型：将AI能力深度融入现有业务系统，如小鹅通将其AI能力植入私域经营全链路。
    终端型：指运行在用户设备上的智能体，如阶跃星辰发布的“智能体原生操作系统”和手机。