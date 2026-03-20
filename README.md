# AgentScan Action

GitHub action that analyzes PR authors' recent activity patterns to detect automation signals.

## Setup

Create a workflow file in your repository (e.g., `.github/workflows/agentscan.yml`):

```yaml
name: AgentScan

on:
  pull_request:
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

Stay safe out there, fellow human.

![](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExNTZyOWRramhsZGpsY2lxNHhzazZ2b2R4N2ZmYmRwOG5odmRvMmJnbiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/CmFMWpEa4IFtS/giphy.gif)


