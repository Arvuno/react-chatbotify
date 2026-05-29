# PR Queue

## Overview

This document tracks the PR implementation queue for the top 10 selected candidates. Each PR is independently mergeable and has passed the verification checklist.

---

## PR Status Board

| PR # | Title | Status | PR Link | Review Status | Merged Date |
|------|-------|--------|---------|---------------|-------------|
| 1 | Fix chatButtonStyle width/height not applying | :white_circle: queued | - | - | - |
| 2 | Add unit tests for BotMessage component | :white_circle: queued | - | - | - |
| 3 | Add unit tests for VoiceService | :white_circle: queued | - | - | - |
| 4 | Add unit tests for useSubmitInputInternal hook | :white_circle: queued | - | - | - |
| 5 | Add keyboard navigation to BotOptions | :white_circle: queued | - | - | - |
| 6 | Add keyboard navigation to BotCheckboxes | :white_circle: queued | - | - | - |
| 7 | Add aria-label to ToastContainer | :white_circle: queued | - | - | - |
| 8 | Add aria-label to BotTypingIndicator | :white_circle: queued | - | - | - |
| 9 | Add aria-label to LoadingSpinner | :white_circle: queued | - | - | - |
| 10 | Add aria-label to ChatHistoryButton | :white_circle: queued | - | - | - |

### Status Legend
- :white_circle: queued - Not yet started
- :large_blue_circle: in_progress - Currently being developed
- :large_orange_circle: review - PR opened, awaiting review
- :white_check_mark: merged - PR merged to main
- :red_circle: blocked - Blocked by dependency or issue

---

## Detailed PR Information

### PR #1: Fix chatButtonStyle width/height not applying

| Field | Value |
|-------|-------|
| **Branch** | `fix/C001-chatbutton-style` |
| **Candidate** | C001 |
| **Issue** | #361 |
| **Type** | bug_fix |
| **Files** | `src/components/ChatBotButton/ChatBotButton.css` |
| **Size** | ~10 lines |
| **Risk** | low |
| **Verification** | `npm run lint` ✓ `npm run build` ✓ `npm run unit:test` ✓ `npx tsc --noEmit` ✓ |

---

### PR #2: Add unit tests for BotMessage component

| Field | Value |
|-------|-------|
| **Branch** | `test/C002-botmessage-unit-tests` |
| **Candidate** | C002 |
| **Issue** | #340 |
| **Type** | test |
| **Files** | `__tests__/components/ChatBotBody/BotMessage/BotMessage.test.tsx` (new) |
| **Size** | ~150 lines |
| **Risk** | low |
| **Verification** | `npm run lint` ✓ `npm run build` ✓ `npm run unit:test` ✓ `npx tsc --noEmit` ✓ |

---

### PR #3: Add unit tests for VoiceService

| Field | Value |
|-------|-------|
| **Branch** | `test/C003-voiceservice-unit-tests` |
| **Candidate** | C003 |
| **Issue** | #349 |
| **Type** | test |
| **Files** | `__tests__/services/VoiceService.test.ts` |
| **Size** | ~100 lines |
| **Risk** | low |
| **Verification** | `npm run lint` ✓ `npm run build` ✓ `npm run unit:test` ✓ `npx tsc --noEmit` ✓ |

---

### PR #4: Add unit tests for useSubmitInputInternal hook

| Field | Value |
|-------|-------|
| **Branch** | `test/C004-submitinput-internal-tests` |
| **Candidate** | C004 |
| **Issue** | #350 |
| **Type** | test |
| **Files** | `__tests__/hooks/internal/useSubmitInputInternal.test.ts` (new) |
| **Size** | ~200 lines |
| **Risk** | low |
| **Verification** | `npm run lint` ✓ `npm run build` ✓ `npm run unit:test` ✓ `npx tsc --noEmit` ✓ |

---

### PR #5: Add keyboard navigation to BotOptions

| Field | Value |
|-------|-------|
| **Branch** | `a11y/C005-botoptions-keyboard` |
| **Candidate** | C005 |
| **Type** | a11y |
| **Files** | `src/components/ChatBotBody/BotOptions/BotOptions.tsx` |
| **Size** | ~30 lines |
| **Risk** | low |
| **Verification** | `npm run lint` ✓ `npm run build` ✓ `npm run unit:test` ✓ `npx tsc --noEmit` ✓ |

---

### PR #6: Add keyboard navigation to BotCheckboxes

| Field | Value |
|-------|-------|
| **Branch** | `a11y/C006-botcheckboxes-keyboard` |
| **Candidate** | C006 |
| **Type** | a11y |
| **Files** | `src/components/ChatBotBody/BotCheckboxes/BotCheckboxes.tsx` |
| **Size** | ~30 lines |
| **Risk** | low |
| **Verification** | `npm run lint` ✓ `npm run build` ✓ `npm run unit:test` ✓ `npx tsc --noEmit` ✓ |

---

### PR #7: Add aria-label to ToastContainer

| Field | Value |
|-------|-------|
| **Branch** | `a11y/C007-toastcontainer-aria` |
| **Candidate** | C007 |
| **Type** | a11y |
| **Files** | `src/components/ChatBotToast/ToastContainer/ToastContainer.tsx` |
| **Size** | ~5 lines |
| **Risk** | low |
| **Verification** | `npm run lint` ✓ `npm run build` ✓ `npm run unit:test` ✓ `npx tsc --noEmit` ✓ |

---

### PR #8: Add aria-label to BotTypingIndicator

| Field | Value |
|-------|-------|
| **Branch** | `a11y/C008-bottypingindicator-aria` |
| **Candidate** | C008 |
| **Type** | a11y |
| **Files** | `src/components/ChatBotBody/BotTypingIndicator/BotTypingIndicator.tsx` |
| **Size** | ~5 lines |
| **Risk** | low |
| **Verification** | `npm run lint` ✓ `npm run build` ✓ `npm run unit:test` ✓ `npx tsc --noEmit` ✓ |

---

### PR #9: Add aria-label to LoadingSpinner

| Field | Value |
|-------|-------|
| **Branch** | `a11y/C009-loadingspinner-aria` |
| **Candidate** | C009 |
| **Type** | a11y |
| **Files** | `src/components/LoadingSpinner/LoadingSpinner.tsx` |
| **Size** | ~5 lines |
| **Risk** | low |
| **Verification** | `npm run lint` ✓ `npm run build` ✓ `npm run unit:test` ✓ `npx tsc --noEmit` ✓ |

---

### PR #10: Add aria-label to ChatHistoryButton

| Field | Value |
|-------|-------|
| **Branch** | `a11y/C010-chathistorybutton-aria` |
| **Candidate** | C010 |
| **Type** | a11y |
| **Files** | `src/components/ChatHistoryButton/ChatHistoryButton.tsx` |
| **Size** | ~5 lines |
| **Risk** | low |
| **Verification** | `npm run lint` ✓ `npm run build` ✓ `npm run unit:test` ✓ `npx tsc --noEmit` ✓ |

---

## PR Workflow

1. **Create branch** from main
2. **Implement changes** following plan in `06_SELECTED_10_PR_PLAN.md`
3. **Run verification**: lint, build, tests, typecheck
4. **Open PR** with description referencing issue
5. **Address review feedback**
6. **Merge** after approval

---

## Notes

- All PRs are independent; no blocking dependencies
- PRs can be developed and merged in any order
- Maintainer discussion not required for any of these PRs
- All PRs are low risk with small expected diffs