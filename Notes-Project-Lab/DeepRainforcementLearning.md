## A Deep Reinforcement Learning-Enabled Dynamic Redeployment System for Mobile Ambulences

#### 标题：

基于深度强化学习的移动救护车动态部署系统

#### 关键词：

移动计算、城市计算、深度强化学习、<font color = red>深度评分网络</font>、动态部署

#### 摘要：

为了减少病人的等待时间，他们提出了一种动态救护车部署的系统。

1. 需要考虑车站的一些动态因素，他们使用深度神经网络（深度评分系统）来权衡这些不定因素。
2. 基于已经学好的深度评分网络，他们提出了有效的救护车部署算法。

算法优势：比一般的baseline节省100s(20%)，提高病人10min内被接上的比例（0.786--->0.838）

#### 结论：

深度评分网络  +  深度强化学习算法  =  动态部署算法

接病人的时间减少

未来：深度评分网络可应用于其他的顺序决策问题[sequential decision making problem]，例如，出租车调度[dispatch]，食品运输调度[food carrier dispatch]，快递运输调度。

**dispatch** and **redeploy** ambulances using deep score networks【多任务强化学习问题】1. 需要两个评分网络 2. 用两个评分网络的多任务强化学习 3.调度问题的参数设置

#### introduce：

dynamic fasctors:

1. 哪里人多往哪走：考虑到未来一段时间内车站附近活跃的病人数
2. 哪里车少去哪里：考虑每一个车站当前拥有的车辆数
3. 离哪里近去哪里：考虑车当前位置到车站路上花费的时间
4. 考虑其他备用的车的当前状态

很多方法将好几种因素整合到一个指标indicators，车站覆盖率是最广泛使用的一个

他们做的主要贡献：

1. 深度评分网络【深度神经网络】：整合所有的动态因素，针对每一个车站给出评分
2. 深度强化学习框架【策略梯度算法】--->深度评分网络。无监督学习
3. 真实数据实验时间效果很好；加入其它因素之后，鲁棒性也很好

#### 详细介绍

1. 多因素整合成分数

激活函数：如果没有激活函数，相当于f(x)=x，隐藏层和上一层的关系就是线性关系，所以无论有多少个隐藏层，都是没有用的，相当于矩阵相乘。所以使用非线性函数作为激励函数深层网络就有意义了，可以增加网络模型的非线性。

![1571731375683](../../图片/1571731375683.png)

1. 深度评分网络
2. 重新部署









