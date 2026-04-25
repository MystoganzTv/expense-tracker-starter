# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm install      # install dependencies
npm run dev      # start dev server at http://localhost:5173
npm run build    # production build
npm run preview  # preview production build
npm run lint     # run ESLint
```

No test runner is configured.

## Architecture

This is a single-component React app (React 19, Vite). All state and logic live in `src/App.jsx` — there are no child components, routing, or external state management.

**State in App.jsx:**
- `transactions` — array of `{ id, description, amount, type, category, date }`. `amount` is stored as a string; arithmetic on it currently uses string concatenation instead of numeric addition (known bug).
- `description`, `amount`, `type`, `category` — controlled form inputs for adding a new transaction.
- `filterType`, `filterCategory` — filter state applied inline before rendering the table.

**Known intentional issues (per README — this is a course starter):**
- Bug: `amount` is a string, so `totalIncome`/`totalExpenses` accumulate via string concatenation instead of summing numbers.
- UI needs improvement.
- Code needs refactoring (monolithic component, no separation of concerns).

`src/App.css` contains all styles. The `.delete-btn` class is defined in CSS but the delete button is not yet wired up in the JSX.
