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
