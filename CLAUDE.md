# gmrdad82 — profile repo guide (for Claude / agents)

## ⛔ THE COMMIT IS THE OWNER'S (owner law, 2026-08-29 — global, all repos)

**Claude never runs `git commit` / `git tag` / `git push` here unless Gamer
Dad explicitly asks for that commit.** Finishing the work is not permission to
commit it — the change is left in the working tree and he is told what to
commit. Never in any case: `stash`, `checkout`, `restore`, `reset`, `clean`,
force-push, amend, or history rewrite. When he does ask: stage the files
explicitly (never `git add .` / `-A`), no AI trailers, this repo's message form.

> The global working agreement (`~/.claude/CLAUDE.md`) applies; this file carries only repo specifics.

This is `gmrdad82/gmrdad82`, a GitHub **profile** repo. The whole repo exists
to keep `README.md` healthy — that file IS the profile page at
<https://github.com/gmrdad82>. There is no application code, no test suite,
no build step. Markdown in, markdown out.

## Layout

- `README.md` — the profile content (terminal-aesthetic bio, the Pito family,
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

- When he asks for a commit: straight to `main` — no branches, no PRs.
- One-line imperative message; no multi-line bodies needed here.
- Stage files explicitly (no `git add .`).

## Checks (mirror CI before pushing)

```bash
npx --yes prettier@latest --check '**/*.md'   # formatting (CI mirror)
npx --yes prettier@latest --write '**/*.md'   # auto-fix wrapping
npx markdown-link-check README.md             # link smoke test
```

## Language and design canon (owner law, 2026-08-05)

Every language and design decision in this repo — voice, copy,
marks, lockups, interface grammar — follows the Pito estate design
canon (`LANGUAGE-AND-DESIGN-LANGUAGE.md`, kept in the owner's
private dev-notes archive). Sessions on the owner's machine read
it before designing or wording anything user-facing. Per-product
amendments are ratified by the owner; the canon is amended, never
forked.
