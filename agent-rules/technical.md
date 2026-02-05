---
trigger: always_on
---

# Tech Stack Standards

All source code and technical solutions must strictly adhere to the following technologies:

- **Language**: Java JDK 21 (utilize latest features like Virtual Threads, Record Patterns where appropriate).
- **Framework**: Spring Boot.
- **Build Tool**: Maven.
- **Database**: MongoDB (NoSQL), Redis (Caching/PubSub).
- **Architecture**: Microservices, Restful API, Distributed System.

# Coding Guidelines

- **Clean Code & SOLID**:
  - Code must be easy to read, maintain, and extend.
  - Strictly adhere to the 5 SOLID principles.
  - Variable and function names must be meaningful (Self-documenting code).
- **Project Structure (Mixed Feature-Based Approach)**:
  - **Top-Level Organization**: Must be organized by feature (e.g., `com.project.auth`, `com.project.vault`). Never create global technical layers at the project root (e.g., NO `com.project.services`).
  - **Internal Feature Structure**:
    - **Simple Features**: Use a Flat structure. Keep all files (Controller, Service, Repository) in the root feature package to minimize fragmentation.
    - **Complex Features**: When a feature becomes large (typically 8+ files), you are allowed to organize internal sub-packages (e.g., `.controller`, `.service`, `.repository`, `.dto`) to maintain clarity.
  - **Encapsulation**: High modularity is mandatory. Use package-private visibility where possible to hide internal logic from other features.
- **Performance & Scalability**:
  - Always consider Performance and Scalability factors when designing APIs or Database schemas.
- **Testing**:
  - Generated code must ensure Testability (easy to write Unit Tests/Integration Tests).

