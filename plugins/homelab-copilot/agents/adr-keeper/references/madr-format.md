# MADR — reference for `adr-keeper`

> Companion reference for the `adr-keeper` agent. Summarises the
> Markdown Any Decision Records (MADR) format and this repo's local
> conventions. Canonical source: <https://adr.github.io/madr/>.

## Why MADR

- Plain Markdown — readable in any editor, on GitHub, and in a CLI.
- Stored next to the code (`docs/adr/`), not in a wiki or external
  tool — survives repo forks, clones, and history rewrites.
- Lightweight: short header, free-form body. No tooling required.
- Versionable: ADRs flow through git like everything else.

We considered (and rejected):

- **`adr-tools` CLI** (Nygard / npryce) — adds a binary dependency for
  what is essentially `cp template.md NNNN-slug.md`. Not worth the install.
- **Wiki / Notion / Confluence** — breaks the "decisions live with the
  code" property. Decisions outlive any external tool.
- **Inline code comments** — fine for *what*, terrible for *why this
  over the alternatives*. Doesn't capture rejected options.

## MADR structure (long form, what we use)

```markdown
# NNNN. <Short title in present tense imperative>

* Status: <Proposed | Accepted | Deprecated | Superseded by ADR-NNNN>
* Date: YYYY-MM-DD
* Deciders: <list of people / agents>
* Tags: <optional, comma-separated, e.g. mcp, safety>

## Context and problem statement

<What is the problem we are solving? What forces are at play?
Quote enough of the originating discussion that a cold reader gets it.
Link the issue / PR / chat snippet.>

## Decision drivers

<Bullet list of the criteria we weighed against.>

## Considered options

* Option A — <one-line description>
* Option B — <one-line description>
* Option C — <one-line description>

## Decision outcome

Chosen option: **<Option X>**, because <one-sentence why>.

### Consequences

* Positive: <what we get>
* Negative: <what we give up>
* Risks: <what could bite us; how we'd notice>

## Pros and cons of the options

### Option A
* Good, because …
* Bad, because …

### Option B
* Good, because …
* Bad, because …

## Links

* Originating issue: #N
* Related ADRs: NNNN, NNNN
* External references: <URLs>

## Changelog

* YYYY-MM-DD — Created (Proposed).
* YYYY-MM-DD — Accepted.
```

## Local conventions

- **Filename**: `NNNN-<slug>.md`. `NNNN` is zero-padded four digits.
  Slug is kebab-case, present-tense imperative
  (e.g. `0003-split-llm-and-infra-repos.md`).
- **Numbers never reused.** If an ADR is withdrawn before acceptance,
  leave the number burned; document the withdrawal in its Changelog.
- **Status transitions**: `Proposed` → `Accepted` → optionally
  `Deprecated` or `Superseded by ADR-NNNN`. No other states.
- **One decision per ADR.** Split if a conversation produces several.
- **Append-only history.** Don't rewrite accepted ADRs; supersede them.
- **Alternatives are mandatory.** At least one rejected option with the
  rejection reason. "We didn't consider any" is a smell.

## Last verified

Upstream MADR spec last cross-checked: 2026-05-30.
