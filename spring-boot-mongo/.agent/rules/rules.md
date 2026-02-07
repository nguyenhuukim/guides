

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
