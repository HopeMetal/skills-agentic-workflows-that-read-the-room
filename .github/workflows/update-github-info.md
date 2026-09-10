---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
  pull-requests: read
engine: copilot
tools:
  edit:
  web-fetch:
  github:
    toolsets: [repos]
network:
  allowed:
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    reviewers: [monalisa]
    draft: true
---

# Update GitHub information

Keep the repository's GitHub information current for Mona to review.

1. Read `notes/mona-notes.md` for repository-specific context and instructions.
2. Use the `web-fetch` tool to read https://github.blog/latest/.
3. Use the `web-fetch` tool to read https://github.blog/changelog/.
4. Use the GitHub repository API tools to read any repository guidance or reference files needed to make the update. Do not use terminal, CLI, or sandboxed commands to read repository guidance or reference files.
5. Update `site/content/github-info.md` with accurate, concise information grounded in the notes and fetched GitHub sources. Preserve the existing format and make no unrelated changes.
6. Review the diff for correctness. Use the `create-pull-request` safe output to open a draft pull request containing the update for Mona to review. Do not write directly to the default branch.

If there is no substantive update to make, do not create a pull request.