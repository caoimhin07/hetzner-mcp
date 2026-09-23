## 2026-09-23 - Cost Guard Path Normalization

**Vulnerability:** Input paths containing query parameters (for example /servers?foo=bar), hash fragments, or lacking leading slashes bypassed the cost classification regex checks because exact end-of-string matching ($) failed.

**Learning:** Cost classification logic must normalize and clean raw path inputs (stripping query parameters and hash fragments, decoding percent-encoding safely, and adding leading slashes) before matching against cost-guard regular expressions.

**Prevention:** Ensure any security guard that evaluates path-based permissions or billing rules normalizes the path to its canonical form prior to regex or path comparison.
