# Jest and React Native Testing Library

## Custom Hook Exercise

Write unit tests for a custom hook such as `useDebounce` using Jest and React Native Testing Library.

Include cases for:
- The value remaining unchanged before the debounce interval.
- The value updating after the interval.
- A newer value resetting the pending timer.
- Cleanup when the hook unmounts.
- Edge cases such as a zero delay or repeated equal values, where supported by the API.