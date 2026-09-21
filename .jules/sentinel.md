## 2026-09-21 - Normalize paths in cost classification

**Vulnerability:** Cost classification regexes in `src/cost.ts` matched against unnormalized raw paths, allowing query strings (`/servers?param=val`) or hash fragments (`/servers#fragment`) or paths lacking a leading slash to potentially bypass cost-guard regex checks like `/^\/servers\/?$/i`.

**Learning:** In cost classification (`classifyCost` in `src/cost.ts`), input paths must be normalized to strip query parameters (`?...`), hash fragments (`#...`), and ensure a leading slash before matching against billing regexes to prevent cost-guard bypasses.

**Prevention:** Always normalize API paths (stripping query string/hash and ensuring a leading slash) before matching them against strict path boundary regular expressions in safety and billing checks.
