# ReAct
## Thought-Action-Observation





# Plan
## Goal
## Context
区分事实、假设、缺失信息、执行约束。
## Choice
方案中多个选型，
对某个选型的选取原因。
## Checkpoint 检查点
## Correction
## Prompt
1. 不要直接回答用户问题，而是先生成Plan
2. 范式：分析需求、执行任务、总结结果
3. 要求模型设计Checkpoint
4. 用户信息不足时先追问
5. Plan生成后先经过用户评审，而不是直接执行
## Evaluation
## DAG Plan 有向无环图
DAG的每个node设计哪些字段？
## RePlan
1. 避免目标漂移
2. 确定上下文内容
3. 设定触发条件
4. 判断检查点失败的原因在于步骤还是计划
5. 处理用户变更计划的目的和情境的中断
6. 正确复用中间结果
## Try-Confirm-Cancel


# workflow
## auto
大模型可能足以自主判断每一步该怎么做，
然后实时创建一些链路，并根据运行情况随时调整。