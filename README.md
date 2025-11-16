# Farmer Connect – Backend (Spring Boot)

Farmer Connect is a map-based discovery platform that helps people find nearby farmers and the fresh produce they grow.
It is not an e-commerce marketplace — the platform does not provide online ordering, payment, or delivery.
Instead, it acts as a local discovery tool, enabling direct communication between buyers and farmers.

This repository contains the backend services, built using Java + Spring Boot, powering authentication, product listings, geolocation search, comments, wishlist, farmer tools, and more.

> Live Application: https://farmer-connect-web.vercel.app/

> Frontend: https://github.com/anurag-tarai/krushak-sanyog-frontend   

---

## 1. System Architecture Overview

> Diagram Placeholder  
Insert: *High-level System Architecture Diagram (Frontend → Backend → RDS → S3)*

---

## 2. Tech Stack

**Core Frameworks & Libraries**
- Java 17
- Spring Boot 3.1.1
- Spring Security (boot-managed)
- Spring Data JPA

**Cloud & Infra**
- AWS RDS (MySQL)
- AWS S3 (Storage)
- Render (Backend Deployment)
- Vercel (Frontend Deployment)

**Other**
- JWT (jjwt 0.11.5)
- Swagger (springdoc-openapi 2.5.0)
- Lombok 1.18.34
- AWS SDK v2 (2.36.0)
- Maven (with Maven Wrapper)

---

## 3. Software Versions

```
Java: 17
Spring Boot: 3.1.1
MySQL Connector/J: 8.0.33
Spring Security: Managed by Spring Boot
JWT (jjwt): 0.11.5
Swagger (springdoc-openapi): 2.5.0
AWS SDK v2: 2.36.0
Lombok: 1.18.34
Maven: Maven wrapper + recommended local installation
```

---

## 4. Backend Architecture

> Diagram Placeholder  
Insert: *3-Tier / Clean Architecture Diagram*

---

## 5. Features

- 30+ secured RESTful APIs
- JWT Authentication and HttpOnly cookie-based sessions
- Role-based access control
- Farmer profile and marketplace product management
- Image uploads via AWS S3
- Order management flow
- Global exception handling with standardized API responses
- Deployed via a scalable 3-tier architecture (Vercel → Render → AWS RDS → S3)

---

## 6. Project Structure

```
krushak-sanyog-backend/
├── .mvn/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── farmerconnect/
│   │   │       ├── config/         # All app configuration
│   │   │       ├── controller/     # REST controllers
│   │   │       ├── dto/            # Request/Response DTOs
│   │   │       ├── enums/          # Enumerations (e.g. UserRoles)
│   │   │       ├── exception/      # Custom Exceptions & Global handler
│   │   │       ├── model/          # JPA entities
│   │   │       ├── repository/     # Repository layer
│   │   │       ├── security/       # JWT filters & authentication
│   │   │       ├── service/        # Business logic
│   │   │       └── KrushakSanyogApplication.java
│   │   └── resources/
│   │       └── application.properties
│   └── test/
│       └── java/
├── .gitignore
├── Dockerfile
├── pom.xml
└── README.md
```

---

## 7. Configuration (`application.properties`)

### Server
```properties
server.port=8181
```

### AWS RDS
```properties
spring.datasource.url=${RDS_ENDPOINT}
spring.datasource.username=${RDS_USERNAME}
spring.datasource.password=${RDS_PASSWORD}
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQLDialect
```

### HikariCP
```properties
spring.datasource.hikari.maxLifetime=1800000
spring.datasource.hikari.maximum-pool-size=10
spring.datasource.hikari.connection-timeout=30000
spring.datasource.hikari.validation-timeout=5000
spring.datasource.hikari.idle-timeout=600000
```

### AWS S3
```properties
application.bucket.name=${BUCKET_NAME}
cloud.aws.region.static=${AWS_REGION}
cloud.aws.credentials.access-key=${AWS_ACCESS_KEY_ID}
cloud.aws.credentials.secret-key=${AWS_SECRET_ACCESS_KEY}
```

### JPA
```properties
spring.jpa.hibernate.ddl-auto=update
spring.mvc.throw-exception-if-no-handler-found=true
spring.web.resources.add-mappings=false
```

### File Upload
```properties
spring.servlet.multipart.enabled=true
spring.servlet.multipart.max-file-size=20MB
spring.servlet.multipart.max-request-size=20MB
```

### JWT
```properties
jwt.secret=${JWT_SECRET}
jwt.expiration-ms=${JWT_EXPIRATION_MS}
```

---

## 8. API Documentation

Swagger API Docs:

> https://farmerconnect-backend.onrender.com/swagger-ui/index.html


---

## 9. Local Development Setup

### Requirements
- Java 17+
- Maven 3+
- MySQL local or AWS RDS
- AWS S3 Bucket

### Steps
1. Clone the repository:
   ```bash
   git clone https://github.com/anurag-tarai/krushak-sanyog-backend
   ```

2. Configure environment variables

3. Run the backend service:
   ```bash
   mvn spring-boot:run
   ```

---

## 10. Deployment Architecture

> Diagram Placeholder  
Insert: *Render (Backend) → AWS RDS → AWS S3 → Vercel (Frontend)*

---

## 11. Security

- JWT with HttpOnly cookies
- Stateless authentication
- BCrypt password hashing
- Input validation and exception handling
- AWS RDS + S3 secure configuration

---

## 12. Future Enhancements

- Farmer profiles
- WebSocket live updates
- Recommendation engine for farmers/products
- Optimized asset delivery with S3 presigned URLs

---

## 13. License

MIT License (update as needed)
