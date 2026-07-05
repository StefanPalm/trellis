# trellis

**A trellis is a structure you build once so that something living can grow
along it.** This repo is that structure for your knowledge: four agent skills
that let an AI agent build, maintain, grow, and answer from markdown knowledge
wikis — one wiki per context, fully isolated, fully shareable.

The practice this enables is **compounded learning**. Most notes are written
once and never work again. Here, you drop raw material in an inbox (notes,
articles, transcripts, half-thoughts); the agent compiles it into a curated,
interlinked wiki; a scheduled lint pass keeps the wiki healthy and tells you
what to feed it next; and asking the wiki questions turns its gaps into new
inbox material. Every pass through the loop makes the next one more valuable.
You do the judgment; the agent does the filing. [PRACTICE.md](PRACTICE.md)
describes the practice itself — cadences, milestones, and failure modes.

Built on three open foundations:

- Andrej Karpathy's **llm-wiki** pattern — the agent-compiled personal wiki
- Google's **Open Knowledge Format (OKF)** — the on-disk format, so every wiki
  is a portable, standard knowledge bundle
- The **Agent Skills specification** ([agentskills.io](https://agentskills.io))
  — the packaging, so the skills work in Claude Code, Claude Cowork, and
  anything else that speaks skills

## Getting started (10 minutes)

Works with any agent that supports Agent Skills. No coding required.

1. **Get the skills.** Clone this repo, or download it as a zip
   (green "Code" button → Download ZIP) and unpack it anywhere.
2. **Install the skills** — the four folders under `skills/`:
   - *Claude Code*: copy them into `~/.claude/skills/` (available everywhere)
     or into a project's `.claude/skills/`.
   - *Claude Desktop (Cowork)*: add the four folders to your Cowork skills.
   - *Other runtimes*: any agent that implements the Agent Skills spec;
     install per its documentation.
3. **Create your knowledge home.** Make an empty folder on your disk, e.g.
   `Knowledge/`, and point your agent's project/workspace at it. This folder
   will hold all your wikis.
4. **Create your first wiki.** Say: *"Set up a new wiki for [subject]."* The
   agent will interview you briefly about the wiki's purpose, propose a
   starting topic structure, and scaffold everything.
5. **Feed it.** Drop a few files into the wiki's `inbox/` folder, then say:
   *"Process the inbox."* No material of your own yet? Copy the files from
   [examples/starter-inbox/](examples/starter-inbox/) into the inbox and
   watch your first ingest run on those.
6. **Grow it.** Once a week (or on a schedule — see
   [PRACTICE.md](PRACTICE.md)), say: *"Lint the wiki."* You get a health
   report and, more importantly, concrete suggestions for what the wiki
   should learn next.
7. **Use it.** Ask it things: *"What does my wiki say about X?"* Answers cite
   pages; questions the wiki can't answer land in the inbox as gaps to fill.

Want to see the destination before you start? Browse
[examples/compounded-learning/](examples/compounded-learning/) — a small,
complete wiki built and maintained with these skills.

Start with a small, low-stakes wiki to get a feel for it before pointing it at
anything important.

## The four skills

| Skill | What it does | How you run it |
|---|---|---|
| `wiki-init` | Interviews you about purpose, proposes a topic taxonomy, scaffolds a new wiki | On demand |
| `wiki-ingest` | Compiles everything in a wiki's inbox into interlinked concept pages, archives the sources | On demand or scheduled |
| `wiki-lint` | Health and growth pass: conformance, staleness, contradictions, duplicates, gaps, expansion proposals | Scheduled |
| `wiki-ask` | Answers questions from the wiki with citations; unanswered questions become inbox gap notes | On demand |

## What a wiki looks like on disk

```
Knowledge/                  <- your project folder
├── dynamics-pricing/       <- one wiki
│   ├── AGENTS.md           <- the wiki's constitution: purpose, topics, rules
│   ├── inbox/              <- drop raw material here
│   ├── archive/            <- processed sources, kept for provenance
│   └── wiki/               <- the knowledge itself (an OKF bundle)
│       ├── index.md        <- entry point — agents and humans start here
│       ├── log.md          <- record of every change and proposal
│       ├── topics.md       <- the topic map
│       ├── reports/        <- dated lint reports
│       └── <topic>/...     <- one markdown page per concept
├── golf/                   <- another wiki, fully isolated from the first
└── ...
```

Everything is plain markdown. No database, no app, no lock-in. You can read,
edit, and grep your knowledge with anything.

## Design principles worth knowing

**Isolation is a guarantee.** Wikis never reference each other. Context A can
never leak into context B's wiki, because the skills are forbidden from
crossing wiki boundaries. This is why you make one wiki per context rather
than one big one.

**The taxonomy is agent-owned.** The agent proposes the topic structure and
maintains it as your knowledge evolves. Changes are staged as proposals in the
wiki's log; nothing is restructured without your acceptance (unless you
explicitly grant autonomy in that wiki's AGENTS.md).

**Contradictions are surfaced, not smoothed.** When new material conflicts
with what the wiki believes, the page states both positions and is marked
`contested`. The agent never silently picks a winner.

**Provenance everywhere.** Every page lists the archived sources it came from,
and carries a status (`established` / `provisional` / `contested`) so you know
how much to trust it.

**Lint never destroys.** It flags, proposes, and reports. Deleting and
rewriting is human work.

## Sharing a wiki

The wiki folder is the unit of sharing. Hand someone the folder and they get
the knowledge, the topic map, the provenance, and the AGENTS.md that lets
*their* agent keep growing it. Because the `wiki/` directory is a standard OKF
bundle, it also works with any other OKF-aware tooling.

## A note on sensitive material

The system keeps contexts separate by design, but the usual rules apply: only
put confidential or client material in a wiki if you're allowed to store it
locally, and treat a wiki containing such content with the same care as any
other sensitive file.

## Customizing

Each wiki's `AGENTS.md` is authoritative for that wiki — you can tighten
naming rules, extend the frontmatter, or grant the agent specific autonomy
there without touching this repo. The template lives in
[skills/wiki-init/references/agents-template.md](skills/wiki-init/references/agents-template.md).

## Contributing

Feedback, improvements, and new skills welcome — open an issue or a PR. Run
[`skills-ref validate`](https://github.com/agentskills/agentskills/tree/main/skills-ref)
on any skill you touch.

## License

[MIT](LICENSE). Created by Stefan Palm.
