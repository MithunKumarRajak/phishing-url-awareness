# Test Results

Python version used: 3.11.0 | Operating system: Windows | Date: 2026-11-04

| # | Input | Expected result | Actual result | Pass/Fail |
|---|-------|-----------------|---------------|-----------|
| 1 | `https://example.com` | No listed warning signs | No listed warning signs found. This does NOT prove safety. | PASS |
| 2 | `http://192.0.2.10/account` | IP address + HTTP | Uses an IP address instead of a familiar domain; Uses HTTP. HTTPS alone does not prove trust. | PASS |
| 3 | `http://example.com@sample.invalid/login` | @ symbol + HTTP | Contains an @ symbol; inspect carefully; Uses HTTP. HTTPS alone does not prove trust. | PASS |
| 4 | `https://a.b.c.d.e.example.invalid/path` | Many hostname segments | Contains many hostname segments/subdomains. | PASS |
| 5 | `https://xn--example.invalid/` | Punycode-style hostname | Contains a punycode-style hostname. | PASS |

## Additional checks

| Input | Expected result | Actual result | Pass/Fail |
|---|---|---|---|
| *(empty input)* | No URL entered | No URL entered. | PASS |
| `http://[bad` | Clear format error, no crash | This text is not a valid URL format. | PASS |
| `http://example.com:bad` | Clear format error, no crash | This text is not a valid URL format. | PASS |
| `https://example.invalid/` + 101 `a` characters | Unusually long URL | Unusually long URL (over 100 characters). | PASS |

## Notes

The checker only reads URL text; it never visits a website or sends a request.
The most important limitation is that no warning signs does not prove a URL is safe.
Malformed input is handled as a result instead of stopping the program.
