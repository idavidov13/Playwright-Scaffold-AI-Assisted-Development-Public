# Playwright Scaffold — AI-Assisted Test Automation

A production-ready Playwright test automation scaffold built with TypeScript. Designed from the ground up for **AI-assisted test development** — just describe what you need, and your AI coding assistant generates tests, page objects, and schemas that follow the framework's conventions automatically.

> **This is a scaffold, not a library.** Clone it, point it at your app, and start building your test suite immediately. Example files demonstrate every pattern so you (and your AI assistant) always have a reference.

---

## Why This Scaffold?

Most Playwright projects start from scratch and accumulate inconsistencies over time — mixed selector strategies, no data isolation, scattered helpers, and patterns that AI tools can't follow reliably.

This scaffold solves that. It gives you a **fully architected starting point** with strict conventions, type safety, and a modular AI rules system that keeps generated code consistent whether you're using Claude Code, Cursor, or GitHub Copilot.

---

## What's Included

### Framework Architecture

- **Page Object Model** with fixture-based dependency injection — no manual instantiation in tests
- **API testing fixture** (`apiRequest`) with generic type support and Zod schema validation
- **Helper fixtures** for reusable setup/teardown lifecycle management
- **Component composition** pattern for shared UI elements across pages
- **Layered fixture merging** — POM, API, and helper fixtures combined into a single import point

### Type Safety & Validation

- **TypeScript strict mode** throughout
- **Zod schemas** (`strictObject`) for runtime API response validation
- **Typed factories** (Faker + Zod) for dynamic test data generation
- **No `any` allowed** — enforced by ESLint rules

### Test Organization

- **Tag-based execution** — `@smoke`, `@sanity`, `@regression`, `@api`, `@e2e`, `@destructive`
- **Given/When/Then step structure** with `test.step()` for readable reports
- **Data-driven tests** with static JSON for boundary cases and Faker factories for happy paths
- **Destructive test isolation** — tests that modify shared state run sequentially with mandatory cleanup hooks
- **Multi-browser support** — Chromium, Firefox, WebKit configurations ready to go

### AI Rules System

- **Modular orchestrator + skills architecture** — always-loaded orchestrator with on-demand detailed skills
- **14 specialized skill files** covering selectors, page objects, fixtures, test standards, API testing, data strategy, type safety, enums, configuration, helpers, common tasks, refactoring, and browser-based page exploration
- **Three-tool support** — rules for Claude Code (`.claude/`), Cursor (`.cursor/`), and GitHub Copilot (`.github/`)
- **Constitution pattern** — MUST / SHOULD / WON'T rules that AI assistants follow to produce consistent, high-quality code
- **Browser exploration skill** — AI navigates your app to discover real selectors before generating page objects

### Developer Experience

- **Dev Container** — one-click setup with Docker (Node.js, Playwright browsers, Python, browser-use CLI, all pre-installed)
- **Local setup script** — automated installation for non-Docker workflows
- **Multi-environment support** — `.env.dev`, `.env.staging`, `.env.prod` with a single env switch
- **Pre-commit hooks** — Husky + lint-staged with ESLint and Prettier auto-fix
- **Authentication handling** — storage state pattern for pre-authenticated tests
- **Comprehensive reporting** — HTML reports with traces, screenshots, and videos on failure

### Code Quality

- **ESLint** with Playwright plugin and TypeScript rules
- **Prettier** for consistent formatting
- **Husky** pre-commit hooks to catch issues before they're committed
- **Semantic selector priority** enforced — `getByRole` > `getByLabel` > `getByPlaceholder` > `getByText` > `getByTestId`

---

## Repository Structure

```
├── .devcontainer/          # Dev Container configuration (Docker-based one-click setup)
├── .claude/                # Claude Code AI skills
│   └── skills/             # 14 detailed skill files
├── .cursor/                # Cursor AI rules and skills
│   ├── rules/              # Always-loaded orchestrator
│   └── skills/             # Cursor-compatible skill files
├── .github/                # GitHub Copilot instructions
│   └── instructions/       # Glob-scoped auto-injected instructions
├── config/                 # Application configuration
├── enums/                  # Constants and enumerations
├── env/                    # Environment configuration (.env per environment)
├── fixtures/               # Playwright test fixtures
│   ├── api/                # API request fixture, types, and Zod schemas
│   ├── helper/             # Setup/teardown helper fixtures
│   └── pom/                # Page Object fixtures and single import point
├── helpers/                # Helper functions (auth, utilities)
├── pages/                  # Page Object Model classes and reusable components
├── scripts/                # Setup and utility scripts
├── test-data/              # Test data (static JSON + dynamic Faker factories)
├── tests/                  # Test specifications (functional, API, E2E)
├── CLAUDE.md               # AI orchestrator for Claude Code
├── playwright.config.ts    # Playwright configuration
├── eslint.config.mts       # ESLint flat config
├── tsconfig.json           # TypeScript configuration
└── package.json            # Dependencies and npm scripts
```

---

## Tech Stack

| Tool | Purpose |
| --- | --- |
| [Playwright](https://playwright.dev/) | Browser automation & testing |
| [TypeScript](https://www.typescriptlang.org/) | Type-safe test code |
| [Zod](https://zod.dev/) | Runtime schema validation |
| [Faker.js](https://fakerjs.dev/) | Dynamic test data generation |
| [ESLint](https://eslint.org/) + [Prettier](https://prettier.io/) | Code quality & formatting |
| [Husky](https://typicode.github.io/husky/) | Git hooks |
| [Docker](https://www.docker.com/) | Dev Container environment |

---

## Who Is This For?

- **QA Engineers** who want a solid, opinionated starting point instead of building from scratch
- **Teams adopting AI-assisted development** who need guardrails that keep AI-generated code consistent
- **Engineering teams** standardizing their Playwright test architecture across projects
- **Freelancers & consultants** who need a reusable scaffold they can adapt per client

---

## How It Works

1. **Clone** the scaffold into your project
2. **Configure** your environment variables (app URL, API URL, credentials)
3. **Replace** the example page objects and tests with your real application's pages and flows
4. **Use AI** — prompt your AI assistant to generate page objects, tests, and schemas. The rules system guides it to follow the framework's conventions automatically
5. **Run tests** — `npm test` and you're live

---

## Actively Maintained

This scaffold is **continuously updated** to keep pace with the fast-moving AI and testing landscape:

- **AI tool updates** — rules and skills are revised as Claude Code, Cursor, and GitHub Copilot release new capabilities, context models, and instruction formats
- **Playwright releases** — framework patterns, configuration, and Dev Container images are updated for new Playwright versions and features
- **Dependency upgrades** — Zod, Faker, ESLint, TypeScript, and all other dependencies are kept current
- **New skills & patterns** — as new best practices emerge in AI-assisted test development, new skills are added and existing ones are refined

When you purchase access, you receive all future updates to the repository — not just a snapshot in time.

---

## Community & Support

Every buyer gets access to the repository's **GitHub Discussions** section — a dedicated space to:

- **Ask questions** about the framework, patterns, or how to adapt the scaffold to your project
- **Share ideas** and suggest new features or skills
- **Learn from others** — see how other engineers are using the scaffold across different applications and tech stacks
- **Get help** with setup, configuration, or AI workflow challenges

You're not just buying a repo — you're joining a community of QA engineers and developers building better test automation with AI.

---

## Getting Access

This is a **private repository**. To get access:

- **Contact:** [LinkedIn](https://www.linkedin.com/in/ivdavidov/)
- **Framework:** [Get Access](https://buymeacoffee.com/idavidov/e/513835)

Once you have access, the full README covers detailed setup instructions, architecture diagrams, code examples, the complete AI workflow documentation, and more.

---

## License

MIT — see the private repository for full license details.
