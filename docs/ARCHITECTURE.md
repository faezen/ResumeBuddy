# Architecture

## High-Level Architecture

```text
Browser UI (React Components)
  ├─ Zustand store (settings + view state)
  ├─ IndexedDB via Dexie (profile/history persistence)
  └─ Gemini API client (fetch with user API key)

No application backend in MVP path
```

## Architectural Decisions

### 1) Client-Side Persistence
- Chosen tech: Dexie + IndexedDB.
- Benefit: privacy-preserving local data store.
- Tradeoff: no cross-device sync by default.

### 2) Direct LLM Calls (BYOK)
- Chosen tech: browser `fetch` to Gemini endpoint.
- Benefit: no server infra, no model proxy cost.
- Tradeoff: key management and browser-exposure concerns.

### 3) Single-Shell View Switching
- Current routing model is app-internal view toggling.
- Benefit: rapid development and cohesive UX.
- Tradeoff: weak deep linking and SEO discoverability.

## Data Flow: Optimization

1. `OptimizerView` validates preconditions (API key + profile + JD text).
2. Prompt assembled via `buildUserPrompt` from profile and job description.
3. `callGemini` posts to model endpoint.
4. Response parsed into `GeminiResponse`.
5. JD + optimized result persisted to `jobDescriptions` and `resumes` tables.
6. UI renders score and findings.

## Evolution Targets

- Introduce service layer between components and persistence/AI clients.
- Add schema validation (`zod`/runtime guards) around model responses.
- Prepare modular provider adapters for multi-LLM support.
- Split monolithic components into reusable domain sections.
