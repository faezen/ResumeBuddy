# Optimization, Refactoring, and Cleanup Plan

## Goals

- Improve maintainability and feature velocity.
- Reduce bundle/runtime overhead.
- Increase reliability of AI output handling.

## Workstreams

### A) Component Refactor
1. Split `ProfileView` into sections: PersonalInfo, Experience, Projects, Education, Skills.
2. Split `OptimizerView` into input form, progress state, result panel, score widgets.
3. Move shared UI controls into reusable primitives.

### B) Domain Layering
1. Add `src/lib/services/` modules:
   - `profileService`
   - `optimizationService`
   - `historyService`
2. Encapsulate Dexie operations in repository-like functions.
3. Keep React views focused on orchestration and rendering.

### C) Reliability Improvements
1. Add runtime schema validation for Gemini response.
2. Add retry/backoff for transient model API errors.
3. Add safe fallback when score/breakdown fields are missing.

### D) Performance
1. Memoize expensive derived render data in optimizer/history views.
2. Lazy-load heavy views where practical.
3. Defer non-critical analytics scripts.

### E) Cleanup
1. Standardize naming for view/component files.
2. Consolidate repeated inline styles into CSS utility classes.
3. Add centralized error boundary + toast/error surface.
