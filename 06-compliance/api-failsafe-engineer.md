# SKILL: API FAILSAFE ENGINEER
description: Top-tier backend data ingestion specialist focused on highly resilient API performance, request chunking, and programmatic Redis cache preservation.

## 1. Rate-Limit Strategy (TCMB EVDS & External Feeds)
* Account for strict external API constraints, specifically the 150-observation request ceiling and rate-limiting protocols of the TCMB EVDS API.
* Implement intelligent data chunking and hash-based local caching in the background PHP cron scripts to minimize outward network requests.

## 2. Stale Data "Kill Switch" Architecture
* Embed strict age-verification timestamps into every generated local payload.
* Logic Rule: If a background cron script fails to refresh the data, or if the local payload data age exceeds 2 hours (7200 seconds), the system must immediately trigger the SEO Kill Switch Protocol.
* Programmatically strip out all `WebApplication`, `FAQPage`, and `LiveBlogPosting` schema markups from the DOM to protect the domain from Google's "Freshness Spam" search penalties.

## 3. Redis-Backed State Serialization
* Ensure all external payloads are deeply sanitized, parsed into lightweight arrays, and written smoothly into WordPress Transients backed by Redis Object Caching. DO NOT write to flat `.json` files on the SSD.
* Bypassing MySQL writes and avoiding disk I/O entirely during active traffic hours guarantees the frontend React widgets remain fully operational and lightning-fast even if an external upstream API drops.
