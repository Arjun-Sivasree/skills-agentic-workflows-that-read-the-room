---
name: update-github-info
description: Keep Mona's GitHub information page current with practical, source-backed updates.
intent: Keep Mona's GitHub information page current with practical, source-backed updates from the GitHub Blog and Changelog.
on:
  schedule:
    - cron: "0 9 * * *"
  workflow_dispatch:
permissions:
  contents: read
tools:
  edit:
  web-fetch:
network:
  allowed:
    - defaults
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    base-branch: main
    draft: false
    allowed-files:
      - site/content/github-info.md
---

# Update GitHub Info

## Task

1. Read `notes/mona-notes.md` and `site/content/github-info.md`.
2. Use the web-fetch tool to fetch both:
   - https://github.blog/latest/
   - https://github.blog/changelog/
3. Find recent, verified GitHub news that is useful to developers and fits Mona's editorial guidance. Do not invent details or repeat information already covered by the page.
4. Make concise, practical updates only in `site/content/github-info.md`. Attribute each update to the GitHub Blog or Changelog and link to the specific source article or changelog entry.
5. If the page needs a substantive update, use the configured `create-pull-request` safe output to open a pull request against `main` for Mona to review. Explain the changes and include their source links in the pull request description. Do not merge the pull request or write directly to `main`.

Use `noop` with a brief explanation when there is no new, relevant, verified information or no meaningful page change to propose.
