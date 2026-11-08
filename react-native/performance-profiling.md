# Performance Profiling

## General Scenario

“Our production React Native app is slow. Users report laggy scrolling, slow startup, high memory usage, and occasional crashes. How would you investigate?”

Suggested approach:
1. Reproduce and quantify the issue.
2. Identify the device, OS, app version, build type, screen, and reproduction steps.
3. Measure startup time, frame time, JavaScript responsiveness, memory, crash rate, and ANRs.
4. Determine whether the bottleneck is JavaScript, native UI, networking, images, or a native SDK.
5. Profile the relevant layer.
6. Fix the measured bottleneck and compare before/after results.

## Tools and Signals

| Problem | Tools | Investigate |
|---|---|---|
| Excessive component renders | React DevTools Profiler | Commit duration, render counts, props and state changes |
| JavaScript CPU bottlenecks | Hermes sampling profiler | Expensive functions and long synchronous work |
| Android UI jank / CPU | Android Studio Profiler, Perfetto | Main-thread stalls, frame timeline, CPU scheduling |
| Android memory leaks | Android Studio Memory Profiler, heap dumps | Retained objects, leaking views, listeners |
| iOS CPU / memory / hangs | Instruments, Xcode Organizer | Time Profiler, Allocations, Leaks, hangs, crashes |
| Production crashes and ANRs | Crash reporting, Play Console, Xcode Organizer | Stack traces, affected versions, device and OS patterns |
| Network latency | Network inspector and backend traces | Slow requests, oversized responses, repeated calls |
| RN rendering / interop | RN DevTools and version-appropriate native tracing | JavaScript work, native UI work, interop overhead |

Tool availability and workflows vary by React Native version, Hermes, and architecture. Prefer release-like builds and realistic workloads; development mode can distort measurements.

## Profiling Questions

### FlatList drops frames during scrolling. How do you debug it?

Reproduce on a physical release-build device, inspect frame timelines and JavaScript versus native UI bottlenecks, profile repeated row work, then inspect image decoding, layout complexity, virtualization, and unstable props. Apply a targeted optimization and compare before/after frame-time results.

Follow-up: Would you always use `React.memo`? Explain the comparison overhead and why changing props can negate its benefit.

### App startup takes five seconds. How do you improve it?

Investigate cold versus warm launch, native initialization, JavaScript bundle loading/evaluation, synchronous startup work, dependency initialization, network-blocked first screens, and image/font loading. Consider lazy initialization, deferring noncritical work, reducing bundle size, and rendering a lightweight first screen. Measure time to first meaningful content.

### Memory grows each time a screen opens and closes. What do you check?

- Compare heap snapshots before and after repeated navigation.
- Inspect retained views, listeners, subscriptions, timers, and event emitters.
- Inspect native SDK references, image caches, and large collections.
- Verify cleanup on unmount and lifecycle transitions.
- Confirm growth persists after garbage collection before concluding there is a leak.

Follow-up: Why might removing a React component from the screen not release native resources?

### The JavaScript thread is blocked for 200 ms. What happens?

JavaScript-dependent updates, event processing, and interactions may be delayed. Native-driven animations may continue depending on the operation and implementation. Identify synchronous work, reduce its cost, move suitable work off the JavaScript thread, or use native capabilities where appropriate. Avoid assuming every operation crosses the legacy bridge.

### The app is smooth in development but slow in production, or vice versa. Why?

Compare build configuration, debugging overhead, minification, Hermes configuration, logging, network conditions, device hardware, and instrumentation. Reproduce with a release-like build and realistic workload.

### How would you diagnose a native SDK memory leak?

Reproduce repeated mount/unmount cycles, capture heap snapshots, inspect retained references, and trace lifecycle and listener ownership. Check that SDK views, camera sessions, callbacks, and observers are released at the correct lifecycle boundary. Compare with the SDK disabled as a controlled experiment.

## Profiling Answer Framework

1. Reproduce and measure.
2. Form a hypothesis.
3. Profile the relevant layer.
4. Make a targeted change.
5. Compare before/after results on realistic devices and workloads.