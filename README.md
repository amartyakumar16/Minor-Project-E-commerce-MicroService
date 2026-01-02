# E-commerce Microservices Application

## Overview
This project is a scalable **E-commerce application built using Microservices Architecture**.  
Each service is independently deployable and communicates using REST APIs and asynchronous messaging.

---

## Tech Stack
- **Backend:** Java, Spring Boot
- **Microservices:** Spring Cloud
- **Service Discovery:** Eureka Server
- **API Gateway:** Spring Cloud Gateway
- **Database:** MongoDB
- **Messaging Queue:** Apache Kafka
- **Build Tool:** Maven
- **Containerization:** Docker

---

## Microservices Architecture

- **Discovery Server**
  - Service registration and discovery using Eureka

- **API Gateway**
  - Central entry point for all client requests
  - Routes requests to appropriate microservices

- **Product Service**
  - Manages product catalog
  - CRUD operations for products

- **Inventory Service**
  - Tracks product stock availability
  - Verifies inventory before order placement

- **Order Service**
  - Handles order creation
  - Communicates with Inventory Service
  - Publishes order events to Kafka

- **Notification Service**
  - Consumes Kafka messages
  - Sends order confirmation notifications

---

## Communication Flow
1. Client sends request to **API Gateway**
2. Gateway routes request to respective service
3. **Order Service** checks inventory availability
4. Order event is published to **Kafka**
5. **Notification Service** consumes event

---

## How to Run the Project

### Prerequisites
- Java 17+
- Maven
- MongoDB
- Apache Kafka
- Docker (optional)

### Steps
```bash
# Clone the repository
git clone <your-repo-url>

# Start Discovery Server
cd discoveryServer
mvn spring-boot:run

# Start API Gateway
cd apigateway
mvn spring-boot:run

# Start remaining services
mvn spring-boot:run
