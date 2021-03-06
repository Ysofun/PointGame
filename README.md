# 《点点点》实现与算法重构
**《点点点》游戏是一款的简单生成敌人，通过鼠标点击，击杀的敌人的项目。**

***

该项目包含了：
* 最佳分数
* 计分规则：点错一次扣 5 分，点对一次得 10 分
* 增加倒计时 10 秒
* 计分规则：倒计时每剩余 1 秒得 10 分
* 每次点击方块，都有一定概率获得 1 ~ 3 金币
* 1 金币可以在游戏开始前购买，抵消点击错误的次数
* 成就系统
> * 百分成就
> * 手残成就
> * 零失误成就
> * 全成就
* 再来一次功能

***

在实现项目的基础上，参考了QFramework架构的实现，将项目分为了四层：
> * 表现层：Controller层
> * 系统层：System层
> * 数据层：Model层
> * 工具层：Utility层
每一个层级都有一定的规则限制：

**表现层**

> * 可以获取 System
> * 可以获取 Model
> * 可以发送 Command
> * 可以监听 Event

**系统层**

> * 可以获取 System
> * 可以获取 Model
> * 可以监听、发送 Event
> * 可以获取 Utility

**数据层**

> * 可以获取 Utility
> * 可以发送 Event

**工具层**

> * 可以集成第三方库，或者封装 API

***

对象之间的交互通过委托和事件、命令模式进行。事件通过类似于事件中心的方式，进行限制和使用

在模块化方面采用单例和IOC容器混合使用的方式。
