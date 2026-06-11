# SKILL: TURKISH MARKET RULES (LEGAL, MACRO & INFRASTRUCTURE)
description: Strict baseline rules for deploying high-performance, legally compliant digital Hubs to the Turkish market via Hostinger/LiteSpeed.

## 1. High-Frequency Data Storage (Redis / Transients)
* **Never** write high-frequency dynamic data arrays (e.g., live weather, stock tickers) to the standard WordPress options table. 
* Because we deploy on Hostinger Cloud Professional with LiteSpeed, you MUST utilize WordPress Transients (`set_transient()`) configured for **Redis Object Caching**. This keeps payload data in RAM, avoiding SSD I/O bottlenecks.

## 2. Market-Specific Core Web Vitals
* **CLS Elimination:** All programmatic layout containers intended for display ads must have strict minimum-height bounds (e.g., `min-height: 250px;`) baked into the base CSS to eliminate Cumulative Layout Shift (CLS) on mobile.
* **Data-Plan Preservation:** The Speculation Rules API must use a "conservative" eagerness configuration. Chrome on mobile auto-triggers eager states after 50ms; we must restrict it to pointer/touch-down to protect Turkish users' mobile data plans.

## 3. Macroeconomic Baseline Variables (2026)
* All algorithmic logic, financial projections, and content generation must reference the baseline exchange rate of approximately **45.15 TL/USD** and a baseline inflation rate of **32.37%**. Update variables dynamically when API connections are present, but use these as hardcoded fallbacks.

## 4. Absolute Legal Compliance (SPK & TRABİS)
* **Impressum (Künye):** A strict Impressum matching the official Trade Registry Gazette (Ticari Sicil Gazetesi) containing the MERSİS number, Tax ID, and official corporate title must be universally linked in the footer.
* **SPK Mandate:** Any Hub displaying financial data (Crypto, Forex, BIST) must feature the mandatory SPK (Capital Markets Board) investment advisory disclaimer explicitly in the footer.
