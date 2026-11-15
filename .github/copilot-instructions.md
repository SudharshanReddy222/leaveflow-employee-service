
# LeaveFlow Employee Service

## Technology
- Java 21
- Spring Boot 3.5.x
- Maven
- Spring Data JPA
- PostgreSQL
- Lombok
- JUnit 5 and Mockito

## Architecture
Follow layered architecture:
Controller -> Service -> Repository -> Database.

## Package structure
com.leaveflow.employee
controller
service
repository
entity
dto
exception
config

## Coding standards
- Use constructor injection.
- Use DTOs for API requests and responses.
- Never expose JPA entities directly through REST APIs.
- Use Bean Validation.
- Implement global exception handling.
- Use meaningful exception classes.
- Keep business logic inside service classes.
- Write unit tests for service classes.
- Avoid unnecessary abstractions.
- Do not hardcode credentials.
- Use environment variables for configuration.

## Security
- Requests arrive through the API Gateway.
- Gateway validates JWT tokens.
- Only the API Gateway should be publicly exposed.
- Do not trust client-supplied employee identity headers.

## Important
Generate clean, maintainable code.
Explain significant design decisions.
Do not modify unrelated files.
Run Maven tests after implementation.
