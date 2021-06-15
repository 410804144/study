### 安装jdk1.8

### 下载kafka
- 访问地址：http://kafka.apache.org/downloads
- 获取binary下载地址
- 进入centos中，使用wget下载

### 安装kafka
- 解压
```shell
tar -xzvf kafka_2.12-2.4.0.tgz
```

- 启动zookeeper
```shell
nohup ./bin/zookeeper-server-start.sh config/zookeeper.properties >> zookeeper.nohup &
```

- 检查zookeeper是否已经启动
```shell
ps -ef|grep zookeeper
```

- 启动kafka
```shell
nohup ./bin/kafka-server-start.sh config/server.properties >> kafka.nohup &
```

# 测试功能
- 创建一个名为test的topic，只有一个副本，一个分区
```shell
sh bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic test
```

- 查看已经创建的topic
```shell
sh bin/kafka-topics.sh -list -zookeeper localhost:2181
```

- 启动producer
```shell
sh bin/kafka-console-producer.sh --broker-list localhost:9092 --topic test
```

- 启动consumer，在另一个终端窗口执行
```shell
sh bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test --from-beginning
```

- 在producer窗口输入消息内容
- 在consumer查看输出的消息内容
- 验证通过，安装成功
