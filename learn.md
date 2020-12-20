1. 环境准备
   将 distribution 目录下的 distribution/conf/broker.conf,distribution/conf/logback_broker.xml,distribution/conf/logback_namesrv.xml
   复制到指定路径下, 并将路径记住、待会儿使用
   eg. 我的是 `/Users/xx/build/rocketmq/conf`
   
2. 修改 broker.conf ,配置如下
  ```
    brokerClusterName = DefaultCluster
    brokerName = broker-a
    brokerId = 0
    deleteWhen = 04
    fileReservedTime = 48
    brokerRole = ASYNC_MASTER
    flushDiskType = ASYNC_FLUSH
    # 存储路径
    storePathRootDir=/Users/xx/build/rocketmq/conf/store
    # commitLog 路径
    storePathCommitLog=/Users/xx/build/rocketmq/conf/store/commitlog
    # 消费队列存储路径
    storePathConsumeQueue=/Users/xx/build/rocketmq/conf/store/consumequeue
    # 消息索引存储路径
    storePathIndex=/Users/xx/build/rocketmq/conf/store/index
    # checkePoint 文件存储路径
    storeCheckpoint=/Users/xx/build/rocketmq/conf/store/checkpoint
    # abort 文件存储路径
    abortFile=/Users/xx/build/rocketmq/conf/store/abort
  ```

3. 启动nameServer
   执行之前先修改一下配置文件，增加 Environment variables:
   ROCKETMQ_HOME=/Users/nj/build/rocketmq

4. 启动broker
   4.1 执行之前先修改一下配置文件，增加 Environment variables:
       ROCKETMQ_HOME=/Users/nj/build/rocketmq
   4.2 增加参数
       -c /Users/nj/build/rocketmq/conf/broker.conf -n localhost:9876 autoCreateTopicEnable=true   
       
5. 找到 example 包中的 quickstart 开始我们的测试
   将Consumer 和 Producer 中的 nameServer地址修改为 "127.0.0.1:9876", 然后分别启动.
          