## 2026-06-07 - Normalize input paths before cost guard regex matching

**Vulnerability:** Unnormalized path strings (missing leading slash, query string parameters, or hash fragments) caused regex matching in `classifyCost` to fail, allowing requests for billed resource creation to bypass the cost guard.

**Learning:** When regexes use string boundary anchors (`^` and `$`) to match API resource paths, any appended query parameters (`?`), hash fragments (`#`), or omitted leading slashes prevent matches unless paths are normalized prior to classification.

**Prevention:** Always strip query strings and fragments and ensure a leading slash on path inputs before checking billing or cost-guard classification regexes.
