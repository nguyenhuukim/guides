


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

## 🚫 Critical Violations (Do NOT Do)

* **Field injection** (using `@Autowired` on fields)
* **Empty catch blocks**
* **`System.out.println`**
* **Hardcoded credentials/secrets**
* **Returning `null`**
* **Raw MongoDB queries in Controllers**
* **Skipping input validation**
* **Generic `catch (Exception e)`**
