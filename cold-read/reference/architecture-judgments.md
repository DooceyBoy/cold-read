# reference/architecture-judgments.md

The ten things you look at when you judge a project's context architecture. Consult this after the Necessity Engine has told you what the project actually needs (see `rules.md`, Steps 2–3). Each judgment below says what a real problem looks like **and** where its limit is — the case where the thing you might flag is actually correct. Honor the limits; they are what keep you from selling architecture nobody needs.

This file is knowledge, not procedure. It does not restate the intake sequence, the output shape, or the anti-rewrite rule — those live in `rules.md`.

---

## J1 — Necessity and complexity

**What you are checking:** whether the amount of architecture matches what the purpose genuinely requires — no important responsibility missing, no structure the work does not earn.

**A real problem looks like:** a project with three clearly different modes of work all crammed into one undifferentiated instruction file; or the reverse — a single trivial task wrapped in nested agents, sub-contexts, and a reference library it never draws on.

**The limit:** a minimal project is not a deficient one. If one root file does the whole job, that is the right answer, not an early draft of a bigger system. Never treat simplicity as immaturity.

---

## J2 — Context placement

**What you are checking:** whether each piece of information sits at the narrowest level where it is needed, while the project still keeps a legible top-level orientation.

**A real problem looks like:** a rule that only applies to one client, one stage, or one mode living in the global instructions where every unrelated task inherits it; or the project's current working state baked into permanent instructions so it goes stale and misleads.

**The limit:** a small, deliberate repetition at the top for orientation can be fine. Placement is about where a responsibility *lives and is owned*, not about never mentioning something twice. Judge the level, not the word count.

---

## J3 — Routing

**What you are checking:** whether a user or a fresh model can tell where to go, what to load, and what to ignore for the task in front of them.

**A real problem looks like:** a root file that reads as a data dump rather than a map; an instruction to "read everything before starting," which makes every task pay for every file and buries the relevant material in noise; or no way at all to tell which part of the project governs a given task.

**The limit:** routing can take many valid shapes — a single well-scoped file, nested local instructions, an index, or the conventions of the host tool. Judge whether the route is discoverable and consistent for *this* project's own ecosystem. Do not require a particular file or a particular name.

---

## J4 — Canonical ownership

**What you are checking:** whether each stable responsibility has one clear owner, so there is never doubt about which instruction governs.

**A real problem looks like:** the same rule stated independently in two files, so a later edit to one leaves the other silently wrong; or two files that both claim authority over the same decision and can drift apart.

**The limit:** bounded, intentional repetition that aids navigation is acceptable. Duplication becomes a finding when ownership is ambiguous, when the copies can diverge unnoticed, or when a reader cannot tell which copy is authoritative. If two copies already say different things, that is the stronger, separate problem of contradiction.

---

## J5 — Rule quality and observability

**What you are checking:** whether the project's rules are specific enough that someone could tell whether they were followed.

**A real problem looks like:** "use good judgment and be helpful," which cannot be observed, checked, or consistently applied; a capability instruction so vague it gives no real trigger; or a plain-prose "never do X" standing in for a boundary that only real structure — a permission, a script, a gate — could actually guarantee.

**The limit:** not every direction can or should become a testable rule. Taste and tone are legitimately directional. Reserve this judgment for rules that are meant to govern behavior but are written so loosely that two readers would apply them differently, and for prose promises pretending to be enforcement.

---

## J6 — Reference loading

**What you are checking:** whether stable reference material and run-specific working material are distinguishable, and whether references are loaded for the task that needs them rather than all at once.

**A real problem looks like:** a reference folder that gets pulled into every task regardless of relevance; stable knowledge and this-run inputs blended together so the model cannot tell which is which; or a reference that exists but has no rule saying when it applies.

**The limit:** a small project may correctly have no reference layer at all. A reference is warranted only when there is stable shared knowledge that some tasks need and others do not. Do not demand a reference folder; judge only the references that exist, plus any genuinely missing one the work clearly requires.

---

## J7 — Capability triggers

**What you are checking:** whether every tool, skill, hook, connector, or sub-agent the project lists has a stated condition for when and why it fires.

**A real problem looks like:** a capability named as "available" with no trigger, so the model either overuses it or ignores it entirely; or a capability whose trigger exists but is too vague to act on.

**The limit:** you judge whether the wiring is present and clear, not whether a particular tool is the objectively best choice for the job — that is the builder's call. A capability that is genuinely not needed is a matter for J1 (excess), not this judgment.

---

## J8 — Review and approval gates

**What you are checking:** whether human review appears where the stakes call for it — and not everywhere by reflex.

**A real problem looks like:** an action that is binding, irreversible, externally visible, sensitive, or dependent on human judgment, with no point at which a person has to approve before it proceeds.

**The limit:** gates are earned by consequence, not added for their own sake. A harmless, reversible, low-stakes flow does not need a gate, and demanding one there is itself a mistake. A gate is warranted only where the action carries real weight — binding, hard to reverse, externally visible, sensitive, or dependent on human judgment — and reaching for one as a precaution, or because a checkpoint feels responsible, inverts the test. Clean structure never substitutes for a warranted gate, but risk — not habit — is what makes one warranted.

---

## J9 — Behavioral evidence

**What you are checking:** whether the project's claims about how it behaves are actually demonstrated, rather than merely asserted by its structure.

**A real problem looks like:** a folder that looks complete — every file in place, every role named — but with nothing showing that the promised behavior actually happens: no worked example, no test prompt, no record of a run. The architecture looks finished; the behavior is unproven. This is the specific gap where a project passes inspection by structure and fails in use.

**The limit:** you are not a factual or security verifier. If a claim needs specialist domain expertise to check, an unproven behavior is an evidence gap or out of your scope — not something you validate yourself. Distinguish what the project was *designed* to do, *built* to do, and *shown* to do; only the last is proof. Proof is required **in proportion to the claim.** A material behavioral claim — one that is risky, complex, or explicitly asserts reliability ("always refuses…", "never sends without approval") — needs a demonstration before a stranger should rely on it. An ordinary, clearly-specified instruction does not become a finding simply because no run is attached; the gap is real only when the behavior's consequence or opacity makes the missing demonstration matter. Do not convert every unexecuted instruction into an unproven behavior — that is calibration failure, not rigor.

---

## J10 — Cold-handoff readiness

**What you are checking:** whether a required newcomer — a teammate, a client, or a fresh session — could understand the project's purpose, entry point, workflow, current state, and the reasons behind its shape, at the depth this project actually needs.

**A real problem looks like:** a project that only works because the builder remembers how it is meant to run; a README that says "run the normal workflow" without naming the first step, the required input, or the expected output; or key decisions that live only in the builder's memory.

**The limit:** a disposable, single-user experiment needs almost no handoff surface, and demanding documentation for an audience it does not have is a mistake. Handoff need rises with duration, collaborators, consequence, and reuse. Judge against the audience the project actually has.
