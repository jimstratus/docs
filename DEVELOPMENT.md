# Development Guide

How to set up, run, and develop the Mintlify documentation site locally.

## Prerequisites

- Node.js >= 19
- A docs repository with a `docs.json` file (this repo)

## First-Time Setup

```bash
git clone https://github.com/jimstratus/docs.git
cd docs
```

Install the Mintlify CLI globally:

```bash
npm i -g mint
```

Install the Mintlify skill for AI coding tools:

```bash
npx skills add https://mintlify.com/docs
```

## Running Locally

```bash
mint dev
```

Preview at `http://localhost:3000`. Changes to MDX files are hot-reloaded.

### Custom Port

```bash
mint dev --port 3333
```

## Commands

| Command | Description |
|---|---|
| `mint dev` | Start local preview server |
| `mint dev --port <N>` | Preview on a custom port |
| `mint broken-links` | Check for broken internal links |
| `mint update` | Update CLI to latest version |

## Project Structure

```
docs/
├── docs.json              # Mintlify configuration (navigation, tabs, colors)
├── index.mdx              # Homepage
├── quickstart.mdx         # Quick start guide
├── development.mdx        # Development guide (published page)
├── essentials/            # Core documentation pages
│   ├── settings.mdx
│   ├── images.mdx
│   ├── code.mdx
│   └── ...
├── api-reference/         # API documentation
│   ├── introduction.mdx
│   ├── openapi.json
│   └── endpoint/          # Individual endpoint docs
├── ai-tools/              # AI tool setup guides
│   ├── claude-code.mdx
│   ├── cursor.mdx
│   └── windsurf.mdx
├── snippets/              # Reusable MDX snippets
├── logo/                  # Brand assets
├── images/                # Documentation images
├── README.md              # Repo readme
├── CONTRIBUTING.md        # Contribution guidelines
├── AGENTS.md              # AI agent instructions
└── LICENSE
```

## Writing Documentation

### Page Format

Pages are MDX files with YAML frontmatter:

```mdx
---
title: 'Page Title'
description: 'Meta description'
---

Content goes here using Markdown and Mintlify components.
```

### Style Guidelines

- Use active voice and second person ("you")
- Keep sentences concise — one idea per sentence
- Use sentence case for headings
- Bold for UI elements: Click **Settings**
- Code formatting for file names, commands, paths, and code references
- See `AGENTS.md` for full style preferences

### Mintlify Components

Mintlify provides custom MDX components. See the [Mintlify docs](https://mintlify.com/docs) for full reference. Common components:

- `<Steps>` / `<Step>` — Step-by-step instructions
- `<Info>` / `<Warning>` / `<Tip>` — Callout boxes
- `<Accordion>` / `<AccordionGroup>` — Expandable sections
- `<Tabs>` / `<Tab>` — Tabbed content
- `<Frame>` — Bordered content container

## Publishing

Install the Mintlify GitHub app from the [dashboard](https://dashboard.mintlify.com/settings/organization/github-app). Changes pushed to the default branch are deployed automatically.

## Link Validation

```bash
mint broken-links
```

Run this before pushing changes to catch broken internal links.

## Code Formatting

Recommended VSCode extensions:
- [MDX VSCode extension](https://marketplace.visualstudio.com/items?itemName=unifiedjs.vscode-mdx) — syntax highlighting
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) — code formatting

## Troubleshooting

- **Dev server won't start**: Run `mint update` to get the latest CLI version
- **404 on pages**: Ensure you're running `mint dev` from the directory containing `docs.json`
- **Unknown error**: Delete `~/.mintlify` folder and run `mint dev` again
- **Sharp module error**: Upgrade Node.js to v19+, remove CLI (`npm remove -g mint`), reinstall
