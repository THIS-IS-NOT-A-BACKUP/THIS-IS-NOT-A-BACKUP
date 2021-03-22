```yaml
# This runs every day on 1800 UTC

name: Sync Upstream

env:
  UPSTREAM_URL: "https://github.com/FFmpeg/FFmpeg.git"
  DOWNSTREAM_BRANCH: "master"
# Controls when the action will run.
on:
  schedule:
    - cron: '1 18 * * *'
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    
    steps:
      - name: GitHub Sync to Upstream Repository
        uses: dabreadman/sync-upstream-repo@v0.1.2.b
        with: 
          upstream_repo: ${{ env.UPSTREAM_URL }}
          branch: ${{ env.DOWNSTREAM_BRANCH }}
          token: ${{ secrets.GITHUB_TOKEN }}
```
