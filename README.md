# homelab-copilot-plugin

Custom GitHub Copilot CLI agents for homelab repositories, packaged as a
publishable Copilot CLI plugin.

Design rationale and migration notes live in the cockpit repo:
<https://github.com/TheLeftMoose/homelab-llm/blob/main/docs/agents.md>.

## Install

### Recommended (marketplace flow)

One-time per machine:

```shell
copilot plugin marketplace add TheLeftMoose/homelab-copilot-plugin
```

Then install or update:

```shell
copilot plugin install homelab-copilot@homelab-copilot
```

### Legacy (direct repo install, deprecated by Copilot CLI)

```shell
copilot plugin install TheLeftMoose/homelab-copilot-plugin
```

This form will be removed in a future Copilot CLI release.

## Releases

Releases are managed by release-please. Merged Conventional Commits on `main`
open release PRs automatically, and release-please owns updates to
`plugins/homelab-copilot/plugin.json`, `.github/plugin/marketplace.json`, and `CHANGELOG.md`.

## Agents

| Agent | Purpose |
| --- | --- |
| `feature-intake` | Captures conversational ideas and future work as well-formed GitHub issues. |
| `scope-warden` | Detects scope creep, delegates capture to `feature-intake`, then refocuses the current task. |
| `backlog-curator` | Reviews open issues for duplicates, overlaps, dependencies, stale work, and vague backlog items. |
| `pr-author` | Implements an issue through GitHub Flow: branch, focused change, verify, commit, push, and PR. |
| `adr-keeper` | Drafts and reviews Architecture Decision Records using MADR-style conventions. |
| `repo-reviewer` | Generic PR review for issue alignment, GitHub Flow, risk tiers, docs, and repo conventions. |
| `homelab-repo-reviewer` | Homelab-specific PR review for MCP architecture, IaC rules, cockpit boundaries, and service MCP conventions. |
| `triage-camera` | Read-only diagnostic agent for the W1 camera-offline-triage workflow from the [homelab-llm](https://github.com/TheLeftMoose/homelab-llm) cockpit. Investigates HA + UniFi + Reolink MCPs and reports a verdict + one recommended action; never executes state changes. |

## Layout

```text
.github/plugin/marketplace.json
plugins/
  homelab-copilot/
    plugin.json
    agents/
      *.agent.md
      pr-author/
        pr-author.agent.md
        references/
      adr-keeper/
        adr-keeper.agent.md
        references/
```

The repository is its own Copilot CLI marketplace. The marketplace manifest
points at the packaged plugin under `plugins/homelab-copilot/`.
