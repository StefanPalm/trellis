---
name: wiki-ingest
description: Process raw material from a wiki's inbox into synthesized, interlinked OKF concept pages, then archive the sources. Use whenever the user asks to process, ingest, add, or file new content into a wiki or knowledge base, says "process the inbox", "add this to my X wiki", or drops files/links/notes destined for a wiki. Also the skill to run on a schedule for automatic inbox processing. Safe to run when the inbox is empty (it reports and exits).
---

# wiki-ingest

Compiles raw inputs into knowledge. Operates on exactly one wiki per run.

## Step 0: Orient

1. Identify the target wiki. If the user named it, use it. If not and only one
   wiki in the knowledge root has a non-empty inbox, use that one and say so.
   Otherwise ask.
2. **Read the wiki's `AGENTS.md` in full. It is authoritative** for format,
   taxonomy, naming, and what you are allowed to do. Where this skill and that
   file differ, the wiki's AGENTS.md wins.
3. Read `wiki/index.md`, `wiki/topics.md`, and skim recent `wiki/log.md`
   entries so you know what already exists. Never ingest blind: the most
   common ingest failure is creating a near-duplicate of an existing page.
4. Never read or write outside the target wiki's folder. If inbox material
   references another wiki, note it in the log for the human; do not follow it.

If the inbox is empty, log nothing, tell the user, stop.

## Step 1: Plan the batch

List inbox items oldest-first. For each, skim and decide the extraction plan
before writing anything: which concepts it contains, which existing pages it
touches, whether anything fails to fit the topic charter. Handle related items
in the same batch together so they are synthesized once, not serially.

## Step 2: Extract and write

For each concept:

- **New page vs edit in place**: new page if it is a distinct concept that
  other pages would want to link to; edit if it is an attribute, example, or
  update of an existing concept. When in doubt, edit — page count is a cost,
  not a score.
- Write synthesized prose against the wiki's purpose, not a copy of the
  source. The source survives in the archive; the page is the understanding.
- Full frontmatter per the wiki's format rules, including `sources` (pointing
  into the archive) and `status`. New claims from a single source are
  `provisional`; they earn `established` when independent sources agree.
- **Contradictions**: if new material conflicts with an existing page, update
  the page to state both positions with their sources, set
  `status: contested`, and log it. Never silently overwrite the old claim,
  never silently discard the new one.
- Link densely. When the text mentions a concept that has a page, link it,
  bundle-relative.

## Step 3: When material doesn't fit the charter

You own topic health, but not unilaterally:

- If a batch produces pages that belong to no existing topic, place them in
  the closest topic, then write a **taxonomy proposal** in `wiki/log.md`:
  proposed topic, rationale, pages that would move. Do not restructure unless
  the wiki's Autonomy section explicitly permits it.
- If you notice the purpose itself drifting (repeated material the charter
  never anticipated), say so in the log in one honest paragraph. This signal
  is the human's, not yours, to act on.

## Step 4: Close the batch

1. Move each processed file to `archive/` as `YYYY-MM-DD--<original-name>`,
   and write `<same-name>.intake.md` beside it: what was extracted, pages
   created/updated, anything skipped and why.
2. Update `wiki/index.md` (new pages appear on the map) and `wiki/topics.md`
   if page counts or emphasis shifted.
3. Append one log entry for the batch: date, items processed, pages
   created/updated, proposals raised.
4. Report to the user in a few sentences: what came in, what the wiki learned,
   any proposals awaiting their ruling.

## Hard rules

- One wiki per run; total isolation between wikis.
- Never delete inbox material without archiving it; never edit the archive.
- The wiki must be left conformant after every run: valid frontmatter, working
  links, updated index and log. If interrupted mid-batch, finish the current
  file's bookkeeping before stopping.
