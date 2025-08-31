# Reactive Spring Boot POC with WebFlux

This is a complete reactive Spring Boot application demonstrating reactive programming using WebFlux, R2DBC, and H2 database.

## Features

- **Reactive Web Layer**: Built with Spring WebFlux for non-blocking I/O
- **Reactive Data Access**: Uses R2DBC with H2 in-memory database
- **Complete CRUD Operations**: All operations return Mono/Flux reactive types
- **Server-Sent Events**: Streaming endpoint for real-time data
- **Validation**: Input validation with Bean Validation
- **Comprehensive Testing**: WebTestClient for reactive endpoint testing

## Technology Stack

- Java 17
- Spring Boot 3.5.5
- Spring WebFlux
- Spring Data R2DBC
- H2 Database
- Lombok
- Gradle
- JUnit 5

## Project Structure

```
src/
├── main/java/com/example/reactive/
│   ├── ReactiveSpringBootPocApplication.java  # Main application class
│   ├── model/Student.java                     # Entity model
│   ├── repository/StudentRepository.java      # Reactive repository
│   ├── service/StudentService.java            # Business logic layer
│   ├── controller/StudentController.java      # REST controllers
│   └── config/DatabaseConfig.java             # Database configuration
└── main/resources/
    ├── application.properties                 # Application configuration
    ├── schema.sql                            # Database schema
    └── data.sql                              # Sample data
```

## API Endpoints

### Students API (http://localhost:8081/api/students)

- `GET /api/students` - Get all students (returns Flux<Student>)
- `GET /api/students/{id}` - Get student by ID (returns Mono<Student>)
- `POST /api/students` - Create new student (returns Mono<Student>)
- `PUT /api/students/{id}` - Update student (returns Mono<Student>)
- `DELETE /api/students/{id}` - Delete student (returns Mono<Void>)
- `GET /api/students/department/{department}` - Get students by department
- `GET /api/students/age/{minAge}` - Get students by minimum age
- `GET /api/students/search?name={name}` - Search students by name
- `GET /api/students/stream` - Server-Sent Events streaming endpoint

## Running the Application

1. **Build and run:**
   ```bash
   ./gradlew bootRun
   ```

2. **The application will start on port 8081**
   - API Base URL: http://localhost:8081/api/students
   - H2 Console: http://localhost:8081/h2-console

3. **Run tests:**
   ```bash
   ./gradlew test
   ```

## Testing the Reactive Endpoints

### 1. Get All Students
```bash
curl http://localhost:8081/api/students
```

### 2. Get Student by ID
```bash
curl http://localhost:8081/api/students/1
```

### 3. Create New Student
```bash
curl -X POST http://localhost:8081/api/students \
  -H "Content-Type: application/json" \
  -d '{"name":"New Student","email":"new@university.edu","age":25,"department":"Engineering"}'
```

### 4. Stream Students (Server-Sent Events)
```bash
curl -N http://localhost:8081/api/students/stream
```

### 5. Get Students by Department
```bash
curl http://localhost:8081/api/students/department/Computer%20Science
```

## Sample Data

The application comes with 8 pre-loaded students:
- John Doe (Computer Science, Age 20)
- Jane Smith (Mathematics, Age 22)
- Mike Johnson (Computer Science, Age 21)
- Sarah Wilson (Physics, Age 23)
- David Brown (Chemistry, Age 19)
- Emily Davis (Computer Science, Age 24)
- Robert Miller (Mathematics, Age 20)
- Lisa Anderson (Physics, Age 22)

## Reactive Programming Features Demonstrated

1. **Non-blocking I/O**: All endpoints return Mono/Flux reactive types
2. **Backpressure**: Handled automatically by Reactor
3. **Streaming**: Server-Sent Events for real-time data streaming
4. **Reactive Data Access**: R2DBC for non-blocking database operations
5. **Error Handling**: Reactive error handling with doOnError
6. **Async Processing**: Delayed processing simulation with delayElements

## Database Configuration

- **Type**: H2 In-Memory Database
- **R2DBC URL**: r2dbc:h2:mem:///testdb
- **Console**: Available at http://localhost:8081/h2-console
- **Credentials**: username=sa, password=(empty)

## Key Reactive Concepts

- **Mono**: Single value or empty (0..1 elements)
- **Flux**: Stream of values (0..N elements)
- **Non-blocking**: Operations don't block threads
- **Functional Style**: Chain operations with map, flatMap, filter, etc.
- **Backpressure**: Automatic handling of fast producers/slow consumers
# reactive
# reactive-prog
