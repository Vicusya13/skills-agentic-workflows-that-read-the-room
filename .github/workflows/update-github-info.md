---
name: update-github-info
description: Keeps Mona's GitHub Info page up to date from her notes, the GitHub Blog and the GitHub Changelog.
on:
  workflow_dispatch:
  schedule: daily
permissions:
  contents: read
  copilot-requests: write
engine:
  id: copilot
  copilot-sdk: true
  model: gpt-5-mini
tools:
  edit:
  web-fetch:
  github:
    toolsets: [repos]
network:
  allowed:
    - defaults
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
---

# Update Mona's GitHub Info page

You keep Mona's website page `site/content/github-info.md` current with the latest GitHub news and community workflows.

## Sources

1. Read Mona's notes in `notes/mona-notes.md` from this repository using the GitHub repository tools. They describe what Mona cares about and how she likes the page written.
2. Use web-fetch to read the GitHub Blog: https://github.blog/latest/
3. Use web-fetch to read the GitHub Changelog: https://github.blog/changelog/
4. Use web-fetch to read the Awesome Copilot workflows collection: https://awesome-copilot.github.com/workflows/ and include notable new community workflows.

## What to do

- Compare the latest posts and changelog entries with what is already on `site/content/github-info.md`.
- Pick the most relevant new items for Mona's audience, following her notes.
- Update `site/content/github-info.md` with short, friendly summaries and a link to each source.
- Keep the existing structure and front matter of the page. Do not edit any other files.
- If nothing new is worth adding, make no changes.

## Output

Open a pull request for Mona to review with the changes. In the pull request description, list each new item and its source link so Mona can review it quickly.
