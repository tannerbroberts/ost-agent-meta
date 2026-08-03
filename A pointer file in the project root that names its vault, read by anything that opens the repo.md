---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

A small committed file at the project root recording where the vault lives and what outcome it serves. Anything that opens the repository — an agent starting cold, a new contributor, a tool looking for context — finds it in the first place it would look. The link travels with the code, survives clones, and is versioned alongside the thing it describes.

The direction is the point. A vault that knows about its project is the arrangement that already exists and it does not help, because the discovery always starts from the code.

**Compared to the alternatives.** Trivial to implement and to understand, works for humans and agents equally, and it is inert — nothing has to be running for it to do its job. Its weakness is that it is only a string: it goes stale the moment the vault moves, and nothing will say so. An agent-side convention that searches for a vault would survive relocation; embedding the tree in the repository would remove the question entirely.

**What would make this the wrong pick.** A pointer nobody is required to read is a pointer that gets ignored. If the tools that matter do not look for this file by convention, adding it changes nothing except that the information is now technically present.
