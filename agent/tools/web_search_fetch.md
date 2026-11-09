# web_search
快速定位包含相关信息的网页
接收查询参数，返回包含标题、URL 和摘要的候选结果列表

## 实现
### 自托管的三阶段管道
搜索提供方 (Search Provider)：负责执行实际的检索。例如，它可以配置为调用自托管的 SearXNG 实例的 API（GET /search?q=&format=json），返回结构化的结果列表。

爬虫提供方 (Scraper Provider)：这是一个可选的深度组件。当模型需要某个特定结果的更多信息时，可以触发二次抓取。例如，调用 Firecrawl 的 API（POST /scrape）来获取该 URL 的 Markdown 内容。

缓存层：搜索结果（包括摘要和稳定的 result_id）通常会被缓存（如 SQLite），确保在后续的 web_fetch 调用中能准确引用同一个结果。

### 服务端托管工具
在商业 API（如 Anthropic Claude）中，web_search 被实现为一个服务端工具（Server Tool），搜索在模型提供方的基础设施上执行。

工作流程：模型在推理过程中自主决定是否需要搜索。如果需要，它会生成查询，API 在服务端执行搜索，并将结果（含引用来源）注入回模型的上下文中。这个过程可以在单次请求中重复多次。

动态过滤（Dynamic Filtering） ：较新版本（如 web_search_20260209 及更高版本）引入了此功能。模型可以编写并运行代码，在搜索结果进入上下文窗口之前进行过滤，仅保留相关内容，从而显著减少 token 消耗。



# web_fetch
将指定 URL 的内容“翻译”成模型能直接阅读的格式。
接收一个具体的 URL，抓取页面，
并返回剥离导航、广告、脚本等无关元素,
清洗后的可读文本（通常是 Markdown）。

## 实现
1. HTTP 请求
2. 内容提取
可读性算法（Readability）
Mozilla Readability（即 Firefox 阅读器视图背后的引擎）
3. 格式转换
正文 HTML 转换为 Markdown。
常用的转换库包括 Turndown（支持 GFM 扩展）。
4. 降级与缓存
如果 Readability 提取的内容过少（例如，在文档中心或落地页上），
一些实现会降级到更宽泛的全页提取策略。
抓取结果通常会被缓存，以减少对同一 URL 的重复请求。

关键差异：JavaScript 处理能力
许多轻量级 web_fetch 工具明确不执行 JavaScript，
因此无法处理依赖客户端渲染的页面。
而另一些工具（如 Claude Code 内置的 WebFetch）也不执行 JavaScript，
但有社区方案（如 render-fetch）
通过集成 Playwright 无头浏览器来专门处理 JS 渲染页面，
其管道变为：Playwright → networkidle → Readability → Markdown。