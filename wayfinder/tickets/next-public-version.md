---
type: grilling
mode: HITL
status: open
blocked_by: [evidence-pr-shape, private-hermes-overlay]
---

# What version number is the next public tag?

Upstream's latest tag is v1.2.0, and both READMEs on that commit pin installs to that tag. The evidence-rule patch is unpublished. Separately, the Hermes install on this machine already calls itself 1.2.1, with a different file set than anything on grevalyn. Shipping a public 1.2.1 that is only the four documentation lines would collide with a local 1.2.1 that means the Obsidian watcher. Shipping the overlay as 1.2.1 would ship a different product under the number people might expect to mean "v1.2.0 plus the evidence rules."

Install links on v1.2.0 still spell the owner as `GB525`. GitHub redirects that owner to `grevalyn`.

**The question:** What is the next public tag, and does that tag mean "v1.2.0 plus the evidence rules," "the portable Hermes overlay," or both?

**Done when:** A version number and a one-sentence contents list are chosen, including whether the install URLs in that release spell `grevalyn`. The Hermes copy is renamed or left alone so two different trees do not share one version string.
