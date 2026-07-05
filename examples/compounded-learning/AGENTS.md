# AGENTS.md — compounded-learning

This file is the constitution of this wiki. Any agent operating on this wiki
must read this file first and treat it as authoritative. It overrides skill
defaults where they differ.

## Purpose

Answer, for a practitioner building the habit, which compounded-learning
practices actually work, why they work, and what evidence supports them — so
the practice improves instead of merely continuing.

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

- `practices` — rationale: the purpose is about what works; concrete habits,
  cadences, and workflows are the primary dimension knowledge accumulates
  along.
- `failure-modes` — rationale: a practice is understood by how it dies;
  documented failure modes are what make the practices trustworthy.
- `foundations` — rationale: the patterns and formats this practice builds on
  (llm-wiki, OKF, agent skills) will keep generating material as they evolve.
- `open-questions` — rationale: the purpose is open-ended; lint feeds this
  topic with what the wiki cannot yet answer.

Topic naming rule: lowercase, hyphenated, singular nouns. Before creating any
new topic or page, check for an existing near-duplicate under a different
spelling, case, or synonym. Taxonomy drift is the primary failure mode of this
system.

## Format rules (OKF v0.1 + producer extensions)

The `wiki/` folder is the OKF bundle; link paths treat it as root (`/`).

**Reserved files** (per OKF): `wiki/index.md` is the map and entry point — its
only frontmatter is `okf_version: "0.1"`. `wiki/log.md` is the chronological
record — no frontmatter, one `## YYYY-MM-DD` heading per day, **newest first**,
entries opening with a bold convention word (**Creation**, **Update**,
**Proposal**, **Report**). `wiki/reports/` holds dated lint reports and is not
a topic.

Every other markdown file under `wiki/` carries YAML frontmatter:

```yaml
---
type: concept            # required. one of: concept | overview | report
title: Human-readable title
description: One-sentence summary used by indexes and consuming agents
tags: [topic-name, ...]  # concept pages; first tag is the owning topic
created: YYYY-MM-DD      # producer extensions refining OKF's `timestamp`
updated: YYYY-MM-DD
status: provisional      # established | provisional | contested
sources:                 # provenance, producer extension: paths relative to
  - ../archive/2026-07-02--example.md   # the bundle root, or URLs
---
```

- `sources` intentionally point outside the OKF bundle into this wiki's
  `archive/`. OKF consumers tolerate unknown fields and unresolvable paths;
  anyone holding the whole wiki folder gets working provenance.
- One concept per file. New page if it is a distinct concept other pages would
  link to; edit in place if it is an attribute of an existing concept.
- In-body links are absolute from the bundle root, starting with `/`
  (e.g. `[taxonomy drift](/failure-modes/taxonomy-drift.md)`), per OKF's
  recommendation — they survive page moves. Dense interlinking is a feature:
  when a page mentions a concept that has a page, link it.
- Pages are written for a reader with the wiki's purpose, not as raw notes:
  synthesized, in plain prose, contradictions surfaced rather than smoothed.

## Behavioral contract

- **Ingest** may create and edit concept pages, update `index.md`, `topics.md`
  and `log.md`, and move processed files from inbox to archive. It stages
  taxonomy change proposals in the log; it does not restructure.
- **Lint** writes dated report pages (`type: report`) and log entries. It never
  deletes and never rewrites concept pages. It may read the archive; it never
  modifies it.
- **Ask** answers questions from the wiki, citing pages and respecting
  `status`. It writes nothing under `wiki/` or `archive/`; it may add a dated
  gap note to the inbox when a question exposes missing knowledge.
- Every agent action gets a log entry (newest-first): date, skill, what
  changed, why.
- When new material contradicts an existing page, the page is updated to state
  both positions, `status` is set to `contested`, and the log notes it. Agents
  do not silently pick winners.

## Autonomy

Taxonomy changes require human acceptance.

## History

- 2026-07-01 — wiki created by wiki-init. Initial taxonomy above.
