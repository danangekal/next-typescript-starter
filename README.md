This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Demo

You can check [demo](https://next-typescript-starter-demo.vercel.app/)

## Features

- ⚛️ [React.js 19](https://react.dev/blog/2024/04/25/react-19) - Latest React with improved performance and new features
- ⚡ [Next.js 15](https://nextjs.org/blog/next-15) - App framework with Turbopack support
- 📘 [TypeScript 5](https://www.typescriptlang.org/) - Strongly typed JavaScript
- 📦 [pnpm](https://pnpm.io/) - Fast, disk space efficient package manager
- 🎨 [Biome](https://biomejs.dev/) - Fast formatter and linter (replaces ESLint + Prettier)
- 🐶 [Husky 9](https://typicode.github.io/husky/#/) - Git hooks made easy
- ✨ [Lint Staged 15](https://github.com/okonet/lint-staged) - Run linters on git staged files
- 🐳 [Docker](https://docs.docker.com/) - Containerization support

## Prerequisites

- Node.js >= 22.0.0
- pnpm >= 9.0.0 (install via `npm install -g pnpm` or use Corepack)

## Getting Started

### Installation

```bash
# Clone repository
git clone https://github.com/danangekal/next-typescript-starter.git
cd next-typescript-starter

# Install dependencies
pnpm install
```

### Development

```bash
# Start development server with Turbopack (default: http://localhost:3000)
pnpm dev
```

### Code Quality

```bash
# Run Biome linter
pnpm lint

# Format code with Biome
pnpm format

# Run Biome check and auto-fix
pnpm check

# Type check with TypeScript
pnpm type-check
pnpm type-check:watch  # Watch mode
```

### Production

```bash
# Build for production
pnpm build

# Start production server
pnpm start
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `pages/index.tsx`. The page auto-updates as you edit the file.

## Project Structure

```
.
├── pages/              # Next.js pages (Pages Router)
│   ├── _app.tsx       # Custom App component
│   ├── _document.tsx  # Custom Document
│   ├── index.tsx      # Home page
│   └── api/           # API routes
├── components/        # React components
├── styles/            # CSS files
├── public/            # Static assets
├── biome.json         # Biome configuration
├── tsconfig.json      # TypeScript configuration
└── next.config.js     # Next.js configuration
```

**API Routes:**
- API endpoints are available at [http://localhost:3000/api/hello](http://localhost:3000/api/hello)
- Edit `pages/api/hello.ts` to modify the API route
- The `pages/api` directory is mapped to `/api/*`

**Fonts:**
- Uses [`next/font`](https://nextjs.org/docs/basic-features/font-optimization) to optimize and load Inter (Google Font)

## Docker

### Build Image

```bash
docker build -t next-typescript-starter .
```

### Run Container

```bash
docker run --rm -it -p 3000:3000 next-typescript-starter
```

### Docker Compose

```bash
docker-compose up
```

### Pre-built Images

Pre-built images are available on Docker Hub:

```bash
docker pull danangekal/next-typescript-starter
```

## Git Hooks

This project uses Husky 9 and lint-staged 16 to run code quality checks before commits:

- **Pre-commit**: Automatically formats and lints staged files with Biome
- **Configuration**: `.husky/pre-commit` and `.lintstagedrc.json`
- **Workflow**: On `git commit`, Biome automatically checks and fixes all staged files

## Code Style

This project uses Biome for both linting and formatting:

- **Linter**: Enforces code quality rules (no-console, no-unused-variables, etc.)
- **Formatter**:
  - Single quotes for JavaScript
  - 2-space indentation
  - 80 character line width
  - Semicolons always
  - Trailing commas
- **Configuration**: `biome.json`

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.

---

Copyright © 2021 by Danang Eko Alfianto
