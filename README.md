# sync-upstream-repo

**Usage:**

1. Setup [PAT(personal access token)](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token), and ensure to enable workflow permisson.
1. Setup `secrets.PAT_TOKEN` with PAT value
1. Add workflow yaml, like:


```yaml
name: Sync Upstream

# This runs every day on 1801 UTC
on:
  schedule:
    - cron: '1 18 * * *'
  # Allows manual workflow run (must in default branch to work)
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: GitHub Sync to Upstream Repository
        uses: Andrey1994/sync-upstream-repo@0.0.2
        with: 
          upstream_repo: https://github.com/Andrey1994/sync-upstream-repo # change this
          upstream_branch: main # change this
          downstream_branch: main # change this
          token: ${{ secrets.PAT_TOKEN }}
```
