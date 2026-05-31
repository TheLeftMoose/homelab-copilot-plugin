# homelab-copilot-plugin

Custom GitHub Copilot CLI agents for homelab repositories, packaged as a
publishable Copilot CLI plugin.

Design rationale and migration notes live in the cockpit repo:
<https://github.com/TheLeftMoose/homelab-llm/blob/main/docs/agents.md>.

## Install

Local development install:

```shell
copilot plugin install /home/desck/src/homelab-copilot-plugin
```

Future GitHub install after a published tag is available:

```shell
copilot plugin install TheLeftMoose/homelab-copilot-plugin
```

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

## Layout

```text
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

The manifest follows GitHub's Copilot CLI plugin reference and uses
`plugin.json` at the repository root.
