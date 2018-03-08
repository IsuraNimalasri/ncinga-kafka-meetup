

### Zookeeper Start 
```
./bin/zookeeper-server-start.sh config/zookeeper.properties
```


# Single Broker
### Broker 0 start 
```
./bin/kafka-server-start.sh config/server-0.properties 
```

### Create a topic 
./bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic ncinga

### List of topics
bin/kafka-topics.sh --list --zookeeper localhost:2181

### topic Describe
bin/kafka-topics.sh --describe --zookeeper localhost:2181 --topic ncinga

### Send Message from producer 
bin/kafka-console-producer.sh --broker-list localhost:9092 --topic ncinga

### Start Consumers
bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic ncinga --from-beginning



# Multiple Brokers 

### Broker 0 start 
./bin/kafka-server-start.sh config/server-0.properties 

### Broker 1 start 
./bin/kafka-server-start.sh config/server-1.properties

### Broker 2 start 
./bin/kafka-server-start.sh config/server-2.properties  

### Create a topic 
./bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 3 --partitions 1 --topic ncinga-replica

### Topic Describe
bin/kafka-topics.sh --describe --zookeeper localhost:2181 --topic ncinga--topic ncinga-replica

## Test  replication 

### Kill leader (Linux)
1. ps aux | grep server-1.properties
2. kill -9 7564



