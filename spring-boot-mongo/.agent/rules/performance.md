---
trigger: always_on
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
