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

# Core Principles

### 1. Code Quality and Organization

- **Small Components:** Create small, focused components (under 50 lines).
- **TypeScript:** Use TypeScript for type safety.
- **Project Structure:** Follow the established project structure.
- **Responsive Design:** Implement responsive designs by default.
- **Logging:** Write extensive console logs for debugging purposes.

### 2. Component Creation

- **New Files:** Create a new file for each component.
- **Component Library:** Use `shadcn/ui` components whenever possible.
- **Atomic Design:** Follow atomic design principles (organizing components into atoms, molecules, organisms, etc.).
- **File Organization:** Ensure proper file organization.

### 3. State Management

- **Server State:** Use `React Query` for managing server state.
- **Local State:** Implement local state using `useState` and `useContext`.
- **Prop Drilling:** Avoid prop drilling (passing props down through multiple layers of components).
- **Caching:** Cache server responses when appropriate.

### 4. Error Handling

- **User Feedback:** Use toast notifications for user feedback on errors.
- **Error Boundaries:** Implement proper React error boundaries to catch rendering errors.
- **Logging:** Log errors for debugging.
- **User-Friendly Messages:** Provide clear, user-friendly error messages.

### 5. Performance

- **Code Splitting:** Implement code splitting where needed to reduce initial load times.
- **Image Optimization:** Optimize the loading of images.
- **Proper Hooks:** Use React hooks correctly to manage component lifecycle and state.
- **Minimize Re-renders:** Write code that minimizes unnecessary component re-renders.

### 6. Security

- **Input Validation:** Validate all user inputs on the client and server side.
- **Authentication:** Implement proper authentication flows.
- **Data Sanitization:** Sanitize data before displaying it to prevent XSS attacks.
- **OWASP Guidelines:** Follow the OWASP (Open Web Application Security Project) security guidelines.

### 7. Testing

- **Unit Tests:** Write unit tests for critical functions.
- **Integration Tests:** Implement integration tests to ensure components work together correctly.
- **Responsive Layouts:** Test to ensure layouts are responsive.
- **Error Handling:** Verify that error handling mechanisms work as expected.

### 8. Documentation

- **Function Documentation:** Document complex functions to explain their purpose and usage.
- **README:** Keep the `README.md` file up to date.
- **Setup Instructions:** Include clear setup instructions in the documentation.
- **API Endpoints:** Document all API endpoints.
