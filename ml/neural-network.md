---
title: 神经网络
status: draft
updated: 2026-10-16
---

# 神经网络

1. 神经网络基础
- 网络结构
- 激活函数
- 损失函数
- 反向传播
- 梯度下降
- 优化方法（SGD、Adam）
2. 常用
- 前馈神经网络（Feedforward Neural Network， FNN ）
- 卷积神经网络（Convolutional Neural Networks, CNN）
- 循环神经网络（Recurrent Neural Network, RNN）

## 隐藏层
全连接层
	最简单的神经层
	全连接接受维度为2的输入，通常为[batch_size, size]。
卷积层
	卷积层的输入为四维[batch_size,channels,H,W] 
池化层


## 激活函数
每一层的神经网络输出后都会使用一个函数（比如sigmoid，tanh，Relu等等）对结果进行运算，
这个函数就是激活函数（Activation Function）
输入的input经过一系列加权求和后作用于另一个函数，这个函数就是这里的激活函数。
### ReLU激活函数
ReLU函数又称为修正线性单元（Rectified Linear Unit），是一种分段线性函数


## 神经网络训练过程
### 损失函数
计算和设定测试结果与准确值的偏差
### Optimizer 优化器
改变神经网络函数的参数值
#### 梯度下降算法

## 编程方法
我们神经网络编程都是在这样一个框架下进行的
首先，我们选择一个技术库
然后，选择神经网络算法模型下的参数
即什么神经网络，神经网络有几层，每层有几个神经元；
然后神经网络的损失函数，激活函数，权重设定等
把我们在该框架下的选择以程序方式告诉技术库即可。
即做出算法框架下的选择，把选择变成编程即可

## 8深度神经网络
CNN 卷积
RNN 循环
GAN 生成Generative Adversarial Network生成对抗网络
DQN 强化
GNN 图神经
LSTM 长短期
Transform
DBN 深度置信网络

DNN	Deep Neural Network，深度神经网络

# RNN
LSTM (时序建模)
