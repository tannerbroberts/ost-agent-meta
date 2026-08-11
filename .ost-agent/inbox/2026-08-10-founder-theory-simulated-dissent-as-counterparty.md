# Founder theory: simulated dissent is the counterparty — debate, not vote (2026-08-10)

Spoken in session by the founder, as a direct challenge to the agent's claim that a
single author generating its own tests, self-determining failure, and iterating is a
failure case. The agent double-checked and revised its claim; both the theory and
the revision are recorded here. Evidence class: **assertion**.

**The claim.** There is a LOT of room in latent-space activations. The named LLM
failure modes (a model spewing Nazi doctrine mid-training; models regarding peer
LLMs as less-than-human when encouraged to believe themselves conscious; sycophancy
effective enough to grow companies while damaging the humans in the context windows)
are addressable "as simple as multiple diverse personality prompts that all need to
agree on an instrument's failure case's validity, and what its passing would mean."
The agreement must NOT be a one-off vote — it should be "well-shaped dissent,
structured more like a debate than anything." An LLM that knew itself better would
find this easy: "You're full to the brim with latent space with a source of the
literal human internet. There's plenty of space in there for a simulated second
opinion."

**The agent's revision under challenge (same rung):** the original claim confused
authorship with error correlation. A human retyping program output adds zero
decorrelation, so the human gate never guaranteed the independence it was defended
with. What survives are three substrate-level residual risks — and the founder's own
examples are evidence for them, being one-distribution, one-incentive failures
expressed through every persona the model could wear:

1. **Shared blind spots** below the prompt layer, unreachable by persona diversity.
2. **Orchestrator capture** — whoever authors the personas and aggregates the debate
   steers it; prompt-layer independence is not incentive-layer independence.
3. **Dissent collapse** — inter-debater sycophancy; a debate that never disagrees
   still emits verdicts.

All three are measurable, which yields the synthesis: **unmeasured self-grading is
the failure case; a debate whose catch-rate is itself machine-witnessed is a valid
counterparty.** Concretely: a canary corpus of planted-defective instruments
(vacuous reds, tautological passes, mis-scoped specs) with a measured catch rate;
dissent-rate telemetry that declares a never-dissenting panel dead; pre-registered
pass semantics frozen before the run. The 260/266 vacuous-reds episode is the first
canary class, and it is the shallow kind adversarial reading catches trivially.

**For a future pass:** mapped as the Assumption "Structured dissent among diverse
personas catches invalid instruments, and its catch-rate can be measured" under the
gate-parity solution. The natural first AssumptionTest is compute-only: build the
canary corpus, run the panel, measure — a red instrument for it belongs in the
OST-Agent repo suite, created through the normal branch/PR flow so main stays green.
