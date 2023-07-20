# Kafka_ApacheKafkaSeries_LearnApachKafkaForBeginnersV3

## Example code
- https://github.com/conduktor/kafka-beginners-course


## Kafka Topics
- Topics: a particular stream of data
   + Like a table in database
   + I can have as many topics as I want
   + A topic is identifed by its name
   + Any kind of message format
   + The sequence of message is called a data stream
   + I can't query topics, instead use Kafka Producers to send data and Kafa Consumers to read the data
   + Topics are split in partitions
      - Messages within each partition are ordered
   + Kafka topics are **immutable**: once data is written to a partition, it cannot be changed
   + Data is kept only for a limited time. (default is one week - configurable)
   + Offset only have a meaning for a specific parition
      - ex) offset 3 in partition 0 doesn't represent the same data as offset 3 in partion 1
      - Offsets are not re-used even if previous messages have been deleted
   + Order is guaranteed only within a partion(not across partitions)
   + Data is assigned randomly to a partition unless a key is provided
   + I can have as many as partitions per topic as I want


## Producers
- write data to topics(which are made of partitions)
- Producers know to which partition to write to (and witch Kafka broker has it)
- In case of Kafka broker failures, Producer will automatically recover
- Message Key
   + Producer can choose to send a key with the message
   + If key == null, data is sent round robin (partition 0, then 1, then2 ...)
   + If key != null, then all messages for that key will always go to the same partition(hashing)
- Kafka Message anatomy
   + key - binary
   + Value - binary
   + compression type
   + Headers (optional)
   + Partition + Offset
   + Timestamp
- Kafka Message Serializer
   + Kafka only accepts bytes as an input from producers and sends bytes out as an output to consumers
   + Transform objects/data into bytes
   + They are used on the value and the key

## Consumers
- Consumers read data from a topic (identified by name) - pull model
- Consumers automatically know which broker to read from
- In case of broker failures, consumers know how to recover
- Data is read in order from low to high offset **within each partitions**
- Consumer Deserializer
   + Deserialize indicates how to transform bytes into objects / data
   + They are used on the value and the key of the message
   + The serialization / deserialization type must not change during a topic lifecycle (create a new topic instead)

### Consumer Groups
- All the consumers in an application read data as a consumer groups
- In Kafka it is acceptable to have multiple consumer groups on the same topic

### Consumer Offsets
- Kafka stores the offsets at which a consumer group has been reading
- The offsets committed are in Kafka topic named **__consumer_offsets**


### Delivery semantics for consumers
- Java Consumers will automatically commit offsets
- There are 3 delivery semantics if you choose to commit manually
- At least once(usually preferred)
   + Offsets are committed afte the message is processed
   + If the processing goes wrong, the message will be read again
- At most once
   + Offsets are committed as soon as messages are received
   + If the processing goes wrong, some messages will be lost
- Exactly once
   + Kafka workflows: use the Transactional API
 
## Kafka Brokers
- A Kafka cluster is composed of multiple brokers(servers)
- Each broker is identified with its ID(Integer)
- Each broker contains certain topic partitions








## How to install
- at least jdk11
- install using brew














