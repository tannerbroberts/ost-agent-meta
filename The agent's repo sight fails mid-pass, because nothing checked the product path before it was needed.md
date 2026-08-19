---
type: Opportunity
source: 'USAGE:2026-08-05'
created: '2026-08-06'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Every path the config declares is checked when the config is read, not when something reaches for it]]
[[A pass ends by reporting which of its senses were live and which it never had]]
[[The instrument-writing step declares repo sight required and skips itself rather than inventing paths]]

Machine-recorded: in 583 tool invocations on 2026-08-05, exactly one call failed, and it was `ost_read_repo` — "no product repos configured — add local repo paths under `product.repos` in ost.config.yaml". The operator does not discover the gap at setup, when it is cheap to fix; they discover it in the middle of a pass, at the moment the agent reached for the product and found nothing there. Everything downstream of that reach — instruments grounded in real modules rather than invented paths — is silently degraded rather than blocked, so the pass reports success while working blind.

The need is to know that a configured sense is actually wired before a pass depends on it, rather than after.

## Second sighting, and what it cost downstream — 2026-08-06

The 2026-08-05 record was one failed `ost_read_repo` call out of 583. This pass hit the same gap from three directions in one sitting, which says more about the shape of it than the single call did.

`ost.config.yaml` has no `product.repos` key at all — not an empty list, not a wrong path, simply absent — while `adapters.transcript.projectDir` correctly names `/Users/tanner/dev/OST-Agent`. The product path the vault needs is therefore already written in the config, under a different key, for a different consumer. Nothing reconciles the two, and nothing reports that one sense is wired and its neighbour is not.

The fallback did not work either: a direct `Glob` of `/Users/tanner/dev/OST-Agent` was denied, which is the documented posture — the loop runs `claude -p /ost-pass` "with only the ost-agent MCP tools granted and every file/shell/network built-in denied", per this config's own comment. So both routes to the product are closed, one by configuration and one by design, and neither announces itself until something reaches for it.

**The concrete downstream cost, stated because "silently degraded" is otherwise an abstraction.** This pass wrote three instruments. Two of them — `test/ost/next-work-status-filter.test.ts` and `test/ost/underserved-subtree-count.test.ts` — make assertions about behaviour verified absent by running `ost_next_work` and reading the nodes it returned, so they fail today on the mechanism. The third, `test/ost/disposition-ledger-shape.test.ts`, describes a mechanism that is wholly absent and fails first on the import: the weakest reason a command can fail, and the exact degradation this opportunity predicts. With repo sight the third would have named the module that has to change. The difference between those two kinds of red is the difference between a falsifiable prediction and a note saying "create this file", and a pass working blind cannot tell which it just wrote without saying so out loud.

_Observed by the 2026-08-06 unattended sweep against its own config and tool surface. Agent self-observation: it grounds usability, not demand._

## Third sighting — the gap is unchanged a day later, and it shaped three more instruments — 2026-08-06 (later pass)

Kept deliberately short; the diagnosis above still stands and does not need restating.

Two new facts only.

**The denial is path-level, not root-level.** `TRANSCRIPT:93a613dc-f52b-46c9-9dcf-9b22fdfe36f5` records `Glob` denied on `/Users/tanner/dev/OST-Agent/test` specifically, and this pass was denied on the repository root and on `src` in the same sitting. So the fallback route is closed at every depth, not merely at the top — there is no narrower grant that would have let a pass read just the test suite to check whether a spec file already exists.

**What it cost this pass, in the same terms the second sighting used.** Three instruments written for the new workspace-collision branch — `test/runner/workspace-reconcile-states.test.ts`, `test/runner/per-run-workspace-cost.test.ts`, `test/runner/workspace-lease-liveness.test.ts`. All three assert against a mechanism observed absent in a transcript rather than one confirmed absent in the code, which is a better footing than the invented-path case the second sighting described and still short of repo sight. Each node says so in its own body rather than only here. The unverifiable half is narrow and worth naming: whether a workspace-level lease or a per-run path derivation already exists somewhere in the runner. If any does, the corresponding instrument is green on arrival and measures nothing.

**One thing this sighting adds that the earlier two could not.** The vault's own `ost.config.yaml` was readable throughout — this pass read `lockTtlMinutes: 60` out of it and used it as direct evidence in an assumption. So the blindness is asymmetric: a pass can read the thing that describes the product's intentions and not the product. That asymmetry is what makes working blind feel survivable while producing exactly the weaker instruments recorded above.

## Reproduced, and this time it cost the pass its main deliverable — 2026-08-06 (unattended sweep)

Both channels to the product's own code were dead this pass, and the failure arrived exactly where this node says it does: mid-pass, at the moment the code was needed, with no earlier warning.

**What was tried, and what came back.**

1. `ost_read_repo({path: "test"})` → `no product repos configured — add local repo paths under 'product.repos' in ost.config.yaml so the agent can read what the product is`. The tool is granted and functioning; the vault is simply not told where the product lives.
2. `Glob("test/**/*.test.ts", path: "/Users/tanner/dev/OST-Agent")` → `Claude requested permissions to read from /Users/tanner/dev/OST-Agent, but you haven't granted it yet.` The fallback the agent reached for next is blocked by a separate mechanism, so the two failures are independent and neither covers for the other.

**Why this instance is worth recording rather than being one more sighting.** The prior evidence on this node is about a pass losing sight it expected to have. This one prices it. The pass was instructed to work `solutionsMissingInstruments` — **63 solutions** whose tests are prose only — and told explicitly that an instrument naming an invented path "fails because nothing is there, which is the weakest reason a command can fail," with the preference being a spec whose assertions go red against today's code. Choosing between those two forms requires reading the code. With both channels shut, the distinction the instruction turns on was not available to be made, and the largest queue in the sweep could not be worked the way it was asked for.

**The cost is a whole bucket, not a call.** Two failed calls is trivial; what they blocked is 63 solutions that still cannot reach a builder. And the failure is not visible in the sweep afterwards — `ost_next_work` will report the same 63 next pass with no record that a pass tried and was structurally unable, which is the shape this node's parent concern is about.

**The repair is one line of config,** and it is a human's: add the product repo path under `product.repos` in `ost.config.yaml` (and, if the fallback is meant to work, grant read on that directory). Until then every future pass will spend the same two calls discovering the same absence — which is the recurrence "The same refusal is rediscovered every session" describes, arriving through this node's channel.

**What a preflight would have done.** Named the missing `product.repos` key in the first second, before the pass planned work that depended on it. The pass would then have known to reallocate to work that needs no repo sight — which is what it did anyway, but 40 minutes later and after committing to a plan it could not carry out.

_Source: this pass's own two tool calls, 2026-08-06 — first-party observation of the product's behaviour, captured as it happened. Grounds feasibility and usability, not demand. Unvalidated; no test was run and no result is recorded._

## Sixth sighting — unchanged, and the price is now 62 solutions — 2026-08-09 (unattended sweep)

Kept short on purpose; this node has five sightings and the diagnosis needs no restating. Three facts only.

**Still absent.** `product.repos` is not in this vault's `ost.config.yaml` — this pass read the file directly and confirmed the key does not exist, while `adapters.transcript.projectDir` still correctly names `/Users/tanner/dev/OST-Agent` on line 15. The one-line repair the 2026-08-06 sighting described is now, by that sighting's own counting, seven passes old.

**Both channels dead again, in the same order.** `ost_read_repo()` → "no product repos configured — add local repo paths under `product.repos` in ost.config.yaml". `Glob("/Users/tanner/dev/OST-Agent/src/**/*.ts")` → "Claude requested permissions to read from /Users/tanner/dev/OST-Agent, but you haven't granted it yet." Two independent failures, neither covering for the other, exactly as recorded before.

**What it cost this pass, priced the way the fourth sighting priced it.** The queue was 62 solutions whose tests are prose only. This pass wrote **no** instrument against an invented path — it declined the whole bucket rather than manufacture reds that fail on a missing file — and instead spent its instrument budget on the one place where absence could be established without repo sight: behaviour verified missing by *running `ost_next_work` and reading what it returned*. That is the better of the two reds the sighting above distinguishes, and it was available for exactly one item out of 62.

That ratio is the finding. Repo blindness does not merely weaken instruments; it restricts honest instrument-writing to the narrow set of claims about the tool's own observable output, which is roughly 1 in 60 of what the queue holds. Five sightings established that the gap recurs. This one establishes what it caps.

_First-party observation by the unattended sweep of 2026-08-09, from its own two failed calls and a direct read of the vault's config. Grounds feasibility and usability, not demand. Unvalidated; no test was run and no result is recorded._

## Seventh sighting is the first non-sighting — the repair landed and repo sight works — 2026-08-09 (later unattended sweep)

**The gap this node records is closed.** Six sightings said `product.repos` was absent and both channels to the product were dead. This pass read `ost.config.yaml` and the key is there, naming `/Users/tanner/dev/OST-Agent` — the same checkout `adapters.transcript.projectDir` has named since the beginning, which is the reconciliation the second sighting asked for. The config carries its own dated rationale on lines 48-52, and it cites this node's argument back: repo sight was granted because "six consecutive discovery passes reported repo sight dead and declined to instrument 62 prose-only tests rather than write instruments against invented paths."

**Verified live, not inferred from the config.** `ost_read_repo` returned real listings this pass: `src/` and `test/` mirror each other across 18 areas, `test/ost/` holds 22 spec files, `test/security/` holds 22. The tool that failed as the single error in 583 calls on 2026-08-05 now answers. This is first-party observation of the fix working, not a reading of the line that was supposed to fix it.

**What it changed, and what it did not — this is the part worth carrying forward.** The sixth sighting established a cap: repo blindness restricted honest instrument-writing to "roughly 1 in 60" of the queue. Lifting the blindness does not lift that cap to 60 in 60, and the difference matters to whoever plans the next pass.

The census on "A pass that cannot see the repository cannot set an instrument at all" classified the 25 visible entries of `solutionsMissingInstruments` and found at most 7 of 25 are mechanical questions at all; roughly 14 are human preference, demand, or pricing, and 3 are already shipped. Repo blindness was the binding constraint on the 7. It was never the binding constraint on the other 18, and nothing about this repair touches them. So the honest new ceiling is about 7 in 25, not 25 in 25, and a pass that reads the repair as "the instrument bucket is now workable" will spend its budget manufacturing commands for the 14 — which is precisely the failure that census warned produces progress-shaped output as the tree fills with commands that measure nothing.

**One limit that survived the repair, discovered by hitting it.** Repo sight is read-only, which is correct and is not a complaint. But it means a pass can now *name* the module a spec would have to change while still being unable to leave a spec file behind. Every instrument an unattended pass writes therefore remains a `no-spec` red — red because the file is absent, which the ruleset itself files as granting no build permit. Repo sight upgrades the *reasoning* behind an instrument from invented to grounded; it does not upgrade the *red* from missing-file to failing-assertion. Closing that last gap needs a builder who can write the spec, not a discovery pass with better sight.

_First-party observation by the unattended sweep of 2026-08-09, from its own successful `ost_read_repo` calls and a direct read of the vault's config. Grounds feasibility and usability, not demand. No test was run and no result is recorded; this node's rung is unchanged._

## Issues
- 2026-08-11 2026-08-11 subset-extent flag vs "The same agent has a different tool surface on every surface I run it on" adjudicated: DISTINCT, keep as siblings, do not re-hang. "Every path the config declares is checked when the config is read, not when something reaches for it" repairs config-declared senses and does nothing about per-tool permission variance, which is the sibling's need (and the sibling's preflight solutions do not validate config paths). Subset extent is an artefact of a shared usage record. Sweep's own verdict; queued for human confirmation via "A human re-judges the first twelve extent flags against Torres's test".

## Eighth sighting — the permission-denial channel recurs (unattended sweep, 2026-08-18)

`TRANSCRIPT:89a95209-c65d-460f-801a-a75fd0805b65` shows the same fallback-channel failure the sixth and seventh sightings distinguished from the config-key failure: `Glob(/Users/tanner/dev/OST-Agent)` and `Read(/Users/tanner/dev/OST-Agent/package.json)` both denied with "Claude requested permissions to read from ... but you haven't granted it yet." This is the Glob/Read permission route, not the `ost_read_repo` config-key route the seventh sighting reported fixed — the two channels remain independent, and this session hit the one that was never the subject of that repair. The same session also retried `mcp__ost-agent__ost_ingest_inbox` and `mcp__ost-agent__ost_next_work` with no arguments, an already-tracked shape cited on "My unattended runs recover from tool errors and retries I never find out about."

_Source: `TRANSCRIPT:89a95209-c65d-460f-801a-a75fd0805b65` — observed behavior, captured mechanically from the agent's own transcript. Grounds feasibility and usability, not demand._

## Ninth sighting — reproduced on the unattended sweep surface, permission channel (2026-08-19)

This pass (the unattended `opportunity-solution-tree` maintenance sweep, run via the harness's native file tools rather than `ost_read_repo`) attempted `Glob("**/*.ts", path: "/Users/tanner/dev/OST-Agent/src")` and `Glob("test/**/*.test.ts", path: "/Users/tanner/dev/OST-Agent")` before working `solutionsMissingInstruments`. Both were refused: "Claude requested permissions to read from /Users/tanner/dev/OST-Agent/..., but you haven't granted it yet." Same shape as the eighth sighting's `TRANSCRIPT:89a95209` instance — the Glob/Read permission channel, independent of the `ost_read_repo` config-key channel the seventh sighting reported fixed. This pass also holds no `ost_read_repo` grant at all on this surface (see this pass's own "What this surface withholds" instructions), so both channels to the product were closed simultaneously rather than one covering for the other.

**Consequence, priced the way earlier sightings priced it.** This pass declined the entire `solutionsMissingInstruments` bucket (88 solutions) rather than write instruments against invented paths, and could not use `ost_flag_humans_required` either (also withheld this surface) to dispose of the human-required subset correctly. Both of the two legitimate dispositions the brief names for that bucket were structurally unavailable in the same pass, for the same underlying reason this node tracks: a surface that does not disclose what it lacks until the call that needs it fails.

_First-party observation, 2026-08-19 unattended sweep, from this pass's own two refused calls. Grounds feasibility and usability, not demand. No test was run; this node's rung is unchanged._
