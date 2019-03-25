知乎文章链接：https://zhuanlan.zhihu.com/p/58642177
对比文章摘要如下：
DolphinDB和MongoDB都是为大数据而生的数据库。但是两者有这较大的区别。前者是列式存储的多模型数据库，主要用于结构化时序数据的高速存储、查询和分析。后者是文档型的NoSQL数据库，可用于处理非结构化和结构化的数据，可以根据键值快速查找或写入一个文档。MongoDB有着自己最合适的应用场景。但是市场上缺少优秀的大数据产品，不少用户试图使用MongoDB来存储和查询物联网和金融领域的结构化时序数据。本测试的目的是评估MongoDB是否适合此类海量时序数据集。

时间序列数据库DolphinDB和MongoDB在时序数据库集上的对比测试，主要结论如下：

DolphinDB的数据导入速度比MongoDB高出两个数量级。数据量越大，性能差距越明显。数据导出方面，DolphinDB比MongoDB快50倍左右。
磁盘空间占用方面，MongoDB占用磁盘是DolphinDB的2~ 3倍。
数据库查询性能方面，DolphinDB在4个查询性能测试中速度比MongoDB快30倍；在5个查询性能测试中速度比MongoDB快10 ~30倍；在12个查询性能测试中速度比MongoDB快数倍；仅在两个点查询测试中，DolphinDB慢于MongoDB。
1. 测试环境
本次测试在单机上进行，测试设备配置如下：

主机：DELL OptiPlex 7060

CPU：Intel(R) Core(TM) i7-8700 CPU@3.20GHZ，6核12线程

内存：32 GB (8GB x 4, 2,666 MHz)

硬盘： 2T HDD (222MB/s读取；210MB/s写入)

OS：Ubuntu 18.04 LTS

DolphinDB选用Linux0.89作为测试版本，所有节点最大连接数为128，数据副本设置为2，设置1个控制节点，1个代理节点，3个数据节点。

MongoDB选用Linux4.0.5社区版作为测试版本，shard集群线程数为12，所有服务器的最大连接数均为128。MongoDB的shard集群设置为1个config服务器，1个mongos路由服务器，3个分片服务器，其中config服务器设置为有1个主节点和2个从节点的replica集群，3个分片服务器均设置为有1个主节点，1个从节点，1个仲裁节点的replica集群。DolphinDB和MongoDB的参数配置请参考附录1。

