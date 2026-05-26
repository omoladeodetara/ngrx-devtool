# Plan: Refactor /ingest onto shared helper

Source: PLANNING.md -> Next Execution Queue (Item 2).

## Scope
- Route /ingest through a shared normalization/validation helper
- Preserve existing API behavior
- Add parity regression tests

## Acceptance Criteria
- /ingest delegates to shared helper
- Backward-compatible behavior
- Regression tests prove parity before/after