---
trigger: always_on
---

# 🎯 Code Quality Standards

## Principles

- Code must be easy to read, maintain, test, and extend.
- Strictly adhere to the 5 SOLID principles.

## Naming Conventions

- Variable and function names must be meaningful (Self-documenting code).

## Structure Requirements

- **Single Responsibility**: Each class MUST have a single responsibility (SRP)
- **Method Length**: Service methods MUST NOT exceed 30 lines
- **Controller Logic**: Controllers only handle HTTP concerns; delegate all business logic to Services

## Documentation

- **Javadoc**: All public methods MUST have Javadoc with `@param`, `@return`, and `@throws`
- **Inline Comments**: Complex business logic MUST have inline comments for clarification
