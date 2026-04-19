# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

An **index-only** Claude Code plugin marketplace for NexusFlow. No plugin code lives here — only pointers to plugins hosted in other repositories. The sole source of truth is `.claude-plugin/marketplace.json`.

Users install the marketplace with `/plugin marketplace add nxsflow/plugin-marketplace`, then install individual plugins with `/plugin install <name>@nxsflow`.

## Adding or updating a plugin

Edit `.claude-plugin/marketplace.json` and add an entry to the `plugins` array. The `source` field determines where Claude Code fetches the plugin manifest from:

- **`source: "github"`** — the plugin manifest (`.claude-plugin/plugin.json`) must live at the **root** of the source repo. Use `repo` (`owner/name`) and `ref` (branch/tag).
- **`source: "git-subdir"`** — use when the manifest lives in a subdirectory. Use `url` (no `https://` prefix) and `path` (subdir containing `.claude-plugin/plugin.json`).

Picking the wrong source type is the common failure mode: if the referenced repo's manifest is not at its root, `github` will 404 and you need `git-subdir` with `path`.

## Tooling

- **Biome** handles formatting and linting for JS/TS/JSON/CSS (`biome.json`, 4-space indent, React + Next domains enabled). Pinned as a devDependency in `package.json` so the version stays reproducible — run `npm run lint` or `npm run format`. There is no runtime code, no build, no tests.
- Markdown is formatted by Prettier + markdownlint via VS Code (`.vscode/settings.json`), not Biome.
