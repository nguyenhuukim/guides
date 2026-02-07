---
trigger: always_on
---

# 🔒 Security Requirements

## Data Protection

- **Encryption at rest** for sensitive data
- **DO NOT log sensitive information** (passwords, tokens, PII)

## Input Validation

- **Validate ALL user inputs** using Bean Validation
- **Sanitize inputs** to prevent injection attacks
- **Use `@Valid`** on request bodies
- **Custom validators** for complex business rules

```java
public record CreateUserRequest(
    @NotBlank @Email String email,
    @NotBlank @Size(min = 8, max = 100) String password,
    @NotBlank @Size(min = 2, max = 50) String name
) {}
```
