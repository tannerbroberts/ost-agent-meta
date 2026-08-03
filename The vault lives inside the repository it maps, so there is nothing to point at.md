---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

Put the tree in a directory of the project itself. It is committed with the code, branches with the code, reviews with the code in the same pull request, and cannot be lost, moved, or forgotten independently of it. The question of where the vault is stops having an answer because it stops being a question.

There is a second effect worth as much as the first: a change to the product and the change to the reasoning behind it can arrive in the same diff, and a reviewer can see both.

**Compared to the alternatives.** The strongest guarantee available — a pointer can go stale and a search convention can miss, but co-location cannot be wrong. It also forces the tree to share the code's access control, its review process, and its history, and that is a genuine cost: discovery evidence often includes things that should not sit in a repository every engineer can read, and a vault that maps several products has no single repository to live in.

**What would make this the wrong pick.** One tree per product is the rule, but products and repositories are not the same thing. A product spread across four repositories has no obvious home, and a monorepo holding six products has too many.
