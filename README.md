# Tutorial for the Kafka Streams
See http://kafka.apache.org/24/documentation/streams/tutorial for reference.

## things to run first
1. Download and untar the kafka tar ball for the scala version being used
2. Start zookeeper: `/bin/zookeeper-server-start.sh config/zookeeper.properties`
3. Start the kafka binary for the default config (and port): `./bin/kafka-server-start.sh config/server.properties`
4. Create the two topics `bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic streams-plaintext-input`
5. Get producers to produce the two topics: `bin/kafka-console-producer.sh --brokelist localhost:9092 --topic streams-plaintext-input`
6. Have a consumer be ready: `bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic streams-wordcount-output --from-beginning --formatter kafka.tools.DefaultMessageFormatter --property print.key=true --property print.value=true --property key.deserializer=org.apache.kafka.common.serialization.StringDeserializer --property value.deserializer=org.apache.kafka.common.serialization.LongDeserializer`
