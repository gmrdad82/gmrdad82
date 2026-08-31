---
name: copy-content
description: Wording and formatting the profile README — proposals for the owner's validation, in the page's own voice.
triggers: [profile updates, CV wording, README edits, bio]
---

# Copy & content

## Project context

The README is a public CV and profile. Its facts are the owner's; its voice
is already established. Agent work here is proposals — he validates before
anything is committed.

## Conventions

- First person, terminal aesthetic (fake shell sessions in code blocks) —
  keep additions in that voice.
- Present tense for current roles, past for past; chronology
  most-recent-first; date ranges `YYYY - YYYY` or `YYYY - Present`.
- 80-column prose wrapping (prettier enforces); tables, code blocks, and
  long URLs exempt. Tech terms keep vendor casing (Toptal, 2Performant,
  Sidekiq, Kafka, GraphQL).
- Voice and design decisions follow the Pito estate design canon (kept in
  the owner's private notes archive — read it before rewording anything
  user-facing).
- Wording changes arrive as a small deck: current line → proposed line →
  one-line why where not obvious. Typos may be fixed directly but are still
  listed.
- Keep links live — vet with the link checker before handover.

## Anti-patterns

- Inventing or "improving" any CV fact, date, title, or accomplishment.
- Breaking the fake-shell framing with ordinary markdown prose blocks.
- A reformat-only diff mixed into a wording change.
