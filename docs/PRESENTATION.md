# Presentation ownership

The public repository owns `README.md`, `assets/brand/`, `docs/`, `CONTRIBUTING.md`, `SECURITY.md` and `.github/`. They are maintained presentation/community content, not generated runtime output. The development project owns runtime behavior, contracts, packaging and acceptance. Never import private development reports or user data to fill public documentation gaps.

## Release staging boundary

Stage a validated release into `plugins/codex-desktop-control/` and the intended `.agents/plugins/marketplace.json` entry only. Do not replace the repository root or overwrite its README/artwork/community files with generated release notes. Review version and verification references deliberately. Keep existing release tags immutable. The strict inventory is scoped to the plugin directory; presentation assets stay outside it.

## Identity

Graphite background `#10151e`, light surface `#f6f8fb`, indigo `#3458d6` on light and `#8ca7ff` on dark. Text uses high-contrast neutral colors. The original focus brackets and pointer represent exact visual targeting; they are not a product GUI or a screenshot. Artwork is static SVG with system-font fallbacks, no scripts, embedded private data, remote font dependencies or animation.

- `assets/brand/hero-light.svg` / `hero-dark.svg`: 1280×420, theme-aware README artwork.
- `assets/brand/social-preview.svg`: editable vector source.
- `assets/brand/social-preview.png`: 1280×640 solid-background social image, under GitHub's 1 MB limit.

Important meaning remains in Markdown and descriptive alt text, not only in an image. Keep artwork version-independent. Typography: Segoe UI, Arial, sans-serif; the repository embeds no font files. Preserve the theme picture sources and readable mobile scale.

## Review checklist

Render the proposed Markdown using GitHub's Markdown API; inspect the sanitized GFM output with GitHub styles in light and dark modes at desktop and narrow widths. Review image loading/selection, text scale, contrast, code blocks, table overflow and links. A local styled preview is not live GitHub acceptance; verify the published page after approved publication. Check all payload hashes and tag identity before and after presentation changes. Do not add badges, screenshots, testimonials or universal-platform claims without evidence.

Repository About, topics, homepage and social preview are separate GitHub settings. Record the proposed values and require owner confirmation before changing them. A committed social image alone does not activate GitHub's social-preview setting. License and private-reporting decisions also require owner approval.
