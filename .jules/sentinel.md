## 2026-08-30 - Cost-Guard Path Bypass via Query Strings and Unnormalized Paths

**Vulnerability:** Input paths containing query parameters (`?...`), hash fragments (`#...`), or lacking leading slashes (`servers`) failed exact-match cost classification regexes in `classifyCost`, allowing billed operations to bypass confirmation guards.

**Learning:** Cost evaluation regexes like `/^\/servers\/?$/i` assume sanitized path structures. Upstream input must be normalized to strip query/hash suffixes and ensure a canonical leading slash before cost evaluation.

**Prevention:** Normalize input paths (`split('?')[0].split('#')[0]` and leading `/`) prior to testing against billing pattern regexes in `classifyCost`.
