# Selected 10 PR Plan

## Overview

This document outlines the implementation plan for the top 10 selected PR candidates. Each PR is independently mergeable and targets a specific improvement.

---

## PR #1: Fix chatButtonStyle width/height not applying

| Field | Value |
|-------|-------|
| **Candidate ID** | C001 |
| **Linked Issue** | #361 |
| **Category** | bug_fix |
| **Risk Level** | low |
| **Expected Diff** | ~10 lines |
| **Merge Likelihood** | high |
| **Maintainer Discussion** | no |

### Problem
CSS hardcodes `width: 75px` and `height: 75px` on `.rcb-toggle-button`, overriding user-provided `chatButtonStyle` width/height.

### Implementation
1. Modify `src/components/ChatBotButton/ChatBotButton.css` to remove hardcoded `width` and `height`
2. Add `min-width` and `min-height` as fallback instead
3. Verify inline styles from `chatButtonStyle` now take precedence

### Target Files
- `src/components/ChatBotButton/ChatBotButton.css`

### Test Plan
1. Apply `{ chatButtonStyle: { width: 100, height: 100 } }` via settings
2. Verify button renders at 100x100 instead of 75x75
3. Run existing ChatBotButton tests

---

## PR #2: Add unit tests for BotMessage component

| Field | Value |
|-------|-------|
| **Candidate ID** | C002 |
| **Linked Issue** | #340 |
| **Category** | test |
| **Risk Level** | low |
| **Expected Diff** | ~150 lines |
| **Merge Likelihood** | high |
| **Maintainer Discussion** | no |

### Problem
BotMessage component (77 lines, core message rendering) has no test coverage.

### Implementation
1. Create `__tests__/components/ChatBotBody/BotMessage/BotMessage.test.tsx`
2. Test cases:
   - String content renders correctly
   - JSX content renders correctly
   - Avatar displays when `isNewSender` and `showAvatar` enabled
   - Offset style applies when `showAvatar` and not new sender
   - Animation class applies when `botBubble.animate` enabled
   - `contentWrapper` wraps content correctly

### Target Files
- `__tests__/components/ChatBotBody/BotMessage/BotMessage.test.tsx` (new)

### Test Plan
1. Run `npm run unit:test`
2. Verify BotMessage tests pass
3. Verify no regressions in other tests

---

## PR #3: Add unit tests for VoiceService

| Field | Value |
|-------|-------|
| **Candidate ID** | C003 |
| **Linked Issue** | #349 |
| **Category** | test |
| **Risk Level** | low |
| **Expected Diff** | ~100 lines |
| **Merge Likelihood** | high |
| **Maintainer Discussion** | no |

### Problem
VoiceService test coverage incomplete; missing timeout handling and error edge cases.

### Implementation
1. Review existing `__tests__/services/VoiceService.test.ts`
2. Add test cases for:
   - `handleTimeout` function behavior
   - `syncVoiceWithChatInput` with various settings combinations
   - Error handling when speech recognition unavailable
   - Character limit enforcement in voice input

### Target Files
- `__tests__/services/VoiceService.test.ts`

### Test Plan
1. Run `npm run unit:test`
2. Verify VoiceService tests pass
3. Verify coverage increase

---

## PR #4: Add unit tests for useSubmitInputInternal hook

| Field | Value |
|-------|-------|
| **Candidate ID** | C004 |
| **Linked Issue** | #350 |
| **Category** | test |
| **Risk Level** | low |
| **Expected Diff** | ~200 lines |
| **Merge Likelihood** | high |
| **Maintainer Discussion** | no |

### Problem
useSubmitInputInternal (224 lines, critical hook for user input handling) has no test coverage.

### Implementation
1. Create `__tests__/hooks/internal/useSubmitInputInternal.test.ts`
2. Mock all dependencies (contexts, other hooks, services)
3. Test cases:
   - `handleSubmitText` dispatches event and calls handleActionInput
   - `handleSubmitText` returns early when event is prevented
   - `handleActionInput` trims whitespace and ignores empty input
   - `handleActionInput` calls handleSendUserInput and postProcessBlock
   - Sensitive input masking works correctly
   - Stream message simulation works

### Target Files
- `__tests__/hooks/internal/useSubmitInputInternal.test.ts` (new)

### Test Plan
1. Run `npm run unit:test`
2. Verify useSubmitInputInternal tests pass
3. Verify no regressions in other hook tests

---

## PR #5: Add keyboard navigation to BotOptions

| Field | Value |
|-------|-------|
| **Candidate ID** | C005 |
| **Category** | a11y |
| **Risk Level** | low |
| **Expected Diff** | ~30 lines |
| **Merge Likelihood** | high |
| **Maintainer Discussion** | no |

### Problem
BotOptions uses mouse-only `onMouseDown` interaction; keyboard users cannot select options.

### Implementation
1. Add `tabIndex={0}` to each option div
2. Add `onKeyDown` handler for Enter/Space activation
3. Add `role="list"` to container div
4. Add `role="listitem"` to each option div

### Target Files
- `src/components/ChatBotBody/BotOptions/BotOptions.tsx`

### Test Plan
1. Tab to BotOptions, verify focus visible
2. Use Enter/Space to select option, verify it works
3. Run existing BotOptions tests

---

## PR #6: Add keyboard navigation to BotCheckboxes

| Field | Value |
|-------|-------|
| **Candidate ID** | C006 |
| **Category** | a11y |
| **Risk Level** | low |
| **Expected Diff** | ~30 lines |
| **Merge Likelihood** | high |
| **Maintainer Discussion** | no |

### Problem
BotCheckboxes uses mouse-only interaction; keyboard users cannot check/uncheck.

### Implementation
1. Add `tabIndex={0}` to each checkbox row
2. Add `onKeyDown` handler for Space toggle
3. Add `role="listbox"` to container
4. Add `role="option"` to each row

### Target Files
- `src/components/ChatBotBody/BotCheckboxes/BotCheckboxes.tsx`

### Test Plan
1. Tab to checkboxes, verify focus visible
2. Use Space to toggle checkbox, verify it works
3. Run existing BotCheckboxes tests

---

## PR #7: Add aria-label to ToastContainer

| Field | Value |
|-------|-------|
| **Candidate ID** | C007 |
| **Category** | a11y |
| **Risk Level** | low |
| **Expected Diff** | ~5 lines |
| **Merge Likelihood** | high |
| **Maintainer Discussion** | no |

### Problem
ToastContainer missing `role="status"` and `aria-live` for screen reader notification.

### Implementation
1. Add `role="status"` and `aria-live="polite"` to ToastContainer div

### Target Files
- `src/components/ChatBotToast/ToastContainer/ToastContainer.tsx`

### Test Plan
1. Open chat, trigger toast notification
2. Verify screen reader announces new toast
3. Run existing ToastContainer tests

---

## PR #8: Add aria-label to BotTypingIndicator

| Field | Value |
|-------|-------|
| **Candidate ID** | C008 |
| **Category** | a11y |
| **Risk Level** | low |
| **Expected Diff** | ~5 lines |
| **Merge Likelihood** | high |
| **Maintainer Discussion** | no |

### Problem
BotTypingIndicator has no aria-label; screen readers don't announce "bot is typing".

### Implementation
1. Add `aria-label="Bot is typing"` to the typing indicator container

### Target Files
- `src/components/ChatBotBody/BotTypingIndicator/BotTypingIndicator.tsx`

### Test Plan
1. Trigger bot typing state
2. Verify screen reader announces "Bot is typing"
3. Run existing BotTypingIndicator tests

---

## PR #9: Add aria-label to LoadingSpinner

| Field | Value |
|-------|-------|
| **Candidate ID** | C009 |
| **Category** | a11y |
| **Risk Level** | low |
| **Expected Diff** | ~5 lines |
| **Merge Likelihood** | high |
| **Maintainer Discussion** | no |

### Problem
LoadingSpinner missing aria-label or role="status" for accessibility.

### Implementation
1. Add `aria-label="Loading" role="status"` to LoadingSpinner container

### Target Files
- `src/components/LoadingSpinner/LoadingSpinner.tsx`

### Test Plan
1. Trigger loading state
2. Verify screen reader announces "Loading"
3. Run existing LoadingSpinner tests

---

## PR #10: Add aria-label to ChatHistoryButton

| Field | Value |
|-------|-------|
| **Candidate ID** | C010 |
| **Category** | a11y |
| **Risk Level** | low |
| **Expected Diff** | ~5 lines |
| **Merge Likelihood** | high |
| **Maintainer Discussion** | no |

### Problem
ChatHistoryButton missing aria-label for screen reader users.

### Implementation
1. Add `aria-label` from `settings.ariaLabel?.chatHistoryButton` or fallback text "View chat history"

### Target Files
- `src/components/ChatHistoryButton/ChatHistoryButton.tsx`

### Test Plan
1. Verify button has accessible name
2. Run existing ChatHistoryButton tests

---

## Implementation Order

| Order | PR | Priority Rationale |
|-------|-----|---------------------|
| 1 | C001 - chatButtonStyle fix | Issue #361, immediate user pain |
| 2 | C002 - BotMessage tests | Issue #340, good first issue |
| 3 | C003 - VoiceService tests | Issue #349, good first issue |
| 4 | C004 - useSubmitInputInternal tests | Issue #350, good first issue |
| 5 | C005 - BotOptions keyboard | A11y, straightforward |
| 6 | C006 - BotCheckboxes keyboard | A11y, straightforward |
| 7 | C007 - ToastContainer aria | A11y, quick win |
| 8 | C008 - BotTypingIndicator aria | A11y, quick win |
| 9 | C009 - LoadingSpinner aria | A11y, quick win |
| 10 | C010 - ChatHistoryButton aria | A11y, quick win |

---

## Verification Checklist (All PRs)

- [ ] `npm run lint` passes
- [ ] `npm run build` passes
- [ ] `npm run unit:test` passes
- [ ] `npx tsc --noEmit` passes
- [ ] No new dependencies added
- [ ] No breaking API changes
- [ ] Test coverage maintained or improved