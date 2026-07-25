# Compute docket — 2026-07-24

Everything below was executed by compute against existing data. Nothing was recorded:
`ost-agent result` is yours alone. Your total job here: read, then paste the commands
you agree with. Estimated involvement: **3 minutes.**

## Verdict drafts (3 tests run from the compute-only lane)

### 1. Journal-alert rule replay — SUPPORTED ✅

All 14 run journals replayed against the proposed rule (`error` field present → failed):
caught the 1 known failure (the auth-failed P2_map), zero of 13 healthy runs
misclassified. Journals as they exist today are sufficient — no schema change needed
before building the supervisor lane.

```bash
ost-agent result "Replay the three recorded failed runs through the journal-alert rule on paper" \
  --verdict supported --note "14 journals replayed: 1/1 failures caught, 0/13 healthy misclassified" \
  --by "Tanner" --evidence observed --vault ~/ost-agent-meta
```

### 2. Rename audit, both vaults — REFUTED ❌ (kill)

Full git history of ost-agent-meta and tetrix-ost: **zero** rename-shaped link breaks
beyond the known incident (which was a type edit, not a rename). Threshold was ≥2.
The solution "Detect renames from link topology and repair the edge" ranked itself
last among its siblings and questioned its own existence — the data agrees. First
evidence-driven kill in this vault's history.

```bash
ost-agent result "Audit both vault histories for rename-shaped link breaks" \
  --verdict refuted --note "0 rename incidents beyond the known non-rename across both vaults' full histories; threshold was >=2" \
  --by "Tanner" --evidence observed --vault ~/ost-agent-meta
```

→ On recording, I'll set "Detect renames from link topology and repair the edge" to
`deferred` with the result cited.

### 3. Stranded-evidence census, both vaults — REFUTED ❌ (kill)

30 evidence items in ost-agent-meta, 6 in tetrix-ost. Genuinely stranded items that
only a Context node type could home: **1** (the builder-loop-stopping report). The
other uncited items are noise-rung transcripts, and the grind friction is dispositioned
(cited with a truncated filename — a small mapper bug, noted). Threshold was ≥3.
The lighter sibling ("acknowledged, with a reason") covers the real gap.

```bash
ost-agent result "Count stranded evidence items across both vaults that only a Context node could home" \
  --verdict refuted --note "1 bucket-c item across both vaults (builder-loop-stopping); threshold was >=3; acknowledge-affordance sibling suffices" \
  --by "Tanner" --evidence observed --vault ~/ost-agent-meta
```

→ On recording, I'll set "A Context node type for evidence that is true, useful, and
not a customer need" to `deferred` with the result cited.

## Meta-verdict this enacts

These three drafts are themselves the method of the new test **"Run the compute-only
backlog today and count decisive verdict drafts"** (threshold: ≥3 decisive, ≥1 kill —
met, pending your recordings). If you record all three, that test's command is:

```bash
ost-agent result "Run the compute-only backlog today and count decisive verdict drafts" \
  --verdict supported --note "3 decisive drafts recorded unchanged, 2 kills — compute-only lane is real" \
  --by "Tanner" --evidence observed --vault ~/ost-agent-meta
```

## Backlog lane classification (first pass, auditable)

Of 72 assumption tests: **~6 compute-only** (3 now run; remaining: stall-definition
replay, half-life backdate, commit paper-classification), **~12 one-command** (compute
drafts everything, you record), **~54 humans-required** (real outside people — the
external-demand branch lives here, irreducibly).

## One decision pending from you (unrelated to the above)

Cold-offer sourcing sweep: name network exclusions, or say "go" and prune the list
after. Your compressed share of that test is now ~45 minutes (sourcing, all 20
personalization drafts, tracking, filing, and verdict prep are compute).
