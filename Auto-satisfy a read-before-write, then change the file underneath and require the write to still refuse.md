---
type: AssumptionTest
source: 'TRANSCRIPT:57249c25-2e61-480d-b234-007ddf101fa3'
created: '2026-08-06'
evidence: assertion
threshold: >-
  With auto-satisfaction enabled, a write whose target changed after the
  caller's own read is still refused. One silent overwrite is a failure — this
  is a zero-tolerance bar, not a rate.
instrument: npx vitest run test/preflight/auto-satisfy-preserves-staleness-guard.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** A concurrent-edit race is reproducible on disk in a temp directory. No person is the measurement.

**What it does.** Turn on the auto-satisfying path. Have a caller read a file, mutate that file out of band, then issue a write. Assert the write is refused. Then repeat with a precondition that carries no detection duty — a closed parameter set — and assert auto-satisfaction *does* apply there. The test passes only if the surface distinguishes the two.

**Why it is red today.** The auto-satisfying path does not exist, so the spec has nothing to exercise. Stated plainly: this is missing-file red rather than mechanism-missing red, because the pass that wrote it had no repository sight — `ost_read_repo` is off the unattended surface and a direct source-tree Grep was refused. Re-point it at the real guard module before trusting a green.

**What a green does NOT settle.** Only that the staleness guard survives one narrowing. It does not establish that removing preconditions is what operators want, that the narrowed solution still removes enough friction to matter, or that the remaining ceremony is the expensive part. Those stay open.
