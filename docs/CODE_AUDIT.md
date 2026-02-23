# Code Audit (Static)

## Executive Summary

The codebase is clean and approachable for an MVP, with clear user value and minimal infrastructure overhead. The most urgent maintainability opportunities are modularity, runtime validation, and reducing large-component complexity.

## Findings

### 1) Very large UI components increase change risk
- `ProfileView.tsx` and `OptimizerView.tsx` own many responsibilities (forms, validation, persistence, rendering).
- Impact: higher regression risk and more difficult onboarding.

### 2) Limited domain service boundaries
- Components directly call DB and AI clients.
- Impact: weaker testability and hard-to-reuse domain operations.

### 3) Runtime response assumptions
- Gemini responses are parsed from text JSON and trusted after parse.
- Impact: malformed model output can degrade UX or crash specific render paths.

### 4) Typed models are good, but validation is compile-time only
- Strong TS interfaces exist in `db.ts` and `gemini.ts`.
- Missing: runtime guards on persisted/modeled data.

## Recommended Action Themes

1. Extract hooks/services for profile, optimization, and history domains.
2. Add runtime schema validation for API responses and persisted migrations.
3. Introduce narrower presentational components + container pattern.
4. Add lightweight test coverage for prompt-building and parsing edges.
