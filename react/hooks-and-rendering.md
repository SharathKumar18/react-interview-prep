# Hooks and Rendering

## Debugging Effects and Stale State

Given a component with stale state in `useEffect`, repeated API calls, and unnecessary rendering, inspect its effect dependencies, captured values, and ownership of asynchronous work.

Questions to work through:
- Are all reactive values used by an effect represented in its dependency array?
- Is a callback closing over an outdated value?
- Does the effect need cleanup when dependencies change or the component unmounts?
- Is state being mutated directly rather than replaced immutably?
- Is state stored at a level that causes unrelated parts of the tree to render?

Use `useRef` for mutable values that should persist across renders without triggering a render. Use `useState` when a change should be reflected in the UI. `useMemo` caches a computed value; `useCallback` caches a function reference. Neither prevents rendering by itself, and both are useful only when their dependencies and consumers make the cached identity meaningful.

## Search Request Race Conditions

For debounced search, a response for an older query must not replace results for a newer query. Cancel obsolete requests when the transport supports cancellation, or associate each request with a sequence/query identity and ignore results that are no longer current. Clean up timers and requests when the effect is replaced or the component unmounts.