---
type: Solution
source: 'agent-ideation:2026-09-02-unattended-sweep'
created: '2026-09-02'
evidence: assertion
killIf: >-
  On a hand-labelled sample of fifty errored Bash results drawn from this
  vault's own records, the automatic demotion disagrees with a person's reading
  on more than ten.
killBy: '2026-12-01'
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[An errored result's body keeps enough text to tell a command's own negative finding from a diagnosis of the command]]

**Variation dimension: automated-vs-manual — which half is mechanised. Position taken: the detection is fully automatic with nothing hand-maintained, and the half left deliberately manual is the verdict.**

No allow-list, no marker, no per-tool table — all three are things somebody has to keep current, and a stale table is worse than none because it looks maintained. Instead read the result body itself: a command that reports its own negative finding prints the finding and nothing else; a command that broke prints a diagnostic *about the command* — a shell name and a colon, a stack, a usage line, `command not found`. Where the body carries only the former, file the event as a new kind, `observation`, instead of `tool_error`.

**The manual half, and why it is the verdict rather than the detection.** The observation is not dropped. It is emitted, counted in the session summary and rendered in the record like every other kind, just under a name that does not claim something went wrong. So a human reading the channel can still see every one and overrule the classifier by hand, and a wrong demotion costs visibility rather than the evidence itself. That is the opposite trade from the sibling that trusts the caller, where a wrong mark deletes a genuine failure with nothing left to notice.

**Why this position and not another.** It is the only one of the three that reclassifies the corpus already on disk. The other two need something that was not recorded at the time — a marker the caller never wrote, or an exit code the transcript keeps only as prose — so both are prospective. This one runs over the 566 existing records unchanged, which is where the whole backlog is.

**Cheapest form.** `src/adapters/transcript.ts` already has the discriminator in embryo and pointing the wrong way: `ERROR_LINE` matches `/error|not found|no match|failed|…/i` and `errorDetail()` uses it to pick the *most* error-looking line to quote. Those words — `no match`, `not found`, `failed` — are exactly what a successful negative answer prints, so today the helper cannot tell the two apart and would call a clean grep miss the most diagnostic line in the body. The work is a second, narrower pattern for diagnoses-the-command (a `^(zsh|bash|sh):` prefix, `command not found`, `Traceback`, `usage:`) consulted before `ERROR_LINE`, and one branch on it in the `is_error` arm of `extractFriction`.

**What it deliberately does not do.** It says nothing about whether the caller wanted the negative answer — only about whether the tool broke. A search the agent ran in the wrong directory returns a clean, undiagnosed miss and demotes to an observation, even though it was a real navigation failure. This candidate accepts that and hands the case to the human census; the caller-declaration sibling is the only one of the three that could catch it, and only if the caller was honest.

**What it gives up, plainly.** It is a heuristic over prose, so it will be wrong, and the kill condition above puts a number on how wrong is too wrong. It also adds a new `FrictionKind`, which every downstream reader of the channel — the renderer, the counts in the session summary, anything filtering on kind — has to learn.

**What would make this the wrong pick.** If the bodies turn out not to carry the distinction at all — if the host truncates a Bash result to its exit code line before it reaches the transcript — there is nothing to read and this candidate is unbuildable, which is exactly what the assumption beneath it is aimed at.

**Honest note on how this was ideated.** All three candidates under this opportunity were composed in one context by one author. This unattended surface holds no grant to run independent parallel ideators, so the blindness the ruleset asks for was not available and their apparent distinctness should be discounted accordingly.

Unvalidated. Agent-ideated 2026-09-02; a human to review.
