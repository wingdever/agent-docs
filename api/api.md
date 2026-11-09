核心对话:
post chat_completions_api
    POST /chat/completions
    最标准的对话接口（OpenAI兼容）
    适合绝大多数通用聊天场景
post responses_api
    POST /responses
    面向Agent与工作流的对话
    支持服务端状态链、原生JSON Schema输出
post messages_api
    POST /messages
    Anthropic兼容的对话接口
    方便Claude SDK或Claude Code等应用直接迁移

代码补全：
post fim_completion_api(beta)
    POST /beta/completions
    代码填充（FIM）
    Beta功能，专用于“中间填充”式代码生成

基础管理：
get lists_models
    GET /models
    获取可用模型列表
    查询当前账户支持的模型
get get_user_balence
    GET /user/balance
    查询账户余额
    获取总余额、赠金等详情

资源管理:
post upload_file
    POST /files
    上传图片文件
    用于多轮复用，避免重复上传
get list_files
    GET /files
    列出已上传文件
    支持分页、排序与过滤
get retrieve_file
    GET /files/{id}
    查询文件元信息
    获取大小、创建时间、有效期等
del delete_file
    DELETE /files/{id}
    删除文件
    清理不再需要的资源

联网能力:
post search
    POST /v1/tools/search
    网页搜索
    返回结构化搜索结果列表
post fetch
    POST /v1/tools/fetch
    网页抓取
    抓取单个URL，返回Markdown正文