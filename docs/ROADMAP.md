# Product & Engineering Roadmap

This roadmap includes requested features and additional strategic initiatives.

## Phase 1 — UX and Input Quality (Near-Term)

### 1) PDF Resume Parser (Auto-Populate Fields)
- Upload PDF resume.
- Extract text and map fields into Master Profile sections.
- Let user review/edit parsed content before save.
- Handle multi-column resumes and malformed PDFs gracefully.

### 2) Job Description Link Ingestion ("Insert JD Link")
- Add input for JD URL in Optimizer workflow.
- Fetch and parse title/company/description automatically.
- Support fallback methods where legal and permitted:
  - direct HTML extraction
  - RSS feed sources
  - simplified curl/text endpoints
- Always show source preview and allow manual correction.

### 3) Better Prompt Controls
- Allow seniority/tone/length optimization presets.
- Add role-family templates (frontend, backend, PM, data, etc.).

## Phase 2 — Discoverability and Experience

### 4) PWA Enablement
- Add `manifest.webmanifest`.
- Generate app icons/favicons for install contexts.
- Add service worker for offline shell and cached assets.
- Introduce install prompt UX and offline status indicators.

### 5) SEO Foundation
- Public marketing pages with static metadata and OpenGraph tags.
- Structured data for product/faq/how-to pages.
- Sitemap and robots configuration.
- Conversion-oriented landing content for targeted keywords.

## Phase 3 — AI Platform Flexibility

### 6) Local/User LLM Provider Adapter Layer
- Introduce provider abstraction (`Gemini`, `OpenAI`, `Anthropic`, `Ollama`, `LM Studio`, custom endpoint).
- Adapter contract for generate/stream/health-check capabilities.
- User-selectable provider in settings.
- Support local model execution for privacy-sensitive users.

### 7) Prompt and Evaluation Pipeline
- Add rubric regression dataset for quality checks.
- Track quality metrics over prompt/version changes.
- Build deterministic evaluation harness for releases.

## Phase 4 — Enterprise/Business Milestone

### 8) ResumeChad API (Monetizable Platform)
- Build authenticated API for resume optimization and scoring.
- Offer usage tiers, API keys, quotas, and billing.
- Multi-tenant usage analytics and audit trails.
- Webhooks for workflow automation (ATS/HRIS integration).

### 9) Enterprise Features
- Team workspaces and role-based access control.
- Shared brand/company templates.
- Data retention controls and compliance posture (SOC2 roadmap).
- Admin dashboards and SLA-backed plans.

## Parallel Tracks (Recommended)

- Accessibility hardening (keyboard nav, screen-reader labels, contrast audits).
- Internationalization/localization.
- Resume style/template marketplace.
- Interview prep companion (question bank from JD + profile gaps).
- Skill-gap planner and learning recommendations.

## Prioritization Guidance

1. PDF parser + JD-link ingestion directly reduce user friction and improve conversion.
2. PWA + SEO increase adoption and retention.
3. LLM adapter layer protects against provider lock-in.
4. API platform unlocks B2B monetization and enterprise expansion.
