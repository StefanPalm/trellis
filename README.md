# trellis

**A trellis is a structure you build once so that something living can grow
along it.** This repo is that structure for your personal knowledge: three
agent skills that let Claude build, maintain, and grow markdown knowledge
wikis for you — one wiki per context, fully isolated, fully shareable.

You drop raw material in an inbox (notes, articles, meeting transcripts,
half-thoughts). The agent compiles it into a curated, interlinked wiki. A
scheduled lint pass keeps the wiki healthy and tells you what to feed it next.
You do the judgment; the agent does the filing.

Built on three open foundations:

- Andrej Karpathy's **llm-wiki** pattern — the agent-compiled personal wiki
- Google's **Open Knowledge Format (OKF)** — the on-disk format, so every wiki
  is a portable, standard knowledge bundle
- The **Agent Skills specification** (agentskills.io) — the packaging, so the
  skills work in Claude Cowork, Claude Code, and anything else that speaks
  skills

## Getting started (Columbus colleagues, 10 minutes)

You need Claude Desktop with Cowork. No coding required.

1. **Get the skills.** Clone this repo, or download it as a zip
   (green "Code" button → Download ZIP) and unpack it anywhere.
2. **Install the skills in Cowork.** Add the three folders under `skills/`
   (`wiki-init`, `wiki-ingest`, `wiki-lint`) to your Cowork skills.
3. **Create your knowledge home.** Make an empty folder on your disk, e.g.
   `Knowledge/`, and point a Cowork project at it. This folder will hold all
   your wikis.
4. **Create your first wiki.** In the project, say:
   *"Set up a new wiki for [subject]."* The agent will interview you briefly
   about the wiki's purpose, propose a starting topic structure, and scaffold
   everything.
5. **Feed it.** Drop a few files into the wiki's `inbox/` folder, then say:
   *"Process the inbox."*
6. **Grow it.** Once a week (or on a schedule), say: *"Lint the wiki."* You
   get a health report and, more importantly, concrete suggestions for what
   the wiki should learn next.

Start with a small, low-stakes wiki to get a feel for it before pointing it at
anything important.

## The three skills

| Skill | What it does | How you run it |
|---|---|---|
| `wiki-init` | Interviews you about purpose, proposes a topic taxonomy, scaffolds a new wiki | On demand |
| `wiki-ingest` | Compiles everything in a wiki's inbox into interlinked concept pages, archives the sources | On demand or scheduled |
| `wiki-lint` | Health and growth pass: conformance, staleness, contradictions, duplicates, gaps, expansion proposals | Scheduled |

## What a wiki looks like on disk

```
Knowledge/                  <- your Cowork project folder
├── dynamics-pricing/       <- one wiki
│   ├── AGENTS.md           <- the wiki's constitution: purpose, topics, rules
│   ├── inbox/              <- drop raw material here
│   ├── archive/            <- processed sources, kept for provenance
│   └── wiki/               <- the knowledge itself (an OKF bundle)
│       ├── index.md        <- entry point — agents and humans start here
│       ├── log.md          <- record of every change and proposal
│       ├── topics.md       <- the topic map
│       └── <topic>/...     <- one markdown page per concept
├── golf/                   <- another wiki, fully isolated from the first
└── ...
```

Everything is plain markdown. No database, no app, no lock-in. You can read,
edit, and grep your knowledge with anything.

## Design principles worth knowing

**Isolation is a guarantee.** Wikis never reference each other. Client A's
context can never leak into client B's wiki, because the skills are forbidden
from crossing wiki boundaries. This is why you make one wiki per context
rather than one big one.

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

The wiki folder is the unit of sharing. Hand a colleague the folder and they
get the knowledge, the topic map, the provenance, and the AGENTS.md that lets
*their* agent keep growing it. Because it's a standard OKF bundle, it also
works with any other OKF-aware tooling.

## A note on client material

The system keeps contexts separate by design, but the usual rules apply: only
put client material in a wiki if you're allowed to store it locally, and treat
a wiki containing client content with the same care as any other client file.

## Customizing

Each wiki's `AGENTS.md` is authoritative for that wiki — you can tighten
naming rules, extend the frontmatter, or grant the agent specific autonomy
there without touching this repo. The template lives in
`skills/wiki-init/references/agents-template.md`.

Feedback, improvements, and new skills welcome — open an issue or a PR.

---

*Maintained by Stefan Palm, Group AI. Free to use and adapt within Columbus.*
