# gmrdad82 — GitHub Profile README

Public profile / résumé repository for `gmrdad82` on GitHub. The whole
repo exists to keep `README.md` healthy — that file is surfaced as the
profile page at <https://github.com/gmrdad82>.

## Layout

- `README.md` — the profile content (CV chronology, current roles,
  bio). The only user-facing artifact.
- `.github/workflows/ci.yml` — Prettier markdown format check +
  markdown link check on push to `main` and on pull requests.
- `.github/dependabot.yml` — monthly bumps for GitHub Actions.
- `docs/agents/` — project-specific agent instructions for the two
  named agents (`docs.md`, `reviewer.md`). These are self-contained
  templates embedded in the repo.
- `.gitignore`, `LICENSE`, `AGENTS.md` — repo-level housekeeping.

## Commands

```bash
npx --yes prettier@latest --check '**/*.md'   # Format check (CI mirror)
npx --yes prettier@latest --write '**/*.md'   # Auto-fix wrapping
npx markdown-link-check README.md             # Local link smoke test
```

There is no test suite, no application stack, no build step.

## Workflow rules

- Commit directly to `main` with a one-line meaningful message. No
  branches, no PRs needed for routine README edits.
- Always pull with `--rebase`.
- No Co-Authored-By, no AI authorship mentions, no multi-line commit
  bodies.
- Markdown wraps at 80 chars (`prose-wrap: always` via Prettier
  defaults). Run `prettier --write` before committing if in doubt.
- Do NOT commit until the user has reviewed the rendered diff.
- Tech terms (Toptal, 2Performant, Sidekiq, Kafka, GraphQL, etc.) are
  proper nouns — keep their casing as the vendor writes them.

## README style

- First person, professional tone.
- Present tense for current roles, past tense for past roles.
- `##` headers mark each company / role boundary; `**bold**` line
  underneath for the role title; bullet list for highlights when
  present.
- CV chronology: most recent role first, oldest last. Ranges use the
  pattern `YYYY - YYYY` or `YYYY - Present`.
- Keep links live — broken external links get caught by CI's
  `markdown-link-check`, but it is faster to vet them locally first.

## Agent orchestration

This repo runs a **minimal master-agent** workflow with two named
subagents:

- **gmrdad82-docs** — owns `README.md` and any future top-level `*.md`.
  Stub: `docs/agents/docs.md`. Forbidden from editing CI, Dependabot,
  or `.github/`.
- **gmrdad82-reviewer** — runs the pre-commit gauntlet (Prettier check,
  markdown link check, GitHub Actions version pinning, CV chronology
  sanity check). Writes a playbook to
  `docs/orchestration/playbooks/<YYYY-MM-DD>-<slug>.md` (creates the
  directory on first run). Stub: `docs/agents/reviewer.md`. Forbidden
  from editing README content.

The master agent (CodeWhale in this terminal) plans, dispatches,
reviews, and commits — it does NOT write README content directly when a
docs agent is appropriate, and does NOT run the review gauntlet itself
when a reviewer agent is appropriate. Subagents do not commit or push;
the master commits after the user validates.

For routine, single-line edits (a fixed typo, a date bump) the master
may edit directly without dispatching — the agent layer is overhead
that only pays off for substantive content changes.

## Hard rules

- **No application code.** This is a documentation repo. Any urge to
  add scripts, tooling beyond CI, or generated content is a sign the
  work belongs in a different repo.
- **CI workflow files use pinned action versions** (e.g.,
  `actions/checkout@v5`), never `@master` or `@main`. The reviewer
  agent flags drift; Dependabot raises monthly bumps.
- **No secrets, no tokens, no private contact details** beyond what
  the user has chosen to publish on the GitHub profile itself.
- **Do not invent employer history, dates, or accomplishments.** All
  CV content is the user's to dictate — the docs agent rewords and
  formats; it does not author claims.

## Glossary

- **Profile README** — the special `gmrdad82/gmrdad82` repo on GitHub
  whose `README.md` renders on the user's profile page.
- **Master agent** — CodeWhale in the terminal you are reading.
- **Subagent** — `gmrdad82-docs` or `gmrdad82-reviewer`, dispatched
  via the Agent tool.
