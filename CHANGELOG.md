# Changelog

## 0.2.0 — 2026-07-05

- **New skill: `wiki-ask`** — the read side of the loop. Answers questions
  from a wiki with page citations and status-aware confidence; unanswerable
  questions become dated gap notes in the inbox, so using the wiki grows it.
- **OKF v0.1 conformance fixes**: `wiki/index.md` now carries only
  `okf_version` frontmatter (reserved-file rule); `wiki/log.md` carries no
  frontmatter and runs newest-first under `## YYYY-MM-DD` headings; in-body
  links are absolute from the bundle root (`/topic/page.md`); producer
  extensions (`created`/`updated`, `status`, `sources`, `wiki/reports/`) are
  now documented as such in the AGENTS.md template.
- **Fixed invalid YAML** in wiki-lint's frontmatter (unquoted `: ` in the
  description broke strict parsers).
- Clarified that lint may read the archive (intake records are lint input)
  but never writes to it.
- Added `license` and `metadata` (version, author) to all skill frontmatter.
- **New docs**: [PRACTICE.md](PRACTICE.md) (the compounded-learning practice:
  loop, cadences, milestones, failure modes, scheduling), a worked example
  wiki under [examples/compounded-learning/](examples/compounded-learning/),
  and starter inbox material under [examples/starter-inbox/](examples/starter-inbox/).
- README generalized for any Agent Skills-compatible runtime; repo licensed
  MIT.

## 0.1.0 — 2026-07-05

- Initial release: `wiki-init`, `wiki-ingest`, `wiki-lint` skills built on
  Karpathy's llm-wiki pattern, Google's Open Knowledge Format (OKF) v0.1, and
  the Agent Skills specification.
