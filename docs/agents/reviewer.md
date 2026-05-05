# gmrdad82-reviewer — project-specific extensions

Project-scoped overrides for the reviewer agent in gmrdad82 (GitHub
profile README repo). Base template:
`~/Dev/claude-dotfiles/agents/reviewer.md`.

## gmrdad82 specifics

- Review pipeline (mirror what `.github/workflows/ci.yml` runs):
  - `npx --yes prettier@latest --check '**/*.md'` — formatting.
  - `gaurav-nelson/github-action-markdown-link-check` (or run locally
    via `npx markdown-link-check README.md` for a faster smoke).
  - GitHub Actions pinning: every `uses:` line should reference a
    tagged version (e.g., `actions/checkout@v5`), not `@master` or
    `@main` — drift surface for supply-chain risk.
- Output: `docs/orchestration/playbooks/<YYYY-MM-DD>-<slug>.md` (create
  the directory on first run if it doesn't exist).
- For CV-content edits, the reviewer also sanity-checks chronological
  ordering, that all listed companies / roles still resolve via the
  link check, and that no stale role contradicts an active one.

## Out of scope

- Editing the README content — route content changes through
  gmrdad82-docs.
- Committing or pushing.
