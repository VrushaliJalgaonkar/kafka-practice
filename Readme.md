# Kafka understanding
Apache Kafka is an open-source distributed event streaming platform designed for high-throughput, fault-tolerant, and scalable real-time data streaming. It is used to handle large volumes of data and enables applications to communicate through event-driven architecture.

## Easy flow understanding:
<img src="images/kafka-simple-understanding.png" alt="Description" width="800" height="500">

## Kafka components
1. Producer: Publishes (writes) data to Kafka topics.
2. Topic: A category or feed where records are stored.
3. Partition: Topics are split into partitions to allow parallel processing.
4. Broker: A Kafka server that stores data and serves client requests.
5. Cluster: Group of multiple Kafka brokers working together to distribute, replicate, and manage event streaming data
6. Consumer: Reads data from Kafka topics.
7. Consumer Group: A group of consumers working together to read data.
8. Zookeeper: Manages metadata and leader election for Kafka brokers.
9. Offset: A unique identifier that tracks the position of a message within a partition

## Kafka architecture
<img src="images/full-kafka-architecture.png" alt="Description" width="800" height="500">

# Why Use Kafka?
* High Throughput & Low Latency – Handles millions of messages per second.
* Scalability – Can scale horizontally by adding brokers.
* Durability & Fault Tolerance – Data is replicated across multiple brokers.
* Real-time Data Streaming – Ideal for event-driven systems.
* Decoupling of Services – Microservices use Kafka to communicate asynchronously.

## Common Use Cases
* Real-time analytics and monitoring (e.g., logs, metrics)
* Messaging systems (like a pub-sub model)
* Microservices communication
* Event-driven architecture
* ETL pipelines and data lake ingestion



## The flow of Kafka is as follows,
1. Start Zookeeper, default port = 2181
2. Start Kafka, default port = 9092
3. Create topic

# Install Kafka using Docker
1. Create [docker-compose.yml](/docker-compose.yml)
2. Run docker compose to pull zookeeper and kafka images
```bash
docker compose -f docker-compose.yml up -d
```
3. Check if services are pulled successfully
```bash
docker images
```
**Expected Output:**
```bash
REPOSITORY               TAG       IMAGE ID       CREATED       SIZE
wurstmeister/kafka       latest    db97697f6e28   2 years ago   457MB
wurstmeister/zookeeper   latest    3f43f72cb283   6 years ago   510MB
```
```bash
docker ps
```
**Expected Output:**
```bash
CONTAINER ID   IMAGE                    COMMAND                  CREATED          STATUS          PORTS                                                NAMES
8037f3fe330e   wurstmeister/kafka       "start-kafka.sh"         21 minutes ago   Up 20 minutes   0.0.0.0:9092->9092/tcp                               kafka
cfdc17a3e7bd   wurstmeister/zookeeper   "/bin/sh -c '/usr/sb…"   21 minutes ago   Up 20 minutes   22/tcp, 2888/tcp, 3888/tcp, 0.0.0.0:2181->2181/tcp   zookeeper
```
4. Enter inside kafka container
```bash
docker exec -it kafka /bin/sh
```



