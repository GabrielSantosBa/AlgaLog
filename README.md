# AlgaLog API

REST API for a delivery company: manage customers, deliveries and delivery occurrences.

This project was built while studying the AlgaWorks course. It shows how I organize a Spring Boot API in layers, with validation, error handling and database migrations.

## Features

- **Customers**: create, update, list, search by id and delete.
- **Deliveries**: request a delivery, list, search by id and mark a delivery as finished.
- **Occurrences**: register and list occurrences of a delivery.
- **Validation** of input data and a custom error response (`ApiExceptionHandler`).
- **Database migrations** with Flyway.

## Tech stack

| Area | Technology |
| --- | --- |
| Language | Java 11 |
| Framework | Spring Boot (Web, Data JPA, Validation) |
| Database | MySQL |
| Migrations | Flyway |
| Mapping | ModelMapper, Lombok |
| Build | Maven |

## Project structure

```
src/main/java/com/algaworks/algalog
├── api
│   ├── controller        # REST endpoints
│   ├── assembler         # entity <-> model conversion
│   ├── model             # response models and input classes
│   └── exceptionhandler  # error handling
├── domain
│   ├── model             # entities
│   ├── repository
│   ├── service
│   └── exception         # business exceptions
└── common                # ModelMapper config
```

## Endpoints

| Method | Path | Description |
| --- | --- | --- |
| GET | `/clientes` | List customers |
| GET | `/clientes/{clienteId}` | Get a customer |
| POST | `/clientes` | Create a customer |
| PUT | `/clientes/{clienteId}` | Update a customer |
| DELETE | `/clientes/{clienteId}` | Delete a customer |
| GET | `/entregas` | List deliveries |
| GET | `/entregas/{entregaId}` | Get a delivery |
| POST | `/entregas` | Request a delivery |
| PUT | `/entregas/{entregaId}/finalizacao` | Finish a delivery |
| GET | `/entregas/{entregaId}/ocorrencias` | List occurrences of a delivery |
| POST | `/entregas/{entregaId}/ocorrencias` | Register an occurrence |

## How to run

**Requirements:** Java 11, Maven and a MySQL database.

1. Clone the repository:
   ```bash
   git clone https://github.com/GabrielSantosBa/AlgaLog.git
   cd AlgaLog
   ```
2. Create a MySQL database and set the connection (url, user and password) in `src/main/resources/application.properties`. Flyway creates the tables when the app starts.
3. Run the application:
   ```bash
   ./mvnw spring-boot:run
   ```
4. Call the API, for example: `GET http://localhost:8080/clientes` (default port).

## What I practiced

- Layered REST API with Spring Boot and Spring Data JPA
- DTO-style models and assemblers with ModelMapper
- Bean validation and a global exception handler
- Database versioning with Flyway

## Author

**Gabriel Bahia**, Java Backend Developer.
LinkedIn: https://www.linkedin.com/in/gabriel-santosba/
