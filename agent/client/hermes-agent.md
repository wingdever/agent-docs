---
title: 🤖 Hermes Agent — 完整使用手册
status: draft
updated: 2026-10-16
---

好的，我已经搜集了 Hermes Agent 的全面资料。下面是整理好的完整使用指南。

---

# 🤖 Hermes Agent — 完整使用手册

**Hermes Agent** 是由 **Nous Research** 开发的开源 AI 智能体框架。
它不是一个 IDE 插件或聊天机器人，而是一个**自主智能体**——意为赫尔墨斯，
能运行终端命令、读写文件、搜索网页、浏览网站、编程、调度任务、跨消息平台交互，
并且具备**自我进化**的能力。

---

## 📦 一、安装

### Linux / macOS / WSL2 / Android (Termux)
```bash
curl -fsSL https://hermes-agent.nousresearch.com/install.sh | bash
```

### Windows (PowerShell)
```powershell
iex (irm https://hermes-agent.nousresearch.com/install.ps1)
```

### macOS / Windows 桌面版
从官网下载 **Hermes Desktop** 安装器，包含 CLI + 桌面应用。

**要求**：模型上下文窗口至少 **64K tokens**。

---

## ⚙️ 二、基本配置

### 最快上手路径
```bash
# 安装后只需要这一个命令
hermes setup --portal
```
一次 OAuth 登录搞定模型 + 4 个工具 (网页搜索、图像生成、TTS、浏览器)。

### 其他方式
```bash
hermes setup          # 交互式向导（分步配置所有选项）
hermes model          # 选择模型和提供商
```

### 配置文件结构
```
~/.hermes/
├── config.yaml       # 所有非密钥设置
├── .env              # API 密钥和 secrets
├── auth.json         # OAuth 凭证
├── SOUL.md           # 智能体人格定义
├── memories/         # 持久化记忆
├── skills/           # 技能库
├── cron/             # 定时任务
├── sessions/         # 会话记录
└── logs/             # 日志
```

### 常用配置命令
```bash
hermes config                  # 查看当前配置
hermes config edit             # 用编辑器打开 config.yaml
hermes config set KEY VAL      # 设置值（密钥自动写入 .env）
hermes config get KEY          # 读取值
hermes config check            # 检查缺失选项
hermes doctor                  # 诊断环境问题（--fix 可自动修复）
```

### 支持的主要提供商（20+）
| 提供商 | 认证方式 | 说明 |
|--------|----------|------|
| **Nous Portal** | OAuth | 一键订阅，含 Tool Gateway |
| **OpenAI Codex** | OAuth | ChatGPT 账户 |
| **Anthropic** | OAuth / API Key | Claude 系列 |
| **OpenRouter** | API Key | 多模型路由 |
| **DeepSeek** | API Key | 直连 |
| **Google Gemini** | API Key | Gemini 模型 |
| **xAI Grok** | API Key / OAuth | Grok 模型 |
| **GitHub Copilot** | OAuth | Copilot 订阅 |
| **Custom Endpoint** | 任意 | vLLM / Ollama / SGLang 等 |

---

## 🚀 三、启动与使用

### 启动方式
```bash
hermes                    # 默认 CLI 界面
hermes --tui              # TUI 界面（模态窗口、鼠标选择）
hermes desktop            # 启动桌面应用（也支持 hermes gui）
hermes dashboard          # Web 管理面板
```

### 单次查询
```bash
hermes chat -q "列出当前目录的文件"
```

### 快捷键
| 按键 | 功能 |
|------|------|
| `Alt+Enter` / `Ctrl+J` | 多行输入 |
| `/` | 查看斜杠命令补全 |
| `Ctrl+C` | 中断当前操作 |
| `Ctrl+D` | 退出 |

---

## 💬 四、斜杠命令（会话内）

### 会话控制
| 命令 | 功能 |
|------|------|
| `/new` 或 `/reset` | 新会话 |
| `/retry` | 重发上一条消息 |
| `/undo` | 撤销上一步 |
| `/title 名称` | 为会话命名 |
| `/compress` | 手动压缩上下文 |
| `/model 模型名` | 切换模型 |
| `/personality 名称` | 设置人格（如 pirate） |
| `/reasoning 级别` | 设置推理深度 |
| `/voice on/off/tts` | 语音模式 |
| `/yolo` | 跳过危险命令确认 |
| `/save` | 保存会话 |
| `/help` | 查看所有命令 |
| `/quit` 或 `/exit` | 退出 |

---

## 🧰 五、工具集（Toolsets）

使用 `hermes tools` 交互式管理，或 `hermes tools enable/disable 名称`。

| 工具集 | 功能 |
|--------|------|
| `terminal` | 执行 Shell 命令 |
| `file` | 读写、搜索、编辑文件 |
| `web` | 网页搜索与内容提取 |
| `browser` | 浏览器自动化 |
| `code_execution` | 沙箱化 Python 执行 |
| `vision` | 图像分析 |
| `image_gen` | AI 图像生成 |
| `video` | 视频分析与生成 |
| `memory` | 跨会话持久记忆 |
| `session_search` | 搜索历史会话 |
| `delegation` | 子智能体任务委派 |
| `cronjob` | 定时任务管理 |
| `clarify` | 向用户提问 |
| `tts` | 文字转语音 |
| `skills` | 技能管理 |
| `todo` | 任务看板 |
| `messaging` | 跨平台消息发送 |

---

## 📚 六、技能系统（Skills）

**核心特性：智能体可以自我改进。** Hermes 在解决复杂任务后会创建技能文件，后续会话自动加载。

```bash
hermes skills list            # 列出已安装技能
hermes skills browse          # 浏览技能市场
hermes skills install ID      # 安装技能
hermes skills search QUERY    # 搜索技能
hermes skills check           # 检查更新
hermes skills update          # 更新技能
hermes skills uninstall ID    # 卸载技能
hermes skills config          # 按平台启用/禁用技能
```

---

## 🧠 七、记忆系统（Memory）

Hermes 能在会话间记住你——偏好、环境细节、教训。每个对话都自动加载记忆。

```bash
hermes memory status          # 查看记忆状态
hermes memory setup           # 配置记忆提供商
hermes memory off             # 关闭记忆
```

---

## 🌐 八、消息网关（Gateway）

Hermes 可部署在 20+ 消息平台上，通过统一网关管理。

```bash
hermes gateway setup          # 配置消息平台
hermes gateway run            # 启动网关
hermes gateway install        # 安装为后台服务
hermes gateway status         # 查看状态
hermes gateway restart        # 重启
```

支持的平台：**Telegram、Discord、Slack、WhatsApp、Signal、iMessage、Matrix、Mattermost、Microsoft Teams、Google Chat、Email、SMS、LINE、Feishu、WeCom、Weixin (微信)、DingTalk、Home Assistant** 等。

---

## ⏰ 九、定时任务（Cron）

```bash
hermes cron list              # 列出任务
hermes cron create SCHED      # 创建（如 "30m"、"0 9 * * *"）
hermes cron pause ID          # 暂停
hermes cron resume ID         # 恢复
hermes cron run ID            # 立即触发
hermes cron remove ID         # 删除
```

支持：持续时间（`30m`、`2h`）、Cron 表达式（`0 9 * * *`）、ISO 时间戳。

---

## 👤 十、多配置文件（Profiles）

同时运行多个相互独立的 Hermes 实例，配置、会话、技能、记忆完全隔离。

```bash
hermes profile list           # 列出所有配置
hermes profile create NAME    # 创建新配置
hermes profile use NAME       # 设为默认
hermes profile delete NAME    # 删除
hermes profile export NAME    # 导出为 tar.gz
hermes profile import FILE    # 导入
```

---

## 🏗️ 十一、项目上下文文件

在项目根目录放置以下任一文件，Hermes 会将其内容注入系统提示：

| 文件 | 发现范围 | 适用场景 |
|------|----------|----------|
| `.hermes.md` / `HERMES.md` | 向上搜索至 git root | 项目专属规则 |
| `AGENTS.md` | 仅当前目录 | 多智能体工具通用 |
| `CLAUDE.md` | 仅当前目录 | Claude Code 兼容 |
| `.cursorrules` | 仅当前目录 | 从 Cursor 迁移 |

示例 `.hermes.md`：
```markdown
# My Project

## Build
- Always run `make test` before declaring done
- Use `uv run` for Python

## Style
- Use pathlib.Path over os.path
- Use logger, not print()
```

---

## 🔐 十二、安全功能

| 功能 | 说明 | 命令 |
|------|------|------|
| 密钥脱敏 | 自动在工具输出中隐藏 API 密钥 | `config set security.redact_secrets true` |
| PII 过滤 | 在网关上哈希用户 ID 和手机号 | `config set privacy.redact_pii true` |
| 命令审批 | 对危险命令弹窗确认 | `config set approvals.mode smart` |
| YOLO 模式 | 跳过所有审批 | `hermes --yolo` |

---

## 🛠️ 十三、实用技巧

### 多智能体并行工作
```bash
# 终端 A: 后端
tmux new-session -d -s backend 'hermes -w'
# 终端 B: 前端
tmux new-session -d -s frontend 'hermes -w'
```

### 子任务委派（不用开新进程）
使用 `delegate_task` 工具——子智能体有独立上下文和终端，结果自动返回。

### MCP 服务器集成
```bash
hermes mcp add NAME --url URL    # 添加 MCP 服务器
hermes mcp list                  # 列出已配置
hermes mcp test NAME             # 测试连接
```

### Webhooks
```bash
hermes webhook subscribe NAME    # 创建 Webhook 路由
hermes webhook list              # 列出
hermes webhook remove NAME       # 删除
```

### 检查点与回滚
```bash
# 在会话中启用文件系统检查点
hermes chat --checkpoints
# 会话内使用 /rollback 回滚
```

### 故障排查
```bash
hermes doctor              # 诊断环境
grep "error" ~/.hermes/logs/gateway.log | tail -20   # 查看网关日志
```

---

## 📖 十四、学习路径推荐

1. **安装** → `curl ... | bash`
2. **配置模型** → `hermes setup --portal`（最快）或 `hermes model`
3. **验证** → `hermes chat -q "写个 hello world 程序"`
4. **学会基本斜杠命令** → `/help`、`/model`、`/new`
5. **探索技能** → `hermes skills browse`
6. **配置网关** → `hermes gateway setup`
7. **设置定时任务** → `hermes cron create`
8. **自定义** → `SOUL.md`、`.hermes.md`、多配置文件

---

## 🔗 十五、官方资源

| 资源 | 链接 |
|------|------|
| 官方文档 | https://hermes-agent.nousresearch.com/docs |
| GitHub | https://github.com/NousResearch/hermes-agent |
| 技能市场 | https://hermes-agent.nousresearch.com/docs/reference/skills-catalog |
| 视频教程 | YouTube: "Hermes Agent Masterclass" |
| Discord | 官方文档页面上方 |
| 安装脚本 | https://hermes-agent.nousresearch.com/install.sh |

---

**总之**：Hermes 是一个自主 AI 智能体——不只是聊天，它可以直接操控你的系统、运行代码、管理文件、调度任务，还能通过**技能系统**从每次交互中学习改进。门槛不高（一条命令安装），但能力天花板很高。如果你已经在跑 `hermes` 会话，你现在就是在用它——随时可以让我帮你做更多事情！😊