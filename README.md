# GitHub Actions Workflows to Rule Them All

This project is a centralized repository for GitHub Actions workflows used across projects to simplify development wherever possible.

## Notes

### actions/checkout Version Pinning

All workflows and examples in this repository pin `actions/checkout` to **v5 by full commit SHA**. This is intentional.

`actions/checkout@v6` is **not compatible with Docker container actions** — manual credential setups do not work in v6. Only v5 is currently functional for container-based workflows such as those using [release-it-containerized](https://github.com/juancarlosjr97/release-it-containerized).

See upstream bug report: [actions/checkout#2359](https://github.com/actions/checkout/issues/2359)

The Renovate configuration in this repository is set to allow only v5.x updates for `actions/checkout` and will never auto-update to v6.

## GitHub Actions Shared Workflows

### Docker

#### Security

The [Workflow](./.github/workflows/shared-docker-security.yml) has the following inputs:

| Environmental Variable  | Type  | Description                                              | Required |
| ----------------------- | ----- | -------------------------------------------------------- | -------- |
| IMAGE_REFERENCE         | INPUT | The tag to use for loading and scanning the image        | true     |
| IMAGE_TAR_ARTIFACT_NAME | INPUT | The name of the artifact containing the Docker image tar | true     |
| IMAGE_TAR_FILE_PATH     | INPUT | The path to the Docker image tar file                    | true     |

The workflow requires to pass the built image with a reference and as a tar file to be downloaded, and added to the security job.

##### Example

```yml
jobs:
  build:
    runs-on: ubuntu-latest
    outputs:
      image_reference: ${{ steps.build.outputs.image_reference }}
      image_tar_artifact_name: ${{ steps.save.outputs.image_tar_artifact_name }}
      image_tar_file_path: ${{ steps.save.outputs.image_tar_file_path }}
    steps:
      - name: Checkout repository
        uses: actions/checkout@93cb6efe18208431cddfb8368fd83d5badbf9bfd # v5
        with:
          fetch-depth: 0

      - name: Build the Image
        id: build
        run: |
          docker build --tag ghcr.io/${{ github.repository }}:${{ github.sha }} .
          echo "image_reference=ghcr.io/${{ github.repository }}:${{ github.sha }}" >> $GITHUB_OUTPUT

      - name: Save Docker image to tarball
        id: save
        run: |
          docker save ghcr.io/${{ github.repository }}:${{ github.sha }} -o ${{ github.sha }}.tar
          echo "image_tar_artifact_name=docker-image-${{ github.sha }}" >> $GITHUB_OUTPUT
          echo "image_tar_file_path=${{ github.sha }}.tar" >> $GITHUB_OUTPUT

      - name: Upload image tarball as artifact
        uses: actions/upload-artifact
        with:
          name: docker-image-${{ github.sha }}
          path: ${{ github.sha }}.tar

  security:
    needs: build
    uses: juancarlosjr97/github-actions-workflows-to-rule-them-all/.github/workflows/shared-docker-security.yml
    with:
      IMAGE_REFERENCE: ${{ needs.build.outputs.image_reference }}
      IMAGE_TAR_ARTIFACT_NAME: ${{ needs.build.outputs.image_tar_artifact_name }}
      IMAGE_TAR_FILE_PATH: ${{ needs.build.outputs.image_tar_file_path }}

```

### Snyk

#### Docker Security Scan

The [Workflow](./.github/workflows/shared-snyk-docker.yml) scans a locally built Docker image for vulnerabilities using Snyk CLI.

| Environmental Variable  | Type   | Description                                                        | Required |
| ----------------------- | ------ | ------------------------------------------------------------------ | -------- |
| IMAGE_REFERENCE         | INPUT  | The Docker image reference to scan (e.g., ghcr.io/org/image:sha)  | true     |
| IMAGE_TAR_ARTIFACT_NAME | INPUT  | The name of the artifact containing the Docker image tar           | true     |
| IMAGE_TAR_FILE_PATH     | INPUT  | The path to the Docker image tar file                              | true     |
| SNYK_SEVERITY_THRESHOLD | INPUT  | Minimum severity level to fail on (low, medium, high, critical)    | false    |
| SNYK_TOKEN              | SECRET | The Snyk authentication token for scanning                         | true     |

The workflow requires the Docker image to be passed as a tar artifact (same pattern as the Trivy Docker security workflow). Authenticate with Snyk by providing a `SNYK_TOKEN` secret. Obtain a token from your [Snyk account settings](https://app.snyk.io/account).

##### Example

```yml
jobs:
  build:
    runs-on: ubuntu-latest
    outputs:
      image_reference: ${{ steps.build.outputs.image_reference }}
      image_tar_artifact_name: ${{ steps.save.outputs.image_tar_artifact_name }}
      image_tar_file_path: ${{ steps.save.outputs.image_tar_file_path }}
    steps:
      - name: Checkout repository
        uses: actions/checkout@93cb6efe18208431cddfb8368fd83d5badbf9bfd # v5
        with:
          fetch-depth: 0

      - name: Build the Image
        id: build
        run: |
          docker build --tag ghcr.io/${{ github.repository }}:${{ github.sha }} .
          echo "image_reference=ghcr.io/${{ github.repository }}:${{ github.sha }}" >> $GITHUB_OUTPUT

      - name: Save Docker image to tarball
        id: save
        run: |
          docker save ghcr.io/${{ github.repository }}:${{ github.sha }} -o ${{ github.sha }}.tar
          echo "image_tar_artifact_name=docker-image-${{ github.sha }}" >> $GITHUB_OUTPUT
          echo "image_tar_file_path=${{ github.sha }}.tar" >> $GITHUB_OUTPUT

      - name: Upload image tarball as artifact
        uses: actions/upload-artifact@bbbca2ddaa5d8feaa63e36b76fdaad77386f024f # v7
        with:
          name: docker-image-${{ github.sha }}
          path: ${{ github.sha }}.tar

  snyk-docker-security:
    needs: build
    uses: juancarlosjr97/github-actions-workflows-to-rule-them-all/.github/workflows/shared-snyk-docker.yml
    with:
      IMAGE_REFERENCE: ${{ needs.build.outputs.image_reference }}
      IMAGE_TAR_ARTIFACT_NAME: ${{ needs.build.outputs.image_tar_artifact_name }}
      IMAGE_TAR_FILE_PATH: ${{ needs.build.outputs.image_tar_file_path }}
      SNYK_SEVERITY_THRESHOLD: high
    secrets:
      SNYK_TOKEN: ${{ secrets.SNYK_TOKEN }}
```

#### Security Scan (Non-Docker)

The [Workflow](./.github/workflows/shared-snyk-security.yml) scans a project's dependencies for vulnerabilities using Snyk CLI. Supports any ecosystem that Snyk CLI supports (npm, pip, cargo, composer, etc.).

| Environmental Variable  | Type   | Description                                                                | Required |
| ----------------------- | ------ | -------------------------------------------------------------------------- | -------- |
| PROJECT_DIRECTORY       | INPUT  | The directory containing the project to scan (relative to repository root) | false    |
| SNYK_SEVERITY_THRESHOLD | INPUT  | Minimum severity level to fail on (low, medium, high, critical)            | false    |
| SNYK_TOKEN              | SECRET | The Snyk authentication token for scanning                                 | true     |

Obtain a `SNYK_TOKEN` from your [Snyk account settings](https://app.snyk.io/account) and add it as a repository or organization secret.

##### Example

```yml
jobs:
  snyk-security:
    uses: juancarlosjr97/github-actions-workflows-to-rule-them-all/.github/workflows/shared-snyk-security.yml
    with:
      PROJECT_DIRECTORY: .
      SNYK_SEVERITY_THRESHOLD: high
    secrets:
      SNYK_TOKEN: ${{ secrets.SNYK_TOKEN }}
```

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

### Skills Update

The [Workflow](./.github/workflows/shared-agents-skills-sh-update.yml) automatically keeps [skills.sh](https://skills.sh) agent skills up to date by running on a weekly schedule (every Monday at midnight UTC) or on demand via `workflow_dispatch`.

#### How it works

1. Runs `npx skills check` to capture the current state of skills.
2. Runs `npx skills update` to apply any available updates.
3. If any files changed, opens a pull request with the `dependencies` and `skills.sh` labels containing the `skills check` output as context.
4. No-ops if all skills are already up to date.

#### Triggering manually

Navigate to **Actions → Skills Update → Run workflow** in the repository to trigger an immediate check and update.

#### Required permissions

The workflow requires the following permissions at the job level (already configured):

| Permission    | Level | Reason                          |
| ------------- | ----- | ------------------------------- |
| contents      | write | Commit updated skill files      |
| pull-requests | write | Open the update pull request    |

No additional secrets or inputs are needed.

### Rust

#### Tests

The [Workflow](./.github/workflows/shared-rust-tests.yml) has the following inputs:

| Environmental Variable | Type   | Description                                    | Required |
| ---------------------- | ------ | ---------------------------------------------- | -------- |
| CODECOV_TOKEN          | SECRET | The key to record the code coverage to CodeCov | true     |
