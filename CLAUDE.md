# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Next.js 15 TypeScript starter template with modern tooling, Docker support, and pre-configured code quality tools.

**Tech Stack:**
- Next.js 15.5.4 (Pages Router) with Turbopack
- React 19.2.0
- TypeScript 5.7.3
- pnpm package manager
- Biome (replaces ESLint + Prettier)

**Requirements:**
- Node.js >= 22.0.0
- pnpm >= 9.0.0 (via Corepack or global install)
- Package manager locked to pnpm@10.0.0 via `packageManager` field

## Development Commands

```bash
# Install dependencies
pnpm install

# Development server with Turbopack (http://localhost:3000)
pnpm dev                   # Uses --turbopack flag automatically

# Production
pnpm build                 # Build for production
pnpm start                 # Start production server

# Code Quality
pnpm lint                  # Run Biome linter
pnpm format                # Format code with Biome
pnpm check                 # Run Biome check and auto-fix (recommended)
pnpm type-check            # TypeScript type checking
pnpm type-check:watch      # TypeScript type checking in watch mode

# Testing
pnpm test                  # Placeholder (no test framework configured)

# Docker
docker build -t next-typescript-starter .
docker run --rm -it -p 3000:3000 next-typescript-starter
docker-compose up
```

## Project Architecture

**Next.js Pages Router Structure:**
- `pages/` - File-based routing (Pages Router, not App Router)
  - `pages/_app.tsx` - Custom App component, imports global styles
  - `pages/_document.tsx` - Custom Document for HTML structure
  - `pages/index.tsx` - Home page
  - `pages/api/` - API routes (serverless functions)
- `components/` - Reusable React components
- `styles/` - CSS files (globals.css, CSS Modules)
- `public/` - Static assets

**Path Aliases:**
- `@/*` resolves to project root (configured in tsconfig.json)
- Example: `import '@/styles/globals.css'`

## Code Quality Tools

### Biome (Linter + Formatter)

**Configuration**: `biome.json`

Biome replaces both ESLint and Prettier for better performance and consistency.

**Linting Rules:**
- `noConsole: error` - Console statements not allowed in production code
- `noUnusedVariables: error` - Unused variables not allowed
- `noUnusedImports: error` - Unused imports not allowed
- `useImportType: error` - Enforce type-only imports when applicable
- Auto-organizes imports

**Formatting Style:**
- Single quotes for JS/TS
- Double quotes for JSX
- 2-space indentation
- 80 character line width
- Trailing commas everywhere
- Semicolons always
- Arrow function parentheses always

**Usage:**
- Run `pnpm check` before committing (auto-fixes most issues)
- Pre-commit hooks will enforce these rules automatically

### TypeScript

**Configuration**: `tsconfig.json`

- Strict mode enabled (all strict type-checking options)
- `noUnusedLocals: true` - Error on unused local variables
- `noUnusedParameters: true` - Error on unused function parameters
- `noImplicitReturns: true` - Error when not all code paths return a value
- `noImplicitAny: true` - Error on implicit any types
- Path alias: `@/*` → project root

### Git Hooks

**Husky 9.1.7 + lint-staged 16.2.3**

- **Pre-commit**: Runs Biome check on staged files (`.husky/pre-commit`)
- **Configuration**: `.lintstagedrc.json`
- Uses `pnpm lint-staged` command
- Automatically formats and fixes issues before commit
- Note: `prepare-commit-msg` hook removed (commitizen not installed)
- **Requires Node.js >= 20.17** (lint-staged v16 requirement)

## Important Notes

- **Routing**: Uses Next.js Pages Router (not App Router)
- **Testing**: No test framework configured (test script is a placeholder)
- **React**: Strict mode enabled in next.config.js
- **Dev Server**: Uses Turbopack for faster builds (`--turbopack` flag in dev script)
- **Package Manager**: Must use pnpm (not npm or yarn)
- **Node Version**: Requires Node.js >= 22.0.0
- **Deprecated Options**: `swcMinify` removed from next.config.js (enabled by default in Next.js 15)
- **Docker**: Pre-built images available at `danangekal/next-typescript-starter`
- **Biome vs ESLint/Prettier**: This project uses Biome exclusively - do not add ESLint or Prettier

## Migration Notes

This project was recently upgraded from:
- React 18 → React 19
- Next.js 13 → Next.js 15
- Node 16 → Node 22
- Yarn → pnpm
- ESLint + Prettier → Biome
- Husky 8 → Husky 9
