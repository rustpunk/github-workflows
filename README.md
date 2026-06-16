# rustpunk agent workflows

Reusable GitHub Actions workflows for rustpunk repositories.

## PR Branch Updater

Caller repositories keep a small workflow with their local triggers and delegate
the implementation to this repository:

```yaml
jobs:
  update:
    uses: rustpunk/agent-workflows/.github/workflows/pr-auto-update-branches.yml@main
    with:
      base: main
```

The updater rebases same-repository open PR branches onto the configured base
branch when the caller workflow runs. Fork PRs are intentionally skipped because
the default `GITHUB_TOKEN` cannot safely push to them.
