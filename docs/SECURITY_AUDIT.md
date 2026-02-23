# Security Audit (Static)

## Threat Model Snapshot

### Assets
- User resume/profile data (PII, career history).
- User API key.
- Generated outputs and historical job descriptions.

### Trust Boundaries
- Browser local environment.
- Third-party Gemini endpoint.
- Optional Vercel-hosted static frontend.

## Key Risks

### 1) API key in localStorage
- Current persisted Zustand partial includes `apiKey`.
- Risk: any XSS issue can expose key.
- Severity: Medium-High.

### 2) PII persistence without encryption controls
- IndexedDB stores personal profile and job history in plaintext at rest on device.
- Risk: local compromise/shared machine exposure.
- Severity: Medium.

### 3) Prompt injection/untrusted JD content
- Arbitrary job descriptions are fed to model prompts.
- Risk: instruction hijacking, malformed output, lower quality/safety.
- Severity: Medium.

### 4) Lack of strict response validation
- JSON parse succeeds even if semantic structure deviates.
- Risk: integrity/reliability issues in scoring and rendering.
- Severity: Medium.

## Hardening Recommendations

1. Remove API key from persisted storage by default; keep in-memory session mode as default and optional encrypted persistence.
2. Add CSP headers + strict escaping policy review across UI.
3. Validate model responses using runtime schema (reject/fallback gracefully).
4. Add “sensitive mode” to disable local history writes.
5. Provide one-click “wipe all local data” and visible privacy indicators.
6. Consider optional passphrase-based local encryption for IndexedDB payloads.
