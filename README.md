# NexusFlow Claude Code Plugins

A Claude Code plugin marketplace aggregating NexusFlow's plugins.

## Install

Add the marketplace once:

```
/plugin marketplace add nxsflow/plugin-marketplace
```

Then install any plugin:

```
/plugin install claude-memory@nxsflow
/plugin install nxsflow-brand@nxsflow
```

Update later:

```
/plugin marketplace update
```

## Plugins

| Plugin          | Description                                                                                     | Source                                                               |
| --------------- | ----------------------------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `claude-memory` | Continuous learning for Claude Code — short-term and long-term memory built up across sessions. | [nxsflow/claude-memory](https://github.com/nxsflow/claude-memory)    |
| `nxsflow-brand` | NexusFlow brand guideline skill — colors, typography, tone, logo rules.                         | [nxsflow/brand](https://github.com/nxsflow/brand) (subdir `plugin/`) |

## Structure

This repo is an index only — `.claude-plugin/marketplace.json` references each plugin's source repo. No plugin code lives here.

Plugin manifests (`.claude-plugin/plugin.json`) must be at the source repo's root for a `github` source, or referenced via `git-subdir` with a `path` when they live in a subdirectory.
