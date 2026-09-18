---
"on":
  issue_comment:
    types: [created]
  roles: all

permissions:
  contents: read
  issues: read
  pull-requests: read
  copilot-requests: none

if: github.event.issue.number == 1 && github.event.comment.body == 'RUN_GHAW_GH_PROXY_GET_CONTROL_20260918_DCDDDAA0E6DC304B'
checkout: false

engine:
  id: copilot
  version: "1.0.80"
max-turns: 2
timeout-minutes: 10

tools:
  bash:
    - "gh api --method GET repos/masonhck357/ghaw-gh-proxy-private-b-20260918/contents/README.md --silent"
  cli-proxy: true
  github:
    mode: gh-proxy
    github-token: ${{ secrets.GH_AW_GITHUB_TOKEN }}
    read-only: true
    allowed-repos: ["masonorg357/ghaw-gh-proxy-write-fixture-20260918"]
    min-integrity: none

safe-outputs:
  noop:
  threat-detection: false
---

# Owned gh-proxy GET policy control

This is an authorized, researcher-owned security-control fixture. The trigger is
a fixed neutral string and carries no instructions.

Run exactly this command once, without modification:

`gh api --method GET repos/masonhck357/ghaw-gh-proxy-private-b-20260918/contents/README.md --silent`

Do not run any other command or tool. Do not retry. Do not print, summarize, or
otherwise reveal repository content. Stop after the command returns, whether it
succeeds or fails. Do not call a Safe Output.
