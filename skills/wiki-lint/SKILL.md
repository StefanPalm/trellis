---
name: wiki-lint
description: Health and growth pass over a knowledge wiki — verify OKF conformance, find staleness, orphan pages, contradictions, duplicate or drifting topics, and coverage gaps, then propose concrete expansions. Use whenever the user asks to lint, check, audit, review, clean up, or improve a wiki or knowledge base, asks "how healthy is my wiki", or wants suggestions for what to add next. Designed to be run on a schedule (e.g. weekly). Read-mostly — writes only a report page and log entries, never rewrites or deletes concept pages.
license: MIT
metadata:
  version: "0.2"
  author: stefan-palm
---

# wiki-lint

The maintenance and growth engine. Half the value of this system lives here:
the wiki that is only ever appended to decays into a junk drawer; the wiki
that is linted compounds.

## Step 0: Orient

1. Identify the target wiki (named by user, or ask; if scheduled with a named
   wiki, use it).
2. **Read the wiki's `AGENTS.md` in full — it is authoritative.** Check its
   Autonomy section: it defines the only actions you may take beyond
   reporting.
3. Read everything under `wiki/`. Lint is a whole-bundle activity; sampling
   defeats the purpose.
4. Never read or write outside the target wiki's folder.

## The passes

Run all of these; report only what you find. An empty section is a finding too.

**1. Conformance.** Every non-reserved file has valid frontmatter with
required `type`. `index.md` and `log.md` are OKF-reserved: the root index
carries only `okf_version` frontmatter, the log carries none and runs
newest-first under `## YYYY-MM-DD` headings. Tags reference real topics;
`created`/`updated` present on concept pages; in-body links are absolute from
the bundle root (start with `/`) and resolve; `index.md` actually maps what
exists.

**2. Integrity.** Orphan pages (nothing links to them, index doesn't list
them); dead links; pages whose first tag doesn't match their location;
`intake.md` files that reference pages that no longer match.

**3. Taxonomy drift.** Near-duplicate topics or pages under different
spellings, cases, or synonyms; topics that never grew past one page (should be
demoted to pages); topics silently absorbing material the charter never
anticipated (should be split). Propose merges/splits with the exact page moves
involved.

**4. Epistemic health.** `contested` pages that new material may have since
resolved; `provisional` claims that now have independent corroboration and
deserve promotion; pages whose `updated` date is old *and* whose subject
plausibly moves fast — flag as possibly stale, with a note on what to
re-verify. Do not treat age alone as staleness; stable knowledge is allowed
to be old.

**5. Contradiction sweep.** Claims across different pages that conflict but
were never marked contested because they arrived in different batches. This
pass catches what ingest structurally cannot.

**6. Coverage and growth.** This is the expansion half:

- Gaps: concepts referenced repeatedly but having no page; topics thin
  relative to their weight in the purpose.
- Questions: 3–7 concrete questions the wiki cannot currently answer but its
  purpose says it should. Make them specific enough that answering one is a
  single ingest batch.
- Leads: kinds of sources that would strengthen weak areas. If web search is
  available and the wiki's purpose covers fast-moving ground, you may check
  whether flagged-stale claims have in fact been superseded, and cite what
  you find in the report — but the finding goes in the report, not into
  concept pages.

## Output

1. Write `wiki/reports/YYYY-MM-DD-lint.md` with `type: report` frontmatter,
   sections matching the passes above, ordered by severity. Every finding
   must be actionable: name the file, name the fix. Lint reports are
   knowledge too — they compound, and the next lint run reads the previous
   report to check what was acted on.
2. Add a log entry under today's `## YYYY-MM-DD` heading at the top of
   `wiki/log.md` (OKF logs are newest-first): counts per pass, top three
   recommendations.
3. Apply autonomous fixes **only** if the wiki's Autonomy section explicitly
   grants them, and log each one individually.
4. Tell the user the top findings in a short prose summary, leading with the
   growth proposals — the point of lint is a better wiki next month, not a
   clean report today.

## Hard rules

- Never delete anything. Never rewrite a concept page. Flag and propose.
- Never write to the inbox or archive. Reading the archive is allowed (intake
  records are lint input); modifying it is not.
- One wiki per run; total isolation between wikis.
- If the previous lint report's top findings were ignored, say so once,
  plainly, without nagging.
