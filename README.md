# github-actions-workflow-template
[![Release](https://github.com/infra-blocks/github-actions-workflow-template/actions/workflows/release.yml/badge.svg)](https://github.com/infra-blocks/github-actions-workflow-template/actions/workflows/release.yml)
[![Trigger Update From Template](https://github.com/infra-blocks/github-actions-workflow-template/actions/workflows/trigger-update-from-template.yml/badge.svg)](https://github.com/infra-blocks/github-actions-workflow-template/actions/workflows/trigger-update-from-template.yml)

This repository is a template for creating reusable GitHub Actions Workflows. Go through the below checklist
upon instantiating this template:
- Remove the [trigger update from template workflow](.github/workflows/trigger-update-from-template.yml)
- Edit the content of [the placeholder](.github/workflows/workflow.yml) for your reusable workflow.
- Update the status badges:
    - Remove the `Trigger Update From Template` status badge.
    - Add the `Update From Template` status badge.
    - Rename the rest of the links to point to the right repository.
- Edit this document and update the relevant sections
- Prepare the [changelog](CHANGELOG.md) for the first version of the module that will be released.

## Inputs

|     Name      | Required | Description                                                                                                                                                                  |
|:-------------:|:--------:|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| example-input |   true   | An example input.                                                                                                                                                            |
|     skip      |  false   | A boolean indicating whether to skip the workflow. This is to workaround the required checks discrepancy when the workflow is skipped from the caller. It defaults to false. |

## Secrets

|      Name      | Required | Description        |
|:--------------:|:--------:|--------------------|
| example-secret |   true   | An example secret. |

## Outputs

|      Name      | Description        |
|:--------------:|--------------------|
| example-output | An example output. |

## Permissions

|     Scope     | Level | Reason   |
|:-------------:|:-----:|----------|
| pull-requests | read  | Because. |

## Concurrency controls

Describe concurrency controls of the workflow.

## Timeouts

Describe the timeouts configured, if any.

## Usage

```yaml
name: Template Usage

on:
  push: ~

# This needs to be a superset of what your workflow requires
permissions:
  pull-requests: read

jobs:
  example-job:
    uses: infra-blocks/github-actions-workflow-template/.github/workflows/workflow.yml@v1
    with:
      example-input: Nobody cares
    secrets:
      example-secret: ${{ secrets.EXAMPLE }}
```

### Releasing

The releasing is handled at git level with semantic versioning tags. Those are automatically generated and managed
by the [git-tag-semver-from-label-workflow](https://github.com/infra-blocks/git-tag-semver-from-label-workflow).
