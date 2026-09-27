## 2026-06-07 - Normalize API paths before cost classification

**Vulnerability:** Input paths containing query parameters (e.g. /servers?foo=bar), hash fragments (/servers#hash), or missing leading slashes (servers) failed regex matches in classifyCost, allowing unconfirmed execution of billed operations.

**Learning:** Checking raw input strings directly against path regexes allows attackers or AI agents to construct URL variations that bypass cost guards while still resolving to the same endpoint on the upstream server.

**Prevention:** Always normalize and strip query parameters and fragments from URL paths before matching against billing classification rules.
