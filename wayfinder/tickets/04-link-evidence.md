---
type: task
mode: AFK
status: open
blocked_by:
  - 02-align-baseline.md
---

# Can the link ledger distinguish failed access from absent or broken resources?

## Evidence

The current reference warns that crawler failure does not prove a broken public link, but lacks concrete status examples and named-resource-without-URL guidance. [Open PR #4](https://github.com/grevalyn/youtube-analyzer-skill/pull/4) and [open PR #5](https://github.com/grevalyn/youtube-analyzer-skill/pull/5) address those gaps.

## Work

Review the proposed rules and add a small synthetic description/link ledger covering redirects, duplicate destinations, 403, 429, 503, 404/410 and a named tool with no standalone URL. Preserve original public target, final destination, observed status, retrieval date, relevance and uncertainty. Keep sensitive query parameters redacted.

## Done when

- 403/429/503 examples are not labeled broken merely because retrieval failed. A 503 cause remains unknown unless evidence establishes bot protection or another cause.
- 404/410 or independently confirmed removal has an explicit basis for a broken classification.
- A missing standalone URL remains a gap rather than an unrelated repository substitute.
- Every supplied distinct URL has a ledger entry, duplicate destinations retain context, and summary coverage matches the ledger.
- Sanitized fixtures and expected classifications are ready for ticket 08 without live crawling or form submission.
