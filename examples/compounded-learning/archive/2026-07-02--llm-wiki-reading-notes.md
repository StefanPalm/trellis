# reading notes — llm-wiki idea + formats (raw)

karpathy's llm-wiki sketch (from his posts + people's writeups): the problem
with chatting with an LLM is the output evaporates. instead have the agent
maintain a *wiki* — a persistent, growing, interlinked body of pages it keeps
editing as new stuff comes in. you feed it, it files. "the chat is the
interface, the wiki is the memory" is how someone summarized it.

key division of labor: human keeps judgment (what goes in, what to believe),
agent does structure (filing, linking, dedup, format).

capture thought: this only works if putting stuff in is basically free. the
moment i have to decide where a note goes, i won't take the note. inbox
pattern — dump now, let the agent sort at processing time.

processing thought: probably ingest each item the moment it lands? then the
wiki is always current and the inbox never rots. feels right, not sure.

format skim — google's OKF (open knowledge format, v0.1): markdown bundles,
every page has yaml frontmatter with a required `type`, reserved index.md and
log.md files, consumers must be permissive (tolerate unknown fields, broken
links). point is portability: a wiki that's an OKF bundle can be read by any
OKF-aware tool, not just the agent that wrote it.

also skimmed agentskills.io — skills are just folders with a SKILL.md, name +
description frontmatter, progressive disclosure. so the whole wiki system can
ship as a few skill folders. neat.

naming worry: saw someone's note graveyard with "Meetings", "meeting-notes",
"mtg" as three separate folders. whatever system this becomes needs naming
discipline from day one or the taxonomy silently forks.
