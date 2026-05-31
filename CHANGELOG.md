# Changelog

## [1.0.0](https://github.com/TheLeftMoose/homelab-copilot-plugin/compare/v0.3.0...v1.0.0) (2026-05-31)


### ⚠ BREAKING CHANGES

* The Copilot CLI install path changes from the direct repository plugin install to the plugin@marketplace flow. Consumers should add the self-marketplace and install homelab-copilot@homelab-copilot.

### Features

* reshuffle into plugins/ + add marketplace.json ([#6](https://github.com/TheLeftMoose/homelab-copilot-plugin/issues/6)) ([a2d1545](https://github.com/TheLeftMoose/homelab-copilot-plugin/commit/a2d1545be00ec7d79e11d70bb8c2a673ec61855d)), closes [#5](https://github.com/TheLeftMoose/homelab-copilot-plugin/issues/5)

## [0.3.0](https://github.com/TheLeftMoose/homelab-copilot-plugin/compare/v0.2.0...v0.3.0) (2026-05-31)


### Features

* **ci:** add release-please + minimum CI ([74f2d6a](https://github.com/TheLeftMoose/homelab-copilot-plugin/commit/74f2d6a031d721dea9976bec4522e79536ebdf5e)), closes [#2](https://github.com/TheLeftMoose/homelab-copilot-plugin/issues/2)

## v0.2.0 - 2026-05-31

- Add `mcp-bootstrap`, a Sonnet-backed custom agent for creating new homelab MCP service repositories from the copier template and filing the initial W1 scoping issues.

## v0.1.0 - 2026-05-31

- Initial Copilot CLI plugin with seven agents:
  - `feature-intake`
  - `scope-warden`
  - `backlog-curator`
  - `pr-author`
  - `adr-keeper`
  - `repo-reviewer`
  - `homelab-repo-reviewer`
