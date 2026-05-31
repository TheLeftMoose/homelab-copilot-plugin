# GitHub Flow — reference for `pr-author`

> Companion reference for the `pr-author` agent. Summarises the
> practices that guide every PR this agent produces. Canonical source:
> <https://docs.github.com/en/get-started/using-github/github-flow>.
>
> Keep this file short. If GitHub publishes a substantive change to the
> upstream doc, update the summary and bump the "Last verified" line.
> Don't mirror the full doc here — link to it.

## Why GitHub Flow

A lightweight, trunk-based workflow built around short-lived branches
and PR review. Suits small teams, continuous deployment, and projects
where `main` is always meant to be deployable. Use these defaults so that:

- `main` is always in a state we'd be willing to ship.
- Every change passes through review (human or `repo-reviewer` agent).
- Branch history doubles as a change log of intent (one branch = one
  issue = one PR = one merge commit / squash).

## The six steps (per the upstream doc)

1. **Create a branch.** Off the latest `main`. Short-lived. Name it
   after what it does.
2. **Make changes.** Commit incrementally with meaningful messages.
3. **Create a pull request.** Early if you want feedback (draft PR).
4. **Address review comments.** Push more commits to the same branch;
   never rewrite shared history after review starts.
5. **Merge the pull request.** Only after review approves and checks
   pass. Prefer the merge style the repo's settings enforce.
6. **Delete the branch.** Tidy up after merge; the PR keeps the history.

## How this repo applies them

| Upstream practice | GitHub Flow defaults |
|---|---|
| Branch naming | `<type>/<short-slug>`, types ∈ `feat`, `fix`, `docs`, `chore`, `refactor`. Slug kebab-case, prefix with issue number when there is one (e.g. `feat/12-caddy-reverse-proxy`). Prefer the consuming repo's `CONTRIBUTING.md` when it defines a different convention. |
| Commit messages | Conventional Commits (`<type>(<scope>): <subject>`). Always include the `Co-authored-by: Copilot` trailer. |
| PR description | Use `.github/PULL_REQUEST_TEMPLATE.md` when present. Always include `Closes #N` (or `Refs #N` for partial work). |
| Review | Built-in `code-review` for generic concerns + `repo-reviewer` for repo-specific conventions. Author never self-merges. |
| Branch protection | Respect the consuming repo's branch protection and hooks. Never bypass them. |
| Force-push | Only on your own topic branch, only before review starts. Never on `main` or after review begins. |
| Anti-patterns | See agent body. Plus: never open a PR without the explicit pre-PR checkpoint (step 7 of the agent's process). |

## Anti-patterns the agent must refuse

- Pushing directly to `main`.
- Bundling unrelated changes into one PR ("while I'm in here…"). Use
  `scope-warden` to capture the off-topic idea as a new issue.
- Rewriting history after review has started.
- Self-merging.
- Skipping the verify step (lint / format / type-check / test) because
  "it's a small change".

## Last verified

Upstream content last cross-checked: 2026-05-30.
