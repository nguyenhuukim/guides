---
trigger: always_on
---

- Do not use Field injection (using `@Autowired` on fields), use constructor injection instead.
- Do not leave catch blocks empty, always handle or log the exception.
- Do not use `System.out.println`, use a proper logging framework (SLF4J/Logback).
- Do not hardcode credentials or secrets, use environment variables or a secret manager.
- Do not return `null`, use `Optional<T>`, empty collections, or Null Objects.
- Do not write raw MongoDB queries in Controllers, keep data logic in the Repository/Service layer.
- Do not skip input validation, always use @Valid or manual assertions.
- Do not use generic catch (Exception e), catch specific checked or runtime exceptions.
- Do not arbitrarily reformat, beautify, or reorder content in existing source code files.
