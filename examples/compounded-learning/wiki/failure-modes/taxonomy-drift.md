---
type: concept
title: Taxonomy drift
description: Near-duplicate topics under different names silently fork the structure; naming discipline and lint are the countermeasures.
tags: [failure-modes]
created: 2026-07-02
updated: 2026-07-04
status: established
sources:
  - ../archive/2026-07-02--llm-wiki-reading-notes.md
  - ../archive/2026-07-04--first-week-retro.md
---

# Taxonomy drift

The structure forks silently: `Meetings`, `meeting-notes`, and `mtg` as three
separate homes for the same knowledge (observed in a pre-agent note graveyard,
reading notes 2026-07-02). Each variant looks reasonable at creation time;
the damage is cumulative, because material lands in whichever variant the
current batch resembles, and cross-links between the forks never form.

Independently confirmed in week one of this wiki: item-by-item ingestion
nearly grew a `capturing` topic alongside the existing
[capture](/practices/inbox-capture.md) pages under `practices`. The
[weekly lint pass](/practices/weekly-lint-cadence.md) caught it before the
fork took.

Two countermeasures, both structural rather than willpower-based:

- **Naming discipline at creation time** — lowercase, hyphenated, singular
  nouns, with a mandatory check for near-duplicates under other spellings or
  synonyms before any new topic or page is created.
- **Lint's drift pass** — proposes merges and demotions with the exact page
  moves involved, so correcting a fork is a decision, not a project.

Drift pressure appears related to
[ingest batch size](/practices/ingest-batch-size.md): smaller, more frequent
ingests gave the near-fork its opening.
