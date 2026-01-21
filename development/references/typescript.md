# TypeScript (Dev Steward Reference)

Use this reference when writing, reviewing, or debugging TypeScript/React in the current repo.

## Type Safety Rules

- Enable and respect TypeScript `strict` mode; prefer precise types over assertions.
- Do not use `any` for React props; model data and events explicitly.
- Type all component props, state, custom hooks, and event handlers.
- Prefer interfaces for public component/module APIs.
- Use `React.ReactNode` for `children`.

## React & Component Design

- Prefer functional components.
- Keep components small and focused; separate concerns (data vs logic vs presentation).
- Favor variants/composition over ad-hoc styling overrides.

## Tailwind + shadcn/ui Guidelines

- Use semantic design tokens and manage them via `index.css` and `tailwind.config.ts`.
- Avoid inline styles; ensure accessible contrast for all states.
- Update components via variants, not override classes.
- Do not use RGB colors wrapped in `hsl()` in `tailwind.config.ts`.
- For shadcn outline variants, ensure text remains visible in all states.

## Default Library Preferences (when choosing tooling)

| Purpose | Libraries |
| --- | --- |
| Database | Drizzle |
| Forms & validation | React Hook Form, Zod |
| Generative AI | Vercel AI SDK, ai-elements |
| Linting & formatting | ESLint, Prettier |
| Package management | pnpm |
| State management | React Query, Zustand |
| Testing | Vitest, React Testing Library |

