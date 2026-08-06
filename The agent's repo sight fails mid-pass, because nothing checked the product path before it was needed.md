---
type: Opportunity
source: 'USAGE:2026-08-05'
created: '2026-08-06'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Every path the config declares is checked when the config is read, not when something reaches for it]]
[[A pass ends by reporting which of its senses were live and which it never had]]

Machine-recorded: in 583 tool invocations on 2026-08-05, exactly one call failed, and it was `ost_read_repo` — "no product repos configured — add local repo paths under `product.repos` in ost.config.yaml". The operator does not discover the gap at setup, when it is cheap to fix; they discover it in the middle of a pass, at the moment the agent reached for the product and found nothing there. Everything downstream of that reach — instruments grounded in real modules rather than invented paths — is silently degraded rather than blocked, so the pass reports success while working blind.

The need is to know that a configured sense is actually wired before a pass depends on it, rather than after.

## Second sighting, and what it cost downstream — 2026-08-06

The 2026-08-05 record was one failed `ost_read_repo` call out of 583. This pass hit the same gap from three directions in one sitting, which says more about the shape of it than the single call did.

`ost.config.yaml` has no `product.repos` key at all — not an empty list, not a wrong path, simply absent — while `adapters.transcript.projectDir` correctly names `/Users/tanner/dev/OST-Agent`. The product path the vault needs is therefore already written in the config, under a different key, for a different consumer. Nothing reconciles the two, and nothing reports that one sense is wired and its neighbour is not.

The fallback did not work either: a direct `Glob` of `/Users/tanner/dev/OST-Agent` was denied, which is the documented posture — the loop runs `claude -p /ost-pass` "with only the ost-agent MCP tools granted and every file/shell/network built-in denied", per this config's own comment. So both routes to the product are closed, one by configuration and one by design, and neither announces itself until something reaches for it.

**The concrete downstream cost, stated because "silently degraded" is otherwise an abstraction.** This pass wrote three instruments. Two of them — `test/ost/next-work-status-filter.test.ts` and `test/ost/underserved-subtree-count.test.ts` — make assertions about behaviour verified absent by running `ost_next_work` and reading the nodes it returned, so they fail today on the mechanism. The third, `test/ost/disposition-ledger-shape.test.ts`, describes a mechanism that is wholly absent and fails first on the import: the weakest reason a command can fail, and the exact degradation this opportunity predicts. With repo sight the third would have named the module that has to change. The difference between those two kinds of red is the difference between a falsifiable prediction and a note saying "create this file", and a pass working blind cannot tell which it just wrote without saying so out loud.

_Observed by the 2026-08-06 unattended sweep against its own config and tool surface. Agent self-observation: it grounds usability, not demand._
