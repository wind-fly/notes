
<!-- TOC -->

- [监听Topic](#监听topic)

<!-- /TOC -->

## 监听Topic
``` bash 
# 生产数据
bin/kafka-console-producer.sh --broker-list 192.168.32.43:9092,192.168.32.44:9092,192.168.32.45:9092 --topic ITOA_TO_HUB_REQ


bin/kafka-console-producer.sh --broker-list 192.168.32.43:9092,192.168.32.44:9092,192.168.32.45:9092 --topic wind006

# 消费数据
bin/kafka-console-consumer.sh --bootstrap-server 192.168.32.43:9092,192.168.32.44:9092,192.168.32.45:9092  --topic fly101 --from-beginning


bin/kafka-console-consumer.sh --bootstrap-server 192.168.32.43:9092,192.168.32.44:9092,192.168.32.45:9092  --topic ITOA_TO_HUB_RSP

# 创建topic

# config.storage.topic=connect-configs
$ bin/kafka-topics.sh --create --zookeeper 192.168.32.43:2181,192.168.32.44:2181,192.168.32.45:2181 --topic eoi-connect-configs2 --replication-factor 3 --partitions 1 --config cleanup.policy=compact

# offset.storage.topic=connect-offsets
$ bin/kafka-topics.sh --create --zookeeper 192.168.32.43:2181,192.168.32.44:2181,192.168.32.45:2181 --topic eoi-connect-offsets2 --replication-factor 3 --partitions 50 --config cleanup.policy=compact

# status.storage.topic=connect-status
$ bin/kafka-topics.sh --create --zookeeper 192.168.32.43:2181,192.168.32.44:2181,192.168.32.45:2181 --topic eoi-connect-status2 --replication-factor 3 --partitions 10 --config cleanup.policy=compact

eoi-connect-configs2
eoi-connect-offsets2
eoi-connect-status2

```

