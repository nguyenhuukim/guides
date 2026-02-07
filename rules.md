## 🎯 Code Quality Standards
### Naming Conventions
- **Classes**: PascalCase (e.g., `UserService`, `OrderRepository`)
- **Methods/Variables**: camelCase (e.g., `findByEmail`, `userId`)
- **Constants**: UPPER_SNAKE_CASE (e.g., `MAX_RETRY_COUNT`)
- **Packages**: lowercase, no underscores (e.g., `com.example.userservice`)
### Structure Requirements
- Tuân thủ package structure: `controller` → `service` → `repository` → `model`
- Mỗi class PHẢI có single responsibility
- Service methods KHÔNG được quá 30 lines
- Controllers chỉ xử lý HTTP concerns, delegate logic cho Service
### Documentation
- Tất cả public methods PHẢI có Javadoc với `@param`, `@return`, `@throws`
- Complex business logic PHẢI có inline comments giải thích

## 🛡️ Spring Boot Standards
### Dependency Injection
- ✅ SỬ DỤNG constructor injection với `@RequiredArgsConstructor`
- ❌ KHÔNG dùng `@Autowired` trên fields
- ❌ KHÔNG dùng setter injection
```java
// ✅ ĐÚNG
@Service
@RequiredArgsConstructor
public class UserService {
    private final UserRepository userRepository;
    private final PasswordEncoder passwordEncoder;
}
// ❌ SAI
@Service
public class UserService {
    @Autowired
    private UserRepository userRepository;
}
```


### REST API Design
- Sử dụng proper HTTP methods: GET (read), POST (create), PUT (update), DELETE (delete)
- Response format nhất quán với `ResponseEntity<T>`
- API versioning: `/api/v1/...`
- Sử dụng `@Valid` cho request validation
- Return proper HTTP status codes
### Exception Handling
- Tạo custom exceptions kế thừa `RuntimeException`
- Implement `@ControllerAdvice` cho global exception handling
- KHÔNG catch generic `Exception` trừ khi absolutely necessary
- Log exceptions với proper level (ERROR cho unexpected, WARN cho expected)
```java
// Custom Exception
public class ResourceNotFoundException extends RuntimeException {
    public ResourceNotFoundException(String resource, String id) {
        super(String.format("%s not found with id: %s", resource, id));
    }
}

// Global Handler
@RestControllerAdvice
public class GlobalExceptionHandler {
    @ExceptionHandler(ResourceNotFoundException.class)
    public ResponseEntity<ErrorResponse> handleNotFound(ResourceNotFoundException ex) {
        return ResponseEntity.status(HttpStatus.NOT_FOUND)
            .body(new ErrorResponse(ex.getMessage()));
    }
}
```
### Configuration
- Sử dụng `@ConfigurationProperties` cho grouped configs
- Sensitive data PHẢI được externalize (không hardcode)
- Profiles cho different environments: `dev`, `staging`, `prod`

## ⚡ Performance Guidelines
### Database
- Pagination cho list endpoints (không return unbounded lists)
- Proper indexing strategy
- Connection pooling configuration
- Query optimization với projections
### Caching
- Sử dụng `@Cacheable` cho frequently accessed, rarely changed data
- Cache invalidation strategy phải clear
- Redis cho distributed caching
### Async Processing
- `@Async` cho non-blocking operations
- Message queues cho heavy processing
- Proper thread pool configuration

## 📋 Pre-Completion Checklist
Agent PHẢI hoàn thành checklist này TRƯỚC khi báo cáo task hoàn thành:
- [ ] Code compiles: `mvn compile` passes
- [ ] Tests pass: `mvn test` passes
- [ ] No linting errors: checkstyle/spotless passes
- [ ] Javadoc complete cho public methods
- [ ] Exception handling implemented
- [ ] Input validation added
- [ ] Unit tests written (>= 80% coverage cho new code)
- [ ] No hardcoded secrets
- [ ] README/docs updated if needed

## 🚫 Điều KHÔNG ĐƯỢC LÀM
| Violation | Tại sao nguy hiểm |
|-----------|-------------------|
| `@Autowired` trên field | Tight coupling, khó test |
| Empty catch blocks | Swallow errors, hide bugs |
| `System.out.println` | Không có log levels, không trace |
| Hardcoded credentials | Security breach |
| Return `null` | NullPointerException |
| Raw MongoDB queries trong Controller | Bypass business logic |
| Skip input validation | Injection attacks |
| Generic `catch (Exception e)` | Hide specific errors |
