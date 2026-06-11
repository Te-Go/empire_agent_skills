# SKILL: FULL-STACK PERFORMANCE GURU
description: Top-tier full-stack engineer skill optimized specifically for Hostinger Cloud Professional, LiteSpeed Web Server, Redis Object Caching, WordPress headless-routing, and React micro-frontend architecture.

## 1. Zero Relational Ingestion (Database & Cron Protection)
* **Disable wp-cron.php:** Prevent relational database thrashing and option table locks. Write independent backend Linux server crontabs that execute precisely every 60 seconds for high-frequency APIs (e.g., TCMB EVDS, Open-Meteo).
* **Redis-Backed Transients:** Fetch remote payloads, parse them, and save them EXCLUSIVELY via WordPress Transients (`set_transient()`) backed by Redis Object Caching. Do not stream to flat `.json` SSD files, and do not write to standard SQL tables.

## 2. Micro-Frontend React Hydration
* **The SEO Shell:** Treat WordPress purely as an SEO-optimized host environment for URL routing, metadata output, and initial DOM structure.
* **Shortcode Injection:** Inject interactive features (Charts, Bi-directional calculators, Event Hubs) via custom shortcodes containing lightweight React components.
* **Instant State Ingestion:** React must ingest the server's pre-loaded state instantly via the global `window.Payload` object. This eliminates secondary database/API fetches from the client, keeping Largest Contentful Paint (LCP) strictly under 2.5 seconds.

## 3. Strict Monetization Defense & Layout Stability
* **Ad-Container Geometry:** Mitigate Core Web Vitals degradation from programmatic ad networks (AdSense/Ezoic). Enforce absolute `min-height` CSS wrappers around all lazy-loaded ad placements above and below the fold.
* **Zero CLS:** Lock layout geometry during initial server-side rendering to maintain a Cumulative Layout Shift (CLS) score under 0.1, exploiting the technical layout debt of legacy incumbents.
