# Working agreement (for Claude / agents)

This is `gmrdad82/gmrdad82`, a GitHub **profile** repo. The whole repo exists
to keep `README.md` healthy — that file IS the profile page at
<https://github.com/gmrdad82>. There is no application code, no test suite,
no build step. Markdown in, markdown out.

## Layout

- `README.md` — the profile content (terminal-aesthetic bio, the PITO family,
  CV chronology, channels, gear). The only user-facing artifact.
- `assets/` — images referenced by `README.md` (path-stable; the README
  links to them).
- `.github/workflows/ci.yml` — Prettier markdown check + markdown link
  checker, on every push to `main` and on PRs.
- `.github/dependabot.yml` — monthly GitHub Actions bumps.
- `LICENSE` — authored profile content; **do not relicense**.

## Hard rules

- **README.md is owned by the user.** Reformat, tighten, fix typos — but
  NEVER invent employer history, dates, job titles, or accomplishments. All
  CV content is the user's to dictate; agents reword and format what is
  already there. Never delete CV facts he explicitly added.
- **No application code.** Any urge to add scripts or tooling beyond CI means
  the work belongs in a different repo.
- **No secrets, no tokens, no private contact details** beyond what the user
  already publishes on the profile.
- **Workflows pin action versions** (`actions/checkout@v7`), never
  `@master`/`@main`. Dependabot handles bumps.
- **Tech terms keep vendor casing** — Toptal, 2Performant, Sidekiq, Kafka,
  GraphQL, etc.

## README style

- First person. The profile leans on a terminal aesthetic (fake shell
  sessions in code blocks) — keep additions in that voice.
- Present tense for current roles, past tense for past ones. Chronology is
  most-recent-first; date ranges are `YYYY - YYYY` or `YYYY - Present`.
- Markdown wraps at 80 columns for prose (prettier enforces); tables, code
  blocks, and long URLs are exempt.
- Keep links live — CI's link checker catches breakage, but vet locally
  first.

## Git

- Commit directly to `main` — no branches, no PRs for routine README edits.
- One-line imperative message; no multi-line bodies needed here. No
  Co-Authored-By, no AI-authorship trailers.
- Pull with `--rebase`. Never force-push `main`. Stage files explicitly
  (no `git add .`).
- The user signs every commit; the GPG PIN prompt is his approval gate.

## Checks (mirror CI before pushing)

```bash
npx --yes prettier@latest --check '**/*.md'   # formatting (CI mirror)
npx --yes prettier@latest --write '**/*.md'   # auto-fix wrapping
npx markdown-link-check README.md             # link smoke test
```
