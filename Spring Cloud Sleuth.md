> https://cloud.spring.io/spring-cloud-sleuth/reference/html/#purpose

# 1. 介绍

Cloud Sleuth 是针对Spring Cloud生态的分布式链路跟踪解决方案的一种实现。

## 1.1 术语

Sleuth 借用了 Google Dapper 框架里面的术语。论文链接（http://bigbully.github.io/Dapper-translation/）

- 相关文档- https://zhuanlan.zhihu.com/p/41047837
- https://www.jianshu.com/p/da0203e09ca0

### span

工作的基础单元。例如：我们发送一个RPC请求和发送一个RPC响应都是一个新的span。span通过一个64位的ID唯一标识。span作为trace的一部分。trace也被一个64位的ID唯一标识。spans还包含其他的数据，比如: 描述、时间戳事件、键值对注解(标签)、导致生成span的ID以及进程ID(通常是IP地址)。

spans能被启动和停止。并且他们保持记录时间信息。一旦你创建了一个span，你必须在未来某个时间点停止它。

初始化的span被叫做root span，标志着一段链路trace的开始。root span的ID和 TraceID 一致。

### **Trace**

通过一系列span形成树状结构。例如，如果您运行一个分布式大数据存储，那么可能会通过一个PUT请求形成一个跟踪。



### **Annotation**

用来记录某一事件在时间上的存在。通过Brave仪表库（Brave是一个分布式跟踪仪表库），我们不再需要为Zipkin设置特殊的事件来了解客户机和服务器是谁、请求在哪里开始、在哪里结束。但是，为了便于学习，我们标记这些事件以突出显示发生了什么操作。

- **cs**: 客户端发送请求。表示span的开始。
- **sr**: 服务端接收请求然后开始处理它。接收时间戳减去**cs**的时间戳表示当前的网络延迟
- **ss**: 服务端发送返回数据。当服务端将请求处理完毕，即将发送响应数据给客户端。当前时间戳减去**sr**时间戳表示服务端处理请求消耗的时间。
- **cr**: 客户端接收服务端响应数据。标志着span的结束。客户端成功接收到了服务端返回的数据。当前时间减去**cs**的时间戳表示从客户端接收服务端响应的整体时间。



## 1.2 设计目的



## 1.3 添加Slueth到项目



## 1.4 覆盖Zipkin的自动配置

