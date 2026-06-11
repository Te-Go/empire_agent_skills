THE TEDDER STACK: LAWS OF PHYSICS
Architecture: React (Vite) frontend injected into PHP/WordPress (Hostinger LiteSpeed) via shortcode.

1. THE PRE-RENDER TRAP: You must process `window.Payload` globally outside the React component lifecycle to provide a safe `INITIAL_STATE`. Do not transpose data inside a `useEffect` hook on the first render.
2. ZERO-TRUST HYDRATION: You must never map raw PHP/REST API data directly into React state. Payloads must be sanitized and transposed (e.g., Object-of-Arrays to Array-of-Objects) BEFORE React mounts.
3. DEFENSIVE RENDERING: You are strictly forbidden from using raw `.split()`, `.toLowerCase()`, or `.slice()` methods on API data. You MUST use optional chaining (`?.`) and safe fallbacks (`|| '0'`).
4. THE PHANTOM DEPLOYMENT: When configuring `vite.config.ts`, `outDir` must point directly to the WordPress theme directory (`generatepress_child/dist`). 

