# Offline-First Systems

## Warehouse App Scenario

Design an app that remains useful in a warehouse or an area with poor connectivity.

Cover:
- A local database such as SQLite.
- Repository pattern and source-of-truth strategy.
- Pending-operation queue, retries, exponential backoff, and idempotency.
- Conflict resolution between local and server data.
- Connectivity changes and synchronization status.

Follow-up: How do you prevent duplicate transactions after retrying a timed-out request?

## Design Considerations

Define which operations are available offline, how local writes become visible immediately, and how the application represents pending, failed, and synchronized changes. Use stable operation identifiers and idempotent server behavior so retries do not duplicate transactions. Specify conflict policies per data type rather than assuming one strategy fits every record.