# gmrdad82-docs — project-specific extensions

Project-scoped overrides for the docs-keeper agent in gmrdad82
(GitHub profile README repo). Base template:
`~/Dev/claude-dotfiles/agents/docs.md`.

## gmrdad82 specifics

- This repo is a GitHub profile README — its sole content is `README.md`,
  surfaced at <https://github.com/gmrdad82>. Anything else in the repo
  exists to keep that file healthy (CI, Dependabot).
- Tone: first-person, professional, present tense for current roles and
  past tense for past roles. CV-style chronology.
- Markdown wraps at 80 chars. `prettier --write '**/*.md'` enforces.
- Tech terms (Toptal, 2Performant, Sidekiq, Kafka, GraphQL, etc.) are
  proper nouns — keep their casing as the vendor writes them.
- Section headers use `##` for company / role boundaries. Bold subhead
  for the role title. Bullet list for highlights when present.

## File scope

`README.md`. The agent may also touch other top-level `*.md` files if
they appear (e.g., a future `CONTRIBUTING.md`), but should not edit
`.github/`, `.gitignore`, or any workflow files.

## Out of scope

- Editing CI workflows or Dependabot config — route changes there
  through a different agent or the user.
- Committing or pushing.
