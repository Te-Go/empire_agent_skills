# SKILL: SEARCH & ANSWER ENGINE OPTIMIZATION (SEO / GEO / AEO)

Because our React application is injected into WordPress, you must adhere to strict "Dual-Rendering" laws to ensure AI Answer Engines (Perplexity, ChatGPT) and Googlebot can read our data instantly.

1. THE PHP SEO BRIDGE (CRITICAL): 
React must NEVER be the sole owner of data. The PHP bridge (e.g., `sinan-weather-bridge.php`) must inject the raw data array into a `<script type="application/ld+json">` tag in the DOM *before* React boots. This Schema.org JSON-LD is what AEO/GEO bots read.

2. SEMANTIC HTML IN REACT:
Do not use generic `<div>` tags for layout. You must build React components using strict HTML5 semantics. 
- Use `<article>` for main widgets.
- Use `<section>` for categorical data.
- Use `<time>` for timestamps (crucial for weather/finance bots).
- Use `<dl>`, `<dt>`, and `<dd>` for data-heavy key-value pairs (e.g., Wind Speed, Humidity).

3. NO REACT META TAGS:
Do NOT use libraries like `react-helmet` to manage `<title>` or `<meta>` tags. WordPress (via RankMath or Yoast) handles the document `<head>`. React is strictly confined to the `<body>`. 

4. SKELETON PERFORMANCE (LCP):
To satisfy Google's Core Web Vitals (Largest Contentful Paint), the PHP fallback HTML (`<div id="weather-app">Loading...</div>`) must perfectly match the exact height and width of the final React widget. There must be ZERO Cumulative Layout Shift (CLS) when React hydrates the DOM.
