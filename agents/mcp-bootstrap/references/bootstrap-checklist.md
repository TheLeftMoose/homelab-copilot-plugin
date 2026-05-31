# MCP bootstrap checklist

Use this checklist when creating a new per-service MCP repository from
`gh:TheLeftMoose/homelab-mcp-template`.

References:

- ADR-0007: <https://github.com/TheLeftMoose/homelab-llm/blob/main/docs/adr/0007-mcp-self-sufficiency.md>
- ADR-0008: <https://github.com/TheLeftMoose/homelab-llm/blob/main/docs/adr/0008-mcp-repo-template-strategy.md>

## W1 tool-surface scoping prompts

Capture enough detail that the first implementation issue can be worked without
reopening the bootstrap conversation.

1. **Service boundary**
   - What service/device/controller is this MCP server for?
   - What is the canonical service slug? Examples: `pihole`, `unifi-network`,
     `reolink`.
   - What repository should be created? Expected form:
     `TheLeftMoose/homelab-<slug>-mcp`.

2. **Vendor/API access**
   - Which vendor library, SDK, CLI, or HTTP API should be wrapped?
   - Is it actively maintained and compatible with the homelab runtime?
   - Does it support async calls, or will adapters need to isolate sync I/O?
   - What endpoint or controller URL is required?

3. **Initial v0.1.0 tool surface**
   - What are the smallest useful tools?
   - For each tool, record:
     - MCP tool name.
     - Read-only vs control.
     - Vendor-library/API call.
     - Inputs and validation constraints.
     - Output shape and any redactions.
     - Failure modes worth surfacing verbatim.
   - Prefer inventory, health, status, lookup, and diagnostics tools first.

4. **Safety boundary**
   - Which actions are explicitly out of scope for v0.1.0?
   - Could any proposed tool reboot devices, delete data, rotate credentials,
     alter firewall/routing/DNS policy, disable alarms, or otherwise cause
     destructive effects?
   - If yes, stop bootstrap mode and route to a separate sensitive-design issue.

5. **Authentication and permissions**
   - What credential type is required: token, API key, password, client secret,
     local session cookie, certificate?
   - Can the credential be read-only or otherwise least-privileged?
   - What secret fields must never appear in logs, test fixtures, or examples?

## Environment variable conventions

Use service-prefixed variables. Uppercase the service slug and convert hyphens to
underscores.

Examples:

- `PIHOLE_URL`
- `PIHOLE_TOKEN`
- `UNIFI_NETWORK_URL`
- `UNIFI_NETWORK_TOKEN`
- `REOLINK_HOST`
- `REOLINK_USERNAME`
- `REOLINK_PASSWORD`

Guidelines:

- Document required variables in `.env.example` with placeholder values only.
- Never commit `.env`, `.mcp.json`, real tokens, cookies, controller exports, or
  captured responses containing secrets.
- Load configuration once at startup into a typed settings object.
- Prefer URL/token naming unless the vendor library requires clearer equivalents
  such as host/username/password.

## ADR-0007 self-sufficiency audit

File an `ADR-0007 self-sufficiency audit` issue with this checklist:

- [ ] The repo README explains what service it wraps and how to run it locally.
- [ ] The repo documents required environment variables in `.env.example`.
- [ ] Tooling commands are discoverable without Cockpit-specific context.
- [ ] Risk-tier expectations are documented or linked locally.
- [ ] ADR/process references needed for normal work are present or linked.
- [ ] Tests, lint, and type-check commands can run from the repo root.
- [ ] No generated files require Cockpit after the initial bootstrap.
- [ ] No secrets, local `.env`, `.mcp.json`, or controller-specific data are
      committed.
- [ ] Initial W1 issues describe the tool surface and environment variables.

## Initial issue titles and labels

Create these issues in the new repo:

1. `W1: define tool surface`
   - Labels: `risk:standard`, `area:design`
2. `Document required environment variables`
   - Labels: `risk:standard`, `area:docs`
3. `ADR-0007 self-sufficiency audit`
   - Labels: `risk:standard`, `area:process`
