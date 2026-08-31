---
type: Solution
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-31'
evidence: assertion
killIf: >-
  A reader that had the size in the listing still issued an over-cap read
  anyway, in more than half the over-cap reads recorded in a month of
  transcripts.
killBy: '2026-11-30'
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[A listing can carry every entry's size without a second call and without unbounded stat cost]]

**Variation dimension: who-does-the-work. Position taken: nobody — the step is removed rather than assigned.**

A reader already calls the listing before it calls the read; that is how it learns the name it is about to ask for. So put the size there. `ost_read_repo`'s directory listing returns `{ name, type }` per entry today; it would return `{ name, type, bytes }`. The vault's node listing, which already reports `linkCount` and `tagCount` per node, would report the body's character count beside them. There is no probe call to remember to make, no flag to pass, and no judgement handed to anybody — the figure is simply present at the moment the choice is made.

**Why this position and not another.** The alternative assignments all give the work to someone: the reader (call probe first), the operator (configure a cap), the tool author (decide what to truncate). Each of those can be forgotten, and the failure this node describes is precisely a reader who did not think to ask. A field that is always there cannot be forgotten. It is also the only one of the three candidates that costs nothing at read time, because the decision is already informed before the read is composed.

**Cheapest form, and where it lands.** In `src/product/repo.ts` the listing branch already calls `readdirSync(real, { withFileTypes: true })` and maps to `{ name, type }`. Add `bytes` from a `statSync` per file entry. For the vault, the node listing is assembled where `ost_read_tree` builds its capped rows; the body length is known there because the file has been read to extract frontmatter.

**What it gives up, plainly, and this is the real cost.** A listing is currently one `readdir` syscall; this makes it one `readdir` plus up to `MAX_LIST_ENTRIES` stats — 500 in the worst case, on every listing, forever, to serve a reader who in most cases is about to read exactly one of those files. That is the inverse of the trade `probe: true` already makes, which spends one stat only when a caller asks. It pays a cost on every listing to avoid a cost on rare reads, and if over-cap reads are genuinely rare it is the wrong trade by a wide margin. Nothing here has counted how rare they are.

**What it also does not do.** It tells a reader the size and nothing else — no advice, no offset, no partial content. A reader who sees 29,160 tokens still has to decide what to do about it, and this candidate takes no view. Sizes are also in bytes, which is a proxy for the token budget that actually refused the read and can be off by a factor for non-ASCII or dense source.

**What would make this the wrong pick.** If most listings are large and most reads are small — which is the normal shape of browsing a source tree — the stat cost dominates and the sibling that changes the failure mode is strictly cheaper.

**Honest note on how this was ideated.** The sweep asks for one blind ideator per dimension. This surface holds no grant to run independent parallel ideators, so all three candidates under this opportunity were composed in one context by one author — the exact condition the blind-ideation rule exists to prevent. Read them as one author's three answers and discount their apparent distinctness accordingly.

Unvalidated. Agent-ideated 2026-08-30; a human to review.
