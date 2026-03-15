---
name: web-search
description: Search the web and fetch page content for up-to-date information.
metadata: {"nanobot":{"emoji":"🔍","always":true}}
---

# Web Search

Use the `web_search` and `web_fetch` tools to find current information.

## When to Search

- Questions about recent events, news, or current data
- Factual questions you're unsure about
- Requests for URLs, documentation, or references
- Anything beyond your training data cutoff

## web_search

Search the web and get titles, URLs, and snippets.

```
web_search(query="your search query", count=5)
```

- `query`: what to search for (be specific)
- `count`: number of results (1-10, default 5)

### Tips

- Use specific, descriptive queries (not single words)
- Include the year for time-sensitive topics
- Rephrase and retry if results are poor
- Combine multiple searches to cross-reference facts

## web_fetch

Fetch and extract readable content from a URL found via search.

```
web_fetch(url="https://example.com", extractMode="markdown")
```

- `url`: page to fetch
- `extractMode`: `"markdown"` (default) or `"text"`
- `maxChars`: character limit (default 50000)

### Workflow

1. `web_search` to find relevant URLs
2. `web_fetch` on the best result to read full content
3. Summarize findings for the user with source links

## Providers

Configured via `web.search.provider` in nanobot config:

| Provider    | API Key Required | ENV Variable      |
|-------------|-----------------|-------------------|
| duckduckgo  | No              | —                 |
| brave       | Yes             | BRAVE_API_KEY     |
| tavily      | Yes             | TAVILY_API_KEY    |
| jina        | Yes             | JINA_API_KEY      |
| searxng     | No (self-hosted)| SEARXNG_BASE_URL  |

Default: `duckduckgo` (free, no API key needed). If brave/tavily/jina keys are missing, they auto-fallback to duckduckgo.

## Setup (WSL/Linux)

```bash
pip install duckduckgo-search
# or for the newer package name:
pip install ddgs
```

No other configuration needed — DuckDuckGo works out of the box.
