# Completion is server-stamped, bool-on-the-wire

**Status**: accepted

Completing a task is represented on the wire as a boolean (`completed: true/false` on write; `completed` only, on read), while the authoritative fact is a server-stamped `completed_at` timestamp that the client never sees. Alternatives were letting the client send the timestamp, or exposing `completedAt` in responses alongside the bool.

- **Hard to reverse**: the wire shape is a client contract; adding or removing the timestamp field later breaks clients.
- **Surprising without context**: a future reader will see the column and wonder why no API field matches it, or wonder why the client can't assert *when* a task was completed.
- **Real trade-off**: exposing the timestamp costs the client rendering and format concerns for no UX gain; letting the client stamp it splits the source of truth for "time" across two systems.
