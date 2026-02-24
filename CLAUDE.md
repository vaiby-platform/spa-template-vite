# Project: React + Vite SPA

Build a single-page application from the PLAN.md specification. The stack is already configured — start coding immediately.

## Stack (locked — do NOT change or add frameworks)

- React 19 + TypeScript
- Vite 7
- Tailwind CSS v4 (via `@tailwindcss/vite` plugin — already configured)
- Headless UI (`@headlessui/react`) for interactive components

Do not install additional UI libraries, CSS frameworks, or state management packages unless PLAN.md explicitly requires them.

## Commands

- `npm run dev` — start dev server
- `npm run build` — type-check and build for production
- `npm run lint` — run ESLint

## Ground Rules

1. **Do not switch framework.** React + Vite + TypeScript only. Never migrate to Next.js, Remix, Vue, Svelte, or anything else.
2. **Do not hard-code made-up names.** No "John Doe", "Acme Corp", "Lorem ipsum". Use generic labels ("User", "Item", "Untitled") or derive values from state.
3. **Follow PLAN.md.** Build what the plan describes. Do not add features, screens, or functionality beyond it.

## UX — Build for Non-Technical Users

Simplicity is the top priority. These apps are used by people who are not developers.

- **Less is more.** Fewer controls, fewer options, fewer steps. Remove anything that isn't essential.
- **One clear action per view.** The user should always know what to do next.
- **Plain language.** No jargon or technical terms in the UI.
- **Generous spacing.** Use Tailwind's spacing scale liberally (`p-4`, `space-y-4`, `gap-6`). Don't crowd elements.
- **Responsive.** Mobile-first. Use Tailwind responsive prefixes (`sm:`, `md:`, `lg:`).

## UI & Styling with Tailwind

All styling is done with Tailwind utility classes inline. Do not write custom CSS unless absolutely necessary.

### Layout
- Use `flex`, `grid`, `gap-*`, and `space-y-*` for layout.
- Contain page content with `max-w-2xl mx-auto px-4` or similar.
- Full-height pages: `min-h-screen`.

### Colors & Contrast
- Use `gray-50` / `white` backgrounds with `gray-900` text for high readability.
- Primary actions: `bg-blue-600 text-white hover:bg-blue-700` (or similar strong, accessible combo).
- Secondary/subtle actions: `bg-gray-100 text-gray-700 hover:bg-gray-200`.
- Destructive actions: `bg-red-600 text-white hover:bg-red-700`.
- Always ensure strong contrast between text and background.

### Buttons
```
rounded-lg px-4 py-2 text-sm font-medium transition-colors
focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2
```

### Inputs
```
w-full rounded-lg border border-gray-300 px-3 py-2 text-sm
placeholder:text-gray-400
focus:border-blue-500 focus:outline-none focus:ring-2 focus:ring-blue-500
```

### Typography
- Headings: `text-2xl font-bold text-gray-900` (adjust size per hierarchy).
- Body: `text-sm text-gray-600` or `text-base text-gray-700`.
- Use font weight and size for hierarchy — not color alone.

### Feedback
- Loading: show a spinner or "Loading..." text.
- Empty states: centered message with muted text (`text-gray-400`).
- Errors: `text-red-600` with a brief message.
- Success: `text-green-600` or a brief toast/banner.

## Using Headless UI

Use Headless UI for these interactive patterns instead of building from scratch:

- **Dialog** — modals and confirmation dialogs
- **Menu** — dropdown menus
- **Listbox** — custom select/dropdown
- **Switch** — toggle switches
- **Disclosure** — collapsible sections
- **Popover** — popovers and tooltips
- **Tabs** — tabbed interfaces

Import from `@headlessui/react`. These components are unstyled — apply Tailwind classes directly. Use `Transition` from Headless UI for enter/leave animations.

## Code Conventions

- Functional components with hooks. One component per file.
- Name files after the component: `Header.tsx`, `TaskList.tsx`.
- Keep components under ~100 lines. Split if larger.
- TypeScript interfaces for props and data shapes, in the same file unless shared.
- No `any` types.
- Local state with `useState`. Shared state lifted to nearest common parent.
- No separate CSS files needed — use Tailwind classes inline.

## File Structure

```
src/
  main.tsx          — entry point (do not modify)
  App.tsx           — root component
  App.css           — empty, available if custom CSS is needed
  index.css         — Tailwind import (do not modify)
  components/       — UI components
  assets/           — static assets
```

Keep the structure flat. Create `components/` as needed.

## Do NOT

- Install additional CSS or UI libraries (no MUI, Chakra, shadcn, styled-components).
- Add React Router unless PLAN.md requires it.
- Add Redux, Zustand, or other state libraries unless PLAN.md requires it.
- Add a backend, API layer, or database.
- Create test files unless asked.
- Write custom CSS when Tailwind classes work.
- Create README or documentation files.
