# File map

Why each thing in this project exists. Nothing here should be a mystery box.

- `.altitude`: known. Links this folder to your Altitude journey so lessons know where you are. Altitude wrote it; never edit it.
- `DESIGN.md`: known. How the app looks: colours, fonts, spacing and the parts of every screen, copied from your Altitude prototype. Every screen gets built to it.
- `package.json`: known. The project's shopping list: its name, its scripts (`dev`, `build`, `lint`, `preview`), and which packages it needs at runtime (`dependencies`) versus only while building (`devDependencies`).
- `package-lock.json`: known. The receipt: the exact version of every installed package, including the ones your packages pulled in, so the next `npm install` rebuilds the same set. Machine-written; commit it, never hand-edit it.
- `node_modules/`: known. The downloaded packages themselves (~115 of them). Machine-made, never edit, always rebuildable with `npm install`.
- `index.html`: known. The one page the browser loads. Its `<div id="root">` is where React draws, and its `<script>` tag loads `src/main.tsx`.
- `src/`: known. The app's code.
  - `src/main.tsx`: known. Starts React: finds `#root` and renders `App` into it.
  - `src/App.tsx`: known. Vite's starter screen; it gets replaced by Study Quest's screens.
  - `src/App.css`, `src/index.css`, `src/assets/`: parked. Starter styles and images; replaced when the design colours go in (section 00, next task).
- `vite.config.ts`: known. Vite's settings; right now it just turns on the React plugin.
- `tsconfig.json`, `tsconfig.app.json`, `tsconfig.node.json`: parked. TypeScript's settings: one for the app code, one for config files like `vite.config.ts`. Covered when a lesson changes them.
- `eslint.config.js`: parked. The linter's rules. Covered when you first run `npm run lint`.
- `public/`: parked. Files served as-is, like the favicon. Covered when the app gets its own icon.
- `README.md`: parked. Vite's starter readme; rewrite it when the project is worth showing.
- `.gitignore`: parked. Tells Git what to leave out (like `node_modules/`). Covered in the first Git lesson.
- `learning/`: known. Your lesson notes. Not part of the app.
  - `learning/plan.md`: known. Your journey's plan, regenerated from Altitude at each lesson. Local edits don't sync.
  - `learning/file-map.md`: known. This file.
  - `learning/scratch/`: known. Your practice drills. Yours to keep; never part of the app.
    - `learning/scratch/tip-calc/`: known. Your drill project: chalk as a dependency, prettier as a pinned dev dependency.
