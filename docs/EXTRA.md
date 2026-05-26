# EXTRA.md (gmrdad82 profile repo)

Project-specific conventions that override the generic guidance in
`AGENTS.md`. Edit freely — `install.sh` never touches this file.

## What this repo is

`gmrdad82/gmrdad82` is a GitHub **profile** repo. The whole repo
exists to keep `README.md` healthy — that file is surfaced as the
profile page at <https://github.com/gmrdad82>.

There is no application code, no test suite, no build step. Markdown
in, markdown out.

## Layout

- `README.md` — the profile content (CV chronology, current roles,
  bio). The only user-facing artifact.
- `assets/` — images referenced by `README.md` (keep these path-
  stable; the README links to them).
- `.github/workflows/ci.yml` — Prettier markdown format check + the
  markdown link checker. Runs on push to `main` and PRs.
- `.github/dependabot.yml` — monthly bumps for GitHub Actions.
- `AGENTS.md`, `docs/EXTRA.md` — agent guidance (this file).
- `LICENSE` — authored profile content; **do not relicense**.

## Hard rules

- **README.md is owned by the user.** Agents may reformat, suggest
  edits, or fix typos — they may NOT invent employer history, dates,
  job titles, or accomplishments. All CV content is the user's to
  dictate; agents reword and format what's already there.
- **No application code.** Any urge to add scripts, tooling beyond
  CI, or generated content is a sign the work belongs in a different
  repo. Keep this repo a single-purpose documentation surface.
- **No secrets, no tokens, no private contact details** beyond what
  the user has chosen to publish on the GitHub profile itself.
- **CI workflow files use pinned action versions** (e.g.,
  `actions/checkout@v6`), never `@master` or `@main`. Dependabot
  raises monthly bumps.
- **Tech terms are proper nouns.** Keep vendor casing as-is —
  Toptal, 2Performant, Sidekiq, Kafka, GraphQL, etc.

## README style

- First person, professional tone.
- Present tense for current roles, past tense for past roles.
- `##` headers mark each company / role boundary; `**bold**` line
  underneath for the role title; bullet list for highlights when
  present.
- CV chronology: most recent role first, oldest last. Ranges use the
  pattern `YYYY - YYYY` or `YYYY - Present`.
- Keep links live — CI's markdown-link-check catches breakage, but
  vet locally first.

## Per-agent overrides

- **docs** — README.md is the only public artifact. Agents may
  rewrite paragraphs, fix typos, tighten phrasing — but never
  fabricate CV content. Markdown wraps at 80 cols (`prettier --write`
  applies). Tech terms keep vendor casing.

- **reviewer** — pre-commit gauntlet is two commands plus a sanity
  pass:
  - `npx --yes prettier@latest --check '**/*.md'`
  - `npx markdown-link-check README.md`
  - CV chronology check: most recent role first; date formats
    `YYYY - YYYY` or `YYYY - Present`; tech-term casing intact.
  - GHA version pinning: every `uses:` line in
    `.github/workflows/*.yml` pins a tag (e.g., `@v6`), never
    `@master` / `@main`.

- **simplifier** — apply to README content (cut filler, collapse
  repetition) but never delete CV facts the user explicitly added.
  Three-line bullets with similar shape are not "redundancy" here;
  they're the CV's voice.

- **git** — commit directly to `main` with a one-line meaningful
  message. No branches, no PRs needed for routine README edits.
  Pull with `--rebase`. No Co-Authored-By, no AI authorship mentions,
  no multi-line commit bodies.

- **github** — Issues and Discussions can stay off if you want a
  one-way profile surface. Dependabot is already wired for
  `github-actions` monthly bumps. CI on every push.

## Commands

```bash
npx --yes prettier@latest --check '**/*.md'   # Format check (CI mirror)
npx --yes prettier@latest --write '**/*.md'   # Auto-fix wrapping
npx markdown-link-check README.md             # Local link smoke test
```
