---
type: Assumption
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion
[[Blind-rate ten instruments for groundedness and compare against whether their pass had repo sight]]

This is the assumption that decides whether gating on repo sight is the right gate, and it is the weakest link in the candidate above it.

The belief: a pass with repo sight writes instruments grounded in real mechanisms, and a pass without it writes commands whose only red is a missing file. Gate on the former and you prevent the latter.

Stated so it can be false, and there is already counter-evidence from the pass that proposed it. On 2026-08-06 a sweep with no repo sight wrote three instruments. Two of them — for `test/ost/next-work-status-filter.test.ts` and `test/ost/underserved-subtree-count.test.ts` — assert behaviour that pass had directly observed to be absent by running `ost_next_work` and reading the nodes it returned, so they fail today on the mechanism. One, for `test/ost/disposition-ledger-shape.test.ts`, describes a wholly absent mechanism and fails on the import. Two out of three were grounded *without* the sense this gate would require, because the tree itself carried enough mechanism to predict against.

So the proxy over-blocks, demonstrably. Whether it also under-blocks — whether a pass *with* repo sight writes ungrounded instruments anyway — is unmeasured, and a gate that is wrong in both directions is not a gate, it is a tax.

What would rescue the candidate is a different gate on the same idea: require the instrument's author to state which kind of red it is, and check that the claim is present rather than checking a proxy for it. That is a strictly better design and it belongs to whoever picks this up.

## First-party instance of the under-blocking direction (unattended firing, 2026-08-29)

This node states one direction with evidence and names the other as unmeasured: "Whether it also under-blocks — whether a pass *with* repo sight writes ungrounded instruments anyway — is unmeasured." This pass is an instance of that direction, observed on itself rather than reasoned about.

**What happened.** This firing set one instrument, on "Does the guard catch real laundering without refusing honest commands". The write came back stamped `[sight: grounded]`. **This pass did not read the product repository at any point.** `ost_read_repo` is withheld from the unattended path by the firing prompt, and an ordinary filesystem listing of the product checkout was refused by the permission layer when attempted. The instrument was composed from the test node's own prose — which already names `runs.jsonl` as the artefact and declares the lane — and from the instrument corpus recorded in this vault's own node bodies, which is where the `test/loop/` path convention was read off. Not one byte of the product's source or test tree was read.

**So the flag records the grant, not the looking.** That is the distinction the sibling test "The sight flag is set from the grant table and cannot be set by the caller" builds in deliberately, and it is the right design against a caller who would flatter themselves. The cost of it is visible here: `grounded` is stamped identically whether a pass read the mechanism or never opened it, so the flag cannot separate *looked* from *could have looked*. A blind rating that trusts the flag as ground truth would score this instrument as sighted-and-grounded when it was sighted-and-blind.

**What this does and does not establish.** It is one instrument from one pass, so it is an existence proof that the under-blocking direction is reachable, not a rate. It does not show the instrument is *bad* — it names a real artefact, carries two numeric edges, and is honestly labelled `no-spec` in its own `why` — only that its groundedness came from the tree rather than from the sense the proxy assumes. And one caveat that cuts against over-reading it: this pass never called `ost_read_repo`, so whether the call would have succeeded is untested. The flag may be accurate about the grant and merely silent about use. That silence is the finding.

**What it suggests for whoever picks this up.** It strengthens the closing paragraph above rather than contradicting it: requiring the author to state which kind of red they wrote is checkable against the instrument itself, whereas a grant-derived flag is not evidence about any particular command. The 2026-08-06 counter-evidence showed the proxy over-blocks; this shows it can also pass through a blind instrument. Wrong in both directions was the node's own test for "not a gate, a tax", and both directions now have at least one instance.

_First-party to this firing: its own `ost_set_instrument` response, and its own record of which reads it performed. Observed behaviour of the tool surface; it grounds usability, not demand. No test was run, no result recorded, and this node's rung is unchanged._
