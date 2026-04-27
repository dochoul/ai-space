# React Boilerplate Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Convert the existing Hello World `index.html` into a minimal Vite + React 19 + TypeScript project.

**Architecture:** Scaffold a standard Vite React-TS project in-place: replace `index.html` with a Vite-compatible version, add `src/main.tsx` and `src/App.tsx`, and add the necessary config files. No routing, no state management, no CSS framework.

**Tech Stack:** Vite 6, React 19, TypeScript 5, pnpm

---

### Task 1: Create `package.json`

**Files:**
- Create: `package.json`

- [ ] **Step 1: Write `package.json`**

```json
{
  "name": "ai-space",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "tsc -b && vite build",
    "preview": "vite preview"
  },
  "dependencies": {
    "react": "^19.1.0",
    "react-dom": "^19.1.0"
  },
  "devDependencies": {
    "@types/react": "^19.1.2",
    "@types/react-dom": "^19.1.2",
    "@vitejs/plugin-react": "^4.4.1",
    "typescript": "~5.8.3",
    "vite": "^6.3.3"
  }
}
```

- [ ] **Step 2: Commit**

```bash
git add package.json
git commit -m "chore: add package.json for Vite + React + TypeScript"
```

---

### Task 2: Create TypeScript configs

**Files:**
- Create: `tsconfig.json`
- Create: `tsconfig.node.json`

- [ ] **Step 1: Write `tsconfig.json`**

```json
{
  "files": [],
  "references": [
    { "path": "./tsconfig.node.json" },
    { "path": "./tsconfig.app.json" }
  ]
}
```

- [ ] **Step 2: Write `tsconfig.app.json`**

```json
{
  "compilerOptions": {
    "tsBuildInfoFile": "./node_modules/.tmp/tsconfig.app.tsbuildinfo",
    "target": "ES2020",
    "useDefineForClassFields": true,
    "lib": ["ES2020", "DOM", "DOM.Iterable"],
    "module": "ESNext",
    "skipLibCheck": true,
    "moduleResolution": "bundler",
    "allowImportingTsExtensions": true,
    "isolatedModules": true,
    "moduleDetection": "force",
    "noEmit": true,
    "jsx": "react-jsx",
    "strict": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noFallthroughCasesInSwitch": true,
    "noUncheckedSideEffectImports": true
  },
  "include": ["src"]
}
```

- [ ] **Step 3: Write `tsconfig.node.json`**

```json
{
  "compilerOptions": {
    "tsBuildInfoFile": "./node_modules/.tmp/tsconfig.node.tsbuildinfo",
    "target": "ES2022",
    "lib": ["ES2023"],
    "module": "ESNext",
    "skipLibCheck": true,
    "moduleResolution": "bundler",
    "allowImportingTsExtensions": true,
    "isolatedModules": true,
    "moduleDetection": "force",
    "noEmit": true,
    "strict": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noFallthroughCasesInSwitch": true,
    "noUncheckedSideEffectImports": true
  },
  "include": ["vite.config.ts"]
}
```

- [ ] **Step 4: Commit**

```bash
git add tsconfig.json tsconfig.app.json tsconfig.node.json
git commit -m "chore: add TypeScript config files"
```

---

### Task 3: Create `vite.config.ts`

**Files:**
- Create: `vite.config.ts`

- [ ] **Step 1: Write `vite.config.ts`**

```typescript
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [react()],
})
```

- [ ] **Step 2: Commit**

```bash
git add vite.config.ts
git commit -m "chore: add Vite config with React plugin"
```

---

### Task 4: Replace `index.html` with Vite entry point

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Replace `index.html` content**

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>AI Space</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.tsx"></script>
  </body>
</html>
```

- [ ] **Step 2: Commit**

```bash
git add index.html
git commit -m "feat: update index.html for Vite entry point"
```

---

### Task 5: Create React source files

**Files:**
- Create: `src/main.tsx`
- Create: `src/App.tsx`

- [ ] **Step 1: Create `src/` directory and write `src/main.tsx`**

```typescript
import { StrictMode } from 'react'
import { createRoot } from 'react-dom/client'
import App from './App'

createRoot(document.getElementById('root')!).render(
  <StrictMode>
    <App />
  </StrictMode>,
)
```

- [ ] **Step 2: Write `src/App.tsx`**

```typescript
function App() {
  return <h1>Hello World</h1>
}

export default App
```

- [ ] **Step 3: Commit**

```bash
git add src/main.tsx src/App.tsx
git commit -m "feat: add React entry point and root App component"
```

---

### Task 6: Install dependencies and verify

**Files:** none

- [ ] **Step 1: Install dependencies**

```bash
pnpm install
```

Expected: `node_modules/` created, `pnpm-lock.yaml` generated, no errors.

- [ ] **Step 2: Type-check**

```bash
pnpm exec tsc -b
```

Expected: No output (zero errors).

- [ ] **Step 3: Start dev server and verify**

```bash
pnpm dev
```

Expected output includes:
```
  VITE v6.x.x  ready in ...ms

  ➜  Local:   http://localhost:5173/
```

Open `http://localhost:5173/` — should show **Hello World** in the browser.

- [ ] **Step 4: Test production build**

```bash
pnpm build
```

Expected: `dist/` directory created, no errors.

- [ ] **Step 5: Commit lockfile**

```bash
git add pnpm-lock.yaml
git commit -m "chore: add pnpm lockfile"
```
