Elastic-job

任务调度是指系统为了自动完成特定任务，在约定的特定时刻去执行任务的过程。

1）、Elastic-job 当当网基于quartz二次开发的弹性分布式任务调度系统，采用Zookeeper实现分布式协调，实现任务高可用以及分片
2）、Saturn 唯品会开源的一个分布式调度平台，可以全域统一配置，统一监控，实现任务高可用以及分片并发处理。
3）、xxl-job大众点评的分布式任务调度平台，是一个轻量级分布式任务调度平台。
4）、TBSchedule 淘宝非常优秀高性能分布式调度框架

分布式系统具体特点
1、分布性 每个部分都可以独立部署，服务之间交互通过网络进行通信
2、伸缩性 每个部分都可以集群方式部署
3、高可用	每个部分都可以集群部分，保证高可用

分布式调度实现的目标
1、并行任务调度
并行任务调度实现靠多线程。
将任务调度程序分布式部署，每个节点还可以部署为集群。
将任务分割成若干个分片，由不同的实例并行执行

2、高可用
若某一个实例宕机，不影响其他实例来执行任务。

3、弹性扩容
当集群中增加实例就可以提高并执行任务的处理效率。

4、任务管理与检测
对系统中存在的所有定时任务统一的管理及监测。

5、避免任务重复执行
分布式锁


Zookeeper的两个作用
Elastic-job依赖Zookeeper完成对执行任务信息的存储(如任务名称、任务参与实例、任务执行策略等)
Elastic-job依赖Zookeeper实现选举机制，在任务执行实例数量变化时（如在快速上手中的启动新实例或停止实例）
	会触发选举机制来决定让哪个实例去执行该任务。


分片概念
作业分片是指任务的分布式执行，需要将一个任务拆分为多个独立的任务项，然后由分布式的应用实例分别执行某一个或几个分片项。

