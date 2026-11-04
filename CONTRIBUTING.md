# Contributing

This is a **binary-plugin distribution and public documentation repository**, not the development source tree. Contributions should match that scope.

## Useful contributions

- Clear installation or update reports with exact versions and expected versus observed behavior.
- Reproducible observation/interaction failures in a disposable, non-sensitive fixture.
- Documentation fixes, accessibility improvements, and corrections to supported behavior.

Use the [bug report form](https://github.com/Zerk0n/Desktop-Control/issues/new?template=bug_report.yml) or open a concise feature request. Describe the application technology when known, such as WPF, WinForms, native Win32 or custom-drawn controls. That information helps investigation; it is not a compatibility claim.

## Safe reports

Include Windows/Codex/plugin versions, a minimal reproduction and whether input was dispatched, refused or uncertain. Include only sanitized diagnostics. Do not attach user policy, configuration, credentials, clipboard data, private screenshots, raw keystrokes or arbitrary application content. Prefer synthetic fixtures. Read [SECURITY.md](SECURITY.md) before reporting a suspected vulnerability.

## Pull requests

Explain the problem, proposed change and verification. Keep presentation changes outside the plugin payload. Do not submit modified runtime binaries, regenerate inventory markers for a changed binary, widen default permissions or rewrite released tags. Runtime/source work needs maintainer coordination in the separately owned development project.

For README and artwork changes, follow [presentation ownership](docs/PRESENTATION.md), show light/dark and narrow/wide previews, preserve alt text, and verify local links. Do not add CI/benchmark badges, application screenshots or compatibility claims without actual evidence.

## License status

No project license has been declared in this repository. Public availability is not an open-source license. License selection and any contribution-license policy require an explicit owner decision; this document makes no new license grant.
