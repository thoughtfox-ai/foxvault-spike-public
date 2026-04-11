# foxvault-source-scanner (spike)

Feasibility spike for the GitHub Actions dispatcher design at [docs/superpowers/specs/2026-04-11-source-review-github-actions-design.md](https://github.com/thoughtfox-ai/Foxvault/blob/feat/stripe-go-live/docs/superpowers/specs/2026-04-11-source-review-github-actions-design.md).

This repo is a throwaway: it exists to verify the dispatch → Actions → callback loop works end-to-end before committing to a full implementation plan. No Semgrep, no real checkout, no real findings — just payload validation + HMAC round-trip.

Trigger via:

```bash
gh api -X POST \
  /repos/thoughtfox-ai/foxvault-source-scanner-spike/dispatches \
  -F event_type=source-review \
  -F 'client_payload[scanId]=test-scan-1' \
  -F 'client_payload[productId]=test-product-1' \
  -F 'client_payload[commitSha]=deadbeef' \
  -F 'client_payload[callbackUrl]=https://httpbin.org/post'
```
