## 2026-06-07 - Cost Guard Path Normalization Bypass

**Vulnerability:** Raw path inputs containing query parameters, hash fragments, or missing leading slashes could bypass regex matching in classifyCost, causing billed resource creation or cost-increasing actions to skip confirmation requirements.

**Learning:** URL paths in generic request tools can contain query parameters or fragments that fail exact-path regexes like ^/servers/?$.

**Prevention:** Always normalize API paths by stripping query strings and hash fragments and ensuring a leading slash before running cost classification checks.
