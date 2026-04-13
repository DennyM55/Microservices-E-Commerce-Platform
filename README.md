# Microservices E-Commerce Platform

A Spring Boot microservices-based backend platform for e-commerce workflows.

## Planned Services

- `product-service`
- `order-service`
- `inventory-service`
- `notification-service`
- `api-gateway`
- `discovery-server` (Eureka)
- `config-server` (centralized configuration)

## Architecture Highlights

- Microservices architecture with independent deployable services
- API Gateway for unified client routing
- Service-to-service communication using REST clients
- Centralized configuration with Spring Cloud Config
- Service discovery with Eureka
- Docker Compose local environment
- Logging and tracing foundations (Zipkin support)
- Resilience/fallback patterns (Resilience4j ready)
- Externalized config management

## Optional Advanced Features

- Kafka-based asynchronous communication
- Redis caching
- Circuit breaker patterns
- Prometheus / Grafana monitoring

## Project Structure

```text
.
├── api-gateway
├── config-server
├── discovery-server
├── inventory-service
├── notification-service
├── order-service
├── product-service
├── docker-compose.yml
└── pom.xml
```

## Quick Start

### Prerequisites

- Java 21+
- Maven 3.9+
- Docker + Docker Compose

### Run locally (non-containerized)

Start in this order:

1. `config-server`
2. `discovery-server`
3. `api-gateway`
4. Domain services (`product-service`, `inventory-service`, `order-service`, `notification-service`)

```bash
mvn clean package
```

Then run each module:

```bash
mvn -pl config-server spring-boot:run
mvn -pl discovery-server spring-boot:run
mvn -pl api-gateway spring-boot:run
mvn -pl product-service spring-boot:run
mvn -pl inventory-service spring-boot:run
mvn -pl order-service spring-boot:run
mvn -pl notification-service spring-boot:run
```

### Run with Docker Compose

```bash
docker compose up --build
```

## Next Steps

- Add inter-service flows (`order-service` -> `inventory-service` -> `notification-service`)
- Introduce Kafka for async order events
- Add Redis caching to `product-service`
- Add Resilience4j circuit breakers and fallback handlers
- Add Prometheus/Grafana dashboards
