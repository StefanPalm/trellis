# quick notes — the llm-wiki idea

saw karpathy's llm-wiki idea going around again. the gist as i understand it:
talking to an LLM produces good thinking that then just evaporates — the chat
log is write-only memory. instead, have the agent maintain a wiki. every
conversation, every article you feed it, updates a persistent set of
interlinked pages. the chat is the interface; the wiki is the memory.

what clicks for me: the division of labor. i keep the judgment (what goes in,
what to believe), the agent does the filing, linking, deduplication. filing is
exactly the part i always abandon in every note system i've tried.

open question for myself: does this actually compound, or is it just tidier
hoarding? i think the difference has to be maintenance — something has to
re-read the wiki and tell me what's stale, contradictory, or missing.
otherwise it's the same graveyard with better formatting.
