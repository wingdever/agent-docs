# 1. install
npm install -g agent-sync-sh
~/.agents/
# 2. workflow
1. init
agent-sync init
2. adopt config
agent-sync adopt <path>
3. sync publish
agent-sync sync
4. check status
agent-sync status
agent-sync doctor
# 3. mcp config
agent-sync mcp list      # 列出所有 MCP 服务器
agent-sync mcp adopt     # 接管一个 MCP 服务器的管理
agent-sync mcp enable    # 启用一个服务器
agent-sync mcp disable   # 禁用一个服务器