
# Install Java 
- [ ] sudo apt install openjdk-11-jre-headless (installs java)
- [ ] java -version  (verifies and checks java version)
# Edit .bashrc file 
- [ ] nano ~/.bashrc  
- [ ] INPUT " export JAVA_HOME="/usr/lib/jvm/java-11-openjdk-amd64"  ''
- [ ] source .bashrc
# Download Kafka And Extract
- [ ] wget https://downloads.apache.org/kafka/3.7.0/kafka_2.13-3.7.0.tgz  (downloads the file directly from source, or download them via web browser manually if error occurs.)
- [ ] tar -xvzf kafka_2.13-3.7.0.tgz  (extracting the zipped file folder)
# Starting ZooKeeper  and Kafka
## First Terminal 
- [ ] (assuming you're in the kafka directory file)
- [ ] Execute command " ./bin/zookeeper-server-start.sh config/zookeeper.properties "
## Second Terminal
- [ ] ./bin/kafka-server-start.sh config/server.properties
- [ ] 
## Third Terminal 
- [ ] ./bin/kafka-topics.sh --create --topic viva-mapua --bootstrap-server localhost:9092 (This creates the topic in the terminal)
- [ ] ./bin/kafka-console-producer.sh --topic viva-mapua --bootstrap-server localhost:9092 ( This creates the console for messages that you want to broadcast to the consumer)
- [ ] A symbol "> " will appear and enter messages here

## Fourth Terminal 
- [ ] ./bin/kafka-console-consumer.sh --topic viva-mapua --from-beginning --bootstrap-server localhost:9092 (This creates the consumer that will receive the messages that will be typed by the producer, which is in the Third terminal that we created and from the symbol ">"  messages will appear in this terminal)
