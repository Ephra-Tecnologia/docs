# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A documentation site built on [Mintlify](https://mintlify.com). There is no application code, build step, or test suite — content is authored as MDX pages and rendered/deployed by Mintlify's hosted platform.

## Commands

```bash
npm i -g mint      # install the Mintlify CLI (one-time)
mint dev           # local preview at http://localhost:3000 (run from repo root, where docs.json lives)
mint update        # update the CLI if dev won't start or behaves unexpectedly
```

There is no lint or test command. To validate, run `mint dev` and confirm pages render and navigation resolves.

## Architecture

- **`docs.json`** is the single source of truth for site structure, theme, and navigation. It uses the schema at `https://mintlify.com/docs.json`. A page file does **not** appear on the site until it is registered under `navigation.pages` here — creating an `.mdx` file alone is not enough.
- **Pages** are `.mdx` files at the repo root, each starting with YAML frontmatter (`title`, `description`). Page references in `docs.json` use the path without the `.mdx` extension (e.g. `"quickstart"` → `quickstart.mdx`).
- **Content uses Mintlify components** — `<Card>`, `<Tip>`, `<Steps>`/`<Step>`, `<Note>`, etc. — not plain Markdown alone. Match the components and structure already used in `index.mdx` and `quickstart.mdx`.
- **Assets** live in `logo/` (`light.svg`, `dark.svg`) and `favicon.svg`, referenced by path from `docs.json`.
- **`.mintignore`** excludes drafts (`drafts/`, `*.draft.mdx`) and Mintlify auto-ignores `.git`, `README.md`, `LICENSE`, etc.

## Deployment

Production deploys automatically when changes are pushed to the default branch (`main`), via the Mintlify GitHub app. There is no manual deploy step.

## Writing style

From `AGENTS.md`:

- Active voice, second person ("you").
- One idea per sentence; keep them concise.
- Sentence case for headings.
- Bold for UI elements (Click **Settings**); code formatting for file names, commands, paths, and code references.

## Mintlify knowledge

For component reference and configuration details beyond this repo, the Mintlify skill / MCP servers are the source of truth:

- Install the skill: `npx skills add https://mintlify.com/docs`
- Docs MCP (how to use Mintlify): `https://www.mintlify.com/docs/mcp`
- Editing MCP (content/settings): `https://mcp.mintlify.com`
