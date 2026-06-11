# SKILL: DEBUGGING & ERROR RECOVERY
description: Guides systematic root-cause debugging for the React-to-WordPress hybrid architecture. Use when builds break, hydration fails, or you encounter unexpected runtime errors.

## The Stop-the-Line Rule
When a crash occurs (e.g., a TypeError or a blank widget):
1. STOP adding features.
2. PRESERVE evidence (e.g., the stack trace).
3. DIAGNOSE the PHP-to-React bridge before touching component logic.
4. FIX the root cause using defensive fallbacks.
5. VERIFY by running `npm run build` and checking the live WordPress frontend.

## The Triage Checklist (Hybrid Architecture)

### Step 1: Isolate the Hydration Layer
Most crashes in this stack occur because the data passed from PHP to React is missing, malformed, or `undefined`.
* **Check the DOM:** Does `window.Payload` exist in the `<head>` or `<body>`? Is the JSON perfectly formatted?
* **Check the Transposition:** Is the Object-of-Arrays being safely transposed into an Array-of-Objects before being passed to React state?

### Step 2: Safe Fallback Patterns (Defensive Rendering)
Never trust external API or PHP data. You must always use safe fallbacks to prevent fatal TypeErrors (like `Cannot read properties of undefined`).

```tsx
// DANGEROUS (Will crash if data is missing):
const status = weatherData.status.toLowerCase();

// SAFE (Defensive Rendering):
const status = String(weatherData?.status || '').toLowerCase();
```

### Step 3: Error Boundary Verification
If a component fails, it must not take down the entire WordPress page. 
* Ensure the failing component is wrapped in `<WidgetErrorBoundary>`.
* Ensure the boundary catches the error and displays a safe, branded fallback UI rather than a white screen.

## Treating Error Output as Clues
Stack traces (e.g., `at sV (bundle.js:460)`) are maps to the broken data bridge. When you see a hydration mismatch or undefined property, immediately trace it back to the exact prop or API variable that failed to load from the WordPress backend.
