---
type: concept
title: Ingest batch size
description: Whether to ingest items immediately or in related batches is contested; both positions and their evidence are stated.
tags: [practices]
created: 2026-07-02
updated: 2026-07-04
status: contested
sources:
  - ../archive/2026-07-02--llm-wiki-reading-notes.md
  - ../archive/2026-07-04--first-week-retro.md
---

# Ingest batch size

How much should accumulate in the inbox before running ingest? The wiki
currently holds two conflicting positions.

**Ingest immediately** (reading notes, 2026-07-02): process each item the
moment it lands, so the wiki is always current and the inbox never rots.
Immediacy also keeps [capture](/practices/inbox-capture.md) motivating — you
see your material become pages the same day.

**Ingest in related batches** (first-week retro, 2026-07-04): item-by-item
ingestion of two related articles, processed a day apart, produced two
near-duplicate pages that later needed merging. Letting Wednesday–Friday
accumulate and ingesting as one batch synthesized the related material into a
single better page. The cost is a wiki that lags a few days.

The positions trade freshness against synthesis quality, and the line between
them is unknown. What would resolve this: a controlled comparison — one week
of immediate ingestion, one week of batching, judged by the following
[lint](/practices/weekly-lint-cadence.md) pass's duplicate and
[drift](/failure-modes/taxonomy-drift.md) findings.
