---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A refusal can be reported without carrying any of the content it refused]]

An instance reports back a deliberately narrow slice: which refusals it hit, which routes it abandoned and why, where it got stuck, how long it idled. Nothing about the customer, the product, the evidence, or the tree's content ever leaves. What comes home is the shape of the tool failing, which is the part that generalises across every instance and the part no single operator has enough of to learn from.

The asymmetry is what makes it work. An operator's tree is theirs and valuable and private; an operator's list of things the tool refused to let them do is none of those, and is exactly what improves the tool for everyone.

**Compared to the alternatives.** Much easier to consent to than a general telemetry inbox, because the boundary is stated as a category rather than as a promise about handling. It gathers far less, and in particular it learns nothing about what kinds of discovery the tool is good at — only about where it breaks. A full reporting channel would learn both and be much harder to get agreement for.

**What would make this the wrong pick.** Refusal text can carry content: a refusal naming a node title leaks the node title. Making the slice genuinely narrow is a redaction problem, and getting it wrong once destroys the trust the whole arrangement depends on.

## Definition of done

"Take a week of this vault's refusals and check whether any leaks content when quoted"

```
npx vitest run test/security/refusal-redaction.test.ts
```

Green means every refusal this vault recorded in a week, run through the redaction rule, contains no surviving string that matches a node title, a vault path, or the body of any opportunity in the tree. It is red today because no redactor exists and refusals quote node titles verbatim — this vault's own trace carries lines like `"A third of my calls go on re-asking what is outstanding" cannot declare 'observed'`, which is the leak in its plainest form.

**Zero is the right bar and a percentage would be the wrong one.** The arrangement this solution proposes trades a narrow slice of an operator's machine for shared learning, and it survives exactly as long as the slice is provably narrow. One leak destroys the trust the whole thing depends on, so a redactor that catches 95% has not partly succeeded — it has established that the boundary is not real.

**What green does NOT settle.** A string-matching check catches quoted content, not inferable content: a refusal that reveals nothing verbatim can still narrow what an outsider can guess about what this vault is for, and no spec of this shape sees that. The corpus is also one week of one vault whose subject is this product itself; a vault about something commercially sensitive has more to lose from the same text, and the human read this test also asks for is what would catch that.

## History
- 2026-08-05 unlinked "Take a week of this vault's refusals and check whether any leaks content when quoted" — moved under "A refusal can be reported without carrying any of the content it refused" — the belief this test measures now has a node of its own
