# Dependencies, Removal Candidates, and Cleanup

## Current Dependencies

### Runtime
- `next`, `react`, `react-dom`
- `dexie`
- `zustand`
- `uuid`
- `@vercel/analytics`, `@vercel/speed-insights`

### Dev
- TypeScript + ESLint + Tailwind/PostCSS stack

## Observations

1. Dependency set is relatively lean.
2. `@types/uuid` may be unnecessary depending on `uuid` version-provided typings and TS config.
3. Vercel analytics packages should be confirmed as actively wired into app runtime before retaining.

## Cleanup Checklist

1. Run import-usage audit and remove unused packages.
2. Lock minimal semver ranges where deterministic behavior is preferred.
3. Add dependency policy doc for adding/removing packages.
4. Introduce periodic dependency risk review (security + bundle size).

## Candidate Additions (Planned)

- `zod` for runtime validation.
- PDF parsing stack (e.g., `pdfjs-dist`) for resume import.
- scraping/ingestion adapters (with strict legal/robots compliance) for JD autofill pipeline.
- PWA toolchain (manifest/service worker/icon generation).

## Removal Guidance

Before removal, verify:
1. No dynamic imports rely on package.
2. No transitive peer requirement breaks lint/build.
3. Lockfile is regenerated cleanly.
