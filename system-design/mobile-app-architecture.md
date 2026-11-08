# Mobile App Architecture

## Interview Approach

For each design question, clarify requirements, define the architecture and data flow, explain trade-offs, and cover performance, reliability, accessibility, testing, security, and deployment.

## E-Commerce Mobile App

Design a React Native app with product listing, search, product details, cart, checkout, and order history.

Cover:
- Feature-based modular architecture.
- React Navigation or Expo Router.
- Server state with TanStack Query and client state with Zustand or Redux Toolkit.
- API pagination, caching, optimistic updates, and cache invalidation.
- Authentication, token refresh, secure storage, and checkout idempotency.
- Image optimization, list virtualization, accessibility, and analytics.

Follow-up: What happens if a user adds an item to the cart offline and then logs in on another device?

## High-Performance Feed

Design a feed with thousands of posts, images, video previews, likes, comments, and infinite scrolling.

Cover:
- Virtualized lists and stable row identities.
- Cursor-based pagination and deduplication.
- Image caching and prefetching.
- Isolated row state and memoization.
- Optimistic updates with rollback.

Follow-up: How would you investigate dropped frames during scrolling?

## Real-Time Tracking App

Design an app receiving live updates from a backend.

Cover:
- WebSockets versus polling.
- Connection recovery and background execution limitations.
- Event deduplication and stale data.
- Reconnection strategy and battery usage.

Follow-up: How do you keep the UI responsive when updates arrive several times per second?

## Additional System Design Questions

1. Structure a large React Native app using Clean Architecture or feature-based modules.
2. Choose between Redux Toolkit, Zustand, Context API, and TanStack Query.
3. Design authentication, refresh tokens, logout, and deep links.
4. Design universal links to open a specific product or order on iOS and Android.
5. Design for accessibility AA, including dynamic font sizes, screen readers, contrast, and touch targets.
6. Split a monolithic React Native app into independently maintained modules.
7. Design GraphQL caching and pagination, and compare with REST.
8. Integrate a native SDK while keeping the JavaScript API stable.

## Reference Architecture

- **Presentation:** screens, components, hooks, and navigation.
- **Application:** use cases, business rules, and state coordination.
- **Data:** repositories, API clients, cache, and local database.
- **Remote sources:** REST or GraphQL services.
- **Local sources:** SQLite or key-value storage.

The architecture should isolate business logic from UI and data-source details without adding unnecessary layers.