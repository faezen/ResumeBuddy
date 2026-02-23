# Codebase Guide

## Top-Level Structure

- `src/app/`
  - `layout.tsx`: global layout wrapper.
  - `page.tsx`: main client-side entry + view switching.
  - `globals.css`: design tokens and component styling.
- `src/components/`
  - `LandingPage.tsx`
  - `Sidebar.tsx`
  - `ProfileView.tsx`
  - `OptimizerView.tsx`
  - `CoverLetterView.tsx`
  - `HistoryView.tsx`
  - `SettingsView.tsx`
- `src/lib/`
  - `db.ts`: Dexie schema + app data types.
  - `store.ts`: Zustand persisted app settings.
  - `gemini.ts`: Gemini API request + JSON parse handling.
  - `rubric.ts`: scoring constants and prompt builders.

## Data Model Summary (`src/lib/db.ts`)

- `masterProfile` (`id='current_user'`) 
- `jobDescriptions`
- `resumes` (optimized output + scoring breakdown)
- `coverLetters`

## Runtime Control Flow

1. User enters profile in `ProfileView`.
2. Profile is persisted to IndexedDB.
3. User triggers optimization in `OptimizerView`.
4. `buildUserPrompt(...)` prepares AI input.
5. `callGemini(...)` sends request directly to Gemini API.
6. Response is parsed and saved to IndexedDB history tables.

## State Boundaries

- **Zustand (`store.ts`)**: UX/global preferences (`activeView`, `theme`, `apiKey`).
- **Dexie (`db.ts`)**: durable domain data (profile, job descriptions, outputs).
- **Component local state**: form-level interaction state.
