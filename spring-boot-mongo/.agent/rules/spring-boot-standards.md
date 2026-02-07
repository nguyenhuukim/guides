---
trigger: always_on
---

# 🛡️ Spring Boot Standards

## REST API Design

- Use @Valid for request body validation.
- Return proper HTTP status codes

## Exception Handling

- Create custom exceptions that inherit from `RuntimeException`
- Implement `@RestControllerAdvice` for global exception handling
- DO NOT catch generic `Exception` unless absolutely necessary.
- Log exceptions with the proper level

## Configuration

- Sensitive data MUST be externalized (do not hardcode).
