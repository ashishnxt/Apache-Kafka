# Apache Kafka 
## 📘 Overview
Apache Kafka is a **distributed event streaming platform** capable of handling trillions of events a day. It was originally developed at LinkedIn and later open-sourced through the Apache Software Foundation. Kafka is designed for high throughput, fault tolerance, horizontal scalability, and low latency.

Kafka provides:

- **Publish and subscribe to streams of records** in a fault-tolerant way.
- **Store streams of records** durably.
- **Process streams of records** as they occur.
## Prerequisite
- Knowledge
    - Node.JS Intermediate level
    - Experience with designing distributed systems
- Tools
    - Node.js: [﻿Download Node.JS](https://nodejs.org/en) 
    - Docker: [﻿Download Docker](https://www.docker.com/) 
    - VsCode: [﻿Download VSCode](https://code.visualstudio.com/) 


---

## 📌 Key Concepts Explained
### 1. **Producer**
A producer sends data (also called records or messages) into Kafka topics. Each message consists of a **key**, a **value**, and **optional metadata** (headers, timestamp, etc.).

### 2. **Consumer**
A consumer subscribes to one or more topics and processes the published records. Consumers track their position (offset) in each partition they read.

### 3. **Topic**
A topic is a category or feed name to which records are published. Kafka topics are **append-only logs**, and they can have multiple **partitions**.

### 4. **Partition**
Each topic can be split into partitions, which are ordered, immutable sequences of records. Each record in a partition is assigned a unique **offset**.

- Partitions allow Kafka to scale horizontally and offer parallelism.
### 5. **Broker**
A Kafka server that stores data and serves clients. A cluster typically has multiple brokers, each managing a subset of partitions.

### 6. **Consumer Group**
A group of consumers that collectively consume messages from a topic. Kafka ensures each partition is consumed by only one consumer in a group.

### 7. **Zookeeper**
Zookeeper manages Kafka brokers by maintaining cluster metadata and performing leader elections. Kafka is transitioning to **KRaft mode** (Kafka Raft Metadata mode) to eliminate the need for Zookeeper.

---

## ⚙️ Kafka Setup Using Docker
### 📦 Docker Compose for Kafka + Zookeeper

```
version: "3"
services:
    zookeeper:
        image: zookeeper
        container_name: zookeeper
        ports:
            - "2181:2181"
    kafka:
        image: confluentinc/cp-kafka
        depends_on:
            - zookeeper
        ports:
            - "9092:9092"
        expose:
            - "29092"
        environment:
            KAFKA_ZOOKEEPER_CONNECT: "zookeeper:2181"
            KAFKA_LISTENER_SECURITY_PROTOCOL_MAP: PLAINTEXT:PLAINTEXT,PLAINTEXT_HOST:PLAINTEXT
            KAFKA_INTER_BROKER_LISTENER_NAME: PLAINTEXT
            KAFKA_ADVERTISED_LISTENERS: PLAINTEXT://kafka:29092,PLAINTEXT_HOST://localhost:9092
            KAFKA_OFFSETS_TOPIC_REPLICATION_FACTOR: "1"
            KAFKA_MIN_INSYNC_REPLICAS: "1"
    kafka-ui:
        container_name: kafka-ui
        image: provectuslabs/kafka-ui
        ports:
            - 8080:8080
        environment:
            DYNAMIC_CONFIG_ENABLED: true
```


![diagram-export-29-6-2025-11_43_53-am](https://github.com/user-attachments/assets/db80dbc5-88cd-40d7-8583-033f73ac3a02)


