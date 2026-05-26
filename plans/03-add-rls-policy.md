# Plan: Add RLS policy

Source: PLANNING.md -> Next Execution Queue (Item 3).

## Scope
- Define tenant-scoped RLS for read/write/update/delete
- Add policy tests for cross-tenant denial
- Define explicit service/admin exceptions

## Acceptance Criteria
- Tenant-scoped policies in place
- Cross-tenant access denied by tests
- Service/admin exceptions are explicit and audited