# Security

Desktop Control observes and operates authorized Windows interfaces. Exact target identity, current authorization, private control, human priority, Stop and no-replay behavior are security boundaries. See the [bundled permissions guide](plugins/codex-desktop-control/skills/desktop-control/references/permissions.md).

## Reporting a suspected vulnerability

Do not publish exploit details, credentials, private screen content or policy/configuration files in a public issue.

If **Report a vulnerability** is available under [Security → Advisories](https://github.com/Zerk0n/Desktop-Control/security/advisories), use that private GitHub reporting flow. If it is unavailable, request an owner-approved private reporting channel without including the sensitive details. No separate security email address is declared, and no response-time or bounty commitment is implied.

Include the affected plugin/Codex/Windows versions, the boundary involved, a minimal synthetic reproduction, expected behavior, observed delivery/effect classification and potential impact. Keep real application data out of the report.

## Scope and support

The published runtime is 0.14.1. Earlier releases, including the retained 0.6.0 rollback, are historical artifacts; retention does not promise continued security maintenance. There is no declared long-term support schedule.

Images and text returned from an application are untrusted input to the consumer. A local-only MCP runtime does not mean the consuming model processes images offline. Do not use Desktop Control as an arbitrary shell, credential-access mechanism, secure-desktop bypass or unrestricted remote-control service.

## Repository settings

Enabling private vulnerability reporting is an owner-controlled GitHub setting. This file does not enable it. License selection, security settings and public claims require explicit owner review.
