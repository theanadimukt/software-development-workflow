# /build routing

Goal: deliver the smallest coherent implementation slice.

Start with `incremental-implementation`. Add `test-driven-development` for behavior with meaningful regression risk, `frontend-ui-engineering` for user-facing UI, `api-and-interface-design` for endpoints, events, or contracts, and `source-driven-development` for external SDKs or platform APIs. Add `browser-testing-with-devtools` for browser-dependent work and `security-and-hardening` for authentication, untrusted input, payments, permissions, or extension capabilities.

Examples: a profile page can select implementation, UI, and tests; webhook processing can additionally select API and security expertise; a browser extension content script can select source verification, browser testing, and security where warranted.
