# Agent Instructions

## Repository Purpose

This repository provides centralized, reusable GitHub Actions workflows used across multiple projects. All content is GitHub Actions YAML workflow files, configuration, and documentation — there is no application source code to compile or test locally.

## Commit Messages

This repository strictly follows **Conventional Commits**. Every commit message must use one of the following types:

- `feat:` — New feature or new reusable workflow
- `fix:` — Bug fix in a workflow
- `chore:` — Maintenance tasks (dependency updates, skills updates)
- `docs:` — Documentation-only changes
- `ci:` — Changes to CI/CD configuration
- `refactor:` — Refactoring without behavior change
- `style:` — Formatting/style changes only
- `build:` — Build system changes
- `perf:` — Performance improvements
- `test:` — Test-related changes
- `revert:` — Reverting a previous commit

Format: `<type>(<optional scope>): <short description>`

Examples:
```
feat: add shared workflow for Node.js tests
fix: correct trivy action SHA pin
chore: update agent skills
docs: add example for Docker security workflow
ci: pin actions/setup-node to v6 SHA
```

## Critical Rules

### `actions/checkout` Pinning

**Always** use `actions/checkout` pinned to **v5 by full commit SHA**:

```yaml
uses: actions/checkout@93cb6efe18208431cddfb8368fd83d5badbf9bfd # v5
```

`actions/checkout@v6` is **broken** for Docker container actions. Never use v6 or later. This is enforced by Renovate (`allowedVersions: ">=5.0.0 <6.0.0"`).

### Action Version Pinning

All actions must be pinned to a **full commit SHA** with an inline version comment:

```yaml
uses: actions/setup-node@53b83947a5a98c8d113130e565377fae1a50d02f # v6
```

Never use floating tags like `@v1`, `@latest`, or branch references.

## File Structure

```
.github/workflows/        Reusable and trigger workflows (YAML)
.github/copilot-instructions.md  Repository-wide Copilot guidance
AGENTS.md                 This file
.release-it.json          Release automation config (Conventional Commits)
renovate.json             Dependency update config
VERSION                   Plain-text semantic version
CHANGELOG.md              Auto-generated changelog
README.md                 Workflow documentation and usage examples
```

## Workflow Conventions

- Reusable workflows use `on: workflow_call` and are named `shared-*.yml`.
- All inputs and secrets must have a `description` field and explicit `required` value.
- Every job must specify `timeout-minutes`.
- Job-level `permissions` must be minimal and explicitly declared.
- Use `${{ github.repository }}` and context expressions — avoid hardcoded repository values.
- Step `id` values should be lowercase with hyphens (e.g., `id: skills-check`).

## Validation

There is no local build/test command. Validate changes by:

1. Checking YAML syntax (e.g., `yamllint .github/workflows/` if available).
2. Reviewing that all action references are pinned to SHA.
3. Confirming commit messages follow Conventional Commits format.
4. Pushing to the PR branch and reviewing GitHub Actions run results.

## Release Process

Releases are fully automated via the `release.yml` workflow on push to `main`. The workflow uses `release-it` with:
- Conventional Commits changelog generation → `CHANGELOG.md`
- Version bump → `VERSION` file
- GitHub Release creation with release notes

Do not manually edit `CHANGELOG.md` or `VERSION`.
