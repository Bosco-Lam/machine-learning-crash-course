# 机器学习笔记



## 框架处理

### 机器学习主要术语

#### 监督学习

机器学习系统通过学习如何组合输入信息来对从未见过的数据做出有用的预测。

#### 标签

**标签**是我们要预测的事物，即简单线性回归中的 `y` 变量。标签可以是小麦未来的价格、图片中显示的动物品种、音频剪辑的含义或任何事物。 

#### 特征

**特征**是输入变量，即简单线性回归中的 `x` 变量。简单的机器学习项目可能会使用单个特征，而比较复杂的机器学习项目可能会使用数百万个特征，如下表示：
$$
\{x_1,x_2,…x_N\}
$$
在垃圾邮件检测器示例中，特征可能包括：

- 电子邮件文本中的字词
- 发件人的地址
- 发送电子邮件的时段
- 电子邮件中包含“一种奇怪的把戏”这样的短语。

#### 样本

**样本**是指数据的特定实例：**x**。（我们采用粗体 **x** 表示它是一个矢量。）我们将样本分为以下两类：

- 有标签样本——同时包含特征和标签：
  $$
  \{features, label\}: (x, y)
  $$

- 无标签样本——包含特征但不包含标签：
  $$
  \{features, ?\}: (x, ?)
  $$




在使用有标签样本训练了我们的模型之后，我们会使用该模型来预测无标签样本的标签。在垃圾邮件检测器示例中，无标签样本是用户尚未添加标签的新电子邮件。

####模型

模型定义了特征与标签之间的关系，模型生命周期两个阶段：

- **训练**表示创建或**学习**模型。也就是说，您向模型展示有标签样本，让模型逐渐学习特征与标签之间的关系。
- **推断**表示将训练后的模型应用于无标签样本。也就是说，您使用训练后的模型来做出有用的预测 (`y'`)。例如，在推断期间，您可以针对新的无标签样本预测 `房价中值`。

#### 回归与分类

**回归**模型可预测连续值。例如，预测股价：

**分类**模型可预测离散值。例如，判断是否为垃圾邮件：



## 深入了解机器学习

###线性回归

####模型方程式

$$
y'=b + w_1x_1+w_2x_2+w_3x_3    \\
· y'指的是预测标签（理想输出值）    \\
· b指的是偏差（y 轴截距）。而在一些机器学习文档中，它称为 w_0    \\
· w_1指的是特征 1 的权重。权重与“斜率”的概念相同    \\
· x_1,x_2,x_3指的是特征（已知输入项）
$$



###训练与损失

####平方损失

单个样本的平方损失(y - y')2

#### 均方误差(MSE)

指的是每个样本的平均平方损失。要计算 MSE，请求出各个样本的所有平方损失之和，然后除以样本数量：
$$
MSE = \frac{1}{N} \sum_{(x,y)\in D} (y - prediction(x))^2    \\
· (x,y)指的是样本，其中    \\
· x指的是模型进行预测时使用的特征集。    \\
· y指的是样本的标签。    \\
· prediction(x)指的是权重和偏差与特征集x结合的函数。    \\
· D指的是包含多个有标签样本（即(x,y) ）的数据集。    \\
· N指的是D中的样本数量。
$$
MSE既不是唯一实用的损失函数，也不是适用于所有情形的最佳损失函数 

## 降低损失

### 迭代方法

机器学习系统检查损失函数的值，并为 b 和 w1 生成新值。

通常，可以不断迭代，直到总体损失不再变化或至少变化极其缓慢为止。这时候，我们可以说该模型已收敛。

### 梯度下降法

梯度下降法算法会沿着负梯度的方向走一步，以便尽快降低损失

### 学习速率

梯度矢量具有方向和大小。梯度下降法算法用梯度乘以一个称为**学习速率**（有时也称为**步长**）的标量 

**超参数**是编程人员在机器学习算法中用于调整的旋钮 

学习速率过小，就会花费太长的学习时间 

学习速率过大 ，永远无法到达最低点

如果知道损失函数的梯度较小，则可以放心地试着采用更大的学习速率，以补偿较小的梯度并获得更大的步长 