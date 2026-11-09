# Agentic RL 智能体能力的增强学习
传统的后训练主要关注单轮对话的质量优化，
对于多步推理、工具使用、长期规划的智能体任务也需要训练优化。

## PBRFT: Preference-Based Reinforcement Fine-Tuning
维度|  PBRFT    |Agentic-RL
----|-----------|---------
状态|单一提示s0 |动态演化st
行动|文本生成   |文本+工具+环境操作
转移|none       |状态随行动变化
奖励|单步r(s0,y)|累积sum_t y**t r(st,at)
时间|T=1        |T>>1
目标|短期质量   |长期成功

## Agent Abilities
推理     Reasoning   多步逻辑推导
工具使用 ToolUse     API/工具调用
记忆     Memory      长期信息保持
规划     Planning    行动序列规划
自我改进 SelfImprove 自我反思优化
感知     Perception  多种模态理解

## dataset 
GSM8K 数学推理数据集
原始格式 question + answer
- SFT格式 prompt + completion   包含完整解题过程 用于监督学习
- RL格式  prompt + ground_truth 只包含最终答案   用于强化学习

## 奖励函数
准确奖励(AccuracyReward)      奖励正确结果
长度惩罚(LengthPenaltyReward) 奖励简洁回答
步骤奖励(StepReward)          奖励清晰步骤