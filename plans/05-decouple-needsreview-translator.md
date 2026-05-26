# Plan: Decouple needsReview from in-memory Translator

Source: PLANNING.md -> Next Execution Queue (Item 5).

## Scope
- Extract decision logic into a pure domain service
- Remove runtime state dependency from review decision
- Add deterministic edge-case tests

## Acceptance Criteria
- Pure/testable decision service extracted
- No hard dependency on in-memory Translator lifecycle
- Deterministic unit tests cover edge cases