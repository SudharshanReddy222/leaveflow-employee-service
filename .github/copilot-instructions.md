
# LeaveFlow Employee Service - Copilot Instructions

## Project Overview
This microservice manages employee information for LeaveFlow.

## Technology Stack
- Java 21
- Spring Boot 3.5.x
- Spring Data JPA
- Hibernate
- PostgreSQL
- Maven
- Lombok
- Bean Validation
- JUnit 5
- Mockito

## Port
8082

## Database
Database name: leaveflow_employee

This service owns employee data.

## Package Structure
com.leaveflow.employee
controller
service
repository
entity
dto
request
response
exception
mapper
config

## Employee Entity
Create an Employee entity with:
- id (Long)
- employeeCode (String, unique)
- firstName (String)
- lastName (String)
- email (String, unique)
- department (String)
- designation (String)
- managerId (Long)
- joiningDate (LocalDate)
- active (Boolean)
- createdAt (LocalDateTime)
- updatedAt (LocalDateTime)

Do not store passwords in this service.
Authentication credentials belong to Auth Service.

## API Endpoints
POST   /api/employees
GET    /api/employees
GET    /api/employees/{id}
PUT    /api/employees/{id}
DELETE /api/employees/{id}

Additional endpoint:
GET /api/employees/code/{employeeCode}

## Architecture
Follow layered architecture:

Controller -> Service -> Repository -> Database

## Coding Standards
- Use constructor injection.
- Use DTOs for requests and responses.
- Never expose JPA entities directly.
- Use Bean Validation.
- Implement global exception handling.
- Create custom exceptions where appropriate.
- Use @Transactional for database operations.
- Use pagination for employee listing.
- Use meaningful HTTP status codes.
- Use Lombok only where it improves readability.
- Avoid unnecessary abstractions.

## Security
- API Gateway is the public security boundary.
- This service must not be publicly exposed.
- Do not trust employee IDs or role headers supplied by clients.
- Only permit trusted gateway traffic.
- Apply authorization checks for employee-management operations.
- EMPLOYEE: Can view permitted employee information.
- MANAGER: Can manage employees within authorized scope.
- ADMIN: Can manage all employees.

For the MVP, identity propagation must be explicitly designed and verified. Do not assume that an arbitrary HTTP header is trustworthy.

## Testing
- JUnit 5
- Mockito
- Test controller, service and repository layers.
- Test duplicate employee email.
- Test employee not found.
- Test validation failures.

## Important
Inspect existing files before implementation.
Do not add unnecessary dependencies.
Do not hardcode database credentials.
Run Maven tests after modifications.
