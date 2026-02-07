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
