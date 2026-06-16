# rustpunk github workflows

Reusable GitHub Actions workflows for rustpunk repositories.

## PR Branch Updater

Caller repositories keep a small workflow with their local triggers and delegate
the implementation to this repository:

```yaml
jobs:
  update:
    uses: rustpunk/github-workflows/.github/workflows/pr-auto-update-branches.yml@main
    with:
      base: main
    secrets: inherit
```

The updater rebases same-repository open PR branches onto the configured base
branch when the caller workflow runs. Fork PRs are intentionally skipped.

By default the workflow pushes with `GITHUB_TOKEN`. To make update pushes trigger
normal CI runs, configure a repository or organization secret named
`PR_BRANCH_UPDATE_TOKEN` with a fine-grained PAT or GitHub App token that can read
pull requests and write contents.
