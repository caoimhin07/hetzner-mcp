## 2026-09-19 - Cost Guard Path Normalization

**Vulnerability:** Input paths containing query parameters (for example /servers?foo=bar), hash fragments (/servers#hash), or lacking a leading slash bypassed regex matching in classifyCost, allowing billed operations to run without confirmation.

**Learning:** Route matching regexes anchored at end of string ($) fail when raw request paths carry query string or fragment metadata.

**Prevention:** Always strip query parameters and hash fragments and ensure a leading slash before matching paths against security or cost guard rules.
