# skim notes — OKF + agent skills

two specs skimmed today, both relevant to the agent-maintained-wiki idea:

**open knowledge format (OKF v0.1, google)** — markdown bundles as the unit
of knowledge. every page gets yaml frontmatter with a required `type`;
`index.md` and `log.md` are reserved (map + change record); everything else is
producer's choice, and consumers are required to be permissive — unknown
fields and even broken links must be tolerated, not rejected. the point is
portability: the bundle outlives whatever tool wrote it. that's the answer to
my lock-in worry — if the wiki is an OKF bundle, switching agents or handing
the folder to a colleague costs nothing.

**agent skills (agentskills.io)** — a skill is just a folder with a SKILL.md:
name + description in frontmatter, instructions in the body, optional
scripts/references/assets. progressive disclosure: the agent only loads the
description until the skill is actually needed. so a whole wiki-maintenance
system can ship as a few folders anyone can drop into their agent. no
install, no runtime.

takeaway: persistent memory (wiki) + portable format (OKF) + portable
behavior (skills) seems like a complete stack for compounding knowledge.
worth testing whether it holds up for a month.
