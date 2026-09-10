## 2026-08-30 - Normalize paths before cost classification

**Vulnerability:** Input paths with query strings (e.g. `/servers?foo=bar`) or fragments bypassed cost classification regexes like `/^\/servers\/?$/i`.

**Learning:** URL query parameters and fragments alter the path string passed to cost classification functions, causing regex anchored at `$` to fail to match billed endpoints.

**Prevention:** Always strip query parameters and hash fragments and ensure leading slash normalization before matching paths against cost guard regexes.
