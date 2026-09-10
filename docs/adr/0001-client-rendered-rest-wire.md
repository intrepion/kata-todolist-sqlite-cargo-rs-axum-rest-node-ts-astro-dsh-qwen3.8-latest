# Client-rendered app over a real REST wire

**Status**: accepted

Astro is normally a server-rendering framework, but we decided this app renders statically and talks to the Axum API directly from the browser via `fetch()`. Alternatives were SSR (Astro server pages calling the API) and server endpoints that proxy it.

- **Hard to reverse**: moving an existing data flow from browser to server (or vice versa) means rewriting every handler's error handling, state management, and test layout.
- **Surprising without context**: an Astro reader will expect SSR or islands; finding none looks like a mistake.
- **Real trade-off**: SSR would hide the REST layer and the CORS surface — exactly what this kata exists to practice. The client-rendered wire also keeps the REST contract the single source of truth for clients.
