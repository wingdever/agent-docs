# skill
为智能代理提供结构化、可发现、可复用的操作指南，称之为技能。

## 目录结构
1. 标准目录骨架
```text
skills/<skill-name>/        # 技能名称必须使用 kebab-case (如: pdf-processing)
├── SKILL.md             # 必需：技能的元数据与核心指令入口
├── references/          # 可选：存放详细的参考文档、决策表、长文本
├── assets/              # 可选：存放模板文件（如HTML、Markdown模板）
└── scripts/             # 可选：存放确定性验证脚本（如格式检查、路径校验）
```

2. 关键规则：
- 命名强制：文件夹名和SKILL.md中的name字段必须使用kebab-case（小写字母、数字、连字符）且完全一致。

- 文件精确性：入口文件必须严格命名为SKILL.md，大小写敏感，技能文件夹内禁止出现README.md。

- 职责分离：
SKILL.md只承载核心流程和索引；
超过约100行的详细内容应移至references/；
模板放assets/；
scripts/仅用于确定性的校验逻辑，而非LLM驱动的逻辑。

- 扁平并列：如果多个技能在逻辑上属于一个领域可采用共同名称前缀。

## SKILL.md 编写规范
内容分为元数据（YAML Frontmatter）和正文（Markdown）两部分。

1. YAML Frontmatter (元数据)
文件顶部必须由---包裹的YAML块，这是AI发现和触发技能的依据。

required字段：
name 
description

nullable字段：
license
compatibility
metadata
allowed-tools
disabled-model-invocation



description范例：
好的描述明确了能力（提取、填表、合并）和触发场景（处理PDF、用户提及PDF等），能让AI精确匹配。
```yaml
# 好的描述
description: >
  Extracts text and tables from PDF files, fills forms, merges PDFs.
  Use when working with PDFs or when user mentions PDF, form,
  or document extraction.

# 糟糕的描述
description: Helps with PDFs.
```

2. Markdown正文（核心指令）
正文是AI执行任务时的操作指南。编写时需遵循渐进式披露原则，保持SKILL.md精炼，将详细内容分层。

- 核心流程置于正文：工作流指令、触发示例、少于3个分支的简单决策树应直接写在SKILL.md正文中。
- 详细信息外置：超过50行的复杂决策表、参考矩阵、案例研究等，应放入references/目录，供AI按需加载，以节省上下文Token。
- 篇幅控制：建议主SKILL.md文件保持在500行以内，以便于维护和高效利用上下文。

## 管理技能关系：组合、依赖、编排、检索
Graph-of-Skills (GoS)：该方法在离线阶段将技能包解析成一个可执行的技能图，显式构建技能之间的依赖边和工作流边。

## 参考资料
Agent Skills 官方规范：由Anthropic等机构推动的agentskills.io是事实上的格式标准，其规范文档对目录结构、字段定义有最权威的说明。

Microsoft Learn - Agent Skills：微软官方文档详细阐述了“渐进式披露”等核心设计模式，并提供了清晰的编写指引。