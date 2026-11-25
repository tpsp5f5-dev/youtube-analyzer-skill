---
type: grilling
mode: HITL
status: open
blocked_by:
  - 01-baseline-policy.md
---

# Which minimal host/platform/engine matrix is required before claiming support?

## Why this needs a decision

Both local READMEs explicitly say a fresh-account install and every platform/provider combination have not been tested. Upstream reports one Windows local Watch run, not portable acceptance. Testing every agent, OS and provider is unbounded and may require accounts, downloads or paid calls.

## Suggested decision

Select one primary skill-capable host and OS for fresh-install acceptance. Require a no-Watch assessment and, if visual review is claimed supported, one explicit local-Watch path. Treat Gemini and other hosts as unverified until separately authorized and tested. Add a second OS only if portable-install claims require it. This is a recommendation, not existing policy.

## Done when

Record required host/version, OS, engine paths, test owner, authorized public test media, permitted dependency setup, resource limits and pass/fail criteria. State which configurations remain unverified. No provider credentials belong in the record, and choosing a matrix does not itself authorize spending or machine-wide setup.
