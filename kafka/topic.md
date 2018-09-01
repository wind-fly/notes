
<!-- TOC -->

- [topic](#topic)
- [consumer-group](#consumer-group)
- [consumer](#consumer)
- [producer](#producer)
- [producer-golang](#producer-golang)

<!-- /TOC -->
## topic
``` bash
# 创建topic
bin/kafka-topics --create --zookeeper localhost:2181 --topic connect-configs --replication-factor 3 --partitions 1 

# 查看topic
bin/kafka-topics.sh --zookeeper localhost:2181 --describe --topic windfly001
```
## consumer-group
``` bash
./bin/kafka-consumer-groups.sh --bootstrap-server 192.168.21.11:9092,192.168.21.12:9092,192.168.21.13:9092 --group inputtestgroup  --describe
```
## consumer
``` bash
bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic windfly001

./bin/kafka-console-consumer.sh --zookeeper localhost:2181 --topic TestSimpleParse
```
## producer
``` bash
./bin/kafka-console-producer.sh --broker-list localhost:9092 --topic json_topic

./bin/kafka-console-producer.sh --broker-list localhost:9092 --topic ITOA_TO_PM_REQ --property "parse.key=true" --property "key.separator=:"

./bin/kafka-console-producer.sh --broker-list localhost:9092 --topic ITOA_TO_PM_REQ --property "parse.key=true" --property "key.separator=:"
```
## producer-golang
``` bash
kafka-console-producer-mac

# Minimum invocation
kafka-console-producer -topic=test -value=value -brokers=kafka1:9092

# It will pick up a KAFKA_PEERS environment variable
export KAFKA_PEERS=kafka1:9092,kafka2:9092,kafka3:9092
kafka-console-producer -topic=test -value=value

# It will read the value from stdin by using pipes
echo "hello world" | kafka-console-producer -topic=test

# Specify a key:
echo "hello world" | kafka-console-producer -topic=test -key=key

# Partitioning: by default, kafka-console-producer will partition as follows:
# - manual partitioning if a -partition is provided
# - hash partitioning by key if a -key is provided
# - random partioning otherwise.
#
# You can override this using the -partitioner argument:
echo "hello world" | kafka-console-producer -topic=test -key=key -partitioner=random

# Display all command line options
kafka-console-producer -help
```
