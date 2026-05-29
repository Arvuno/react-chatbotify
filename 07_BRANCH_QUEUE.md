# Branch Queue

## Overview

This document defines the branch naming convention and queue order for implementing the selected 10 PRs.

---

## Branch Naming Convention

Format: `{type}/{candidate_id}-{short-description}`

| Type | Prefix | Example |
|------|--------|---------|
| bug_fix | `fix/` | `fix/C001-chatbutton-style` |
| test | `test/` | `test/C002-botmessage-unit-tests` |
| a11y | `a11y/` | `a11y/C005-botoptions-keyboard` |

---

## Branch Queue

| Queue # | Branch Name | PR # | Candidate | Description | Dependencies |
|---------|-------------|------|-----------|-------------|--------------|
| 1 | `fix/C001-chatbutton-style` | 1 | C001 | Fix chatButtonStyle width/height not applying | none |
| 2 | `test/C002-botmessage-unit-tests` | 2 | C002 | Add unit tests for BotMessage component | none |
| 3 | `test/C003-voiceservice-unit-tests` | 3 | C003 | Add unit tests for VoiceService | none |
| 4 | `test/C004-submitinput-internal-tests` | 4 | C004 | Add unit tests for useSubmitInputInternal hook | none |
| 5 | `a11y/C005-botoptions-keyboard` | 5 | C005 | Add keyboard navigation to BotOptions | none |
| 6 | `a11y/C006-botcheckboxes-keyboard` | 6 | C006 | Add keyboard navigation to BotCheckboxes | none |
| 7 | `a11y/C007-toastcontainer-aria` | 7 | C007 | Add aria-label to ToastContainer | none |
| 8 | `a11y/C008-bottypingindicator-aria` | 8 | C008 | Add aria-label to BotTypingIndicator | none |
| 9 | `a11y/C009-loadingspinner-aria` | 9 | C009 | Add aria-label to LoadingSpinner | none |
| 10 | `a11y/C010-chathistorybutton-aria` | 10 | C010 | Add aria-label to ChatHistoryButton | none |

---

## Queue Management Rules

1. **Independent execution**: All branches are independent and can be developed in parallel
2. **Merge order**: Branches should be merged in queue order to maintain consistency
3. **Rebase vs merge**: Prefer rebase onto main for clean history
4. **Stale branch cleanup**: After PR merge, delete branch from remote

---

## Implementation Notes

### Parallel Development
Since branches are independent, up to 3-4 can be developed simultaneously if resources permit.

### Testing Strategy
- Each branch should include tests (for test PRs) or verification steps (for a11y/fix PRs)
- Run `npm run unit:test` before opening PR
- Ensure no regressions in existing tests

### Review Priority
1. Bug fixes (C001) - highest priority
2. Test coverage (C002-C004) - high priority, improves confidence
3. Accessibility (C005-C010) - medium priority, legal requirement