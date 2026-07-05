# The practice of compounded learning

The skills in this repo are tools. The thing worth developing is the practice
they enable: **compounded learning** — arranging your intake of information so
that each thing you capture makes everything you've already captured more
useful, instead of piling up behind it.

## Why notes don't compound by default

Most knowledge work is write-only. You take notes in a meeting, highlight an
article, paste a thought into a doc — and never touch any of it again. The
notes don't get worse; they just never get *better*. There is no mechanism
that connects Tuesday's note to March's, notices they contradict each other,
or tells you what's missing. Interest never accrues.

An agent-maintained wiki adds the missing mechanisms. Compounding comes from
four moves, each of which the agent does for you but you have to trigger:

## The loop

```
capture ──▶ ingest ──▶ lint ──▶ feed ──▶ (back to capture)
                         ▲
   ask ──────────────────┘  (gaps become new inbox material)
```

1. **Capture** — drop raw material into the wiki's `inbox/`. Zero friction is
   the point: half-thoughts, transcripts, links, screenshots-worth-of-text.
   Don't format, don't sort, don't decide where it goes. That's the agent's
   job.
2. **Ingest** — run `wiki-ingest`. Raw material becomes synthesized,
   interlinked concept pages; sources move to the archive with provenance
   records. This is where a note stops being a note and joins a structure.
3. **Lint** — run `wiki-lint` on a schedule. It keeps the structure healthy
   (duplicates, drift, contradictions) and — the growth half — hands you
   concrete questions the wiki can't answer yet.
4. **Feed** — treat the lint report as a reading list. The 3–7 open questions
   it produces tell you what to capture next. This closes the loop: the wiki
   now directs your learning instead of just recording it.
5. **Ask** — use `wiki-ask` whenever you'd otherwise search your memory or
   the web for something the wiki should know. Every question it can't answer
   becomes a gap note in the inbox. Using the wiki grows the wiki.

## Cadences that work

- **Capture: daily, under 30 seconds.** If capturing takes longer than
  dragging a file or pasting text, you'll stop doing it. Never organize the
  inbox — an organized inbox is wasted effort the agent will redo anyway.
- **Ingest: when a handful of items have accumulated,** or on a schedule.
  Batches synthesize better than single items, because related material gets
  merged in one pass instead of serially.
- **Lint: weekly, scheduled.** This is the habit that separates a compounding
  wiki from a junk drawer, and the one most tempting to skip because nothing
  visibly breaks when you do.
- **Feed: same sitting as reading the lint report.** Pick one open question,
  find one source that answers it, drop it in the inbox. One question per
  week is a fine pace; the point is the loop turning, not the volume.

## What compounding looks like

- **Week 1** — a scaffolded wiki, one or two ingests. It feels like a slightly
  fancy filing system. That's normal; nothing has compounded yet.
- **Month 1** — first `contested` page (two sources disagreeing is a feature:
  the wiki caught what your memory wouldn't have), first taxonomy proposal,
  first lint question that genuinely surprises you.
- **Quarter 1** — `wiki-ask` answers questions with sources you'd forgotten
  you had. The lint report reads like a curriculum. Handing a colleague the
  folder transfers months of context in one gesture.

## Failure modes

- **The junk drawer.** Ingesting without ever linting. Pages accumulate,
  duplicates creep in, and after a while you stop trusting the wiki — at
  which point it's dead. Lint weekly; the schedule matters more than the day.
- **One big wiki.** "My knowledge" is not a context. Purpose-per-wiki is what
  makes taxonomies coherent and sharing safe. When in doubt, split.
- **Taxonomy sprawl.** Accepting every new topic the material suggests. Let
  lint's merge/demote proposals do their work; a topic that never grew past
  one page was a page all along.
- **Hoarding in the inbox.** Capturing forever without ingesting. The inbox
  is a staging area, not storage — nothing in it is linked, deduplicated, or
  askable.
- **Treating the lint report as a grade.** The report's point is not a clean
  bill of health; it's the growth proposals. A report with zero findings and
  zero questions means the wiki has stopped learning, which is the worst
  finding of all.

## Scheduling the loop

The loop compounds only if lint actually runs, so put it on a schedule rather
than on willpower.

- **Claude Code**: ask it to schedule the task for you — e.g. *"Every Monday
  morning, run wiki-lint on the wiki at ~/Knowledge/golf"* — or use plain
  cron with headless mode:

  ```
  0 9 * * 1  claude -p "Lint the wiki at ~/Knowledge/golf and leave the report in the wiki"
  ```

  (Requires the skills installed at user level, `~/.claude/skills/`.)
- **Claude Desktop (Cowork)**: create a scheduled task in the project that
  contains your knowledge folder, with the same one-line instruction.
- **Any runtime**: the skills are stateless — anything that can invoke your
  agent on a timer with "lint wiki X" works.

Ingest can be scheduled the same way (it exits cleanly on an empty inbox), but
many people prefer running it by hand — watching what the wiki learned from
your week is half the fun.

## The meta-move

The skill you are really practicing is *delegating structure while keeping
judgment*: you decide what enters the system and what to believe; the agent
owns filing, linking, format discipline, and remembering what's missing. That
division of labor is the general shape of working well with agents, and a
personal wiki is a low-stakes place to develop it.

Dogfood it: keep a wiki about your own compounded-learning practice. The
worked example in
[examples/compounded-learning/](examples/compounded-learning/) is exactly
that — copy its starter material from
[examples/starter-inbox/](examples/starter-inbox/) and grow your own.
