# API Testing Framework

A Spring Boot REST API with a fully automated testing framework, code coverage reporting, and CI/CD pipeline.

## Tech Stack

- **Java 17**
- **Spring Boot 3.2** — REST API framework
- **JUnit 5** — unit and integration testing
- **Mockito** — mocking dependencies
- **MockMvc** — HTTP layer testing
- **JaCoCo** — code coverage reporting
- **H2** — in-memory database
- **GitHub Actions** — CI/CD pipeline

## Project Structure

```
src/
├── main/java/org/example/
│   ├── Main.java               # Application entry point
│   ├── User.java               # Entity model
│   ├── UserRepository.java     # Database layer
│   ├── UserService.java        # Business logic
│   └── UserController.java     # REST endpoints
└── test/java/org/example/
    ├── UserServiceTest.java    # Unit tests
    └── UserControllerTest.java # Integration tests
```

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/users` | Get all users |
| GET | `/users/{id}` | Get user by ID |
| POST | `/users` | Create a new user |

## Running the Application

```bash
mvn spring-boot:run
```

API will be available at `http://localhost:8080`

## Running Tests

```bash
mvn clean test
```

## Code Coverage Report

```bash
mvn clean test jacoco:report
```

Open `target/site/jacoco/index.html` in your browser to view the report.

## CI/CD Pipeline

Every push to `main` automatically:
- Builds the project
- Runs all 6 tests
- Generates coverage report
- Uploads test results as artifacts

## Test Results

- **6 tests** across 2 test classes
- **0 failures**
- **Unit tests** — service layer logic with Mockito mocks
- **Integration tests** — full HTTP request/response cycle with MockMvc

## Database

Uses H2 in-memory database. View it live while the app is running:

- URL: `http://localhost:8080/h2-console`
- JDBC URL: `jdbc:h2:mem:testdb`
- Username: `SA`
- Password: *(leave blank)*

## Sample Request

Create a user:
```json
POST /users
Content-Type: application/json

{
    "name": "John",
    "email": "john@email.com"
}
```

Response:
```json
{
    "id": 1,
    "name": "John",
    "email": "john@email.com"
}
```