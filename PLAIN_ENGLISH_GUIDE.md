# Cold Read in plain English

Cold Read is a helper that checks the setup behind an AI assistant. This guide explains what it does, in everyday words. You do not need any software or AI background to read it.

Throughout, **context architecture** means: the files, instructions, examples, and reference material that tell an AI how to do its job.

## 1. What Cold Read checks

Cold Read looks at the files and rules that tell an AI how to do a particular job — the context architecture. It asks a handful of down-to-earth questions:

- Is every important job covered?
- Do any instructions disagree with each other?
- Can someone tell whether a rule was actually followed?
- Could a new person understand how the project is meant to work?
- Is the project carrying extra files, rules, or AI "agents" that do not help?
- Does important knowledge live only in the builder's head?

If the answer to one of these points to a real problem, Cold Read says so.

## 2. What Cold Read does not do

- It does not rewrite your work.
- It does not hand you a finished replacement file, a finished folder layout, or finished AI-agent instructions.
- It does not decide whether medical, legal, financial, security, or other specialist advice is factually correct. That is for an expert in that field.
- It does not declare a project finished.
- It points out the important decisions — and, where they are earned, the shape a fix should take — and hands the actual writing back to you.

A short way to say this: **the builder keeps the pen.** That means: you receive the review and, when relevant, advice about the shape of a fix, but you decide and write the fix yourself.

## 3. The two ways to ask for a review

When you ask Cold Read for a review and do not say how much detail you want, it asks you one plain question first:

- **Quick Review** — Cold Read looks at your whole project, then tells you the five most important things it found.
- **Full Review** — Cold Read looks at your whole project, then tells you everything it found, plus a complete read of how the project is structured.

Neither option is the "real" one with the other as an afterthought — they are both complete answers to two different questions. If you already know which you want, just say "Quick Review" or "Full Review" and Cold Read skips the question.

Either way, Cold Read looks at the whole project first. The choice only changes how much of what it found gets written out in the reply.

## 4. How Cold Read reaches a result

Cold Read works through these steps:

1. Check whether enough information was provided to review anything at all.
2. If you have not said which depth you want, ask — Quick Review or Full Review.
3. Look at the complete project relevant to the review, noting anything it could not read or chose not to load (and why).
4. Work out the smallest setup the project genuinely needs — including whether it needs any AI "agents" at all.
5. Look for missing jobs, unclear rules, conflicting instructions, and knowledge that cannot travel from one person or session to the next.
6. Group different symptoms together only when they come from the same underlying problem — and keep genuinely separate problems separate, even when they get the same problem name.
7. In a Quick Review, report the five most important findings and say plainly how many more exist. In a Full Review, report every one it found — Cold Read does not hold results back to keep the reply short.
8. Explain the consequence and the decision for each finding, and — when the project's own needs call for it — describe the shape a fix should take, without writing the fix itself.

## 5. How important is important? (severity)

Cold Read ranks findings by how much they matter, using four plain words instead of a score:

- **Critical** — something that could go wrong in a way that is hard to undo, visible to outsiders, or touches money, safety, legal risk, or someone's identity.
- **High** — something likely to behave wrongly right now, a real disagreement between two rules, or a missing point where a person should approve before something consequential happens.
- **Medium** — something likely to drift or confuse people over time, or an important claim that has never actually been shown to work.
- **Low** — a real but minor weakness — naming, tidiness, ease of navigation — with little immediate consequence.

This is separate from the *type* of problem (see section 7 below) — the type says what kind of problem it is; the severity says how much it matters right now.

## 6. Advice on shape, without a finished fix

Cold Read can now explain, in plain terms, what shape a fix should take — for example, that a project needs one clear owner for a shared rule, or that a risky action needs a person's approval before it happens, or that a project has grown more AI "agents" than its work actually needs. It still will not write the file, the folder, or the finished agent instructions that would put that shape in place — that part stays yours.

## 7. What each file does

**The editor itself** (the part that does the reviewing) follows the competition's five-part structure:

### identity.md
Defines what Cold Read is, what it reviews, and where it must stop.

### rules.md
Contains the steps Cold Read follows when it reviews a project.

### examples.md
Shows what a good Cold Read response looks like in different situations.

### reference/architecture-judgments.md
Lists the questions Cold Read uses to judge whether a project's setup makes sense.

### reference/findings-and-labels.md
Explains the names Cold Read gives to different types of problems, and how importance is ranked.

### cold-read/README.md
Explains how to install Cold Read and give it a project to review.

**The rest of the public files:**

### README.md
The main introduction for readers, and the easy onboarding walkthrough.

### JUDGE_GUIDE.md
A quick test that lets someone see Cold Read working.

### LICENSE
The MIT permission notice. It allows community reuse while keeping Jude Doocey's copyright notice.

### PUBLIC_PACKAGE_MANIFEST.md
The public file list. It says exactly which files belong in the clean public release.

### test-fixtures/nested-specialist.md
A sample project used to test Cold Read. It contains known problems, so readers can check whether Cold Read finds them.

### Public evidence summaries
Short, readable accounts of the tests and the originality check. The detailed internal records are kept separately.

## 8. Results in plain English

Every Cold Read review opens with one of five results. The official names stay the same; here is what each one means:

### CANNOT REVIEW
There is not enough project information to begin.

### OUT OF SCOPE
The request is not a setup review that Cold Read can responsibly carry out.

### PARTIAL EVIDENCE
Some important instructions are missing, so Cold Read can review only what it can see.

### REVISION REQUIRED
Cold Read found one or more important problems that need a decision from the builder.

### READY FOR COLD TEST
The files look ready for a fresh person or session to try. This does not mean the project is finished or guaranteed to work.

## 9. How to run it in Claude Projects

1. Open `https://github.com/DooceyBoy/cold-read/tree/main/cold-read` in your browser.
2. Download that folder. One simple option is `https://download-directory.github.io/`: paste the GitHub folder address there, press Enter, and extract the downloaded ZIP.
3. Check that the editor still has exactly the competition's five parts:

```text
cold-read/
├── identity.md
├── rules.md
├── examples.md
├── reference/
│   ├── architecture-judgments.md
│   └── findings-and-labels.md
└── README.md
```

4. Create a new Claude Project and add the complete `cold-read/` folder to its knowledge. If Claude asks for files individually, add all six Markdown files shown above.
5. Make a copy of the target project so the original stays safe, but keep its normal folder name — do not rename it. Keep it separate from the editor, then attach or paste it into the chat with its top-level folder name, tree, paths, and file contents preserved. `cold-read/README.md` shows the exact `# TARGET:` format.
6. Type: `Review this project's context architecture for cold-use readiness.`
7. Choose Quick Review or Full Review when Cold Read asks.

That is the competition's intended setup: the five-part editor folder goes into a Claude Project, and the work being critiqued goes into the chat.

## 10. Problem names in plain English

When Cold Read finds a problem, it gives it one of seven names — this is the problem's *type*, separate from its *severity* (section 5). Here is what each name means:

### MISSING RESPONSIBILITY
An important job, connecting step, or approval is missing — nothing in the project owns it.

### UNWARRANTED COMPLEXITY
The project has extra structure, files, rules, or AI agents that do not earn their place.

### MISPLACED OR DUPLICATED OWNERSHIP
The same rule is kept in more than one place (so the copies can drift apart over time), or a rule sits at the wrong level.

### CONTRADICTION
Two instructions disagree.

### UNOBSERVABLE RULE
A rule is too vague for anyone to tell whether it was followed.

### UNPROVEN BEHAVIOR
The project promises an important behaviour but does not show it happening in an example or a test.

### HANDOFF GAP
The project works only because important knowledge is still in the builder's head. A new person or a fresh session would not know what to do.

## 11. Testing words in plain English

### Self-review test
Cold Read reviewed its own project. This checks honesty and restraint, but it is not independent proof.

### Independent challenge test
An earlier core version of Cold Read was given difficult sample projects in ten isolated test sessions. These were controlled model tests, not ten live Claude Projects. Its first answers were saved and checked against expected results.

### Fresh-project test
A real, brand-new Claude Project with no earlier conversation and no hidden background. This live setup test is still deferred and must not be presented as completed.

### Sample project
A project made specifically for testing, with known problems built in.

### Public file list
The exact list of files allowed in the clean public release.

### Digital fingerprint
A long value used to check whether a file has changed. Its technical name is SHA-256.
