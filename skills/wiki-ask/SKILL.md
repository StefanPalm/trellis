---
name: wiki-ask
description: Answer a question from a specific knowledge wiki, citing concept pages and respecting each page's status (established, provisional, contested), then capture what the wiki could not answer as a gap note in its inbox so the wiki grows from being used. Use whenever the user asks what a wiki knows, says, or believes about something — "ask my golf wiki", "what does the pricing wiki say about churn", "according to my knowledge base" — or asks a question in a project whose wikis plausibly cover it. Answers come from the wiki's own pages, clearly separated from anything the model adds.
license: MIT
metadata:
  version: "0.2"
  author: stefan-palm
---

# wiki-ask

The read side of the loop. A wiki that is only written to never proves its
worth; a wiki that is asked reveals exactly where it is thin. This skill turns
those misses into inbox material — using the wiki is how the wiki grows.

## Step 0: Orient

1. Identify the target wiki. If the user named it, use it; if only one wiki in
   the knowledge root plausibly covers the question, use it and say so;
   otherwise ask. One wiki per run — never blend answers across wikis.
2. **Read the wiki's `AGENTS.md` in full. It is authoritative.**
3. Read `wiki/index.md` and `wiki/topics.md` to locate the relevant topics.

## Step 1: Retrieve

Follow the map, don't scan the disk: index → topics → the concept pages that
bear on the question, read in full, following their links one hop when a
linked page is clearly relevant. For a narrow question, a handful of pages is
right; reading the whole bundle is a lint behavior, not an ask behavior.

## Step 2: Answer

Write a synthesized answer from what the pages actually say, with the page
paths cited inline (e.g. `wiki/practices/inbox-capture.md`). Status governs
tone:

- `established` — state it plainly.
- `provisional` — state it, flagged as single-sourced and unconfirmed.
- `contested` — present both positions with their sources. Never pick a
  winner the page didn't pick.

If the wiki only partially answers, say precisely which part is covered and
which is not. If the wiki is silent, say so plainly. You may add what you know
from general knowledge **only** in a clearly separated section ("Beyond the
wiki: …") — never blended into the wiki's answer, because the user is asking
what *their* wiki knows.

## Step 3: Close the loop

For each real gap the question exposed — unanswered, partially answered, or
answered only provisionally — write one gap note into the wiki's inbox as
`YYYY-MM-DD--question--<slug>.md`: the question as asked, what the wiki had,
what was missing, and why it matters given the wiki's purpose. The next ingest
files it; the next lint counts it. Tell the user you did this.

Skip the gap note when the question was outside the wiki's charter (say so
instead — that's a signal about scope, not a gap) or the user asked you not to.

## Hard rules

- Never write under `wiki/` or `archive/`. The only permitted write is a new
  gap-note file in `inbox/`.
- One wiki per run; total isolation between wikis.
- Never present model knowledge as wiki content. Cited means it is on a page.
