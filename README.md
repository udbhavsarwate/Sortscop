# Sortscope

An interactive sorting algorithm visualizer built as a polished, production-style educational tool — real-time bar animations, algorithm write-ups, a multi-language code viewer, a live performance dashboard, and a side-by-side race mode.

## Features

- **9 algorithms** across three tiers — Bubble, Selection, Insertion (Basic); Merge, Quick, Heap (Intermediate); Shell, Counting, Radix (Advanced).
- **Real-time bar visualization** with Framer Motion spring animations for comparisons, swaps, pivots, merges, and sorted state.
- **Full playback controls** — generate random / shuffle / reverse / nearly-sorted arrays, a custom array input with validation, array-size and speed sliders, and play / pause / resume / stop.
- **Algorithm info panel** — description, time/space complexity (best/average/worst), stability, in-place status, applications, advantages, and disadvantages.
- **Code viewer** with basic syntax highlighting for JavaScript, Python, Java, and C++, with one-click copy.
- **Live performance dashboard** — comparisons, swaps/writes, elapsed time, array size, and estimated memory, updating in real time.
- **Compare mode** — run two algorithms side by side on the same array and compare their comparisons, swaps, and completion time.
- **6 themes** — Signal (dark), Daylight (light), Ocean, Neon, Cyberpunk, and Minimal — switchable instantly.
- **Persistent stats** (localStorage) — total arrays sorted, favorite algorithm, largest array sorted, fastest run, and average run time.
- **Tested** — Vitest unit tests cover every sorting algorithm's correctness (empty, single-element, duplicates, reverse-sorted, and random arrays), the visualization color-priority logic, the syntax highlighter, and the Zustand store.

## Tech stack

React 19 · TypeScript · Vite · Tailwind CSS v4 · Framer Motion · Zustand · React Icons · ESLint · Prettier · Vitest

## Getting started

```bash
npm install
npm run dev          # start the dev server
npm run build        # type-check and build for production
npm run preview       # preview the production build locally
npm run test          # run the test suite once
npm run test:watch    # run tests in watch mode
npm run lint          # lint the codebase
npm run format         # format with Prettier
```

## Folder structure

```
src/
├── algorithms/       # Pure sort implementations + step recorders, one file per algorithm
├── components/       # Reusable UI components (BarChart, Controls, CodeViewer, etc.)
├── constants/        # Algorithm metadata, code snippets, and theme token definitions
├── hooks/            # useThemeEffect, useSortPlayer (comparison-mode playback)
├── pages/            # VisualizePage (top-level page composition)
├── store/            # Zustand stores: playback/visualizer state, persisted stats
├── styles/           # Global stylesheet and theme CSS variables
├── utils/            # Bar-color resolution, syntax highlighting
└── main.tsx / App.tsx
```

Each algorithm module (`src/algorithms/*.ts`) runs the real algorithm against a working copy of the array and records a step-by-step timeline (`compare`, `swap`, `overwrite`, `merge`, `pivot`, `sorted`, …). The visualizer replays that timeline on a timer, so what's on screen is a faithful animation of the actual algorithm's execution rather than a simulated approximation.

## Deployment

The app builds to a static `dist/` folder and can be hosted anywhere that serves static files.

**Vercel** — a `vercel.json` is included; import the repo in Vercel and it will run `npm run build` with `dist` as the output directory automatically.

**Netlify** — a `netlify.toml` is included with the same build settings; connect the repo or run `netlify deploy --prod` after building.

**GitHub Pages** — `vite.config.ts` uses `base: './'` so the build works from any subpath:
```bash
npm run build
npx gh-pages -d dist
```
Then enable GitHub Pages for the `gh-pages` branch in the repository settings.

## Future improvements

- Additional algorithms (Tim sort, Bucket sort, Cocktail sort)
- Multi-way comparison mode (3+ algorithms racing simultaneously)
- Array import/export (CSV/JSON) and shareable permalinks encoding the current array + algorithm
- Step-by-step "scrubbing" (drag through the timeline instead of only play/pause)
- Toggleable sound design for compare/swap events
