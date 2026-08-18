---
type: AssumptionTest
created: '2026-08-18'
evidence: assertion
lane: humans-required
threshold: >-
  All write paths confirmed able to carry a session id with no breaking
  consumer, or a specific gap named
---
#AssumptionTest #unvalidated #evidence/assertion

Small, fast check: read the commit-producing code paths to confirm a session id is available at every write site, and check for existing tooling that parses commit-message format strictly enough that appending a tag would break it. Threshold: all paths can carry it cleanly, or a specific path/consumer can't.

A person outside the building is the measurement here: This pass holds no repo-read grant to inspect commit-producing code paths or the tooling that parses commit messages. A person with the codebase open (or an attended pass with ost_read_repo) can check this directly.
