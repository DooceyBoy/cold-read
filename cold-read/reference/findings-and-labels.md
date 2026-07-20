# reference/findings-and-labels.md

How to name and phrase a finding. Consult this once you have a real problem to report (see `rules.md`, Steps 6–8). It holds the seven labels, the order that decides which one applies when several seem to, how severity differs from a label, the completeness and grouping tests, and the craft of writing a handback that does not slip into rewriting.

The operative anti-rewrite rule and its paste-test are not here — they live in `rules.md`, Step 10. This file only describes the labels, severity, completeness, and the phrasing.

---

## The seven labels

Every finding gets exactly one, the root cause — the single thing the builder must resolve first.

1. **MISSING RESPONSIBILITY** — a structural element the project genuinely needs is absent: no way to route between materially different modes; a capability that is needed but has no trigger at all; a consequential action with no approval gate. *A deficit.* This label is for a missing structural role — not for information that exists but is trapped in the builder's head, which is a handoff gap.

2. **UNWARRANTED COMPLEXITY** — structure or ceremony the purpose does not earn: nested agents for a single task, a reference layer with nothing stable to hold, gates on reversible low-stakes actions, folders that add navigation cost without adding a distinct job. *A surplus.* Also the home for a capability that is present but not needed at all.

3. **MISPLACED OR DUPLICATED OWNERSHIP** — a responsibility sits at the wrong level, or is owned in more than one place so the copies can drift while they currently still agree. A local rule stranded in the global root; the same instruction independently maintained in two files.

4. **CONTRADICTION** — two instructions or surfaces already disagree. Not "could drift" but *already conflicting*: one file says review is required, another says ship automatically.

5. **UNOBSERVABLE RULE** — a rule too vague for anyone to tell whether it was followed, or a plain-prose promise standing in for a boundary only structure could enforce. Includes a needed capability whose trigger is present but too vague to act on.

6. **UNPROVEN BEHAVIOR** — the project claims a behavior but shows nothing that it holds: no example, no test, no run. The structure looks complete; the behavior is asserted, not demonstrated. Apply this only to a **material** behavioral claim — one whose stakes, complexity, or explicit assertion of reliability make demonstration necessary before a stranger should trust it (a claimed refusal, a safety guarantee, an "always / never" promise). An ordinary, clearly-specified instruction that a reader can plainly see how to follow is not unproven merely for lacking an attached run; demanding an example for every rule collapses positive restraint.

7. **HANDOFF GAP** — the project works only because knowledge lives in the builder's head: a required newcomer could not enter cold, *or* a later, distinct task or session cannot receive or recognize what an earlier one produced because the connecting information was never externalized. This label owns cold-entry, documentation, and cross-task continuity failures.

---

## Precedence — which label wins when several seem to fit

Run the necessity read first (it usually settles things), then apply this order. The root label is the one earliest in this list that genuinely applies, because it is the thing the builder must resolve before the others even make sense:

1. **CONTRADICTION** — an active conflict is the most urgent thing to resolve; nothing downstream can be trusted until it is.
2. **MISSING RESPONSIBILITY / UNWARRANTED COMPLEXITY** — the necessity question: should this element exist at all? Settle that before anything about where it lives or how it reads.
3. **MISPLACED OR DUPLICATED OWNERSHIP** — given the element should exist, is it in the right place and owned once?
4. **UNOBSERVABLE RULE** — given it exists and is well-placed, can anyone tell whether it is being followed?
5. **UNPROVEN BEHAVIOR** — given it is well-formed, is it actually demonstrated?
6. **HANDOFF GAP** — given the architecture is sound, can a newcomer operate it?

A project may carry several findings with several labels. Precedence decides the label *within one finding*, not across the project.

---

## Disambiguation — the boundaries that get confused

- **MISSING RESPONSIBILITY vs HANDOFF GAP.** Ask whether a *structure* is absent or whether *knowledge* cannot travel. No router where modes diverge is missing structure → MISSING RESPONSIBILITY. But when the structure exists — a router is present, the stages are named — and the defect is that a later, *distinct* task or session cannot receive or recognize what an earlier one produced (no passed inputs, no persisted outputs, no next-task entry contract, or stage rules that resolve only because the builder remembers "the usual way"), the root cause is that knowledge cannot cross the boundary → HANDOFF GAP. Reserve MISSING RESPONSIBILITY for a genuinely absent structural role; do not label a continuity-across-tasks failure MISSING merely because you can phrase the gap as "no handoff step exists." If a continuity defect and a separate cold-entry/documentation defect both appear, each is its own finding — do not spend the HANDOFF GAP label on the lesser one and mislabel the continuity root. Conversely, when a router-plus-stages project fails only because stage selection, private stage conventions, and cross-task continuity are *all* un-externalized, those are symptoms of one builder-head defect and are reported as a single HANDOFF GAP, not as separate MISSING RESPONSIBILITY and UNOBSERVABLE RULE findings — the operative grouping rule lives in `rules.md`, Step 6.

- **The unwired capability, three ways.** Run necessity first. Not needed at all → UNWARRANTED COMPLEXITY. Needed, but no trigger exists → MISSING RESPONSIBILITY. Needed, trigger exists but is too vague to act on → UNOBSERVABLE RULE.

- **Indiscriminate reference loading, two ways.** If the problem is that *no rule says what to load when*, the root cause is missing routing → MISSING RESPONSIBILITY. If the problem is that there is *far more reference material than the work needs*, the root cause is excess → UNWARRANTED COMPLEXITY. Precedence breaks the tie: settle whether the material should exist before you worry about how it is routed.

- **DUPLICATED OWNERSHIP vs CONTRADICTION.** Copies that currently agree but can drift → MISPLACED OR DUPLICATED OWNERSHIP. Copies that already say different things → CONTRADICTION.

- **UNOBSERVABLE RULE vs UNPROVEN BEHAVIOR.** The rule is too vague to check → UNOBSERVABLE RULE. The rule is specific but nothing shows it holds → UNPROVEN BEHAVIOR. If a rule is both vague *and* undemonstrated, the vagueness is the root cause — label it UNOBSERVABLE RULE and note the missing demonstration as part of the consequence. Do not file it twice.

---

## Severity is a different axis from the label

A **label** (above) names the *type* of problem — its root cause. **Severity** (`rules.md`, Step 7: Critical, High, Medium, Low) names its *consequence* — how much it matters right now. The two are independent: a `CONTRADICTION` can be Critical (two files disagree about whether a payment gate exists) or Medium (two internal style notes disagree about a cosmetic convention). A `HANDOFF GAP` can be High (nobody but the builder can run the whole workflow) or Low (one folder's naming convention is undocumented but guessable). Never infer severity from the label alone, and never let a label's usual severity substitute for judging this instance on its own facts.

Tie-break order when two findings land on the same severity (fullest form of `rules.md`, Step 7): blast radius first (how much of the project or how many users a failure touches), then likelihood — an observed failure outranks a hypothetical one — then frequency (how often the triggering situation occurs), then recoverability (can it be walked back, or is it a one-way door), then foundational dependency (does resolving this unblock judgment of other things), and only last, evidence strength (a well-evidenced finding edges out a thinner one that is otherwise equivalent).

## Completeness and grouping

Full Review reports every distinct material finding; nothing is dropped for ranking low (`rules.md`, Steps 6–7). Two tests decide whether something you noticed is one finding, several findings, or no finding at all:

- **Is it material?** A distinct material finding has its own underlying failure, decision, or consequence. Spelling, pure taste, harmless duplication that cannot drift apart, and speculative improvements the project never claimed to need are not material — do not inflate the inventory with them to look thorough.
- **Is it one cause or several?** Group repeated symptoms only when they trace to one underlying decision the builder resolves in one move (see the router-plus-stages example in `rules.md`, Step 6, and the disambiguation entries above) — and when you group, list every affected or conflicting location inside that single finding; a grouped finding that hides how many places it touches is a silent omission by another name. Keep two problems separate whenever they have independent causes, even if they share a label — two unrelated contradictions are two findings, not one padded finding or one thinned finding. Never merge distinct builder decisions just to shorten the response; that is the same silent suppression the completeness rule forbids, wearing a tidier label.

## Writing the handback

A finding is only useful if it hands the builder a decision, not an answer. The craft is to be exact about the *problem* and silent about the *solution*.

- **Name the responsibility, not the fix.** "There is no point where a human approves the outbound message before it sends" tells the builder what is missing. It does not tell them where to put the gate, what to call it, or what it should say — those are theirs.

- **Make the revision target a property or a question, never content.** State what the next version must achieve ("the routing must let a reader tell which files load for a drafting task versus a review task") or what it must decide ("which of these two files owns the tone rules"). Before you send any revision target — or any architecture recommendation — run it through the paste-test — the operative test and the action it requires live in `rules.md`, Step 10. This file names the craft; that file owns the rule.

- **Keep forcing questions open.** A good forcing question exposes the decision the builder has been avoiding ("what has to be true before this action is safe to take without review?"). A bad one hides your preferred mechanism inside a yes/no ("should you add an approval file here?"). Ask what they must decide; never propose the thing and ask them to nod.

- **Tie every finding to a consequence in use.** Not "this rule is vague" but "this rule is vague, so two different sessions will resolve it two different ways, and the output a client sees depends on which one they hit." The consequence is what makes a finding land as judgment rather than nitpicking.
