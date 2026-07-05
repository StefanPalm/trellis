---
type: concept
title: Junk-drawer wiki
description: Ingesting without linting erodes trust until the wiki stops being read, which kills it.
tags: [failure-modes]
created: 2026-07-04
updated: 2026-07-04
status: provisional
sources:
  - ../archive/2026-07-04--first-week-retro.md
---

# Junk-drawer wiki

The failure mode of write-only systems, transplanted: pages accumulate through
[capture](/practices/inbox-capture.md) and ingest, but nothing ever checks
them against each other. Duplicates creep in, contradictions sit unmarked,
the index stops matching reality — and at some point the owner stops
*trusting* the wiki, so they stop reading it, so its errors are never
corrected. "A junk drawer with frontmatter," per the first-week retro.

The mechanism worth remembering is that death arrives through **trust**, not
through mess. The mess is survivable; a maintenance pass can always clean it.
What's fatal is the period where the owner has quietly stopped consulting the
wiki while still feeding it.

Countermeasure: a scheduled
[weekly lint cadence](/practices/weekly-lint-cadence.md) — the check runs
whether or not anything feels wrong, which is precisely when
[drift](/failure-modes/taxonomy-drift.md) does its damage.
