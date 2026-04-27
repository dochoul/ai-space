# React Boilerplate Design

**Date:** 2026-04-27
**Status:** Approved

## Overview

Convert the existing `index.html` (Hello World placeholder) into a minimal React-based project using Vite as the build tool.

## Stack

| Tool | Version | Role |
|------|---------|------|
| Vite | 6.x | Build tool & dev server |
| React | 19.x | UI library |
| TypeScript | 5.x | Type safety |
| pnpm | latest | Package manager |

## Project Structure

```
ai-space/
├── index.html          # Vite entry point (replaces current index.html)
├── src/
│   ├── main.tsx        # React DOM mount point
│   └── App.tsx         # Root component (renders Hello World)
├── package.json
├── vite.config.ts
├── tsconfig.json
└── tsconfig.node.json
```

## File Descriptions

- **`index.html`**: Vite-compatible HTML with `<div id="root">` and a `<script type="module">` pointing to `src/main.tsx`
- **`src/main.tsx`**: Calls `ReactDOM.createRoot(...).render(<App />)`
- **`src/App.tsx`**: Functional component returning `<h1>Hello World</h1>`
- **`vite.config.ts`**: Minimal config with `@vitejs/plugin-react`
- **`tsconfig.json`**: Standard React + Vite TypeScript config

## Commands

```bash
pnpm install    # Install dependencies
pnpm dev        # Dev server at http://localhost:5173
pnpm build      # Production build → dist/
pnpm preview    # Preview production build
```

## Scope

Minimal boilerplate only. No routing, no state management, no CSS framework, no testing setup. Those can be added later as needed.
