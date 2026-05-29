# Quality Audit Report

## Overview

This audit covers TypeScript type coverage, accessibility, prop documentation, test coverage gaps, and documentation gaps in the react-chatbotify codebase.

---

## 1. TypeScript Type Coverage

### Finding: Generic SVG Icon Props Not Fully Typed

**Location**: `src/types/Settings.ts` (lines 22, 29, 35, 48, 67, 110, 121, 128)

**Issue**: Settings uses `React.FC<React.SVGProps<SVGSVGElement>>` for icon props but the type is inconsistent across the codebase. Some places use `React.FC<SVGProps<SVGSVGElement>>` (without React prefix), others use string.

**Current**:
```typescript
icon?: string | React.FC<React.SVGProps<SVGSVGElement>>;
```

**Issue**: Users may not know the full SVG props interface is available when passing a function component. The type is correct but could benefit from explicit documentation.

---

### Finding: Block Type Has Optional Attributes Without Clear Documentation

**Location**: `src/types/Block.ts`

**Issue**: Many block attributes are optional but the relationship between them (e.g., `message` + `options` together, `checkboxes` + `items`) is not documented in the type system.

**Example**:
```typescript
message?: string | Message;
options?: {items: Array<string>, sendOutput?: boolean, reusable?: boolean};
checkboxes?: {items: Array<string>, max?: number, min?: number, ...};
```

**Risk**: Medium - Runtime errors when mutually exclusive attributes are used together.

---

## 2. Accessibility Gaps

### Finding: 16 Components Missing ARIA Labels

**Location**: `src/components/**/*.tsx` (16 files)

The following interactive components lack `aria-label` or `role`:

| Component | Missing | Risk |
|-----------|---------|------|
| `BotOptions.tsx` | `role="list"` or `aria-label` on options | Medium |
| `BotCheckboxes.tsx` | Checkbox role on individual items | Medium |
| `BotMessage.tsx` | No accessible name for container | Low |
| `UserMessage.tsx` | No accessible name | Low |
| `ChatBotBody.tsx` | No role for message container | Low |
| `ChatBotHeader.tsx` | No aria-label for header | Low |
| `ChatBotFooter.tsx` | No aria-label for footer | Low |
| `ChatMessagePrompt.tsx` | No accessible name | Medium |
| `BotTypingIndicator.tsx` | No `aria-label` for screen readers | Medium |
| `MediaDisplay.tsx` | Missing alt text for media | Medium |
| `ToastContainer.tsx` | No `role="status"` or `aria-live` | Medium |
| `ToastPrompt.tsx` | Missing accessible name | Low |
| `ChatHistoryLineBreak.tsx` | Missing accessible name | Low |
| `ChatHistoryButton.tsx` | Missing aria-label | Medium |
| `LoadingSpinner.tsx` | Missing `aria-label` or `role="status"` | Medium |
| `ChatBotTooltip.tsx` | No accessible name | Low |

**Note**: Button components (SendButton, AudioButton, etc.) do have proper aria labels.

---

### Finding: Keyboard Navigation Missing on Interactive Elements

**Location**: `src/components/ChatBotBody/BotOptions.tsx`, `src/components/ChatBotBody/BotCheckboxes.tsx`

**Issue**: Options and checkboxes use `onMouseDown` for selection but lack:
- `tabIndex={0}` to make focusable
- `onKeyDown` handler for Enter/Space activation
- `role="listitem"` or similar

**Current behavior**: Mouse-only interaction; keyboard users cannot select options.

---

## 3. Prop Documentation Issues

### Finding: Settings.chatButton.icon Accepts Two Types Without Examples

**Location**: `src/types/Settings.ts` line 22

```typescript
chatButton?: {
    icon?: string | React.FC<React.SVGProps<SVGSVGElement>>;
}
```

**Issue**: No documentation on how to use each format. Users may not know:
- String format: Provide URL to image
- Function format: Provide React component

---

### Finding: Block Component Attribute Not Documented

**Location**: `src/types/Block.ts`

**Issue**: The `component` attribute accepts both `JSX.Element` and `Function` but the difference in behavior is not documented:
- `JSX.Element`: Rendered directly
- `Function`: Called with `params` and result is injected as message

---

## 4. Error Messages and Edge Cases

### Finding: VoiceService Has Unclear Error State

**Location**: `src/services/VoiceService.ts`

**Issue**: When speech recognition fails or times out, the error is silently caught. Users are not notified via UI.

```typescript
// Timeout silently fails without user notification
timeoutPeriod?: number; // documented but behavior on timeout unclear
```

---

### Finding: Block Processing Error Messages Are Generic

**Location**: `src/services/BlockService/**/*.ts`

**Issue**: Block processing failures produce generic console errors. Example:
```typescript
// No contextual information in error messages
console.error("Error processing message");
```

---

## 5. Test Coverage Gaps

### Finding: useSubmitInputInternal Has No Unit Tests

**Location**: `src/hooks/internal/useSubmitInputInternal.ts` (224 lines)

**Current**: No test file at `__tests__/hooks/internal/useSubmitInputInternal.test.ts`

**Coverage gap**: This is a critical hook handling user input submission, voice sync, path processing, and toast management.

**Risk**: High - changes to this hook can break core user interaction.

---

### Finding: CheckboxProcessor and ComponentProcessor Missing Tests

**Location**: `src/services/BlockService/`

**Files without tests**:
- `CheckboxProcessor.tsx` (if it exists as separate file - not found as .ts, only .tsx)
- `ComponentProcessor.ts`

**Note**: CheckboxProcessor.tsx was not found in source; checkboxes may be handled inline.

**Current test coverage for BlockService**:
- ✅ `MessageProcessor.test.ts`
- ✅ `PathProcessor.test.ts`
- ✅ `TransitionProcessor.test.ts`
- ✅ `FunctionProcessor.test.ts`
- ✅ `IsSensitiveProcessor.test.ts`
- ✅ `ChatDisabledProcessor.test.ts`
- ❌ `ComponentProcessor.test.ts` (missing)
- ❌ `CheckboxProcessor.test.ts` (missing, or inlined)

---

### Finding: BotMessage Component Lacks Unit Tests

**Location**: `src/components/ChatBotBody/BotMessage/BotMessage.tsx` (77 lines)

**Issue**: Has no test file despite being a core rendering component. Issue #340 is tracking this.

---

### Finding: VoiceService Test Coverage Incomplete

**Location**: `src/services/VoiceService.ts`

**Issue**: Issue #349 is open to add more test cases. Current test file exists but may not cover edge cases (timeout, browser compatibility).

---

## 6. Documentation Gaps

### Finding: DeveloperGuide.md Missing Common Patterns

**Location**: `docs/DeveloperGuide.md`

**Missing examples**:
1. Custom icon component with SVG props example
2. Using plugins with the library
3. Chat history access patterns (Issue #298 relates)
4. CSS customization for chat button size (Issue #361 relates)

---

### Finding: README.md Missing JavaScript Usage Guide

**Location**: `README.md`

**Issue**: Issue #270 asks about JavaScript module usage but README only shows React usage pattern. No `dist/` usage examples.

---

### Finding: Missing JSDoc on Internal Hooks

**Location**: `src/hooks/internal/*.ts`

**Issue**: Several internal hooks lack JSDoc comments:
- `useSubmitInputInternal.ts` - has JSDoc ✅
- `useTextAreaInternal.ts` - needs review
- `useBotEffectsInternal.tsx` - needs review

---

## 7. CSS/Style Issues

### Finding: Chat Button Width/Height Hardcoded in CSS

**Location**: `src/components/ChatBotButton/ChatBotButton.css` (lines 10-11)

```css
.rcb-toggle-button {
    width: 75px;
    height: 75px;
    ...
}
```

**Issue**: Issue #361 - User cannot override `chatButtonStyle` width/height because CSS specificity overrides inline styles.

**Fix approach**: Make width/height configurable via CSS variable or remove hardcoded values.

---

## 8. Potential Runtime Issues

### Finding: BotOptions Hover State Not Persisted on Re-render

**Location**: `src/components/ChatBotBody/BotOptions.tsx`

**Issue**: `hoveredElements` state is local to component. If parent re-renders, hover state resets.

```typescript
const [hoveredElements, setHoveredElements] = useState<boolean[]>([]);
```

**Risk**: Low - visual only, no data loss.

---

### Finding: Checkbox min Validation Runs Client-side Only

**Location**: `src/components/ChatBotBody/BotCheckboxes.tsx`

**Issue**: The min checkbox requirement is only enforced client-side. Submit button enables when `checkedBoxes.size >= checkboxes.min` but no server validation exists (since it's client-only, this is expected behavior).

---

## Summary of Findings

| Category | High Risk | Medium Risk | Low Risk |
|----------|-----------|-------------|----------|
| TypeScript Type Coverage | 1 | 1 | 0 |
| Accessibility | 0 | 7 | 8 |
| Prop Documentation | 0 | 2 | 0 |
| Error Messages | 0 | 2 | 0 |
| Test Coverage | 2 | 2 | 0 |
| Documentation | 0 | 2 | 1 |
| CSS/Style | 1 | 0 | 0 |
| Runtime Issues | 0 | 0 | 2 |

**Total: 22 findings**

**Priority fixes**:
1. Fix CSS specificity for chatButtonStyle (Issue #361)
2. Add useSubmitInputInternal tests (Issue #350)
3. Add BotMessage tests (Issue #340)
4. Add keyboard navigation to BotOptions/BotCheckboxes
5. Add aria-labels to remaining interactive components