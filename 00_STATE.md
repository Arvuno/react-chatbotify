# Repository State

**Last Updated**: 2026-05-28  
**Researcher**: hermes-agent subagent  
**Purpose**: Initial repository research and mapping

---

## Research Completion Status

- [x] README.md - Read
- [x] CONTRIBUTING.md - Read
- [x] CODE_OF_CONDUCT.md - Read
- [x] LICENSE - Read
- [x] SECURITY.md - Read
- [x] package.json - Read
- [x] tsconfig.json - Read
- [x] jest.config.js - Read
- [x] eslint.config.js - Read
- [x] vite.config.js - Read
- [x] cypress.config.ts - Read
- [x] .github/ directory - Listed and read
- [x] src/ directory - Listed and key files read
- [x] types/ directory - Listed and key files read
- [x] docs/DeveloperGuide.md - Read
- [x] __tests__/ directory - Listed
- [x] SHOWCASES.md - Read
- [x] 01_REPO_MAP.md - Written

---

## Repository Metadata

| Field | Value |
|-------|-------|
| Name | react-chatbotify |
| Version | 2.5.0 |
| Description | A modern React library for creating flexible and extensible chatbots |
| License | MIT |
| Author | Tan Jin (tjtanjin) |
| Homepage | https://react-chatbotify.com |
| Repository URL | https://github.com/react-chatbotify/react-chatbotify |
| Fork Source | Arvuno/react-chatbotify |

---

## Key Findings

### Project Type
React component library for building chatbots. Supports React 16-19 with TypeScript.

### Architecture
- **8 Contexts**: BotRefs, BotStates, ChatBot, Messages, Paths, Settings, Styles, Toasts
- **Services**: Audio, Voice, Block, ChatHistory, Theme, RcbEvent
- **Dual Hook System**: Internal hooks (logic) + External hooks (public API filtering layer)
- **24 Custom Events**: Window-level events for chatbot actions

### Dependencies
- **Peer Dependencies**: react, react-dom (>=16.14.0)
- **Runtime Dependency**: @rcb-plugins/input-validator (^0.3.1)
- **Dev Dependencies**: Comprehensive (Vite, Jest, Cypress, ESLint, TypeScript, Husky)

### Build Output
- ESM: `./dist/index.js`
- CJS: `./dist/index.cjs`
- Types: `./dist/index.d.ts`

---

## Fork Relationship

- **Upstream**: https://github.com/react-chatbotify/react-chatbotify
- **Fork**: https://github.com/Arvuno/react-chatbotify
- **Working Directory**: /root/star-first-1/repos/react-chatbotify

---

## Action Items

### Documentation Created
- [x] 01_REPO_MAP.md - Comprehensive repository map written

### Files Not Found
- 00_STATE.md did not exist - created

---

## Notes

1. **Unit Test Coverage**: According to DeveloperGuide.md, unit testing was "recently setup" and only covers "a small handful of hooks". This is an area for improvement.

2. **Plugin System**: The plugin system is mentioned as work-in-progress in v2. Documentation was slated for release end October/early November 2024.

3. **Theme System**: Themes is a v2 feature with separate themes repository (community-themes).

4. **Mobile Support**: Special handling exists for mobile keyboard resize events in `useBotEffectsInternal` hook.

5. **SSR Validation**: Separate script at `ssr/ssr-validate.js` validates SSR compatibility for Node.js 19+.
