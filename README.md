# 📝 Journal App

The Journal App is a secure and feature-rich web application built with Spring Boot and MongoDB. It allows users to create, manage, and analyze daily journal entries with additional features like weather updates and sentiment analysis.

Designed with scalability, performance, and modern backend practices in mind, this application incorporates advanced tools such as Redis caching, Kafka for asynchronous communication, JWT-based security, and scheduled tasks for automation.

## ✨ Features

### 🔐 User Authentication & Authorization
- Secure user registration and login using JWT (JSON Web Token).
- Role-based access control for Admins and regular Users.

### 📓 Journal Entry Management
- Create new journal entries with title, content, and timestamps.
- Retrieve all journal entries for a specific user.
- View individual journal entries by ID.
- Update and delete existing entries.

### 👤 User Management
- Users can update their profile or delete their account.
- Admins can:
  - View all registered users.
  - Create new admin accounts.

### 😊 Sentiment Analysis
- Optional automatic analysis of journal entry sentiment (positive, negative, neutral).
- Weekly sentiment summary reports sent via email.

### 🌦 Weather Integration
- Displays the current weather for the user’s configured city upon login.

### ⚡ Caching
- Redis is used to cache frequently accessed data to improve performance.

### 📨 Asynchronous Processing
- Kafka is used to handle tasks like sending emails without blocking the main flow.

### ⏱ Scheduled Tasks
- Weekly automated tasks to:
  - Send sentiment reports to users.
  - Clear application-level caches.

### 📘 API Documentation
- Fully interactive Swagger UI to explore and test all API endpoints.

## 🔧 Technologies Used

### 🖥 Backend
- **Java 17**
- **Spring Boot 3.3.11**
- **Spring Data MongoDB** – for database operations.
- **Spring Security** – for authentication and authorization.
- **Spring Mail** – for email services.
- **Spring Kafka** – for asynchronous event handling.
- **Spring Data Redis** – for caching.
- **JJWT** – JSON Web Token implementation for security.
- **Jackson** – for JSON serialization/deserialization.
- **Lombok** – to reduce boilerplate code.
- **Swagger (SpringDoc OpenAPI)** – for API documentation.

### 🗃 Database & Caching
- **MongoDB** – primary NoSQL database.
- **Redis** – in-memory data store for caching.

### 📩 Messaging & Event Streaming
- **Apache Kafka** – for asynchronous communication and task delegation.

### 📦 Build Tool
- **Maven** – project build and dependency management.

## 🚀 Getting Started

Follow these instructions to set up the Journal App on your local machine for development or testing.

---

### ✅ Prerequisites

Make sure the following tools and services are installed and running:

- **Java Development Kit (JDK)** – Version 17 or higher
- **Maven** – Version 3.6.0 or higher
- **MongoDB** – Local instance or MongoDB Atlas
- **Redis** – Running on localhost or remote
- **Apache Kafka** – With Zookeeper
- **SMTP Email Service** – For example, Gmail (requires app-specific password)
- **Weather API Key** – From a service like WeatherStack or OpenWeatherMap

---

### 📥 Installation

1. **Clone the repository**

```bash
git clone <repository-url>
cd journalApp

2.Configure application properties

Create a file named application-dev.properties in src/main/resources/ and populate it with the following configuration:
```
## ⚙️ Configuration

Create or edit `src/main/resources/application-dev.properties` with the following content:

```properties
# ----------------------------
# MongoDB Configuration
# ----------------------------
spring.data.mongodb.uri=mongodb+srv://<username>:<password>@cluster.mongodb.net/journalApp

# ----------------------------
# Redis Configuration
# ----------------------------
spring.data.redis.host=localhost
spring.data.redis.port=6379

# ----------------------------
# Kafka Configuration
# ----------------------------
spring.kafka.bootstrap-servers=<your-kafka-bootstrap-server>
spring.kafka.properties.sasl.mechanism=PLAIN
spring.kafka.properties.security.protocol=SASL_SSL
spring.kafka.properties.sasl.jaas.config=org.apache.kafka.common.security.plain.PlainLoginModule required username="<kafka-api-key>" password="<kafka-api-secret>";
spring.kafka.producer.value-serializer=org.springframework.kafka.support.serializer.JsonSerializer
spring.kafka.consumer.value-deserializer=org.springframework.kafka.support.serializer.JsonDeserializer
spring.kafka.consumer.auto-offset-reset=latest
spring.kafka.consumer.enable-auto-commit=false
spring.kafka.listener.ack-mode=RECORD

# ----------------------------
# Email Configuration (Gmail Example)
# ----------------------------
spring.mail.host=smtp.gmail.com
spring.mail.port=587
spring.mail.username=<your-email>
spring.mail.password=<your-app-password>
spring.mail.properties.mail.smtp.auth=true
spring.mail.properties.mail.smtp.starttls.enable=true

# ----------------------------
# Weather API Configuration
# ----------------------------
weather.api.key=<your-weather-api-key>

# ----------------------------
# Application-wide Configuration (MongoDB config_journal_app collection)
# ----------------------------
# Example entry: { "key": "WEATHER_API", "value": "http://api.weatherstack.com/current?access_key=<apiKey>&query=<city>" }

```

## ▶️ Running the Application

Once you've configured everything and built the project, you can start the application using Maven:

```bash
mvn spring-boot:run
```
## 📘 API Documentation

The Journal App provides interactive API documentation using **Swagger UI**.

Once the application is running, you can access the Swagger interface at:

**http://localhost:8080/swagger-ui.html**

This interface allows you to:
- Browse available endpoints
- View request and response formats
- Try out API calls directly from the browser


By default, the application will start at:
```
http://localhost:8080
```
If everything is configured properly, you should see the application running and ready to serve API requests.

## 🧪 Testing

The Journal App includes unit tests and integration tests to ensure application reliability and correctness.

To run all tests:

```bash
mvn test
```
## 📝 License

This project is licensed under the **MIT License**.  
You are free to use, modify, and distribute it under the terms of this license.

See the [LICENSE](LICENSE) file for full details.

## 📬 Contact

For any questions, feedback, or collaboration opportunities, feel free to reach out:

**SaiRam**  
📧 Email: [mugala.sairam@gmail.com](mailto:mugala.sairam@gmail.com)

---


