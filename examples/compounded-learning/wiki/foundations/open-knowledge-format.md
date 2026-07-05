---
type: concept
title: Open Knowledge Format
description: The markdown bundle format that makes each wiki portable beyond the agent that wrote it.
tags: [foundations]
created: 2026-07-02
updated: 2026-07-02
status: provisional
sources:
  - ../archive/2026-07-02--llm-wiki-reading-notes.md
---

# Open Knowledge Format

Google's OKF (v0.1) defines a knowledge bundle as a directory of markdown:
every non-reserved page carries YAML frontmatter with a required `type`;
`index.md` (the map) and `log.md` (the newest-first change record) are
reserved files; links are recommended absolute from the bundle root.

Its design bet is **permissiveness**: consumers must tolerate unknown types,
unrecognized frontmatter keys, and broken links rather than reject a bundle.
That is what allows producer extensions — this wiki's `status` and `sources`
fields, for instance — without forking the format.

Why it matters for compounded learning: the
[llm-wiki pattern](/foundations/llm-wiki-pattern.md) describes behavior, not
storage. Storing the wiki as an OKF bundle means the knowledge outlives any
particular agent or tool — hand the folder to a colleague or a different
OKF-aware system and it remains a readable, growable wiki. Portability is
part of what makes the accumulated knowledge an asset rather than an export
problem.
