# Plan: De-dup on (tenant, fingerprint, target)

Source: PLANNING.md -> Next Execution Queue (Item 1).

## Scope
- Introduce uniqueness guarantees for (tenant, fingerprint, target)
- Make write path idempotent under retries/concurrency
- Add migration/backfill for historical duplicates

## Acceptance Criteria
- Unique index/constraint on (tenant, fingerprint, target)
- Idempotent write behavior documented and tested
- Concurrency test proving no duplicate rows
- Migration/backfill for existing duplicate rows