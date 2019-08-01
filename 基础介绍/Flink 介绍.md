# Flink 介绍

![0717Flink基础](/Users/xiaotong/Documents/Digital_China/日报/0717Flink基础.png)

### 资料来源

1. [https://flink.apache.org/flink-architecture.html](https://flink.apache.org/flink-architecture.html)
1. 《Flink原理、实战与性能优化》
3. [https://github.com/flink-china/flink-training-course](https://github.com/flink-china/flink-training-course)
### ** Apache Flink的定义、架构、应用与运维**
> Apache Flink 是一个框架和分布式处理引擎，用于在_无边界和有边界_数据流上进行有状态的计算。Flink 能在所有常见集群环境中运行，并能以内存速度和任意规模进行计算。

#### 架构

- 擅长处理有界和无界的数据集，通过精确的时间控制和状态化运行任何处理无界流的应用。有界流则由一些专为固定大小数据集特殊设计的算法和数据结构进行内部处理。
- 是一个分布式系统，需要计算资源来执行应用程序，集成了Hadoop YARN、 Apache Mesos 和Kubernetes等集群资源管理器，也可以作为独立集群运行。
- Flink旨在任意规模上运行有状态流式应用。应用程序被并行化为可能数千个任务，这些任务分布在集群中并发执行。能够充分运用资源，而且易于维护，通过异步和增量的检查点算法对处理延迟产生最小的影响，同时保证精确一次状态的一致性。
- 有状态的 Flink 程序针对本地状态访问进行了优化。任务的状态始终保留在内存中。 Flink 通过定期和异步地对本地状态进行持久化存储来保证故障场景下精确一次的状态一致性。
#### 应用

- 流处理的基本组件：流（有界流和无界流）、状态（Flink中的first-class
citizen）、时间（Event Time / Processing Time / Ingestion Time）
- 分层API：根据抽象程度分层，提供了三种不同API ，由上至下抽象程度降低，表达能力增强。如ProcessFunction 层 API 的表达能力非常强，可以进行多种灵活方便的操作，但抽象能力也相对越小。

#### 运维（待完善）

- Flink 具备 7 X 24 小时高可用的面向服务的架构
- Flink 本身提供监控、运维等功能或接口
### 应用场景
#### 事件驱动应用
> 事件驱动型应用会受制于底层流处理系统对时间和状态的把控能力，它提供了一系列丰富的状态操作原语，允许以精确一次的一致性语义合并海量规模的状态数据。Flink
> 还支持事件时间和自由度极高的定制化窗口逻辑，而且它内置的
> ProcessFunction 支持细粒度时间控制，方便实现一些高级业务逻辑。同时，Flink 还拥有一个复杂事件处理（CEP）类库，可以用来检测数据流中的模式。

典型的应用实例有反欺诈、异常检测、业务流程报警等。

![屏幕快照 2019-07-17 下午5.38.33](/Users/xiaotong/Desktop/屏幕快照 2019-07-17 下午5.38.33.png)

#### 数据分析应用
Flink对持续的批量处理和流式处理都提供了良好的支持。典型的应用实例有电信网络质量监控、实时大屏、实时报表等。

![屏幕快照 2019-07-17 下午5.49.00](/Users/xiaotong/Desktop/屏幕快照 2019-07-17 下午5.49.00.png)

#### 数据管道应用

> 很多常见的数据转换和增强操作可以利用 Flink 的 SQL 接口（或 Table API）及用户自定义函数解决。

应用实例有搜索引擎推荐、实时数仓。

![屏幕快照 2019-07-17 下午5.53.13](/Users/xiaotong/Desktop/屏幕快照 2019-07-17 下午5.53.13.png)