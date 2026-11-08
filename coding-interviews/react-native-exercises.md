# React Native and Frontend Exercises

## 1. Debounced Product Search

Build a React Native product-search screen that calls a REST API.

Requirements:
- Debounce input by 300 ms.
- Show loading, error, empty, and results states.
- Prevent stale responses from replacing newer results.
- Support retry and pagination.
- Avoid unnecessary re-renders.

Follow-up questions:
- How would you cancel an in-flight request with `AbortController`?
- How does debouncing differ from throttling?
- How would you cache search results?
- What happens if the component unmounts while a request is pending?
- Would you use TanStack Query, Redux Toolkit, or local state, and why?

## 2. Optimize a Large List

Build a product list containing 10,000 items, images, search, and selectable rows.

Requirements:
- Use `FlatList` or an appropriate alternative such as FlashList.
- Use stable keys and memoized row components where useful.
- Implement pagination and lazy image loading.
- Keep state updates efficient.

Follow-up questions:
- Why might `React.memo` fail to prevent re-renders?
- How does `FlatList` differ from `ScrollView`?
- How do `windowSize`, `initialNumToRender`, and `maxToRenderPerBatch` affect performance?
- When is `getItemLayout` useful?

## 3. Implement a Cache

Write a TypeScript cache supporting:
- Key-value access.
- TTL expiration.
- Cache hit and miss handling.
- Stale-while-revalidate behavior.
- Deduplication of concurrent requests for the same key.

Follow-up questions:
- How do you invalidate data after a mutation?
- When would you use memory, AsyncStorage, or SQLite?
- How would you handle cache versioning and offline access?

## 4. Debug React Hooks

Given a component with stale state in `useEffect`, repeated API calls, and unnecessary rendering, identify and fix the problems.

Follow-up questions:
- Explain effect dependency arrays and stale closures.
- When should you use `useRef` instead of `useState`?
- How do `useMemo` and `useCallback` differ?
- Why is direct state mutation problematic?

## 5. Additional Coding Exercises

1. Implement an LRU cache with O(1) `get` and `put`.
2. Implement a `useDebounce` hook with cleanup.
3. Implement cursor-based infinite scrolling.
4. Build a multi-step form with validation and persisted draft state.
5. Implement a concurrency-limited API request queue.
6. Fix a race condition where an older response overwrites a newer response.
7. Build an accessible reusable modal with Android back-button handling.
8. Write unit tests for a custom hook using Jest and React Native Testing Library.