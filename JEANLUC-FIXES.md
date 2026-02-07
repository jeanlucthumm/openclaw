# jeanluc-fixes Branch

This branch is what my personal deployment of OpenClaw runs on.

## Purpose

- Contains fixes and features from open PRs that I want to use before they land on `main`
- Serves as the production branch for my personal bot instance

## Current Fixes

- `fix/wake-mode-bypass-empty-heartbeat` - Bypass empty-file check for cron wakeMode "now"
- `fix/session-status-unix-timestamp` - Add ISO-8601 and Unix timestamps to session_status for accurate reminder scheduling (#10836, fixes #10841)

## Workflow

Use **merge** (not rebase) to preserve history of when syncs and fixes were applied.

### Sync with main

```bash
git fetch upstream main

# See what's new on main since last sync:
git log --oneline HEAD..upstream/main

# See a summary of changes:
git log --oneline HEAD..upstream/main | wc -l  # commit count
git diff --stat HEAD..upstream/main            # files changed

# Check if any specific fix PRs landed:
git log --oneline upstream/main --grep="heartbeat"  # search by keyword

# When ready, merge:
git merge upstream/main
```

If there are conflicts, resolve them and commit. No force push needed.

### Add a fix from an open PR

```bash
# If a local fix branch exists:
git merge fix/branch-name

# Or cherry-pick a specific commit:
git cherry-pick <commit-sha>
```

### When a fix lands on main

Once a fix PR is merged upstream, the next sync with main will include it.
You can then remove it from the "Current Fixes" list above.

### Deploy

Deploy from `jeanluc-fixes` after syncing or adding fixes.
