[![add-on registry](https://img.shields.io/badge/DDEV-Add--on_Registry-blue)](https://addons.ddev.com)
[![tests](https://github.com/lexsoft00/ddev-drupal-claude-code/actions/workflows/tests.yml/badge.svg?branch=main)](https://github.com/lexsoft00/ddev-drupal-claude-code/actions/workflows/tests.yml?query=branch%3Amain)
[![release](https://img.shields.io/github/v/release/lexsoft00/ddev-drupal-claude-code)](https://github.com/lexsoft00/ddev-drupal-claude-code/releases/latest)

# DDEV Drupal Claude Code

A [DDEV](https://ddev.com/) add-on that integrates [Claude Code](https://docs.anthropic.com/en/docs/claude-code) with [Serena MCP](https://github.com/oraios/serena) for Drupal 11 development.

## Features

- **Claude Code** running inside your DDEV web container
- **Serena MCP** for semantic code analysis and intelligent editing
- **Drupal 11 optimized** with pre-configured CLAUDE.md and Serena memories
- **Security rules** preventing dangerous operations on core/vendor files
- **Official plugins** including Context7, security-guidance, and code-simplifier

## Requirements

- DDEV v1.24.3+

## Installation

```bash
ddev add-on get lexsoft00/ddev-drupal-claude-code
ddev restart
```

## Usage

```bash
# Enter the DDEV container
ddev ssh

# Start Claude Code (first run - configure initial settings)
claude

# Exit Claude Code (Ctrl+C or /exit), then add Serena MCP and index your project
claude mcp add serena -- uvx --from git+https://github.com/oraios/serena serena start-mcp-server --context ide-assistant --project "$(pwd)"
uvx --from git+https://github.com/oraios/serena serena project index

# Start Claude Code again
claude
```

Inside Claude Code, you have access to:
- **Serena tools** for code search, symbol navigation, and refactoring
- **Drupal memories** with coding standards, Drush commands, and best practices
- **Context7** for up-to-date library documentation

## What Gets Installed

### DDEV Configuration

- **`config.drupal-claude-code.yaml`** - Post-start hooks that configure Claude Code
- **`.ddev/.claude/`** - Symlinked to `~/.claude` for persisting Claude Code runtime data

### Claude Code Settings (`.ddev/drupal-claude-code/`)

- **`settings.json`** - Plugins (Context7, security-guidance, code-simplifier) and statusline
- **`settings.local.json`** - Permission rules protecting core/vendor from edits
- **`statusline.sh`** - Status bar showing git branch and Drupal info

### Serena Configuration (`.ddev/drupal-claude-code/serena/`)

- **`project.yml`** - Project settings for PHP/TypeScript analysis
- **`memories/`** - Drupal knowledge bases:
  - `project-overview.md` - Project structure and patterns
  - `code-style-conventions.md` - Drupal coding standards
  - `commands-reference.md` - Drush and CLI commands
  - `architecture-patterns.md` - Drupal best practices
  - `security-guidelines.md` - Security checklist
  - `task-completion-checklist.md` - Quality gates

### Project Root Files

- **`CLAUDE.md`** - Project-specific instructions for Claude Code
- **`.claudeignore`** - Excludes vendor, node_modules, and generated files from context
