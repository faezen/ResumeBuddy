# Project Overview

## What ResumeChad Is

ResumeChad is a **privacy-first ATS resume optimizer**. Users provide:

1. A master profile (experience, projects, skills, education).
2. A job description.
3. Their own Gemini API key (BYOK).

The app generates:

- Optimized resume content aligned to the job.
- ATS-style score + rubric breakdown.
- Tailored cover letter.
- Download/copy-ready output.

## Product Principles

- **Client-side first:** no backend required for current MVP workflows.
- **User data ownership:** profile and history stored in IndexedDB/localStorage.
- **BYOK AI access:** direct browser → Gemini call with user-provided key.
- **Fast iteration:** single Next.js app with local state and low infra overhead.

## Current Functional Areas

- Landing/onboarding
- Master Profile editor
- Resume Optimizer
- Cover Letter generator
- History view
- Settings (API key + theme)

## Key Constraints

- API key is currently persisted in localStorage (convenient but security-sensitive).
- App router is used mostly as a single client-side shell (`src/app/page.tsx`).
- AI schema robustness relies on prompt discipline + runtime JSON parsing.

## Stakeholders

- **Primary users:** job seekers and career changers.
- **Secondary users:** power users who submit many job variants.
- **Future enterprise users:** recruiting agencies, career-coaching teams, staffing firms.
