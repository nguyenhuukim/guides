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

| Violation | Why it's Dangerous |
| :--- | :--- |
| **`@Autowired` on fields** | Causes tight coupling; makes unit testing difficult. |
| **Empty catch blocks** | Swallows errors and hides critical bugs. |
| **`System.out.println`** | Lacks log levels and cannot be traced in production. |
| **Hardcoded credentials** | Leads to severe security breaches. |
| **Returning `null`** | Frequent cause of `NullPointerExceptions`. |
| **Raw MongoDB queries in Controller** | Bypasses business logic and violates separation of concerns. |
| **Skipping input validation** | Opens the door for Injection attacks. |
| **Generic `catch (Exception e)`** | Masks specific errors and makes debugging impossible. |
