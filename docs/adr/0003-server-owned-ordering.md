# Ordering is owned by the API

**Status**: accepted

The order of lists and tasks is defined by the server in SQL (lists by name; tasks open-first, then due date ascending with open-ended last, then newest first) and is part of the REST contract. The client renders what it receives and never re-sorts. Alternative: the API returns unsorted and each client decides its own ordering.

- **Hard to reverse**: once a client sorts, it can't trust another client not to sort differently, and "the" order of the app no longer exists.
- **Surprising without context**: a UI reader will expect to find the sort logic in the frontend and won't.
- **Real trade-off**: client-side sorting keeps the API dumb, but this app is single-client and the ordering rule ("open first, due soon first") is a domain fact, not a presentation choice — it belongs in one testable place, which happens to be SQL.
