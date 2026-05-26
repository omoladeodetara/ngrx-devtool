# Plan: Webhook parity

Source: PLANNING.md -> Next Execution Queue (Item 4).

## Scope
- Reuse shared mapping/validation in webhook and /ingest
- Align idempotency behavior across both paths
- Add parity tests for equivalent events

## Acceptance Criteria
- Shared mapping/validation rules reused
- Idempotency behavior matches /ingest
- Parity tests pass for logical-equivalent events