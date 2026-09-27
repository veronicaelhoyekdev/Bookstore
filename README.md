# Bookstore REST API

RESTful API for managing books, authors, and publishers, built with **Java 17, Spring Boot, and MongoDB**.

## Overview

Bookstore REST API is a backend application providing structured CRUD operations for a bookstore domain.

The API models relationships between books, authors, and publishers while separating persistence entities from request and response DTOs. It includes input validation, ISBN-10 and ISBN-13 validation, centralized error handling, JWT-based security, and interactive API documentation through OpenAPI.

## Features

- CRUD operations for books, authors, and publishers
- MongoDB persistence
- DTO-based request and response models
- ISBN-10 and ISBN-13 validation
- Custom validation constraints
- JWT-based authentication and authorization
- Structured exception handling
- OpenAPI / Swagger documentation
- Docker support

## Tech Stack

| Area | Technology |
| --- | --- |
| Language | Java 17 |
| Framework | Spring Boot 3 |
| API | Spring Web / REST |
| Database | MongoDB |
| Persistence | Spring Data MongoDB |
| Security | Spring Security, JWT |
| Validation | Jakarta Validation, custom validators |
| API Documentation | OpenAPI / Swagger |
| Build | Maven |
| Containerization | Docker |

## Architecture

The application follows a layered backend structure:

```text
HTTP Request
     │
     ▼
Controllers
     │
     ▼
Services
     │
     ▼
Repositories
     │
     ▼
MongoDB
```

Domain entities, DTOs, validation logic, exception handling, and persistence concerns are separated into dedicated components.

The main domain is composed of:

- **Books** — bookstore catalog entries with ISBN validation
- **Authors** — author information associated with books
- **Publishers** — publisher information and book relationships

## Project Structure

```text
app/
├── src/
│   ├── main/
│   │   ├── java/edu/ua/oop1veronicahoyek/
│   │   │   ├── app/
│   │   │   │   ├── configurations/
│   │   │   │   ├── controllers/
│   │   │   │   ├── exceptions/
│   │   │   │   ├── helper/
│   │   │   │   ├── isbnValidator/
│   │   │   │   ├── models/
│   │   │   │   │   ├── DTOs/
│   │   │   │   │   └── entities/
│   │   │   │   └── repositories/
│   │   │   └── Oop1VeronicaHoyekApplication.java
│   │   └── resources/
│   │       └── application.yml
│   └── test/
├── dockerfile
├── pom.xml
├── mvnw
└── mvnw.cmd
```

## ISBN Validation

Book data is validated using dedicated ISBN validation logic rather than relying only on basic field validation.

Separate specifications handle:

- ISBN-10
- ISBN-13

A custom validation constraint integrates this logic with the application's model validation.

## API Documentation

OpenAPI documentation is integrated using Springdoc.

Once the application is running, the Swagger UI can be used to explore the available endpoints and their request/response models.

```text
http://localhost:8080/swagger-ui/index.html
```

## Configuration

The application requires a MongoDB connection and a JWT signing secret.

Configure the following environment variables before starting the API:

```env
MONGODB_URI=your_mongodb_connection_string
MONGODB_DATABASE=bookstore
JWT_SECRET=your_jwt_secret
JWT_EXPIRATION=86400000
```

`MONGODB_DATABASE` defaults to `bookstore`, and `JWT_EXPIRATION` defaults to 24 hours when not explicitly configured.

Sensitive configuration should never be committed to version control.

## Getting Started

### Prerequisites

- Java 17
- MongoDB
- Maven, or the included Maven Wrapper

Clone the repository:

```bash
git clone https://github.com/veronica-el-hoyek/Bookstore-REST-API.git
cd Bookstore-REST-API/app
```

Configure the required environment variables, then start the application using the Maven Wrapper:

### macOS / Linux

```bash
./mvnw spring-boot:run
```

### Windows

```bash
mvnw.cmd spring-boot:run
```

The API runs by default on:

```text
http://localhost:8080
```

## Docker

A Dockerfile is included for containerized execution of the Spring Boot application.

Build the application and Docker image according to the environment in which the API will be deployed, providing the required MongoDB and JWT configuration at runtime.

## Project Context

Backend software engineering project focused on REST API design, object-oriented architecture, persistence, authentication, validation, and separation of application concerns.

## Author

**Veronica El Hoyek**  
Software & AI Engineer

Portfolio: https://veronica-el-hoyek.vercel.app/  
GitHub: https://github.com/veronica-el-hoyek