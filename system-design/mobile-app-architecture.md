# Mobile App Architecture

## Interview Approach

For each design question, clarify requirements, define the architecture and data flow, explain trade-offs, and cover performance, reliability, accessibility, testing, security, and deployment.

## Question 1 — E-Commerce Mobile App (Highest Priority)

Design a React Native app with product listing, search, product details, cart, checkout, and order history.

Cover:
- Feature-based modular architecture.
- React Navigation or Expo Router.
- Server state with TanStack Query and client state with Zustand or Redux Toolkit.
- API pagination, caching, optimistic updates, and cache invalidation.
- Authentication, token refresh, secure storage, and checkout idempotency.
- Image optimization, list virtualization, accessibility, and analytics.

Follow-up: What happens if a user adds an item to the cart offline and then logs in on another device?

## Question 2 — Offline-First Mobile App

Design an app that remains useful in a warehouse or an area with poor network connectivity.

Cover:
- Local persistence with SQLite or Room through a native integration where needed.
- A repository pattern and a clearly defined source of truth.
- A pending-operation queue with retries, exponential backoff, and idempotency keys.
- Conflict resolution when local and server data disagree.
- Connectivity changes and visible synchronization status.

Follow-up: How do you prevent duplicate transactions when a request times out and is retried?

## Question 3 — High-Performance Feed

Design a feed with thousands of posts, images, video previews, likes, comments, and infinite scrolling.

Cover:
- Virtualized lists and stable row identities.
- Cursor-based pagination and deduplication.
- Image caching and prefetching.
- Isolated row state and memoization.
- Optimistic updates with rollback.

Follow-up: How would you investigate dropped frames during scrolling?

## Question 4 — Reusable Mobile Component Library

Design a component library used by 20 feature teams across iOS and Android.

Cover design tokens, accessibility, theming, typed component APIs, documentation, semantic versioning, visual regression tests, and backward compatibility.

Follow-up: How would you introduce a breaking change without blocking consuming teams?

## Question 5 — Real-Time Tracking App

Design an app receiving live updates from a backend.

Cover:
- WebSockets versus polling.
- Connection recovery and background execution limitations.
- Event deduplication and stale data.
- Reconnection strategy and battery usage.

Follow-up: How do you keep the UI responsive when updates arrive several times per second?

## Question 6 — Expo Production App

Design an application using Expo Router, EAS Build, EAS Submit, and EAS Update.

Cover file-based routing, native modules and config plugins, environment-specific configuration, signing credentials, CI/CD, staged releases, rollback, and compatibility between JavaScript bundles and native binaries.

Follow-up: What happens if a JavaScript update requires a native module that is absent from the installed binary?

## Additional System Design Questions

1. Structure a large React Native app using Clean Architecture or feature-based modules.
2. Choose between Redux Toolkit, Zustand, Context API, and TanStack Query.
3. Design caching with memory and persistent storage, TTL, stale-while-revalidate, and invalidation.
4. Design authentication, refresh tokens, logout, and deep links.
5. Design universal links to open a specific product or order on iOS and Android.
6. Design for accessibility AA, including dynamic font sizes, screen readers, contrast, and touch targets.
7. Split a monolithic React Native app into independently maintained modules.
8. Design GraphQL caching and pagination, and compare with REST.
9. Integrate a native SDK while keeping the JavaScript API stable.

## Reference Architecture

- **Presentation:** screens, components, hooks, and navigation.
- **Application:** use cases, business rules, and state coordination.
- **Data:** repositories, API clients, cache, and local database.
- **Remote sources:** REST or GraphQL services.
- **Local sources:** SQLite or key-value storage.

The architecture should isolate business logic from UI and data-source details without adding unnecessary layers.