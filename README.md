# GitHub Actions Workflow to Rule Them All

This project is a centralized repository for GitHub Actions workflows used across projects to simplify development wherever possible.

## GitHub Actions Shared Workflows

### Python

#### Tests

The [Workflow](./.github/workflows/shared-python-tests.yml) has the following inputs:

| Environmental Variable | Type   | Description                                    | Required |
| ---------------------- | ------ | ---------------------------------------------- | -------- |
| CODECOV_TOKEN          | SECRET | The key to record the code coverage to CodeCov | true     |

