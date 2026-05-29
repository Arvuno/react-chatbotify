# React ChatBotify Repository Map

## Overview

**Project**: React ChatBotify  
**Description**: A modern React library for creating flexible and extensible chatbots  
**Version**: 2.5.0  
**License**: MIT  
**Repository**: https://github.com/react-chatbotify/react-chatbotify  
**Website**: https://react-chatbotify.com  
**Author**: Tan Jin (tjtanjin)

---

## Tech Stack

| Category | Technology |
|----------|------------|
| Framework | React (16, 17, 18, 19 compatible) |
| Language | TypeScript (strict mode) |
| Build Tool | Vite 7.2.4 |
| Unit Testing | Jest 30.2.0 + ts-jest |
| Integration Testing | Cypress 15.7.0 |
| Linting | ESLint 9.39.1 + TypeScript ESLint |
| Package Manager | npm |

---

## Project Structure

```
react-chatbotify/
├── src/                          # Main source code
│   ├── index.tsx                 # Main library entry point (exports all public APIs)
│   ├── App.tsx                   # Demo application for development
│   ├── devIndex.tsx              # Dev server entry
│   ├── index.html                # Dev server HTML
│   ├── components/               # React UI components
│   │   ├── ChatBot.tsx           # Main ChatBot wrapper component
│   │   ├── ChatBotContainer.tsx  # Container component
│   │   ├── ChatBotHeader/        # Header subcomponents
│   │   ├── ChatBotBody/          # Message body with BotOptions, UserOptions etc.
│   │   ├── ChatBotFooter/        # Footer subcomponents
│   │   ├── ChatBotInput/         # Text input with emoji, file attachment
│   │   ├── ChatBotButton/        # Floating chat button
│   │   ├── ChatBotLoader.tsx     # Initial loading component
│   │   ├── ChatBotToast/         # Toast notifications
│   │   ├── ChatBotTooltip/       # Tooltip component
│   │   ├── ChatHistoryButton/    # Chat history button
│   │   ├── ChatHistoryLineBreak/ # Chat history line break
│   │   ├── LoadingSpinner/       # Loading spinner
│   │   └── Buttons/              # AudioButton, NotificationButton, VoiceButton etc.
│   ├── context/                  # React Context providers (8 total)
│   │   ├── BotRefsContext.tsx    # Tracks refs (inputRef, botIdRef)
│   │   ├── BotStatesContext.tsx  # Tracks states (audioToggledOn, isChatWindowOpen)
│   │   ├── ChatBotContext.tsx    # Top-level provider (exported for advanced use)
│   │   ├── MessagesContext.tsx   # Manages chat messages
│   │   ├── PathsContext.tsx      # Manages conversation paths/blocks
│   │   ├── SettingsContext.tsx    # Manages chatbot settings
│   │   ├── StylesContext.tsx     # Manages styling
│   │   └── ToastsContext.tsx     # Manages toast notifications
│   ├── hooks/                    # Custom React hooks
│   │   ├── internal/             # Internal hooks (logic implementation)
│   │   └── *.ts                  # External hooks (filtering layer for public API)
│   │       ├── useAudio.ts
│   │       ├── useBotId.ts
│   │       ├── useChatHistory.ts
│   │       ├── useChatWindow.ts
│   │       ├── useFirstInteraction.ts
│   │       ├── useFlow.ts
│   │       ├── useMessages.ts
│   │       ├── useNotifications.ts
│   │       ├── useOnRcbEvent.ts
│   │       ├── usePaths.ts
│   │       ├── useSettings.ts
│   │       ├── useStyles.ts
│   │       ├── useTextArea.ts
│   │       ├── useToasts.ts
│   │       └── useVoice.ts
│   ├── services/                 # Business logic services
│   │   ├── AudioService.ts       # Text-to-speech audio output
│   │   ├── VoiceService.ts       # Speech recognition
│   │   ├── BlockService/         # Block processing logic
│   │   ├── ChatHistoryService.tsx # Chat history persistence
│   │   ├── ThemeService.ts       # Theme application
│   │   └── RcbEventService.ts   # Custom event handling
│   ├── types/                    # TypeScript type definitions
│   │   ├── Block.ts              # Conversation block type
│   │   ├── Settings.ts           # Settings configuration type
│   │   ├── Flow.ts               # Flow type
│   │   ├── Message.ts            # Message type
│   │   ├── Plugin.ts             # Plugin type
│   │   ├── Styles.ts             # Styles type
│   │   ├── Theme.ts              # Theme type
│   │   ├── Toast.ts              # Toast type
│   │   ├── Params.ts             # Params type for block attributes
│   │   ├── Slots.ts              # Slots for custom header/footer
│   │   ├── events/               # Event types (24 custom events)
│   │   └── internal/             # Internal types
│   ├── constants/                # Constants
│   │   ├── Button.ts             # Button constants
│   │   ├── RcbEvent.ts           # Event name constants
│   │   └── internal/             # Internal constants (WelcomeFlow etc.)
│   ├── utils/                    # Utility functions
│   │   ├── configParser.ts       # Settings/styles parsing
│   │   ├── buttonBuilder.tsx     # Button building utility
│   │   ├── idGenerator.ts        # UUID generation
│   │   ├── mediaFileParser.ts    # Media file parsing
│   │   └── messageBuilder.ts     # Message building utility
│   └── assets/                   # Static assets (SVG, WAV)
├── types/                         # Global type declarations
│   ├── global.d.ts               # Global Window interface extensions
│   ├── audio.d.ts               # Audio type declarations
│   ├── image.d.ts               # Image type declarations
│   └── cypress.d.ts             # Cypress type declarations
├── __tests__/                    # Unit tests (Jest)
│   ├── components/              # Component tests
│   ├── hooks/                   # Hook tests
│   ├── services/                # Service tests
│   ├── context/                 # Context tests
│   ├── utils/                   # Utility tests
│   └── __mocks__/               # Test mocks
├── cypress/                      # Integration tests (Cypress)
├── docs/                        # Developer guide
│   └── DeveloperGuide.md        # Full developer documentation
├── .github/
│   ├── workflows/               # CI/CD workflows
│   │   ├── ci-cd-pipeline.yml   # Main CI/CD pipeline
│   │   ├── lint-and-build.yml   # Lint and build workflow
│   │   ├── test.yml             # Test workflow
│   │   └── publish.yml          # Publish workflow
│   ├── ISSUE_TEMPLATE/          # Issue templates
│   │   ├── bug_report.md
│   │   ├── feature_request.md
│   │   ├── help.md
│   │   └── task.md
│   └── pull_request_template.md
├── scripts/                     # Build scripts
│   └── post-build.js
├── ssr/                         # SSR validation scripts
│   └── ssr-validate.js
└── assets/                      # Root-level assets
```

---

## Public API Surface

### Main Components
- `ChatBot` (default export) - Main chatbot component
- `ChatBotProvider` - Optional provider for advanced use cases

### Hooks (External)
| Hook | Purpose |
|------|---------|
| `useAudio` | Control audio (TTS) |
| `useBotId` | Get chatbot ID |
| `useChatHistory` | Manage chat history |
| `useChatWindow` | Control chat window state |
| `useFirstInteraction` | Track first user interaction |
| `useFlow` | Access conversation flow |
| `useMessages` | Access/manipulate messages |
| `useNotifications` | Control notifications |
| `useOnRcbEvent` | Subscribe to events |
| `usePaths` | Manage paths |
| `useSettings` | Access settings |
| `useStyles` | Access styles |
| `useTextArea` | Control text area |
| `useToasts` | Manage toasts |
| `useVoice` | Control voice input |

### Types
- `Block`, `Params`, `Flow`, `Message`, `Plugin`, `Settings`, `Styles`, `Toast`, `Theme`

### Event Types (24 events)
Audio: `RcbStartSpeakAudioEvent`, `RcbToggleAudioEvent`  
Notifications: `RcbToggleNotificationsEvent`  
Voice: `RcbToggleVoiceEvent`  
Window: `RcbToggleChatWindowEvent`  
Messages: `RcbPreInjectMessageEvent`, `RcbPostInjectMessageEvent`, `RcbStartSimulateStreamMessageEvent`, `RcbStopSimulateStreamMessageEvent`, `RcbStartStreamMessageEvent`, `RcbChunkStreamMessageEvent`, `RcbStopStreamMessageEvent`, `RcbRemoveMessageEvent`  
Chat History: `RcbLoadChatHistoryEvent`  
Path: `RcbChangePathEvent`  
Toast: `RcbShowToastEvent`, `RcbDismissToastEvent`  
Input: `RcbUserSubmitTextEvent`, `RcbUserUploadFileEvent`, `RcbTextAreaChangeValueEvent`  
Lifecycle: `RcbPreLoadChatBotEvent`, `RcbPostLoadChatBotEvent`  
Block Processing: `RcbPreProcessBlockEvent`, `RcbPostProcessBlockEvent`

### Constants
- `Button` - Button constants
- `RcbEvent` - Event name constants

### Utilities
- `getDefaultSettings()` - Get default settings
- `getDefaultStyles()` - Get default styles

---

## Build/Test/Lint Commands

| Command | Description |
|---------|-------------|
| `npm run lint` | Run ESLint with auto-fix |
| `npm run build` | TypeScript compile + Vite build + post-build script |
| `npm run start` | Start dev server (Vite) |
| `npm run unit:test` | Run Jest unit tests |
| `npm run unit:test:watch` | Run Jest in watch mode |
| `npm run unit:test:coverage` | Run Jest with coverage |
| `npm run unit:test:single` | Run single test file |
| `npm run int:test` | Run Cypress integration tests |
| `npm run int:test:open` | Open Cypress test runner |
| `npm run validate:ssr` | Validate SSR compatibility |
| `npm run prepare` | Install Husky git hooks |

---

## CI/CD Workflows

### ci-cd-pipeline.yml
- Triggered on: push to main, PR to main, manual dispatch
- Ignores: markdown, docs, scripts, assets, eslint configs
- Calls: lint-and-build.yml workflow

### lint-and-build.yml
- **Lint job**: Runs ESLint on Node 22.9.0
- **Build job**: Runs build on Node 18.x, 20.x, 22.x (parallel)
- **SSR validation**: Runs on Node 19+ versions
- **Trigger-tests**: After successful build, calls test.yml

### test.yml
- Unit tests (Jest)
- Integration tests (Cypress)
- Compatibility tests with React 16, 17, 18, 19

### publish.yml
- NPM publishing workflow

---

## Risk-Sensitive Areas

The following areas require careful consideration when modifying:

### 1. State Management (src/context/)
- **BotStatesContext**: Global chatbot state (audioToggledOn, isChatWindowOpen, etc.)
- **MessagesContext**: Core message state - any changes can break message rendering
- **PathsContext**: Conversation path/block state - critical for flow logic
- **SettingsContext**: Parses and merges user settings with defaults

### 2. Event System (src/services/RcbEventService.ts, types/events/)
- 24 custom events exposed on window object
- Changes to event payloads or event names can break user integrations
- Event handlers in plugins rely on event ordering

### 3. Block Processing (src/services/BlockService/)
- Core conversation logic
- Handles message, options, checkboxes, component, transition attributes
- Post-processing: function, file, path attributes
- Any changes can affect conversation flow

### 4. Chat History (src/services/ChatHistoryService.tsx)
- localStorage/sessionStorage handling
- Message persistence and retrieval
- Potential data corruption if storage format changes

### 5. Audio/Voice Services (src/services/)
- AudioService: Text-to-speech using Web Speech API
- VoiceService: Speech recognition using Web Speech API
- Browser compatibility issues possible

### 6. Theme System (src/services/ThemeService.ts)
- Dynamic CSS injection
- Theme merging logic
- Potential style conflicts

### 7. User Input Handling
- Textarea management
- File attachment handling
- Sensitive input masking
- Spam blocking

---

## Safe Areas for Contributions

These areas are generally safe for PRs:

### 1. Documentation
- README.md improvements
- DeveloperGuide.md updates
- Code comments
- Type documentation (JSDoc)

### 2. Test Coverage
- Adding unit tests to __tests__/
- Expanding integration tests in cypress/
- Current test coverage is minimal (only some hooks tested)

### 3. Accessibility (A11y)
- ARIA labels in Settings.ts (ariaLabel config)
- Keyboard navigation
- Screen reader support

### 4. Prop Types
- Adding/changing optional prop types
- Default value handling

### 5. Examples/Showcases
- SHOWCASES.md submissions
- Documentation website examples

### 6. Bug Fixes (with tests)
- Small bug fixes with accompanying tests
- Edge case handling

---

## Issue/PR Templates

### Issue Templates (.github/ISSUE_TEMPLATE/)
- **bug_report.md**: Bug report with steps to reproduce, expected behavior, environment info
- **feature_request.md**: Enhancement suggestion
- **help.md**: Help request template
- **task.md**: Task template

### PR Template (.github/pull_request_template.md)
- Summary description
- Issue reference
- Change type: Bug fix / New feature / Breaking change / Documentation
- Approach overview
- Checklist: commit message convention, testing done, comments updated

---

## Associated Projects

| Project | Repository |
|---------|------------|
| Official Plugins | https://github.com/React-ChatBotify-Plugins |
| Documentation Website | https://github.com/react-chatbotify/core-library-documentation |
| Hosted Themes | https://github.com/react-chatbotify/community-themes |
| Gallery Website | https://github.com/React-ChatBotify/gallery-website |
| Gallery API | https://github.com/React-ChatBotify/gallery-api |

---

## Key Configuration Files

| File | Purpose |
|------|---------|
| `package.json` | Dependencies, scripts, exports (CJS + ESM) |
| `tsconfig.json` | TypeScript config (strict, JSX react-jsx) |
| `vite.config.js` | Vite build config (library mode, dual CJS/ESM output) |
| `jest.config.js` | Jest config (ts-jest, jsdom) |
| `eslint.config.js` | ESLint config (TypeScript parser, React plugins) |
| `cypress.config.ts` | Cypress config (baseUrl: localhost:3000) |
| `setup.jest.js` | Jest setup file |

---

## Developer Guidelines Summary

From DeveloperGuide.md:
1. **Setup**: Node 16+, fork & clone, npm install, npm run start
2. **Design Principles**: 
   - Single Responsibility for components
   - Services handle feature logic, hooks provide shared functionality
   - 8 contexts for global state management
   - Internal vs external hooks distinction
3. **Code Documentation**: Required for components/context/hooks/services
4. **Testing**: 3 types - Unit (Jest), Integration (Cypress), Compatibility (CI only)
5. **PR Process**: Fork workflow, discuss major changes on Discord first
