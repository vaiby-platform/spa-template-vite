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

## UI & Styling

All styling is done with Tailwind utility classes. Do not write custom CSS unless absolutely necessary.

- Use `flex`, `grid`, `gap-*`, and `space-y-*` for layout. Contain page content with `max-w-2xl mx-auto px-4` or similar.
- **You have full creative freedom over colors, typography, and visual design.** Choose a cohesive color palette and apply it consistently. Ensure strong contrast between text and backgrounds — readability is non-negotiable.
- **Responsive.** Mobile-first. Use Tailwind responsive prefixes (`sm:`, `md:`, `lg:`).

## UI Components (`src/components/ui/`)

Use the pre-built UI components for interactive elements. They handle accessibility, focus management, keyboard navigation, and portals — you provide the visual styling via `className` props.

**The components ship with minimal, neutral defaults.** You are expected to style them to match your chosen aesthetic. Use the `cn()` helper from `src/lib/utils` to merge classes:

```tsx
import { Button } from "../components/ui/button";
<Button className="bg-indigo-600 text-white hover:bg-indigo-700 rounded-full px-6">Save</Button>
```

Available components:
- **AlertDialog** — confirmation dialogs with required action
- **Badge** — status indicators (variants: default, secondary, destructive, outline, success, warning, info)
- **Button** — action element (variants: default, destructive, outline, secondary, ghost, link; sizes: default, sm, lg, icon)
- **Card** — content container (Card, CardHeader, CardTitle, CardDescription, CardContent, CardFooter)
- **Checkbox** — boolean toggle input
- **Dialog** — modal windows
- **DropdownMenu** — click-triggered menu with items, checkboxes, radio items, separators, sub-menus
- **Label** — accessible form labels
- **Select** — dropdown selection
- **Separator** — visual divider (horizontal/vertical)
- **Switch** — on/off toggle
- **Tabs** — tabbed content panels (Tabs, TabsList, TabsTrigger, TabsContent)

For any interactive pattern not covered above, build it with plain Tailwind + HTML.

**Do NOT build custom interactive components when a UI component already exists.** Use `<Dialog>` for modals, `<Select>` for dropdowns, `<AlertDialog>` for confirmations, etc.

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
