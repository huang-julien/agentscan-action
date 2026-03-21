# AgentScan Action

GitHub action that analyzes PR authors' recent activity patterns to detect automation signals.

## Setup

Create a workflow file in your repository (e.g., `.github/workflows/agentscan.yml`):

```yaml
name: AgentScan

on:
  pull_request_target:
    types: [opened, reopened]

permissions:
  pull-requests: write
  contents: read

jobs:
  agentscan:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: AgentScan
        uses: MatteoGabriele/agentscan-action@v1.0.1
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
```

The action will run automatically on new and reopened pull requests, analyzing the PR author's activity patterns to detect automation signals.

---

Stay safe out there, fellow human, and use AI responsibly.


