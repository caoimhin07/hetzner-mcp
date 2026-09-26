## 2026-09-26 - Cost Classification Path Normalization

**Vulnerability:** Cost guard checks in `classifyCost` could be bypassed when an input path contained query parameters (e.g. `/servers?param=value`), hash fragments, or lacked a leading slash, preventing strict regex matching against billed endpoints.

**Learning:** `classifyCost` evaluates raw path input against strict endpoint regular expressions. When paths contain extra URL components like query strings or fragments, regexes anchored with `$` fail to match, leading to bypass of billing confirmation prompts.

**Prevention:** Always normalize input paths by stripping query parameters (`?...`) and hash fragments (`#...`), trimming whitespace, and ensuring a leading slash before matching against cost classification regexes.
