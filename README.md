# GitHub Actions Workflows to Rule Them All

This project is a centralized repository for GitHub Actions workflows used across projects to simplify development wherever possible.

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
        uses: actions/checkout
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
