---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The agent directories carry enough traffic to be a distribution channel worth packaging for]]

Distribute where agents are already installed from — plugin registries, MCP server directories, skill marketplaces. The person who finds it is not searching for a discovery tool; they are browsing what their agent can be given, and this is one of the things. Discovery happens at the moment they are already deciding to add a capability.

The install path matters more than the pitch here. Something that is one command away from working inside a tool the buyer already runs gets tried by people who would never evaluate a product.

**Compared to the alternatives.** Reaches strangers with no audience-building and no waiting, and it is the only route with a real mechanism for people outside the author's network to arrive. It also selects for a browsing, low-intent visitor, converts poorly, and puts the tool next to hundreds of others in a list where the differentiator is a one-line description. Publishing in public is slower but reaches people who already understand why this is different.

**What would make this the wrong pick.** These directories are new, their traffic is unproven, and their ranking is opaque. Building the packaging for several of them is real work spent on channels that may not have any users a year from now.

## Definition of done

[[List in two directories and measure installs against how far the listing was scrolled]]

`npx vitest run test/release/registry-install-path.test.ts`

The spec asserts what this node says matters more than the pitch — that the thing is one command away from working inside a tool the buyer already runs. Each registry manifest's documented install command must resolve to a version that starts outside a vault.

**This is red against today's reality, and the failure is already recorded elsewhere in this tree.** [[A first-run branch that walks a stranger to a vault in one question]] notes that the plugin's MCP server runs `npx -y ost-agent@latest mcp`, which resolves to **0.9.0** — the release that refuses to start outside a vault. So the install path this whole distribution strategy depends on is currently broken for exactly the person it is aimed at: a browsing stranger who adds the capability and gets the failure two later releases already removed. That is a stronger red than a missing file, and it is arguably a build item rather than a test item.

**What a green here does not settle.** Everything the node is actually unsure about. Whether these directories have traffic, whether their ranking rewards anything an author controls, whether a browsing low-intent visitor converts, and whether the channels exist in a year — none is a property of the code. The listing-and-scroll measurement is the humans-and-market test, and a working install path is its precondition, not its answer.

## History
- 2026-08-05 unlinked [[List in two directories and measure installs against how far the listing was scrolled]] — moved under [[The agent directories carry enough traffic to be a distribution channel worth packaging for]] — the belief this test measures now has a node of its own
