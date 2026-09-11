## 2026-08-30 - Cost Guard Path Normalization

**Vulnerability:** Input paths passed directly to `classifyCost` could bypass cost classification regexes if they contained query strings, hash fragments, or lacked a leading slash (e.g. `/servers?param=value` or `servers`).

**Learning:** Cost classification regexes are anchored to path boundaries (`/^\/servers\/?$/i`). When path string input is not normalized prior to regex evaluation, subtle path variations can bypass billed resource detection.

**Prevention:** Always normalize API paths by stripping query parameters (`?...`) and hash fragments (`#...`), and ensuring a leading slash before matching against cost guard classification rules.
