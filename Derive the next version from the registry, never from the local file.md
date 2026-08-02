---
type: Solution
source: 'agent-ideation:2026-08-02-maintenance-pass'
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Replay every past release against a registry-derived number]]

**The idea.** The release path never reads the next version out of the local `package.json`. It asks the registry what is currently published, asks `origin/main` what is currently tagged, takes the maximum, and increments from there. The local file becomes an output of the release rather than an input to it.

**Why it addresses the need.** It removes the shared mutable counter that caused the near-collision. Two trains that both ask the registry cannot choose the same number unless they ask at the same instant, and the second publish fails loudly on a version conflict rather than quietly clobbering. The observed failure — a local `3b9cc5e` sitting unpushed while the loop released v0.18.0 from elsewhere — becomes impossible to reach by accident.

**How it differs from its siblings.** [[Refuse to release from history that has not been pushed]] stops the *divergence* that makes collisions possible; this stops the *collision* while allowing the divergence. [[The loop proposes a release and a human tags it]] removes the second train entirely. This is the only one of the three that lets both trains keep running independently, which is its whole appeal given that the autonomous loop releasing on its own is a feature rather than a bug here.

**Where it fails.** It makes the release path depend on network reachability of the registry, so a registry outage becomes a release outage — and worse, an ambiguous one, since "cannot reach npm" and "nothing is published yet" must not be conflated or the first release of a package silently picks the wrong number. It also does nothing about the deeper problem: two trains can still produce *divergent content* at consecutive version numbers, so v0.19.0 might contain work that v0.18.0's author never saw. Numbering is the symptom; unshared history is the disease.

**Cost.** Small. One registry query and one `git ls-remote --tags` in the release script.

⚠️ Unvalidated. Agent-ideated from one observed near-miss, 2026-08-02.
