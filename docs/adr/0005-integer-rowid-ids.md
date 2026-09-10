# Integer rowid IDs on the wire

**Status**: accepted

Rows are identified by their SQLite integer rowid (autoincrement), exposed directly in JSON. Alternatives: client-generated or server-generated UUIDs (v4/v7). This is single-user and local; the opacity that argues for UUIDs (enumeration resistance, composite ownership) buys nothing here, while integers make every route trivially callable by hand (`curl localhost:3000/api/tasks/1`) and trivially predictable in tests. The decision is cheap to reverse while the app is young, but it changes every route, row, and both languages — so it is recorded anyway.
