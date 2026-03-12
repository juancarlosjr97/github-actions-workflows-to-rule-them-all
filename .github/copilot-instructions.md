# Copilot Instructions

## Repository Overview

This is a centralized GitHub Actions reusable workflows repository. It provides shared workflows used across projects to simplify CI/CD. There is no application code — all content is GitHub Actions YAML workflow files, configuration files, and documentation.

## Repository Layout

```
.github/
  workflows/
    release.yml                    # Triggers shared release automation on push to main
    shared-agents-skills-sh.yml    # Reusable: weekly/manual agent skills update via skills.sh
    shared-docker-security.yml     # Reusable: Docker image vulnerability scan using Trivy
    shared-python-tests.yml        # Reusable: Python tests with CodeCov and Codacy
    shared-release-automation.yml  # Reusable: Release automation using release-it-containerized
    shared-rust-tests.yml          # Reusable: Rust tests with CodeCov
  CODEOWNERS                       # Repository code owners
  copilot-instructions.md          # This file
.gitignore
.release-it.json                   # Release-it configuration (Conventional Commits preset)
AGENTS.md                          # Agent-specific instructions
CHANGELOG.md                       # Auto-generated changelog
LICENSE
README.md
renovate.json                      # Renovate dependency update configuration
VERSION                            # Plain-text version file (e.g. 0.7.0)
```

## Key Constraints

### `actions/checkout` Version Pinning — **CRITICAL**

- **Always** pin `actions/checkout` to **v5 by full commit SHA**. Example:
  ```yaml
  uses: actions/checkout@93cb6efe18208431cddfb8368fd83d5badbf9bfd # v5
  ```
- `actions/checkout@v6` is **incompatible** with Docker container actions (see [actions/checkout#2359](https://github.com/actions/checkout/issues/2359)).
- Renovate is configured to block v6 updates for `actions/checkout` (`allowedVersions: ">=5.0.0 <6.0.0"`).
- **Never** use `actions/checkout@v6` or later in any workflow.

### Action Version Pinning

- All third-party actions must be pinned to a **full commit SHA** with a version comment:
  ```yaml
  uses: actions/setup-node@53b83947a5a98c8d113130e565377fae1a50d02f # v6
  ```

## Commit Message Conventions

This repository uses **Conventional Commits**. All commit messages must follow this format:

```
<type>(<optional scope>): <description>
```

Recognized types (maps to CHANGELOG sections):

| Type       | CHANGELOG Section           |
| ---------- | --------------------------- |
| `feat`     | Features                    |
| `fix`      | Bug Fixes                   |
| `test`     | Tests                       |
| `chore`    | Chores                      |
| `docs`     | Documentation               |
| `perf`     | Performance Improvements    |
| `refactor` | Code Refactoring            |
| `style`    | Code Style Changes          |
| `build`    | Build Changes               |
| `ci`       | Continuous Integration      |
| `revert`   | Reverts                     |

Examples:
- `feat: add shared workflow for Node.js tests`
- `fix: correct trivy action version pin`
- `chore: update agent skills`
- `docs: update README with Rust workflow inputs`

## Validation

There is no local build or test command — all validation runs via GitHub Actions. After pushing changes:

1. The `release.yml` workflow triggers on push to `main` and runs the shared release automation.
2. Reusable workflows (prefixed `shared-`) are tested by consumer repositories that call them.

When adding or modifying workflows, validate YAML syntax manually:

```bash
# Basic YAML syntax check (if yamllint is available)
yamllint .github/workflows/
```

## Configuration Files

- **`.release-it.json`** — Controls release automation: Conventional Commits changelog generation, VERSION file bump, GitHub release creation. Do not modify unless changing release behavior.
- **`renovate.json`** — Renovate dependency update rules. Extends `juancarlosjr97/renovate-configuration#0.1.5`. Includes custom rule to block `actions/checkout@v6` and auto-bump `skills` CLI major version.
- **`CODEOWNERS`** — All files owned by `@juancarlosjr97`.

## Workflow Authoring Guidelines

- All reusable workflows use `on: workflow_call` and are prefixed `shared-`.
- Secrets and inputs are declared with `description` and `required` fields.
- Job-level `permissions` should be minimal and explicit.
- Use `timeout-minutes` on all jobs.
- Avoid hardcoding repository-specific values; use `${{ github.repository }}` and similar expressions.
