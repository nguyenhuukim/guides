# 🛡️ Spring Boot Standards

## Dependency Injection
- ✅ **USE** constructor injection with `@RequiredArgsConstructor`
- ❌ **DO NOT** use `@Autowired` on fields
- ❌ **DO NOT** use setter injection

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

---

# 🎯 Code Quality Standards

## Naming Conventions
- **Classes**: PascalCase (e.g., `UserService`, `OrderRepository`)
- **Methods/Variables**: camelCase (e.g., `findByEmail`, `userId`)
- **Constants**: UPPER_SNAKE_CASE (e.g., `MAX_RETRY_COUNT`)
- **Packages**: lowercase, no underscores (e.g., `com.example.userservice`)

## Structure Requirements
- **Layered Architecture**: Follow the package structure: `controller` → `service` → `repository` → `model`
- **Single Responsibility**: Each class MUST have a single responsibility (SRP)
- **Method Length**: Service methods MUST NOT exceed 30 lines
- **Controller Logic**: Controllers only handle HTTP concerns; delegate all business logic to Services

## Documentation
- **Javadoc**: All public methods MUST have Javadoc with `@param`, `@return`, and `@throws`
- **Inline Comments**: Complex business logic MUST have inline comments for clarification

---

# 🧪 Testing Requirements

## Unit Tests
- **Minimum Coverage:** 80% for the service layer
- **Scenarios:** Test both happy paths and error scenarios
- **Naming Convention:** `methodName_scenario_expectedResult`

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

---

# ⚡ Performance Guidelines
Always consider Performance and Scalability factors

## Database
- **Pagination for list endpoints** (avoid returning unbounded lists)
- **Proper indexing strategy**
- **Connection pooling configuration**
- **Query optimization** using projections

## Caching
- **Use `@Cacheable`** for frequently accessed, rarely changed data
- **Clear cache invalidation strategy**
- **Redis** for distributed caching

## Async Processing
- **`@Async`** for non-blocking operations
- **Message queues** for heavy processing
- **Proper thread pool configuration**

---

# 📋 Pre-Completion Checklist
The Agent **MUST** complete this checklist **BEFORE** reporting the task as finished:

- [ ] **Code compiles:** `mvn compile` passes
- [ ] **Tests pass:** `mvn test` passes
- [ ] **No linting errors:** Checkstyle/Spotless passes
- [ ] **Javadoc complete:** All public methods are documented
- [ ] **Exception handling:** Properly implemented
- [ ] **Input validation:** Added and verified
- [ ] **Unit tests:** Written (>= 80% coverage for new code)
- [ ] **No hardcoded secrets:** Verified security
- [ ] **Documentation:** README/docs updated if necessary

---

# 🚫 Critical Violations (Do NOT Do)

* **Field injection** (using `@Autowired` on fields)
* **Empty catch blocks**
* **`System.out.println`**
* **Hardcoded credentials/secrets**
* **Returning `null`**
* **Raw MongoDB queries in Controllers**
* **Skipping input validation**
* **Generic `catch (Exception e)`**
* **Arbitrarily reformat, beautify, or reorder** content in existing source code files.
