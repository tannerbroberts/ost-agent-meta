# NEXT BUILD — OST-Agent

**Stable address. Rewritten at the end of every pass; superseded briefings are kept
below under History, so this file only ever grows.** A reading of what the tree
implies, not a decision. Promotion, killing, and validation stay human.

_Last rewritten: 2026-07-25 (autonomous bootstrap loop)._

---

## What changed since the last briefing

- **Shipped: v0.5.0** — a failed pass now exits nonzero and names the failure; `status`
  leads with the last failed run. Closed the observed friction from 2026-07-25T02:00:38Z
  the same day it was filed. 212 tests green.
- **Not shipped: the release itself.** `npm publish` needs a credential the loop does not
  have. v0.5.0 is on `main`, not on npm. See §1.
- **Learned, and it changes the map:** the loop can carry a build end to end with zero
  operator minutes — and stalls at a *permission*, not a decision. That is a fifth item
  on the honest floor of the compute-only opportunity, and the docket candidate below
  does not currently handle it.

## 1. Three things only you can do — about 8 minutes total

Ordered by what unblocks the most. None is a build.

1. **`npm publish` v0.5.0** (~1 min). The commit, tag, changelog, and green suite are
   done. Until this runs, every downstream path in the README is describing a package
   that does not exist at that version — including `npx -y ost-agent@latest mcp`, which
   is how the plugin installs. Also note: the tag push was rejected by this
   environment's git proxy, so `git push --tags` may need re-running locally before the
   GitHub-Release path would work.
2. **Record the three compute-lane verdicts** (~3 min). `.ost-agent/drafts/compute-docket-2026-07-24.md`
   holds three paste-ready `ost-agent result` commands: one SUPPORTED (the journal-alert
   replay — v0.5.0 now *implements* the rule it validated, so code is standing on an
   unrecorded finding) and two kills. This vault has never recorded an
   evidence-driven kill; two are sitting there ready.
3. **Rule on the market-scan gate** (~4 min). `I can't say why anyone wouldn't just do
   this by hand with Claude and Obsidian` has zero solutions by deliberate gate. The
   competitor scan is external evidence about the market but not a customer citing the
   need, so the agent declined to lift the gate itself. Your call — see the annotation
   on that node for both options.

## 2. The next build, once (1) and (2) are done

**Lane triage: classify every assumption test by the human-minutes it actually needs,
and let the loop run the zero-minute lane unprompted.**

Solution: [[Triage every assumption test by the human-minutes it actually needs, and let
compute run the zero-minute lane]] — the leading candidate under the only opportunity in
this vault sourced from a real operator describing their own binding constraint.

Why it is next, concretely: the last two passes ran that lane **by hand**, and it worked
— three decisive verdict drafts including a kill, from a 66-test backlog, at zero
operator cost. The evidence for the mechanism exists; what is missing is that the
mechanism lives in a session's head rather than in the product. Every future pass
re-derives it from scratch.

Shape, smallest version first: a `lane` field at test creation (`compute-only` /
`one-command` / `humans-required`) plus a setter for the existing backlog, and
`ost-agent lanes` to list them. The lane label must be conservative and auditable — a
mislabelled humans-required test run by compute would fabricate evidence, which is the
one failure this product cannot survive.

**Fold in what this run learned:** the docket needs a *pending permissions* lane
distinct from its decisions lane. "Run `npm publish`" is not a yes/no with evidence
behind it, and forcing it into a decision docket will make the docket feel like chores.

## 3. Do not mistake §2 for the highest-information action

It is not. **The cold-offer test is** — 20 qualified strangers, a free done-for-you
discovery pass, pre-committed threshold (≥5 kickoffs, ≥3 sending real artefacts). The
roster (19 named leads plus pools, every row carrying its evidence URL), the outreach
kit, and the tracking sheet are all drafted and waiting in `.ost-agent/drafts/`.

Every node in this vault rests on founder or agent sources. Zero external returning
operators exist, which is the mandate's own metric. The compute share of that test is
already done; what remains is your identity and your consent, which compute must not
absorb. **Until this runs, everything in §2 is tooling for a product nobody outside this
building has asked for.**

## 4. The bias in this briefing, declared

This pass shipped an internal correctness fix and then wrote a briefing recommending
more internal tooling. That is an agent steering toward work it can do alone. §3 is the
correction, and it has now gone three passes without being acted on — a fact worth more
than any argument in §2.

---

## History

### 2026-07-25 (this pass)

Shipped v0.5.0 (exit code + status failure surfacing). Named the lane-triage build as
next, three human minutes as the unblock, and the cold-offer test as the still-unrun
highest-information action.

### Before 2026-07-25

No standing briefing existed; guidance lived in root-Outcome annotations and the
prioritisation section there. The 2026-07-24 hard-fix pass set the target row (external
demand evidence) and the critical path inside it (cold-offer → recruiting → pre-order);
that prioritisation still stands and is not superseded by this file — this file says what
to *pick up*, that section says what the tree is *for*.
