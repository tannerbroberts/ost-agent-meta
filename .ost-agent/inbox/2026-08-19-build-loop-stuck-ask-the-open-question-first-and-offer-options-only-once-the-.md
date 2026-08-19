# Build note — "Ask the open question first, and offer options only once the frame is agreed" has not shipped after 2 attempt(s) in a row

Source: build loop, automated, 2026-08-19T16:52:29Z. Evidence class: observed — an exit code the loop watched, not what the model reported.

This solution cleared a build permit but has now failed to ship 2 firing(s) in a row with its own node file unchanged in between, so each firing was reasoning about the same unresolved definition. The build loop cannot write the tree and is leaving this as evidence, not a verdict.

Most recent build report:

Nothing to build: this target was already fully built and pushed as PR #171 before this pass started. Verified independently — tsc clean, vitest red on exactly the one pre-committed assertion (two-stage costs 92 operator turns vs one-stage's 72 across 46 recorded questions). Finding: this is the third time this identical diagnosis has been produced (#130, an earlier stuck-target note, now #171) because the vault node was never updated after the first two runs to reflect that the assumption failed — the loop keeps re-selecting a dead target and re-deriving the same negative result instead of the tree recording it once. [Loop check: the instrument for this solution is still red after the build, so the definition of done was not met regardless of what the report above says.] [Loop ship: NOT MERGED — a gate went red when the loop re-ran it: not shipped — the "vitest" gate went red (exit 1). the suite is the definition of done for everything already shipped.]

For discovery or a human to decide: whether this is a diagnosed negative worth deferring, a solution worth reframing, or a gate worth revisiting. The build loop will keep passing over this target in favor of other buildable candidates until this node changes.
