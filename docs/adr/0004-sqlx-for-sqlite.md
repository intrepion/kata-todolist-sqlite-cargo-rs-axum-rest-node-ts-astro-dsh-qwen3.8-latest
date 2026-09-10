# sqlx as the SQLite access layer

**Status**: accepted

The Axum server uses **sqlx** (with the SQLite feature) rather than Diesel, raw rusqlite, or tokio-rusqlite. Alternatives: Diesel (synchronous, heavier query-builder stack), rusqlite with manual SQL (synchronous, more boilerplate), tokio-rusqlite (rusqlite parked on a blocking thread).

- **Hard to reverse**: swapping query layers later means touching every handler and test; the migration tooling is baked into `server/migrations/`.
- **Surprising without context**: Diesel is the other "big name" in Rust SQL; a reader may assume we rejected it for the same reasons it's often recommended elsewhere.
- **Real trade-off**: sqlx is one async stack top to bottom (tokio everywhere) with an Axum-friendly ergonomics; Diesel's sync model would either force `.spawn_blocking()` around every query or a second runtime model for no upside in a small app. The rejected alternatives were considered at decision time, not after a failed trial.
