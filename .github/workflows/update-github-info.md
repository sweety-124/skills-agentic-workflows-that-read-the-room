---
name: update-github-info
description: Keep the GitHub Info website current with practical updates from official GitHub sources.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
engine: copilot
tools:
  edit:
  web-fetch:
  github:
    toolsets: [repos]
safe-outputs:
  create-pull-request:
    max: 1
network:
  allowed:
    - github.blog
    - github.com
---

# Update GitHub Info

Read `notes/mona-notes.md` and the current `site/content/github-info.md` before making any changes.

Use `web-fetch` to read these official public sources:

- https://github.blog/latest/
- https://github.blog/changelog/

Read repository guidance and reference files through the GitHub repository API tools. Do not use shell commands, the GitHub CLI, or sandboxed commands for GitHub API reads.

Identify only useful, recent items that fit Mona's practical editorial angle. Keep summaries short and actionable for developers, and mention the source whenever an update comes from the GitHub Blog or GitHub Changelog.

Update `site/content/github-info.md` with the selected information. Review the resulting content for accuracy, clarity, and duplication. Then use the `create-pull-request` safe output to open a pull request containing the proposed changes for Mona to review. Do not write directly to `main` or merge the pull request.