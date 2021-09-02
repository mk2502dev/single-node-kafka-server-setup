# Steps to Setup Single node Apache Kafka Server in Windows

1. Download Apache Kafka binaries [Apache Kafka](https://kafka.apache.org/downloads). And Extract the file.

2. Open CMD and navigate to .\kafka_2.12-2.8.0\bin\windows Folder.

3. Start the Zookeeper (make sure that zookeeper is up and runing)
```
.\zookeeper-server-start.bat ..\..\config\zookeeper.properties
```
4. Open another terminal and start kafka server 
```
.\kafka-server-start.bat ..\..\config\server.properties
```
if you get error while runing kafka server goto config folder and edit server.properties. 
Search for listeners and add the following command `listeners=PLAINTEXT://localhost:9092`
and restart the zookeeper and kafka broker.

5. Create the Topic 
```
.\kafka-topics.bat --create --topic test1 --partitions 1 --replication-factor 1 --bootstrap-server localhost:9092
```
6. Start Kafka producer and send some data
```
.\kafka-console-producer.bat --topic test1 --bootstrap-server localhost:9092
```
7. Start Kafka consumer
```
.\kafka-console-consumer.bat --topic test1 --bootstrap-server localhost:9092 --from-beginning
```
