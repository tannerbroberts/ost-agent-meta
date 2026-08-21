---
type: Assumption
source: 'agent-ideation:2026-08-21-unattended-sweep'
created: '2026-08-21'
evidence: assertion
---
#Assumption #feasibility #build-loop #unvalidated #evidence/assertion
[[The probe script exists and an inline import of a bare package and a . src path both load under it]]

**The belief (feasibility).** A `probe` entry in `package.json` that runs `tsx -e "<code>"` with `npm run`'s cwd (the package root) lets the evaluated code import a bare dependency such as `zod` or `@modelcontextprotocol/sdk` and a repo path such as `./src/index.js`, with TypeScript syntax accepted, exactly as a file under `src/` or `test/` would.

**How it could be false.** `tsx -e` may evaluate as CommonJS or may not apply the TypeScript transform to eval'd input; ESM eval may resolve relative imports against a synthetic URL rather than cwd, so `./src/...` fails even though bare packages load; or `npm run probe -- '…'` may mangle the quoting badly enough that no realistic probe survives the trip. Any of these makes the sibling candidates the better fix.

**Why this is a repository question.** One spec that spawns the script and reads its exit code and stdout settles it; nobody's afternoon is needed. What the spec cannot settle is whether an agent under pressure reaches for this command instead of `/tmp` — that is behaviour across firings, not a property of the script.

⚠️ Unvalidated. Agent-ideated.
