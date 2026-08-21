---
type: AssumptionTest
source: 'agent-ideation:2026-08-21-unattended-sweep'
created: '2026-08-21'
evidence: assertion
threshold: >-
  All 3 assertions in test/automation/build-pass-probe-location.test.ts pass:
  (1) the prompt heredoc in examples/automation/build-pass.sh — the slice
  between `cat >"$PROMPT_FILE" <<PROMPT` and the closing `PROMPT` line — names
  `.scratch/` as where throwaway probes go and says `/tmp` is not; (2)
  .gitignore contains a `.scratch/` line; (3) a fixture file written to
  `.scratch/` that imports `@modelcontextprotocol/sdk` and `./src/index.js`
  exits 0 under `npx tsx`.
instrument: npx vitest run test/automation/build-pass-probe-location.test.ts
sight: grounded
---
#AssumptionTest #feasibility #build-loop #unvalidated #evidence/assertion

**Lane: compute-only.** A spec over three files in this repository settles it; nobody outside the building is the measurement.

**What the spec must assert, stated so the next reader does not inherit a blank file.** Following the pattern `test/automation/build-pass-reports.test.ts` already uses (read the script, slice the heredoc between `cat >"$PROMPT_FILE" <<PROMPT` and `\nPROMPT\n`, regex the text):

1. The prompt slice matches `/\.scratch\//` and matches `/\/tmp/` in a sentence telling the model not to write probes there. Today the slice contains neither — the prompt names where the report goes and says nothing about probes.
2. `.gitignore` (read from the repo root) contains a line `.scratch/`. Today it lists `node_modules/`, `dist/*`, `.superpowers/` and others, and no `.scratch/`.
3. The spec writes `.scratch/__probe_fixture.ts` containing `import "@modelcontextprotocol/sdk/server/index.js"; import "../src/index.js"; console.log("probe-ok");`, runs `execFileSync("npx", ["tsx", ".scratch/__probe_fixture.ts"], { cwd: root })`, expects stdout to contain `probe-ok`, and removes the fixture in `finally`. Today the directory does not exist; the assertion fails on the import the moment the directory does exist but the prompt does not, so the three stay independent.

**Why it is red today, honestly classified.** The spec file does not exist, so today's red is `no-spec` — it would fail identically for any question written on this path and grants no build permit. It becomes a real red the moment the spec above is written: assertions (1) and (2) fail against the current prompt and `.gitignore`. A pass on this surface can name the mechanism but cannot leave the spec behind; the deliverable is the failing spec, not this filename.

**What a green does NOT settle.** Whether a session told where probes live actually puts them there instead of `/tmp` (behaviour over future firings, readable only from transcripts); whether the two observed turns mattered to any operator (desirability — nobody has said so); and nothing about probes written by sessions that never read the build prompt at all.
