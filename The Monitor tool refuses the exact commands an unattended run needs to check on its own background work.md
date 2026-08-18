---
type: Opportunity
source: 'TRANSCRIPT:0f28d01f-35fa-49f0-b085-89170e306ef8'
created: '2026-08-18'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[Monitor accepts a vetted until-loop primitive instead of raw shell polling]]

**The need (operator's voice, inferred from observed behavior):** "When I leave a long-running build or test polling to run in the background, I need to be able to check on it without a person present to approve each check — but the tool that watches background work keeps refusing the exact commands that would let it watch."

**What was observed:** Session `TRANSCRIPT:0f28d01f-35fa-49f0-b085-89170e306ef8` (2026-08-18) hit three separate Monitor refusals in one unattended firing: a `command_substitution`-containing command was rejected outright; a multi-part polling loop (`until pgrep ...; do :; done` chained with `grep`/`tail`) was refused with "the following parts require approval"; and a `tail` against a log file was blocked because Monitor may only read the ends of files inside the session's allowed working directories, while the log it needed sat under a different directory (`/Users/tanner/dev/OST-Agent` vs the session's `/Users/tanner/ost-agent-meta`). Session `TRANSCRIPT:0095203e-ab42-4179-a53e-a2d4d6dd6032` (2026-08-15) shows the same shape once: a Monitor call refused for containing `command_substitution`.

**Why it matters:** Monitor exists specifically so a run can wait on background work (a build, a test suite) without a human in the loop. When the commands that would naturally express "wait until this finishes, then show me the tail of the log" are the ones Monitor refuses — because they use command substitution, chain more than one operation, or read a file outside the session's own working directory — the run has no legitimate way to check on work it itself started, and falls back to blind retries or manual polling that costs a turn each time with nobody there to notice.

**Litmus test:** More than one way to address it — Monitor could accept a narrower vetted grammar for polling loops (an until/sleep primitive with no shell substitution); it could accept an explicit "read the tail of this file" primitive that doesn't route through `tail` and the working-directory restriction; it could allow the session to declare additional readable directories for the duration of a background wait; or the calling agent could be told up front which forms Monitor accepts, instead of discovering the boundary by refusal. Real trade-offs between them. Passes.

**Distinct from its neighbours:** this is not the same as "The unattended run is scoped for tools nobody granted it, and it finds out one denial at a time" — that opportunity is about entire tools/MCP servers being absent or permission-gated; this one is about a tool that IS available (Monitor) refusing specific command shapes it was actually asked to run, mid-task, for reasons unrelated to whether the tool itself is granted.

Evidence: observed behavior, agent's own unattended sessions. Grounds usability, not desirability.
