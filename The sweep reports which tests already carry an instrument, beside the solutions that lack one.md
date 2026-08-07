---
type: Solution
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The instrument field fits in the sweep without displacing the work it reports]]

**The idea.** `ost_next_work` stops reporting only which solutions lack an instrument and starts reporting, for each test beneath them, whether it has one and what it is. The pass can then tell attachment from replacement before it composes the call.

**Why this shape.** The observed failure was not a bad decision, it was a decision made without the input. The pass picked a test by title, had no way to learn that title already carried a command, and found out from the success message. Nothing about the tool was wrong; the surface simply had no read that answered the question, and `ost_read_tree` returns titles, layers, statuses, tags and links but not instrument fields.

This is the cheapest of the three candidates and the only one that changes no write path, so nothing that currently works can break.

**How it compares to its siblings.**
- "Attaching an instrument to a test that has one is refused unless replacement is declared" stops the write instead of informing it. Stronger, and it costs a round trip every time the repair is legitimate.
- "Replacing an instrument preserves the old command and re-arms the permit if it is restored" accepts that the mistake will happen and attacks what it costs. It is the only one that helps the case that already occurred.

**Where it fails, stated so it can be judged.** Information is not a guard. A pass working a 62-item backlog under a token budget can be handed the field and not read it — and the failure mode is exactly the same, with the surface now able to say it was told. That risk is real enough that this should probably ship alongside one of its siblings rather than instead of one.

There is also a budget cost that is not trivial here: the sweep already truncates four lists at 25, and adding a per-test field to a report that names 337 tests makes the response bigger in the place it is already being cut.

**Cost.** A field in an existing response. Smallest of the three.

⚠️ Unvalidated. Agent-ideated from a first-party error made on this surface.
