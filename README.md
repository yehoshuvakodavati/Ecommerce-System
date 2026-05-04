# Ecommerce-System

# Kafka Setup - Day 1

## What I Did

- Installed Docker
- Set up Kafka and ZooKeeper using Docker Compose
- Created a Kafka topic
- Tested producer and consumer

## Commands Used

- docker-compose up -d
- kafka-topics --create
- kafka-console-producer
- kafka-console-consumer

## Tech Used

- Kafka
- ZooKeeper
- Docker

# 🛒 Order Service - Day 2 (Kafka Producer)

## 📌 Overview

This project is part of a real-world backend system where an Order Service sends events to Kafka.

The service exposes a REST API that accepts order data and publishes it to a Kafka topic. This simulates how modern e-commerce systems handle asynchronous communication between services.

---

## 🏗️ Architecture

Client → Spring Boot API → Kafka Producer → Kafka Topic → Consumer

---

## ⚙️ Tech Stack

- Java
- Spring Boot
- Apache Kafka
- Apache ZooKeeper
- Docker
- Maven

---

## 🚀 Features

- REST API to create orders
- Kafka Producer using KafkaTemplate
- Sends order data to Kafka topic (`order-topic`)
- Event-driven communication
- Fully integrated with Docker-based Kafka setup

---

## 📂 Project Structure

src/main/java/com/ecommerce/orderservice
┣ controller → Handles API requests
┣ service → Kafka producer logic
┗ OrderServiceApplication.java

---

## 📡 API Endpoint

### Create Order

POST /orders

Request Body:

```json
{
  "orderId": "101",
  "productName": "Laptop"
}
```

Response:

```
Order sent to Kafka
```

---

## 🔄 How It Works

1. Client sends POST request to `/orders`
2. Controller receives request
3. OrderProducer sends message to Kafka
4. Kafka stores message in `order-topic`
5. Consumer reads the message

---

## 🧪 Testing

### Start Kafka (Docker)

```
docker-compose up -d
```

### Start Consumer

```
kafka-console-consumer --topic order-topic --bootstrap-server localhost:9092
```

### Send Request

```
curl -X POST http://localhost:8080/orders -H "Content-Type: application/json" -d "{\"orderId\":\"101\",\"productName\":\"Laptop\"}"
```

---

## 📥 Sample Output (Kafka Consumer)

```
{"orderId":"101","productName":"Laptop"}
```

---

## 🧠 Key Learnings

- Setting up Kafka using Docker
- Creating and managing Kafka topics
- Implementing Kafka Producer in Spring Boot
- Sending events from REST API to Kafka
- Understanding event-driven architecture

---

## 🎯 Next Steps

- Build Inventory Service (Kafka Consumer)
- Process incoming order events
- Store data in database
- Expand into full microservices architecture

---

## 💡 Summary

This project demonstrates how backend services communicate asynchronously using Kafka. It is a foundational step toward building scalable, real-world systems like e-commerce platforms.

---
