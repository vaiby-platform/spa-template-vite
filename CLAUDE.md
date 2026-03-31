# Project: React + Vite SPA

Build a single-page application from the PLAN.md specification. The stack is already configured — start coding immediately.

## Stack (locked — do NOT change or add frameworks)

- React 19 + TypeScript
- Vite 7
- Tailwind CSS v4 (via `@tailwindcss/vite` plugin — already configured)
- Radix UI primitives + custom components in `src/components/ui/`
- `lucide-react` for icons
- `class-variance-authority` + `clsx` + `tailwind-merge` for styling utilities

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

## UI Components (`src/components/ui/`)

**Always use the pre-built UI components** instead of building interactive elements from scratch. These are Radix UI primitives wrapped with Tailwind styling. Import from `../../components/ui/<component>` or from the barrel `../../components/ui`.

Available components:
- **AlertDialog** — confirmation dialogs with required action
- **Badge** — status indicators (variants: default, secondary, destructive, outline, success, warning, info)
- **Button** — primary action element (variants: default, destructive, outline, secondary, ghost, link; sizes: default, sm, lg, icon). Supports icons via children.
- **Card** — content container (Card, CardHeader, CardTitle, CardDescription, CardContent, CardFooter)
- **Checkbox** — boolean toggle input
- **Dialog** — modal windows
- **DropdownMenu** — click-triggered menu with items, checkboxes, radio items, separators, sub-menus
- **Label** — accessible form labels
- **Select** — dropdown selection with search-friendly items
- **Separator** — visual divider (horizontal/vertical)
- **Switch** — on/off toggle
- **Tabs** — tabbed content panels (Tabs, TabsList, TabsTrigger, TabsContent)

For any interactive pattern not covered above (e.g. accordion, tooltip, popover), build it with plain Tailwind + HTML. Keep it simple.

### Customizing components

These components accept a `className` prop — pass additional Tailwind classes to override or extend the default styling. Use the `cn()` helper from `src/lib/utils` to merge classes cleanly:

```tsx
import { Button } from "../components/ui/button";
import { cn } from "../lib/utils";

<Button className="bg-indigo-600 hover:bg-indigo-700">Custom</Button>
```

**Do NOT build custom interactive components when a UI component already exists.** For example, use `<Dialog>` for modals, `<Select>` for dropdowns, `<AlertDialog>` for confirmations.

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
  lib/
    utils.ts        — cn() helper for merging Tailwind classes
  components/
    ui/             — Radix UI primitives with Tailwind styling (do not modify)
  assets/           — static assets
```

Keep the structure flat. Add page-level components directly in `components/`. Do not modify files in `components/ui/` — customize by passing `className` props.

## TypeScript Rules

This project uses strict TypeScript settings. Pay attention to:

- **`verbatimModuleSyntax` is enabled.** You MUST use `import type` for 
  type-only imports. Use `import { type Foo, bar }` for mixed imports.
- **`noUnusedLocals` and `noUnusedParameters` are enabled.** No dead code. 
  Prefix intentionally unused parameters with `_`.
- Always run `npm run build` (not just `vite build`) to verify the code 
  compiles. The build command runs `tsc -b` first.

## Scope Limits

- Maximum 6 component files in `src/components/`.
- No `hooks/` or `utils/` directories — put helpers in the component 
  files or a single `src/lib.ts` if needed.
- No binary assets (images, sounds, fonts). Use emoji, CSS, or inline 
  SVG for visual elements.
- If PLAN.md exceeds these limits, simplify to fit. Functionality over 
  complexity.

## Do NOT

- Install additional CSS or UI libraries (no MUI, Chakra, shadcn, styled-components). Use the existing `components/ui/` primitives instead.
- Add React Router unless PLAN.md requires it.
- Add Redux, Zustand, or other state libraries unless PLAN.md requires it.
- Add a backend, API layer, or database.
- Create test files unless asked.
- Write custom CSS when Tailwind classes work.
- Create README or documentation files.
