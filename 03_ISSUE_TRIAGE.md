# Issue Triage Report

## Open Issues Summary

| # | Title | Type | Labels | Created | Comments |
|---|-------|------|--------|---------|----------|
| #364 | custom react state to custom button passed to `chatInputArea`, state updates don't cause re-render | help | | 2025-04-20 | 1 |
| #361 | chatButtonStyle does not apply custom width/height | bug | | 2025-04-05 | 1 |
| #350 | Add unit test cases for useSubmitInputInternal hook | task | good first issue, hacktoberfest | 2025-03-23 | 0 |
| #349 | Add unit test cases for VoiceService | task | good first issue, hacktoberfest | 2025-03-23 | 0 |
| #340 | Add unit test cases for BotMessage component | task | good first issue, hacktoberfest | 2025-03-23 | 0 |
| #298 | how can i access previous chat history without going through welcome message | help | | 2025-01-18 | 2 |
| #270 | How can i use this package as a javascript module? | help | | 2024-10-15 | 1 |
| #36 | Add commitizen to format and lint commits | feat | | 2023-08-07 | 7 |

---

## Triage Table

| Issue | Type | Clarity | Repro Available | Existing PR? | Estimated Size | Risk | Selected? | Notes |
|-------|------|---------|-----------------|-------------|----------------|------|-----------|-------|
| #364 | help | medium | unclear | no | medium | low | no | User needs help with React integration pattern; not a bug |
| #361 | bug | high | partially | no | small | low | **yes** | Style prop bug; likely one-line fix in style application |
| #350 | task/test | high | yes | no | small | low | **yes** | Direct request for test coverage on existing hook |
| #349 | task/test | high | yes | no | small | low | **yes** | Direct request for test coverage on existing service |
| #340 | task/test | high | yes | no | small | low | **yes** | Direct request for test coverage on existing component |
| #298 | help | medium | no | no | medium | low | no | Feature question about chat history access; would need API design |
| #270 | help | high | no | no | small | low | no | Documentation question; can be addressed with README update |
| #36 | feat | medium | no | no | large | medium | no | Requires tooling change and commit history rewrite |

---

## Selected Issues for PRs

| Issue | Reason for Selection |
|-------|----------------------|
| **#361** | Bug with clear reproduction; small diff; low risk; directly testable |
| **#350** | Test coverage improvement; good first issue; low risk |
| **#349** | Test coverage improvement; good first issue; low risk |
| **#340** | Test coverage improvement; good first issue; low risk |

---

## Non-Selected Issues

| Issue | Reason for Non-Selection |
|-------|--------------------------|
| #364 | Help request — needs design discussion, not a clear PR candidate |
| #298 | Help request — needs API design, not a straightforward fix |
| #270 | Documentation question, not a code issue |
| #36 | Large tooling change with commit history implications; would need RFC |

---

## Task Breakdown

### Test Coverage Tasks (Issues #340, #349, #350)

| File | Current Test Status | Lines to Cover (approx) |
|------|---------------------|-------------------------|
| `src/components/ChatBotBody/BotMessage/BotMessage.tsx` | no test file | ~77 lines |
| `src/services/VoiceService.ts` | has test file, needs review | ~200 lines |
| `src/hooks/internal/useSubmitInputInternal.ts` | no test file | ~150 lines |

### Bug Fix Task (Issue #361)

| File | Problem | Fix Complexity |
|------|---------|----------------|
| `src/components/ChatBotButton/ChatBotButton.tsx` | `chatButtonStyle` not applying width/height | Likely a CSS specificity issue |

---

## Triage Notes

1. **Three "good first issue" tasks (#340, #349, #350)** are explicitly tagged and well-scoped — ideal PR candidates.
2. **Issue #361** is a clear bug with minimal risk; the fix should be straightforward.
3. **Issues #298, #364, #270** are help requests that need design discussion before they can become PRs.
4. **Issue #36** is a feature that requires tooling decision and would be disruptive.