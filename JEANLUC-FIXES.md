# jeanluc-fixes Branch

This branch is what my personal deployment of OpenClaw runs on.

## Purpose

- Contains fixes and features from open PRs that I want to use before they land on `main`
- Serves as the production branch for my personal bot instance

## Current Fixes

- `fix/wake-mode-bypass-empty-heartbeat` - Bypass empty-file check for cron wakeMode "now"

## Workflow

1. Merge or cherry-pick PRs I care about into this branch
1. Deploy from `jeanluc-fixes`
1. Rebase onto `main` as upstream PRs get merged
