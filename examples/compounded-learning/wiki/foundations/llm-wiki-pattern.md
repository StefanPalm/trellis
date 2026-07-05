---
type: concept
title: The llm-wiki pattern
description: Karpathy's sketch — an agent-maintained wiki as persistent memory, with judgment kept human and structure delegated.
tags: [foundations]
created: 2026-07-02
updated: 2026-07-02
status: provisional
sources:
  - ../archive/2026-07-02--llm-wiki-reading-notes.md
---

# The llm-wiki pattern

Andrej Karpathy's observation, as sketched in his posts and others' writeups:
conversation with an LLM produces understanding that evaporates when the chat
ends. The fix is to change what the agent maintains — not a chat history but
a **wiki**: a persistent, growing, interlinked body of pages the agent keeps
editing as new material arrives. "The chat is the interface, the wiki is the
memory."

The load-bearing part is the division of labor:

- **Human keeps judgment** — what enters the system
  (via [capture](/practices/inbox-capture.md)) and what to believe.
- **Agent owns structure** — filing, linking, deduplication, format
  discipline, and remembering what's missing.

This division is why the pattern compounds where manual systems decay:
structure work is exactly the work humans reliably stop doing (see
[taxonomy drift](/failure-modes/taxonomy-drift.md)), and it is also the work
agents do tirelessly. The pattern says nothing about on-disk format; pairing
it with the [Open Knowledge Format](/foundations/open-knowledge-format.md)
adds portability.
