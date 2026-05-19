# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## About this project

This is a starter project for a Claude Code course on [codewithmosh.com](https://codewithmosh.com/p/claude-code). The app intentionally contains a bug, poor UI, and messy code — fixing these is part of the course.

## Commands

```bash
npm run dev      # Start dev server at http://localhost:5173
npm run build    # Production build
npm run preview  # Preview production build
npm run lint     # Run ESLint
```

No test suite is configured.

## Architecture

The entire app lives in `src/App.jsx` as a single monolithic component. There are no sub-components, no routing, and no external state management — all state is managed via `useState`.

**Known bug:** `amount` is stored as a string in state (the `<input type="number">` value is never parsed). The `totalIncome` and `totalExpenses` reductions use `+` on strings, causing string concatenation instead of numeric addition.

**Data shape:** Each transaction has `{ id, description, amount, type, category, date }`. `type` is `"income"` or `"expense"`; `category` is one of `["food", "housing", "utilities", "transport", "entertainment", "salary", "other"]`.

Styling is split between `src/App.css` (component styles) and `src/index.css` (global/reset styles).
