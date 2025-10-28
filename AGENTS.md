# Repository Guidelines

## Project Structure & Module Organization
- `app/` – Next.js App Router entry points (`app/page.tsx`, `app/layout.tsx`, `app/globals.css`).
- `components/` – Feature components (`scene-detector.tsx`) and UI primitives under `components/ui/*`.
- `lib/` – Pure logic and utilities (`frame-difference.ts`, `translations.ts`, `utils.ts`).
- `e2e/` – Playwright tests (`*.spec.ts`).
- `public/` – Static assets (images, icons).
- `.github/workflows/` – CI for build, tests, and coverage.

## Build, Test, and Development Commands
- `npm install` – Install dependencies (CI/Vercel use npm).
- `npm run dev` – Start local dev server at `http://localhost:3000`.
- `npm run build` – Production build.
- `npm start` – Run the built app.
- `npm test` – Jest unit/component tests.
- `npm run test:watch` – Watch mode for Jest.
- `npm run test:coverage` – Generate coverage reports.
- `npm run test:e2e` – Playwright E2E tests (auto-starts dev server).

Node 18+ is required (`engines.node ">=18"`). Prefer npm for parity with CI and Vercel.

## Coding Style & Naming Conventions
- Language: TypeScript, strict mode; React function components.
- Indentation: 2 spaces; filenames in kebab-case (e.g., `scene-detector.tsx`).
- Components: PascalCase identifiers; place primitives in `components/ui/*`.
- Imports: use path alias `@/*` (see `tsconfig.json`).
- Styling: Tailwind CSS in `app/globals.css`; compose classes with `cn` from `lib/utils`.
- Client components must include `"use client"` at the top.

## Testing Guidelines
- Unit/Component: Jest + Testing Library. Place tests in `__tests__` near source, name `*.test.ts`/`*.test.tsx`.
- E2E: Playwright specs in `e2e/*.spec.ts`. Use `test:e2e` locally; CI runs chromium by default.
- Coverage: `test:coverage` collects from `components/`, `lib/`, and `app/`. Add tests for new logic; keep flakiness low.

## Commit & Pull Request Guidelines
- Use Conventional Commits: `feat: ...`, `fix: ...`, `refactor: ...`, `chore: ...` (e.g., `feat: integrate FFmpeg for video clips`).
- PRs must include: clear description, linked issue (if any), screenshots/GIFs for UI changes, test plan, and passing CI.
- Keep diffs focused; follow structure above; avoid console noise and dead code.

## Security & Configuration Tips
- All processing is client-side; do not introduce server uploads.
- Lazy-load heavy libs (e.g., FFmpeg); handle large files and errors gracefully.
- No secrets needed; avoid adding env vars unless documented.
