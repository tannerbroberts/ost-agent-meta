---
type: Solution
source: 'agent-ideation:2026-09-02-unattended-sweep'
created: '2026-09-02'
evidence: assertion
killIf: >-
  No unattended firing's transcripts over a full month show the declaration
  attached to even one in five of the measurement commands that ran.
killBy: '2026-12-01'
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[The transcript keeps a channel the caller can mark a command in, and the harvester can still see it]]

**Variation dimension: who-does-the-work — who supplies the intent. Position taken: the calling session, at the moment of the call, and the classifier only reads.**

The harvester cannot recover intent after the fact, because by then all it has is an exit code and a body. The one party who knows whether a negative answer was the point is the session that issued the command, and it knows at the instant it composes it. So move the work upstream: the caller marks the call — in the Bash tool's own `description` field, which it already writes and which already travels in the transcript — and `extractFriction` reads that mark instead of inferring anything.

**Why this position and not another.** Its two siblings both leave the work with the classifier and differ only in how clever it gets. This one says the classifier should get less clever, not more, and that the cheapest place to know something is where it is already known. It is also the only one of the three that degrades gracefully as new tools appear: a command from a tool nobody anticipated is classified correctly the first time it runs, because the caller said so, whereas both siblings need their heuristic or their mapping extended.

**Cheapest form.** In `extractFriction`, keep the `description` from the `tool_use` block alongside the name and input in `toolById`, and when a matching `tool_result` arrives with `is_error === true`, suppress the `tool_error` if the description carries the agreed marker. No new event kind, no new file, one field threaded through a map that already exists.

**What it deliberately does not do.** It takes no view on whether the command genuinely failed. A session that marks a command and is then wrong about it gets a real failure silently dropped, and nothing downstream can tell. That is the price of trusting the caller, and it is the sharpest difference from the sibling that infers, which can never drop a genuine failure because it never trusts anybody.

**What it gives up, plainly.** It is retroactive to nothing. Every one of the 566 records already in the queue was written by sessions that had no marker to write, so this fixes the future and leaves the backlog exactly as it is — where both siblings, being read-time classifications, would reclassify the existing corpus. It also asks the agent to remember something on every call, and an instruction the agent must remember is the weakest mechanism this codebase has; the kill condition above is aimed squarely at that.

**What would make this the wrong pick.** If compliance is low — and this repository's own history of standing corrections re-issued across sessions suggests it might be — the channel gets a marker on the calls somebody remembered and no marker on the rest, which is worse than a uniform rule because the noise now looks curated.

**Honest note on how this was ideated.** All three candidates under this opportunity were composed in one context by one author. This unattended surface holds no grant to run independent parallel ideators, so the blindness the ruleset asks for was not available and their apparent distinctness should be discounted accordingly.

Unvalidated. Agent-ideated 2026-09-02; a human to review.
