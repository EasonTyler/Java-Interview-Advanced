聊**分布式**这块，**Dubbo相关的原理**，**Spring Cloud相关的原理**，有的面试官可能会这样问，你有没有看过**Dubbo或者Spring Cloud的源码呢**？**技术广度**、**技术深度**、**项目经验**、**系统设计**、**基本功**

平时看你简历主要是用一些技术来开发一些系统，就会问问你了，对于一些你平时常用的技术，有没有关注过底层的原理，或者是看过源码，你要是说，90%的人，一般都会在这个时候支支吾吾的说

源码看过一点点，但是没怎么看过

在我们面试训练营里，能给你来分析源码吗？不太现实的，任何一个开源项目，**源码**少则几万行，多则几十万行，**Hadoop、Spark**，**面试训练营**，几讲的时间来讲透任何一个**开源项目**的**源码**，不现实

看源码技巧是有，但是，需要**技术功底**

就是说提炼一些**Dubbo、Spring Cloud**相关的一些底层的运行的原理，给大家来用大白话+现场画图的方式，说清楚，你就可以结合我们视频讲解的内容，去现场画图给面试官画一画一些技术底层的运行的一些原理




分布式系统

拆分为了多个子系统之后，各个系统之间如何通过Spring Cloud服务框架来进行调用，Dubbo框架来进行调用

![Dubbo核心架构原理](/docs/distributed-system/images/dubbo-framework-principle.png)
提供接口

服务注册中心：

###消费者

#### 动态代理：Proxy
#### 负载均衡：Cluster，负载均衡，故障转移
#### 注册中心：Registry
#### 通信协议：Protocol，filter机制，http、rmi、dubbo等协议

#### http、rmi、dubbo

比如说，我现在其实想要调用的是，DemoService里的sayHello接口

你的请求用什么样的方式来组织发送过去呢？以一个什么样的格式来发送你的请求？

http协议，/demoService/sayHello?name=leo
rmi，另外一种样子
dubbo协议，interface=demoService|method=sayHello|params=name:leo

信息交换：Exchange，Request和Response

对于你的协议的格式组织好的请求数据，需要进行一个封装，Request

##### 网络通信：Transport，netty、mina
##### 序列化：封装好的请求如何序列化成二进制数组，通过netty/mina发送出去

提供者

#### 网络通信：Transport，基于netty/mina实现的Server
#### 信息交换：Exchange，Response
#### 通信协议：Protocol，filter机制
#### 动态代理：Proxy
