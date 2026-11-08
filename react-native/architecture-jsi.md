# React Native Architecture and JSI

## Interview Questions

1. What is JSI?
2. Compare the legacy bridge with JSI-based interoperability.
3. What are Fabric and TurboModules?
4. What is Hermes, and how can it be profiled?
5. Why do unnecessary React re-renders occur?
6. How do you measure frame drops and jank?
7. How do you prevent memory leaks in JavaScript and native code?

For a 60 Hz display, the frame budget is about 16.7 ms; for 120 Hz, it is about 8.3 ms. The relevant budget depends on the device refresh rate and rendering pipeline.

## Quick Reference

| Topic | Key points |
|---|---|
| JSI | C++ interface for JavaScript engines and native host objects; enables direct interoperability without requiring every interaction to use the legacy serialized bridge |
| Legacy bridge vs JSI | The legacy bridge uses asynchronous serialized communication; JSI enables more direct interaction, but actual performance depends on implementation and threading |
| Fabric | React Native's New Architecture renderer |
| TurboModules | Modern native module system supporting lazy loading |
| Hermes | JavaScript engine optimized for React Native, with bytecode and profiling capabilities |
| React rendering | State placement, parent renders, changing object/function references, Context updates, and broad subscriptions can cause unnecessary work |
| Profiling | Use frame timelines and JavaScript/native traces; average FPS alone may hide jank |
| Memory management | Clean up subscriptions, listeners, timers, native resources, and references; verify with profiling |