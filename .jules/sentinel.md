## 2026-06-07 - Cost Classification Path Normalization

**Vulnerability:** Input paths with query parameters (`?...`), hash fragments (`#...`), or missing leading slashes bypassed regex matching in `classifyCost`, allowing billed resources to bypass the cost guard.

**Learning:** `classifyCost` receives raw relative path inputs from generic API request tools. Matching regexes with end-of-string anchors (`$`) against unnormalized raw paths allows appended query strings to circumvent endpoint regex matching while still hitting the target API endpoint.

**Prevention:** Always strip query parameters and hash fragments and ensure a leading slash before evaluating path classification or authorization regexes.
