---
type: Assumption
source: 'agent-ideation:2026-08-21-unattended-sweep'
created: '2026-08-21'
evidence: assertion
---
#Assumption #feasibility #build-loop #unvalidated #evidence/assertion

**The belief (feasibility).** Naming a `.scratch/` directory in `examples/automation/build-pass.sh`'s prompt and listing it in `.gitignore` is sufficient: a TypeScript file under that directory resolves `@modelcontextprotocol/sdk` from the repo's `node_modules` and `./src/...` from the repo root when run with `npx tsx`, and nothing the build loop does (`git add`, the postflight commit) can carry it into a commit.

**How it could be false.** The build loop or the model may stage with a form that bypasses `.gitignore` (`git add -f`, or an explicit path); `tsx` may resolve relative to the file's own directory in a way that breaks `./src` imports written from the repo root; or the prompt may have no natural place to say where probes go without growing the heredoc the existing spec already guards for apostrophes.

**Why this is a repository question.** Whether the prompt names the directory, whether `.gitignore` lists it, and whether a file under it loads the repo's modules are all settled by a spec over three files in this repository. Whether a session *follows* the instruction is a separate, behavioural belief this node does not carry — it needs firings, not a spec.

⚠️ Unvalidated. Agent-ideated.
