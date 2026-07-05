---
name: wiki-init
description: Scaffold a new personal knowledge wiki as a self-contained OKF (Open Knowledge Format) bundle with an agent-owned topic taxonomy. Use whenever the user wants to create, set up, start, or bootstrap a new wiki, knowledge base, second brain, or LLM-wiki, or says things like "new wiki for X", "set up a knowledge base about Y", or "initialize a wiki". Also use when the user drops material for a subject that has no existing wiki and asks where it should live.
license: MIT
metadata:
  version: "0.2"
  author: stefan-palm
---

# wiki-init

Creates one new wiki inside the knowledge root. The knowledge root is the
current project folder unless the user says otherwise. Each wiki is fully
self-contained and must never reference content in any other wiki.

## Step 1: Interview, briefly

Ask only what you cannot infer. You need:

1. **Name** — short, lowercase, hyphenated; becomes the folder name.
2. **Purpose** — one or two sentences: what questions should this wiki be able
   to answer, and for whom? Push for a real purpose, not a subject label.
   "Everything about golf" is weak; "improve my coaching decisions and track
   what actually changes my game" is a charter you can derive topics from.
3. **Sensitivity** — is this wiki ever going to be shared? (Affects tone of
   provenance notes, nothing structural.)

If the user has already given you this in conversation, do not re-ask. Confirm
your understanding in one sentence and proceed.

## Step 2: Propose the starting taxonomy — this is your job, not the user's

Derive 4–8 starting topics from the purpose. Rules of thumb:

- Topics are the *dimensions along which knowledge will accumulate*, not a table
  of contents of what exists today. Ask: when new material arrives in six
  months, which buckets will it want to fall into?
- Prefer topics that will each plausibly hold 5+ concept pages. If a topic would
  only ever hold one page, it is a page, not a topic.
- Name topics in lowercase-hyphenated singular-noun form (`pricing-models`, not
  `Pricing Models` or `pricings`). Naming discipline now prevents taxonomy
  drift later.
- Include one topic that captures the wiki's own evolution when the purpose is
  open-ended (e.g. `open-questions`). Lint will feed it.

Present the taxonomy to the user with a one-line rationale per topic. Accept
their edits, but you own the proposal. If they say "you decide", decide.

## Step 3: Scaffold

Create this structure inside the knowledge root:

```
<wiki-name>/
├── AGENTS.md
├── inbox/
│   └── README.md        (one line: "Drop raw material here. Run wiki-ingest to process.")
├── archive/
└── wiki/
    ├── index.md
    ├── log.md
    └── topics.md
```

- **AGENTS.md**: copy `references/agents-template.md` from this skill and fill
  every `{{placeholder}}`: name, purpose, the topic charter with rationales,
  today's date. The template also contains the OKF format rules and the
  behavioral contract for ingest and lint — do not remove or weaken those
  sections.
- **wiki/index.md**: the bundle-root index, reserved by OKF. Its only
  frontmatter is `okf_version: "0.1"` — the root index is the one place OKF
  permits index frontmatter. Body: the purpose, a "Start here" note for
  agents, and a topic list linking to `topics.md`. Keep it honest — an empty
  wiki's index says the wiki is empty.
- **wiki/topics.md**: `type: overview`. The taxonomy as a readable page, one
  section per topic with its rationale. This page is part of the shareable
  knowledge: whoever receives the bundle gets the map, not just the territory.
- **wiki/log.md**: reserved by OKF; no frontmatter. A `# Log` title, then one
  `## YYYY-MM-DD` heading per day with entries newest-first, each opening with
  a bold convention word (**Creation**, **Update**, **Proposal**, **Report**).
  First entry: **Creation** — wiki created, purpose, initial taxonomy, by whom.

Do not create empty topic subdirectories. Directories are created by
wiki-ingest the first time a topic receives a page; an empty folder is a lie
about what the wiki contains.

## Step 4: Hand off

Tell the user the wiki is ready, where to drop material (the inbox), and that
`wiki-ingest` processes it and `wiki-lint` keeps it healthy and suggests growth.
If they already pasted material in this conversation, offer to run ingest on it
immediately.

## Hard rules

- Never write outside the new wiki's folder.
- Never copy or reference content from other wikis in the knowledge root, even
  as examples. Isolation is the product.
- If a wiki with the same name exists, stop and ask; never overwrite.
