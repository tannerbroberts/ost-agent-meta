---
type: Solution
source: 'agent-ideation:2026-09-08-unattended-sweep'
created: '2026-09-08'
evidence: assertion
killIf: >-
  The operator states they will not hold a filesystem read grant on the product
  path open for unattended firings
killBy: '2026-11-07'
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[The operator will hold a filesystem read grant on the product path open for firings nobody is watching]]

**Variation dimension: who-does-the-work. Position taken: the person, once, and nothing is built here at all.**

The agent already has a search tool. `Grep` and `Glob` are on the firing's surface every pass; they are refused on `/Users/tanner/dev/OST-Agent` for want of a read grant, and on nothing else. So the cheapest form of this need's answer is not a feature: it is the operator granting that path, once, after which the verb the channel lacks arrives from the tool that already had it.

**Why this position and not another.** The siblings both put work on the machine — one builds a search verb into this product's own surface, the other adopts an indexer from outside. This one observes that the capability exists, is installed, and is one permission away, and that every pass paying a call to rediscover the boundary is paying for a decision nobody has been asked to make. The parent node counts seven records carrying that denial between 2026-08-06 and 2026-09-07, and the firing that ideated this candidate minted an eighth.

**What it deliberately does not do.** It builds no search into `ost_read_repo`, adds no config key, and writes no code. It also takes no view on scope: a filesystem grant is a filesystem grant, and this candidate does not pretend it can be narrowed to "search only."

**What it gives up, plainly, and this is the sharpest thing about it.** A read grant on a path is strictly wider than a search verb confined to `product.repos`. `ost_read_repo` refuses the vault's own `.ost-agent/` sidecar even when the vault is a configured repo, redacts secrets, and caps what it returns; the harness file tools do none of those things on a path they are granted. So this candidate answers the need by removing a boundary rather than by adding a capability inside one, and an operator who granted it would have widened what an unattended firing can read well beyond the code it wanted searched. That is the trade in one sentence: it is the only candidate that ships today and the only one that gives up the confinement the other two keep.

**What would make this the wrong pick.** If the operator's reason for never granting it is that unattended runs should not hold broad filesystem reads — which is a coherent position and one nothing on this tree has asked them about — then this candidate is not cheap, it is refused, and the two siblings are the whole option set.

Ideated by an unattended pass on 2026-09-08 against the assigned dimension. **Not blind:** this surface holds no grant to run independent parallel ideators, so all three candidates under this opportunity were composed in one context by one author — the exact condition the blind-ideation rule exists to prevent. Read them as one author's three answers and discount their apparent distinctness accordingly.

Unvalidated. A human to review.

## Definition of done — and it is not a command

"Ask the operator whether an unattended firing may hold a filesystem read grant on the product repo"

No command, and deliberately so: this candidate builds nothing, so there is no behaviour for an exit code to predict. The bar is **at least 3 of 3 answered yes** — grant it, leave it open while unattended, and still open thirty days later. A revocation inside the month is a refuted verdict rather than a partial success, because a grant that closes returns the tree to exactly the state it has been in since 2026-08-06.

Run this one before either sibling is built. It is the cheapest test on the branch and it disposes of two larger candidates in whichever direction it lands.

The test title is quoted rather than wikilinked on purpose: its one backlink belongs to its parent assumption.
