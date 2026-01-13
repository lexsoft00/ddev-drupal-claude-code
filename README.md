[![add-on registry](https://img.shields.io/badge/DDEV-Add--on_Registry-blue)](https://addons.ddev.com)
[![tests](https://github.com/lexsoft00/ddev-drupal-claude-code/actions/workflows/tests.yml/badge.svg?branch=main)](https://github.com/lexsoft00/ddev-drupal-claude-code/actions/workflows/tests.yml?query=branch%3Amain)
[![last commit](https://img.shields.io/github/last-commit/lexsoft00/ddev-drupal-claude-code)](https://github.com/lexsoft00/ddev-drupal-claude-code/commits)
[![release](https://img.shields.io/github/v/release/lexsoft00/ddev-drupal-claude-code)](https://github.com/lexsoft00/ddev-drupal-claude-code/releases/latest)

# DDEV Drupal Claude Code

## Overview

This add-on integrates Drupal Claude Code into your [DDEV](https://ddev.com/) project.

## Installation

```bash
ddev add-on get lexsoft00/ddev-drupal-claude-code
ddev restart
```

After installation, make sure to commit the `.ddev` directory to version control.

## Usage

| Command | Description |
| ------- | ----------- |
| `ddev describe` | View service status and used ports for Drupal Claude Code |
| `ddev logs -s drupal-claude-code` | Check Drupal Claude Code logs |

## Advanced Customization

To change the Docker image:

```bash
ddev dotenv set .ddev/.env.drupal-claude-code --drupal-claude-code-docker-image="ddev/ddev-utilities:latest"
ddev add-on get lexsoft00/ddev-drupal-claude-code
ddev restart
```

Make sure to commit the `.ddev/.env.drupal-claude-code` file to version control.

All customization options (use with caution):

| Variable | Flag | Default |
| -------- | ---- | ------- |
| `DRUPAL_CLAUDE_CODE_DOCKER_IMAGE` | `--drupal-claude-code-docker-image` | `ddev/ddev-utilities:latest` |

## Credits

**Contributed and maintained by [@lexsoft00](https://github.com/lexsoft00)**
