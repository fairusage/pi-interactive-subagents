# Sync Workflow — pi-interactive-subagents

## Setup

- **Upstream:** `origin` → `HazAT/pi-interactive-subagents` (read-only)
- **Fork:** `fork` → `fairusage/pi-interactive-subagents` (your copy)
- **Settings:** pinned to `git:github.com/fairusage/pi-interactive-subagents@v1.2.0`
- Pinned refs are **skipped by `pi update`** — won't get overwritten

## Check for upstream changes

```bash
cd ~/.pi/agent/git/github.com/HazAT/pi-interactive-subagents
git fetch origin
git log main..origin/main --oneline
```

If there are new commits, review them:

```bash
git diff main..origin/main
```

## Pull upstream changes and re-tag

```bash
# Merge upstream into your main
git checkout main
git merge origin/main

# Resolve conflicts if any, then bump version + tag
# Edit package.json version
git add -A && git commit -m "chore(release): v1.X.0"
git tag v1.X.0

# Push to your fork
git push fork main --tags
```

Then update settings:

```bash
# In ~/.pi/agent/settings.json, change:
#   "git:github.com/fairusage/pi-interactive-subagents@v1.2.0"
# to:
#   "git:github.com/fairusage/pi-interactive-subagents@v1.X.0"
```

Restart pi to pick up the new version.

## Quick check (one-liner)

```bash
cd ~/.pi/agent/git/github.com/HazAT/pi-interactive-subagents && git fetch origin && git log main..origin/main --oneline
```

If empty — you're up to date. If not — time to merge.
