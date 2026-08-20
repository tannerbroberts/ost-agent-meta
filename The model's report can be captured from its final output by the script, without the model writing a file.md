---
type: Assumption
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
---
#Assumption #feasibility #build-loop #unvalidated #evidence/assertion
[[The build prompt no longer instructs a Write to the report file, and the script places the captured report itself]]

**The belief (feasibility).** `build-pass.sh` can obtain the one-paragraph report from the model's final output — the stdout of `claude -p "$(cat "$PROMPT_FILE")"` — and write it to `$REPORT` itself, so the prompt no longer needs to instruct a Write to that path and the harness's read-before-write guard is never asked to refuse one.

**How it could be false.** The `-p` output may interleave tool-call noise or a closing remark with the report, so the script cannot isolate the paragraph without a delimiter the model reliably honours; or the existing postflight, which re-reads `$REPORT` and re-prefixes lineage on one branch, may depend on the model having written the file mid-run rather than the script writing it after. Either makes the capture unreliable and the fallback (prompt reads before it writes) the better variant.

**Why this is a repository question, not a person's.** Whether the script can capture and place the report is settled by the script and a spec over it; nobody's afternoon is needed. Desirability — whether an operator cares about the refused turn — is a separate belief this node does not carry.

⚠️ Unvalidated. Agent-ideated.
