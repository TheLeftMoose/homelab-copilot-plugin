# Changelog

## [1.1.0](https://github.com/TheLeftMoose/homelab-copilot-plugin/compare/v1.0.0...v1.1.0) (2026-05-31)


### Features

* **agents:** add diagnose-integration-setup agent (W3 invokable) ([#13](https://github.com/TheLeftMoose/homelab-copilot-plugin/issues/13)) ([ba758ef](https://github.com/TheLeftMoose/homelab-copilot-plugin/commit/ba758ef3f425577f49536456b77f4828aaf6f9fe))
* **agents:** add triage-camera agent ([#10](https://github.com/TheLeftMoose/homelab-copilot-plugin/issues/10)) ([aaf6f36](https://github.com/TheLeftMoose/homelab-copilot-plugin/commit/aaf6f36cbd09efa0500ddde326172a1afc999f2e))


### Bug Fixes

* **plugin:** list subfolder agent directories so pr-author / adr-keeper / mcp-bootstrap load ([#14](https://github.com/TheLeftMoose/homelab-copilot-plugin/issues/14)) ([4bacc18](https://github.com/TheLeftMoose/homelab-copilot-plugin/commit/4bacc1860ec8a7649dd930d5ba9e6560040b115e)), closes [#8](https://github.com/TheLeftMoose/homelab-copilot-plugin/issues/8)


### Docs

* **pr-author:** handle repos where auto-merge is unavailable ([#12](https://github.com/TheLeftMoose/homelab-copilot-plugin/issues/12)) ([b24f194](https://github.com/TheLeftMoose/homelab-copilot-plugin/commit/b24f1946bfa452c39f84ced23856f8af1e013551))

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
