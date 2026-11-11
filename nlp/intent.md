# Intent 意图


# Intent Recognition 意图识别
## define
kind: question intent, execute intent
分成求知意图和执行意图两类，
对已经陈列的意图枚举或打包的意图集合候选进行匹配，
意图是具体情境下的目的结团。
情境会对目的施加边界和约束。
## implicate
1. intent recognition prompt
2. agentic 
    追问澄清 grill-clarify
    消除歧义 disambiguation
    引导引出 elicitation
    逐步细化 refinement
3. error: unclear, unsupport
## purpose
## slot-filling 槽位填充
将用户模糊的自然语言，转化为机器能理解的、结构化的参数与指令。
1. slot如何定义
2. few-shot
3. spec加载
4. 典型步骤
“识别意图 → 提取已有槽位 → 追问缺失槽位 → 直至集齐”

多意图的意图依赖分析
意图识别测试集

## layers pipeline
语句往往需要进一步解析才能满足用户在其具体情境的需求。
1. 望文生义层：
语句在一般语言上直接近似的语义
2. 用户表达层：
语句由于用户个性化表达潜在的语义补充和语义偏转
3. 真实世界层：
语句描述和作用于真实世界所面临的约束和指定


# Intent Generation 意图生成