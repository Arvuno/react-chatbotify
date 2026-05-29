# Baseline Setup and Status Report

## Commands Run

| Command | Result | Output Summary |
|---------|--------|----------------|
| `npm install` | ✅ pass | 805 packages installed; 18 vulnerabilities reported (8 moderate, 9 high, 1 critical); husky install deprecated warning |
| `npm run build` | ✅ pass | tsc + vite build + post-build script completed in ~2s; 140 modules transformed; output: dist/index.js (170.49 kB), dist/index.cjs (141.61 kB), dist/style.css (15.80 kB) |
| `npm run lint` | ✅ pass | eslint --fix ran with no errors or warnings |
| `npm test` | ❌ not found | No "test" script; used `npm run unit:test` instead |
| `npm run unit:test` | ✅ pass | 72 test suites, 371 tests — all passed in ~19.5s |
| `npx tsc --noEmit` | ✅ pass | TypeScript type-checking passed with no errors |

## Baseline Status

- **Build:** pass
- **Lint:** pass
- **Tests:** pass (via `npm run unit:test`)
- **Typecheck:** pass

## Issues Found (pre-existing vs introduced by us)

**All issues are pre-existing. No modifications were made.**

1. **Vulnerabilities:** 18 vulnerabilities (8 moderate, 9 high, 1 critical) — these are pre-existing in the repository's dependencies.
2. **Husky deprecation:** The `husky install` command in the `prepare` script is deprecated — pre-existing.
3. **Browserslist data age:** `caniuse-lite` is 6 months old — pre-existing.
4. **Baseline browser mapping data:** `baseline-browser-mapping` is over 2 months old — pre-existing.
5. **Vite warning:** `outDir /root/.../dist is not inside project root and will not be emptied` — pre-existing.
6. **Vite named/default exports warning:** `Entry module "src/index.tsx" is using named and default exports together` — pre-existing.
7. **Missing `test` script:** The package.json has no `test` script (only `unit:test` and `int:test`) — this is by design, not a failure.

## Notes

- The repository uses `npm run unit:test` (Jest) for unit tests and `npm run int:test` (Cypress) for integration tests.
- The `npm test` command is not defined; attempting to run it produces an error.
- TypeScript compilation, linting, and all 371 unit tests pass cleanly.
