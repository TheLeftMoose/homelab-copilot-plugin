<!-- Use `gh pr create --fill` to auto-populate this from the latest commit. -->

## Summary

<!-- One or two sentences. What does this PR do and why? -->

## Linked issues

Closes #

<!-- Add more "Closes #N" lines as needed. List "Related #N" for context only. -->

## Type of change

- [ ] feat — new plugin capability or agent behavior
- [ ] fix — bug fix
- [ ] docs — documentation only
- [ ] chore — tooling / housekeeping
- [ ] refactor — no behavior change

## Risk tier

<!--
One of: risk:trivial, risk:standard, risk:sensitive. Agent proposes;
human overrides via label. See the cockpit repo's docs/process/risk-tiers.md.
-->

Tier: `risk:standard`

## Checklist

- [ ] Branch is `<type>/<slug>` off `main`
- [ ] Commit messages follow Conventional Commits + Copilot co-author trailer
- [ ] No secrets staged (`.env`, `.mcp.json`, tokens, local config)
- [ ] `plugin.json` remains valid JSON and matches the plugin manifest contract
- [ ] New or changed agents include valid YAML frontmatter
- [ ] Agent docs / README updated if behavior or install workflow changed
- [ ] Relevant validation passes (CI, frontmatter checks, or targeted tests)

## Notes for the reviewer

<!-- Anything specific you want the reviewer to focus on, or follow-ups you've already filed as separate issues. -->
