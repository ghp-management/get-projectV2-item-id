<p align="center">
    <img src="https://avatars.githubusercontent.com/u/212018926?s=200">
</p>

# get-projectV2-item-id

This action actually outputs the ProjectV2 Item Node ID in long format ID starting from the organization login name, project number and node id.

Actually searching only in Issue nodes using pagination.

## Usage

In order to use this action you need to provide a valid token with Project permissions.

### Inputs

| name           | value  | default | required | description                                      |
|----------------|--------|---------|----------|--------------------------------------------------|
| token          | string | ''      | t        | Github valid Token for Project                   |
| organization   | string | ''      | t        | Organization login name                          |
| project_number | number |         | t        | ProjectV2 Number (took from Project URL path)    |
| node_id        | string | ''      | t        | Item Node ID (like `github.event.issue.node_id`) |

### Outputs

**node_id**: The ProjectV2 Item Node ID in long format, usually starts with `PVTI_` for Issues

## Example usage

workflow.yaml
``` yaml

jobs:
  my-job:
    runs-on: ubuntu-latest
    steps:
      - name: Get ProjectV2 Item Node ID if exists
        id: get-projectv2-item-id
        uses: ghp-management/get-projectV2-item-id@main
        with:
          token: ${{ secrets.GH_PAT_TOKEN }}
          organization: ${{ inputs.organization }}
          project_number: ${{ inputs.project_number }}
          node_id: ${{ github.event.issue.node_id }}

```
