# WP Snaps News Pipeline (Kanban)

This repo is a GitHub Issues + Projects kanban that powers an automated pipeline:

1. Discover high-signal WordPress news (official + community)
2. Draft **WordPress-ready Markdown** (Block Editor friendly, with oEmbed URLs for X/YouTube/etc)
3. Create a GitHub Issue for review
4. **Only when you move the issue card to `Approved`** → the system publishes to https://wpsnaps.com

## Project board
This pipeline expects a GitHub **Projects (v2)** board with `Status` values:

- Inbox
- Draft Ready
- Approved
- Published

## Required GitHub token scopes
The automation uses the GitHub Projects v2 GraphQL API.

Your `gh` auth token must include:
- `project`
- `read:project`

Refresh scopes:

```bash
gh auth refresh -h github.com -s project,read:project
```

Then rerun setup.

## Posting rules
- Drafts are created as GitHub issues first.
- Publishing to WP Snaps happens **only** after approval.
- If there’s nothing genuinely interesting on a given run, it will skip.
