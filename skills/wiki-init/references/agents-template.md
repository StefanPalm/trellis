# AGENTS.md — {{wiki-name}}

This file is the constitution of this wiki. Any agent operating on this wiki
must read this file first and treat it as authoritative. It overrides skill
defaults where they differ.

## Purpose

{{purpose — one or two sentences: what questions this wiki answers, and for whom}}

## Scope and isolation

This wiki lives entirely inside this folder. Agents must never read from or
write to any path outside it, and must never reference other wikis, even if
they exist in the same knowledge root. This bundle must remain shareable as a
standalone unit at all times.

## Layout

- `inbox/` — raw material awaiting processing. Anything goes: notes, articles,
  transcripts, exports, half-thoughts.
- `archive/` — processed sources, renamed `YYYY-MM-DD--<original-name>`, each
  accompanied by `YYYY-MM-DD--<original-name>.intake.md` recording what was
  extracted and which pages were created or updated.
- `wiki/` — the knowledge itself, a conformant OKF bundle. `index.md` is the
  entry point; agents consuming this wiki start there.

## Topic charter (agent-owned)

The taxonomy below was proposed by an agent from the stated purpose and is
maintained by agents over time. Humans correct it; agents propose changes to it
via `wiki/log.md`. A proposal is applied only after human acceptance, unless
the Autonomy section below says otherwise.

{{topic charter — one entry per topic:}}
{{- `topic-name` — rationale: why knowledge will accumulate along this dimension}}

Topic naming rule: lowercase, hyphenated, singular nouns. Before creating any
new topic or page, check for an existing near-duplicate under a different
spelling, case, or synonym. Taxonomy drift is the primary failure mode of this
system.

## Format rules (OKF v0.1 + producer extensions)

Every markdown file under `wiki/` carries YAML frontmatter:

```yaml
---
type: concept            # required. one of: concept | overview | log | report
title: Human-readable title
description: One-sentence summary used by indexes and consuming agents
tags: [topic-name, ...]  # first tag is the owning topic
created: YYYY-MM-DD
updated: YYYY-MM-DD
status: provisional      # established | provisional | contested
sources:                 # provenance: archive-relative paths or URLs
  - ../archive/2026-07-02--example.md
---
```

- One concept per file. New page if it is a distinct concept other pages would
  link to; edit in place if it is an attribute of an existing concept.
- Links are bundle-relative markdown links. Dense interlinking is a feature:
  when a page mentions a concept that has a page, link it.
- Pages are written for a reader with the wiki's purpose, not as raw notes:
  synthesized, in plain prose, contradictions surfaced rather than smoothed.
- `wiki/index.md` and `wiki/log.md` have reserved OKF semantics: index is the
  map and entry point, log is the append-only chronological record.

## Behavioral contract

- **Ingest** may create and edit concept pages, update `index.md`, `topics.md`
  and `log.md`, and move processed files from inbox to archive. It stages
  taxonomy change proposals in the log; it does not restructure.
- **Lint** writes dated report pages (`type: report`) and log entries. It never
  deletes and never rewrites concept pages.
- Every agent action gets a log entry: date, skill, what changed, why.
- When new material contradicts an existing page, the page is updated to state
  both positions, `status` is set to `contested`, and the log notes it. Agents
  do not silently pick winners.

## Autonomy

{{default: "Taxonomy changes require human acceptance. To grant autonomy,
replace this line with explicit permissions, e.g. 'Lint may merge exact
duplicate topics without asking.'"}}

## History

- {{YYYY-MM-DD}} — wiki created by wiki-init. Initial taxonomy above.
