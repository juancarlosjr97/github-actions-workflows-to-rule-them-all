# GitHub Actions Workflows to Rule Them All

This project is a centralized repository for GitHub Actions workflows used across projects to simplify development wherever possible.

## GitHub Actions Shared Workflows

### Python

#### Tests

The [Workflow](./.github/workflows/shared-python-tests.yml) has the following inputs:

| Environmental Variable | Type   | Description                                    | Required |
| ---------------------- | ------ | ---------------------------------------------- | -------- |
| CODACY_PROJECT_TOKEN   | SECRET | The key to record the execution to Codacy      | true     |
| CODECOV_TOKEN          | SECRET | The key to record the code coverage to CodeCov | true     |

### Release Automation

The [Workflow](./.github/workflows/shared-release-automation.yml) has the following inputs:

| Environmental Variable | Type   | Description                                        | Required |
| ---------------------- | ------ | -------------------------------------------------- | -------- |
| PLUGIN_LIST            | INPUT  | List of plugins to use with the release automation | true     |
| PROJECT_GITHUB_TOKEN   | SECRET | Access token for GitHub                            | true     |

The release automation uses the [release-it-containerized](https://github.com/juancarlosjr97/release-it-containerized).

### Rust

#### Tests

The [Workflow](./.github/workflows/shared-rust-tests.yml) has the following inputs:

| Environmental Variable | Type   | Description                                    | Required |
| ---------------------- | ------ | ---------------------------------------------- | -------- |
| CODECOV_TOKEN          | SECRET | The key to record the code coverage to CodeCov | true     |
