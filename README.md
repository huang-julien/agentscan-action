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

## Configuration

### Inputs

- **github-token** (required): GitHub token for API access
- **skip-members** (optional): Comma-separated list of usernames to skip from scanning

### Skip Members

To skip specific team members from being scanned, add their usernames to the `skip-members` input:

```yaml
- name: AgentScan
  uses: MatteoGabriele/agentscan-action@v1.0.1
  with:
    github-token: ${{ secrets.GITHUB_TOKEN }}
    skip-members: "dependabot,renovate,my-trusted-bot"
```

Members in the skip list will be excluded from analysis without any PR comment or labels added.

---

Stay safe out there, fellow human, and use AI responsibly.
