# Deployment & Observability

This guide covers key aspects of deploying and monitoring Spring Boot applications, including packaging, containerization, environment configuration, and observability with Spring Boot Actuator.

---

## 1. Build Executable JAR

- Spring Boot allows packaging applications into self-contained executable JARs.

```b
# Build JAR using Maven
mvn clean package

# Run the JAR
java -jar target/myapp-0.0.1-SNAPSHOT.jar
```

## 2. Docker Image Packaging
- Containerizing the application ensures portability and consistency across environments.

Dockerfile Example:
```
FROM openjdk:17-jdk-slim
VOLUME /tmp
COPY target/myapp-0.0.1-SNAPSHOT.jar app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
```

Build & Run:
```
docker build -t myapp:latest .
docker run -p 8080:8080 myapp:latest
```

## 3. Environment-Based Config
- Spring Boot supports externalized configuration for different environments.

- application.yml:
```
spring:
  profiles:
    active: dev

---
spring:
  config:
    activate:
      on-profile: dev
server:
  port: 8081

---
spring:
  config:
    activate:
      on-profile: prod
server:
  port: 8080
```
Run with a specific profile:
```
java -jar myapp.jar --spring.profiles.active=prod
```

## 4. Spring Boot Actuator
- Actuator provides production-ready features for monitoring and managing applications.

- Add dependency (Maven):
```
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```

## 5. Health, Metrics, Info Endpoints
- Enable useful endpoints in application.yml:

```
management:
  endpoints:
    web:
      exposure:
        include: health,info,metrics
```

### Examples:

- Health check:
GET http://localhost:8080/actuator/health

- Application info:
GET http://localhost:8080/actuator/info

- Metrics:
GET http://localhost:8080/actuator/metrics
