# v0.2 Roadmap

This document tracks proposed work for the next iteration of `@amadeus-it-group/ngrx-devtool`. GitHub Issues are currently disabled on this fork; once enabled, each section below should be promoted to its own issue.

Themes: **AI-agent friendliness**, **replay/testing**, **release hygiene**, **fork maintenance**.

---

## 1. feat(server): Add MCP endpoint so AI agents can subscribe to the live NgRx stream
**Labels:** enhancement, ai, server

### Summary
Expose the existing WebSocket action/state/effect stream (currently `ws://localhost:4000` in `index.ts`) over the <a href="https://modelcontextprotocol.io">Model Context Protocol</a> so AI coding agents can read live NgRx state while debugging.

### Acceptance criteria
- [ ] MCP server starts on a configurable port
- [ ] At least 3 read-only tools exposed (`getCurrentState`, `getActionHistory`, `getEffectInvocations`)
- [ ] Documented in `docs/`
- [ ] Unit tests in Jest

---

## 2. feat(devtool): Record &amp; export action sequences as replayable Jest fixtures
**Labels:** enhancement, testing, dx

### Summary
Let users hit "Record" in the UI, perform a flow, then export the captured action sequence + initial state as a Jest test fixture compatible with this repo's existing `jest.config.js`.

### Acceptance criteria
- [ ] Recording toggle in UI
- [ ] JSON export of a session
- [ ] Generator that emits a runnable `.spec.ts`
- [ ] Example in `projects/ngrx-devtool-demo/`

---

## 3. feat(ui): Add "Explain with AI" pane to Effects and Performance panels
**Labels:** enhancement, ui, ai

### Summary
Optional side-pane in `projects/ngrx-devtool-ui/src/components/effects-panel/` and `performance-panel/` that sends the selected effect/metric to an LLM and renders a plain-English explanation. BYO key; no telemetry.

### Acceptance criteria
- [ ] Settings UI for provider + key
- [ ] "Explain" button in both panels
- [ ] Streaming response render
- [ ] Documented privacy stance in `docs/`

---

## 4. docs: Publish `llms.txt` and structured API manifest for agent consumption
**Labels:** documentation, ai

### Summary
Add an <a href="https://llmstxt.org/">`llms.txt`</a> at the docs site root plus a JSON manifest describing `provideNgrxDevTool` options so coding agents configure the library correctly first try.

### Acceptance criteria
- [ ] `docs/static/llms.txt` published at site root
- [ ] `docs/static/api.json` with typed option schema
- [ ] Linked from README

---

## 5. chore(release): Automate releases via conventional commits + semantic-release
**Labels:** chore, ci, release

### Summary
`commitlint.config.js` and Husky hooks are already in place. Wire up `semantic-release` (or Changesets) so merges to `master` cut npm releases automatically.

### Acceptance criteria
- [ ] `.github/workflows/release.yml` added
- [ ] Conventional-commit driven version bumps
- [ ] `CHANGELOG.md` auto-generated
- [ ] npm provenance enabled

---

## 6. chore: Update `package.json` `repository` field to point at this fork
**Labels:** chore, good first issue

### Summary
`package.json` still references `https://github.com/AmadeusITGroup/ngrx-devtool`. If this fork will publish or diverge, the field should match.

### Acceptance criteria
- [ ] `repository.url` updated
- [ ] `bugs` and `homepage` fields reviewed
- [ ] Decide: keep `"private": true` or publish under a new scope?

---

## 7. feat(server): Add `/ai-explain` HTTP route to the Express UI server
**Labels:** enhancement, server, ai

### Summary
Add `POST /ai-explain` to the Express app in `index.ts` that accepts `{ actions, state, question }` and proxies to a configured LLM provider. CLI flag `--ai` enables it.

### Acceptance criteria
- [ ] Route with input validation
- [ ] Provider config via env vars
- [ ] CLI flag `--ai`
- [ ] Jest tests with mocked provider

---

## 8. chore: Sync fork with upstream `AmadeusITGroup/ngrx-devtool` and document policy
**Labels:** chore, maintenance

### Summary
This fork is currently untouched relative to upstream. Establish a sync cadence and document it.

### Acceptance criteria
- [ ] `.github/workflows/upstream-sync.yml` added (scheduled weekly PR from upstream `master`)
- [ ] Sync policy documented in `CONTRIBUTING.md`
- [ ] Conflict-resolution guidance for maintainers

---

## How to use this document
- When Issues is enabled on this repo, copy each numbered section into a new issue and apply the listed labels.
- Update the checkboxes here as work progresses, or delete sections that become live issues.
