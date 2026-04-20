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
- **`ai-native-workflow` meta skill** — the operating manual that ties every other skill together: the conversation contract, the 7-phase task lifecycle, and the five principles that keep AI-generated output consistent (see [How You Work With the AI Agent](#how-you-work-with-the-ai-agent))
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
|---|---|
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

## How You Work With the AI Agent

Cloning the scaffold gives you the structure. The `ai-native-workflow` meta skill gives you the **operating manual** for actually working with the AI agent on it. The skill routes itself from how you describe the task — you usually don't think about which skill loads.

### The mental model: three layers

| Layer | What it is | When it loads |
|---|---|---|
| **L1: Orchestrator** | `CLAUDE.md` — the constitution, workflow, and skills index | Always loaded |
| **L2: Specialized skills** | `.claude/skills/{name}/SKILL.md` — deep rules and phased instructions | Triggered by the wording of your prompt |
| **L3: Code conventions** | The actual TypeScript — fixtures, page objects, enums, factories | Read on demand from the repo |

The skill suite is the brain, `CLAUDE.md` is the table of contents, the code is the truth.

> `.claude/skills/` is the canonical source. `.cursor/skills/` and `.github/instructions/` are mirrors that may lag — defer to `.claude/` if they disagree.

### The conversation contract

Every non-trivial task follows the same five-step loop, called **audit-then-edit**:

1. You state the goal in plain language.
2. The agent loads the relevant skill and proposes scope — what changes, in which files, why, with trade-offs.
3. You approve, modify, or reject.
4. The agent applies the change.
5. The agent reports what landed and asks whether to commit.

For one-line fixes and obvious typos there's a faster path called **direct mode** — the agent just does it. Opt in for a whole session by saying "just do it" once.

The contract has hard stops baked in. The agent **must stop and ask** when a path, enum value, message, or endpoint is unknown — never invent one. The agent **must refuse** to ship:

- Guessed selectors
- Hardcoded credentials
- Suppressed test failures (`.skip` without `// FIXME:`, raised timeouts, weakened assertions)
- `any` types
- `XPath`
- `z.object()` (use `z.strictObject()`)
- `page.waitForTimeout(...)`

These are refusals, not warnings.

### How the right skill loads itself

The way you phrase the task picks the skill for you:

| You say... | First skill that loads | Then chains to |
|---|---|---|
| "Add tests for `POST /api/...`" | `api-testing` | `data-strategy`, `enums`, `type-safety`, `debugging` |
| "Add a page object for the settings page" | `page-objects` | `selectors`, `playwright-cli`, `enums`, `fixtures` |
| "How do I add Y? / Generate the prompt for X" | `common-tasks` | the matching specialized skill |
| "Test is failing / behaving unexpectedly" | `debugging` | `api-testing`, `selectors`, `fixtures`, `refactor-values` |
| "Rename this enum value / change a static-data row" | `refactor-values` | `enums` or `data-strategy`, then `debugging` |
| "Create a new factory" | `data-strategy` | `type-safety`, `api-testing` |
| "Add a helper / fixture" | `helpers` or `fixtures` | `api-testing` Phase 8 (promotion criteria) |
| "Add an env var / config / utility URL" | `config` | `enums`, `type-safety` |
| "Add an enum / endpoint / message" | `enums` | `playwright-cli` for live-text verification |
| "Refactor a Zod schema / `any` to typed" | `type-safety` | `api-testing` |
| "Add a new spec file / tagging question" | `test-standards` | `data-strategy`, `api-testing`, `page-objects` |

If nothing matches, the agent defaults to `common-tasks` or asks you. The lesson: **describe the work, don't name the skill**. Naming a skill is a fallback for when the agent loaded the wrong one.

### The 7-phase rhythm of every non-trivial task

Once a skill loads, the work moves through the same seven phases — whether you're adding a test, refactoring an enum, or hunting a flaky failure:

1. **Identify the work category** — new artifact, edit, refactor, debug, or investigation.
2. **Explore before generating** — `playwright-cli` for UI (no IDE browser MCP, no Cursor browser, no `playwright codegen`); OpenAPI / Swagger first for API; `ls pages/`, `ls enums/`, etc. for repo conventions. If exploration is impossible, the agent stops and notifies you — never substitute another tool.
3. **Propose scope** (audit-then-edit) — what / where / why / approve-and-I'll-apply.
4. **Apply the critical rules** from each loaded skill — they are hard stops, not preferences.
5. **Verify with the matching skill's checklist** — `api-testing` Phase 5 coverage matrix, `page-objects` Phase 5 fixture registration, `refactor-values` Phase 4 `tsc + eslint + targeted tests` gate.
6. **Run the affected tests** — `npx playwright test <file>`, never the full suite. On red, load `debugging`. Never suppress, raise timeouts, or `.skip` without `// FIXME:`.
7. **Commit with a "why" message** — title imperative and specific, body lists substantive changes; one logical change per commit.

### Five principles that make the scaffold AI-native

These exist so the agent never has to guess:

1. **Single source of truth per value class** — URLs and credentials in `process.env.*`; endpoint paths and UI messages in `enums/{area}/*`; universal invalid arrays in `test-data/static/util/invalid-values.ts`; dynamic happy-path data via Faker factories in `test-data/factories/{area}/`. Exactly one right answer per kind of value.
2. **Hard-stop forbidden patterns** — every Critical block has `NEVER` rules with concrete anti-examples. They trigger refusal, not warnings.
3. **Mandatory exploration discipline** — `playwright-cli` for UI, OpenAPI or docs first for API. No guessing selectors. No inventing endpoints.
4. **Strict folder discipline** — every artifact has exactly one home. Skill triggering by keyword works because folders map cleanly to skill names.
5. **Phased instructions inside skills** — you don't invent a workflow per task; you follow the skill's phases.

### A worked example

You say: _"Add API tests for `POST /api/products`."_

1. `CLAUDE.md` is already loaded → routes to `common-tasks` → which routes to `api-testing` (deep rules).
2. The agent confirms an OpenAPI spec exists for `/api/products`; runs `ls fixtures/api/schemas/`, `ls tests/`, `ls enums/`.
3. The agent proposes scope: schema name + location, factory name + location, spec structure, full status-code coverage matrix, validation tiers.
4. On approval: applies `z.strictObject()` (`type-safety`), `expect(Schema.parse(body)).toBeTruthy()` (`api-testing`), `ApiEndpoints.PRODUCTS` (`enums`), Faker factory (`data-strategy`), single `@api` tag (`test-standards`).
5. Verifies against the `api-testing` Phase 5 coverage matrix.
6. Runs `npx playwright test tests/{area}/api/products.spec.ts`.
7. Commits: `Add POST /api/products tests with full coverage matrix`.

Seven phases, three skills, one approval point.

### Common gotchas

- **Agent generated something off-convention** → it didn't load the right skill. Name the skill in your prompt: "use the `api-testing` skill".
- **Agent invented a folder, enum, or env var** → reject it; require `ls` / OpenAPI / `playwright-cli` re-verification.
- **Agent suppressed a failing test** with `.skip`, raised timeouts, or weakened assertions → reject; require the `debugging` skill's Phase 4-5 root-cause fix.
- **Agent loaded several skills' Critical blocks and seems overwhelmed** → load only the entry-point skill; if you truly need three at once, the task is too big — split it.
- **Cursor and Claude gave you different answers** → defer to `.claude/`.

### What to do on day one

1. Read `CLAUDE.md` — the always-loaded constitution and skills index.
2. Skim the deep skill for whatever you'll touch first — most commonly `api-testing` or `page-objects`.
3. State your goal in plain language and let the agent load the matching skill and propose scope. Approve, push back, or redirect — that loop is the whole workflow.

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
