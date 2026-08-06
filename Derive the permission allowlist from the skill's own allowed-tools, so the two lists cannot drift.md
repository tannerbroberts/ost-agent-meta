---
type: Solution
status: unvalidated
source: 'TRANSCRIPT:6e66c934-24d8-4200-b6f2-7af23002c478'
created: '2026-08-06'
evidence: observed
---
#Solution #unvalidated #evidence/observed

There are two lists of tools and they are maintained by different hands at different times, which is the whole disease.

One is the skill's `allowed-tools` frontmatter — written when the skill is written, by whoever added the capability. The other is the session's permission allowlist — written when the automation is set up, by whoever wired the cron. A tool added to the skill in March does not appear in a grant written in January, and nobody is told. That is exactly the shape of the record: `ost_flag_humans_required` is named in the skill's tool list and denied in five consecutive unattended runs.

The proposal is to stop maintaining the second list. The skill's `allowed-tools` becomes the single declaration, and the run's permission set is generated from it at install time — so adding a tool to the skill is the act that grants it, and there is no second place to forget.

The bet is that the two lists were never independent decisions in the first place. If that is true, splitting them bought nothing and cost five nights. If it is false — if an operator genuinely wants to install the skill and withhold one of its tools — then this solution removes a control they were using deliberately, and the right answer is the preflight sibling instead, which detects the gap without closing it.

That is the real fork between this candidate and "Preflight the run's tool demands against its grant and stop at turn one", and it is a question about what operators want rather than about what is buildable: is a narrower grant than the skill declares a mistake, or a choice? Until somebody asks one, this candidate is the more elegant fix to a problem it may be misdescribing.

Practically it is also the most invasive of the three. It reaches outside the vault into how the plugin is installed and how settings are written, which is a surface this project has otherwise kept its hands off. A generated allowlist that silently rewrites a human's settings file would be, in miniature, the same act the ruleset forbids everywhere else: compute granting itself a permit.
