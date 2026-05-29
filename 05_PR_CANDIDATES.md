# PR Candidates

## Overview

This document lists 18 PR candidate ideas derived from issue triage, quality audit, and codebase analysis. Each candidate is independent and can be merged separately.

| candidate_id | title | category | linked_issue | source | problem | proposed_solution | target_files | test_plan | risk_level | expected_diff_size | merge_likelihood | maintainer_discussion_needed | selected |
|--------------|-------|----------|--------------|--------|---------|-------------------|--------------|-----------|------------|-------------------|------------------|------------------------------|----------|
| C001 | Fix chatButtonStyle width/height not applying | bug_fix | #361 | issue | CSS hardcodes width/height at 75px, overriding user-provided styles | Remove hardcoded width/height from CSS, use CSS variables or make inline styles take precedence | `src/components/ChatBotButton/ChatBotButton.css` | Manual test: apply width/height via chatButtonStyle, verify it renders | low | ~10 lines | high | no | **yes** |
| C002 | Add unit tests for BotMessage component | test | #340 | issue | BotMessage has no test coverage despite being core rendering component | Create BotMessage.test.tsx covering message rendering, avatar display, content types | `__tests__/components/ChatBotBody/BotMessage/BotMessage.test.tsx` | Run jest, verify all scenarios pass | low | ~150 lines | high | no | **yes** |
| C003 | Add unit tests for VoiceService | test | #349 | issue | VoiceService test coverage incomplete; missing edge cases | Expand VoiceService.test.ts with timeout, browser compatibility, error handling cases | `__tests__/services/VoiceService.test.ts` | Run jest, verify new edge case tests pass | low | ~100 lines | high | no | **yes** |
| C004 | Add unit tests for useSubmitInputInternal hook | test | #350 | issue | useSubmitInputInternal has no test coverage (224 lines, critical hook) | Create useSubmitInputInternal.test.ts covering handleSubmitText, handleActionInput, sensitive input | `__tests__/hooks/internal/useSubmitInputInternal.test.ts` | Run jest, verify all scenarios pass | low | ~200 lines | high | no | **yes** |
| C005 | Add keyboard navigation to BotOptions | a11y | - | quality_audit | BotOptions uses mouse-only interaction (onMouseDown); keyboard users cannot select options | Add tabIndex={0}, onKeyDown handler for Enter/Space, role="list" on container | `src/components/ChatBotBody/BotOptions/BotOptions.tsx` | Manual test: Tab to options, activate with Enter/Space | low | ~30 lines | high | no | no |
| C006 | Add keyboard navigation to BotCheckboxes | a11y | - | quality_audit | BotCheckboxes uses mouse-only interaction; keyboard users cannot check/uncheck | Add tabIndex, onKeyDown for Space, proper role="listbox" | `src/components/ChatBotBody/BotCheckboxes/BotCheckboxes.tsx` | Manual test: Tab to checkboxes, toggle with Space | low | ~30 lines | high | no | no |
| C007 | Add aria-label to ToastContainer | a11y | - | quality_audit | ToastContainer missing role="status" and aria-live for screen reader notification | Add role="status" aria-live="polite" to ToastContainer | `src/components/ChatBotToast/ToastContainer/ToastContainer.tsx` | Manual test: Screen reader announces new toasts | low | ~5 lines | high | no | no |
| C008 | Add aria-label to BotTypingIndicator | a11y | - | quality_audit | BotTypingIndicator has no aria-label; screen readers don't announce "bot is typing" | Add aria-label="Bot is typing" or role="status" | `src/components/ChatBotBody/BotTypingIndicator/BotTypingIndicator.tsx` | Manual test: Screen reader announces typing state | low | ~5 lines | high | no | no |
| C009 | Add aria-label to LoadingSpinner | a11y | - | quality_audit | LoadingSpinner missing aria-label or role="status" | Add aria-label="Loading" role="status" | `src/components/LoadingSpinner/LoadingSpinner.tsx` | Manual test: Screen reader announces loading state | low | ~5 lines | high | no | no |
| C010 | Add aria-label to ChatHistoryButton | a11y | - | quality_audit | ChatHistoryButton missing aria-label | Add aria-label from settings.ariaLabel or default text | `src/components/ChatHistoryButton/ChatHistoryButton.tsx` | Manual test: Screen reader announces button purpose | low | ~5 lines | high | no | no |
| C011 | Add ComponentProcessor unit tests | test | - | quality_audit | ComponentProcessor.ts has no tests (JSX.Element and function component handling) | Create ComponentProcessor.test.ts covering both element and function cases | `__tests__/services/BlockService/ComponentProcessor.test.ts` | Run jest, verify component injection works | low | ~100 lines | high | no | no |
| C012 | Add MediaDisplay alt text support | a11y | - | quality_audit | MediaDisplay may render images without alt text; poor accessibility for screen readers | Add alt prop or generate alt from filename | `src/components/ChatBotBody/MediaDisplay/MediaDisplay.tsx` | Manual test: Images have descriptive alt text | low | ~20 lines | high | no | no |
| C013 | Improve VoiceService error messages | enhancement | - | quality_audit | VoiceService silently catches errors (e.g., microphone denied); user not notified | Add user-facing toast notification on permission denied | `src/services/VoiceService.ts` | Manual test: Deny microphone, verify error toast appears | low | ~15 lines | medium | no | no |
| C014 | Add aria-label to ChatBotHeader | a11y | - | quality_audit | ChatBotHeader missing aria-label for header region | Add aria-label="Chat header" or use title text | `src/components/ChatBotHeader/ChatBotHeader.tsx` | Manual test: Screen reader announces header region | low | ~5 lines | high | no | no |
| C015 | Add aria-label to ChatBotFooter | a11y | - | quality_audit | ChatBotFooter missing aria-label for footer region | Add aria-label="Chat footer" | `src/components/ChatBotFooter/ChatBotFooter.tsx` | Manual test: Screen reader announces footer region | low | ~5 lines | high | no | no |
| C016 | Add ChatMessagePrompt keyboard support | a11y | - | quality_audit | ChatMessagePrompt is clickable but not keyboard accessible | Add tabIndex={0}, onKeyDown handler, role="button" | `src/components/ChatBotBody/ChatMessagePrompt/ChatMessagePrompt.tsx` | Manual test: Tab to prompt, activate with Enter | low | ~15 lines | high | no | no |
| C017 | Add CheckboxProcessor unit tests | test | - | quality_audit | CheckboxProcessor (if separate) missing tests; checkbox handling not fully covered | Create CheckboxProcessor.test.ts or extend existing BlockService tests | `__tests__/services/BlockService/CheckboxProcessor.test.ts` | Run jest, verify checkbox logic passes | low | ~100 lines | high | no | no |
| C018 | Document JS module usage in README | documentation | #270 | issue | README only shows React usage; JavaScript module usage not documented | Add section showing import from dist/ for vanilla JS usage | `README.md` | Manual test: Follow instructions to use in plain HTML/JS | low | ~30 lines | high | no | no |

---

## Candidate Selection Summary

| Priority | Candidates |
|----------|------------|
| **Selected for top 10** | C001, C002, C003, C004, C005, C006, C007, C008, C009, C010 |
| **Deferred** | C011, C012, C013, C014, C015, C016, C017, C018 |

**Selection criteria**:
- Prefer issue-backed (C001, C002, C003, C004, C018)
- Prefer low/medium risk
- Prefer test coverage improvements (2 test issues already selected)
- Prefer accessibility improvements (A11y gaps from quality audit)
- Max 10 selected to keep PR queue manageable

**Note**: C011-C018 are valid candidates but may require more review or have lower urgency. They can be revisited in a subsequent planning cycle.