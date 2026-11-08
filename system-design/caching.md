# Caching

## Cache Implementation Exercise

Implement a TypeScript cache with key-value access, TTL expiration, hit/miss handling, stale-while-revalidate behavior, and deduplication of concurrent requests for the same key.

Discuss:
- Invalidating data after a mutation.
- Choosing memory, AsyncStorage, or SQLite based on lifetime, size, query needs, and sensitivity.
- Cache versioning and offline access.
- Avoiding duplicate work when several consumers request the same missing key.

## System Design Prompt

Design caching across memory and persistent storage. Explain TTL, stale-while-revalidate, invalidation, and how the UI behaves while data is fresh, stale, unavailable, or being refreshed. Compare REST and GraphQL pagination and cache behavior where relevant.