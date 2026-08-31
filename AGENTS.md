# gmrdad82

The GitHub **profile** repo — `README.md` IS the profile page at
<https://github.com/gmrdad82>. No application code, no build step. Markdown
in, markdown out.

Task guide: [`agents/skills/copy-content.md`](agents/skills/copy-content.md)
— all agent work here is wording and formatting.

# Layout

- `README.md` — the profile content (terminal-aesthetic bio, the Pito family,
  CV chronology, channels, gear). The only user-facing artifact.
- `assets/` — images the README links to (path-stable).
- `.github/workflows/ci.yml` — Prettier markdown check + link checker.
- `LICENSE` — authored profile content; do not relicense.

# Hard rules

- No AI tool commits or pushes here.
- **The CV is the owner's to dictate**: reword, tighten, fix typos — never
  invent employer history, dates, titles, or accomplishments, and never
  delete CV facts he explicitly added.
- No application code; an urge to add tooling beyond CI means the work
  belongs elsewhere.
- No secrets, tokens, or private contact details beyond what the profile
  already publishes.
- Workflows pin action versions (`actions/checkout@v7`), never
  `@master`/`@main`.

# Checks (mirror CI)

```bash
npx --yes prettier@latest --check '**/*.md'
npx markdown-link-check README.md
```
