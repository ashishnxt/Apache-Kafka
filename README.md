# Apache Kafka
## 📘 Overview
Apache Kafka is a **distributed event streaming platform** capable of handling trillions of events a day. It was originally developed at LinkedIn and later open-sourced through the Apache Software Foundation. Kafka is designed for high throughput, fault tolerance, horizontal scalability, and low latency.

Kafka provides:

- **Publish and subscribe to streams of records** in a fault-tolerant way.
- **Store streams of records** durably.
- **Process streams of records** as they occur.
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

