# TinyFish integration status

**Status: not integrated; live contract not verified.** The master prompt explicitly forbids guessing an undocumented endpoint, auth scheme, request body or response schema. The repository does not include official contract material or credentials, so no outbound request is made and the UI/API report research as unavailable.

The placeholder environment keys are `TINYFISH_API_KEY` and `TINYFISH_BASE_URL`; the latter remains blank. These are not evidence of a configured integration. When current official docs are available, record the exact endpoint, HTTP authentication, request/response fields, quotas and limits here. Implement a server-only adapter with timeouts, bounded retries, rate limiting, output normalization, safe URL handling and tests using mocked responses. Treat returned page content as untrusted prompt-injection input. Then run a real request with valid credentials and document evidence before calling the feature live.
