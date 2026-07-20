# Cold Read in plain English

Cold Read is a helper that checks the setup behind an AI assistant. This guide explains what it does, in everyday words. You do not need any software or AI background to read it.

Throughout, **context architecture** means: the files, instructions, examples, and reference material that tell an AI how to do its job.

## 1. What Cold Read checks

Cold Read looks at the files and rules that tell an AI how to do a particular job — the context architecture. It asks a handful of down-to-earth questions:

- Is every important job covered?
- Do any instructions disagree with each other?
- Can someone tell whether a rule was actually followed?
- Could a new person understand how the project is meant to work?
- Is the project carrying extra files or rules that do not help?
- Does important knowledge live only in the builder's head?

If the answer to one of these points to a real problem, Cold Read says so.

## 2. What Cold Read does not do

- It does not rewrite your work.
- It does not design a replacement set of files for you.
- It does not decide whether medical, legal, financial, security, or other specialist advice is factually correct. That is for an expert in that field.
- It does not declare a project finished.
- It points out the important decisions and hands them back to you.

A short way to say this: **the builder keeps the pen.** That means: you receive the review, but you decide and write the fix.

## 3. How Cold Read reaches a result

Cold Read works through six simple steps:

1. Check whether enough useful information was provided to review anything at all.
2. Work out the smallest setup the project genuinely needs.
3. Look for missing jobs, unclear rules, conflicting instructions, and knowledge that cannot travel from one person or session to the next.
4. Group different symptoms together when they come from the same underlying problem.
5. Return no more than three important findings — the ones that matter most.
6. Explain the consequence and the decision for each finding, but leave the fix to you.

## 4. What each file does

**The editor itself** (the part you install):

### identity.md
Defines what Cold Read is, what it reviews, and where it must stop.

### rules.md
Contains the steps Cold Read follows when it reviews a project.

### examples.md
Shows what a good Cold Read response looks like in different situations.

### reference/architecture-judgments.md
Lists the questions Cold Read uses to judge whether a project's setup makes sense.

### reference/findings-and-labels.md
Explains the names Cold Read gives to different types of problems.

### cold-read/README.md
Explains how to install Cold Read and give it a project to review.

**The rest of the public files:**

### README.md
The main introduction for readers.

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

## 5. Results in plain English

Every Cold Read review opens with one of five results. The official names stay the same; here is what each one means:

### CANNOT REVIEW
There is not enough project information to begin.

### OUT OF SCOPE
The request is not a setup review that Cold Read can responsibly carry out.

### PARTIAL EVIDENCE
Some important instructions are missing, so Cold Read can review only what it can see.

### REVISION REQUIRED
Cold Read found an important problem that needs a decision from the builder.

### READY FOR COLD TEST
The files look ready for a fresh person or session to try. This does not mean the project is finished or guaranteed to work.

## 6. Problem names in plain English

When Cold Read finds a problem, it gives it one of seven names. Here is what each one means:

### MISSING RESPONSIBILITY
An important job, connecting step, or approval is missing — nothing in the project owns it.

### UNWARRANTED COMPLEXITY
The project has extra structure, files, or rules that do not earn their place.

### MISPLACED OR DUPLICATED OWNERSHIP
The same rule is kept in more than one place (so the copies can drift apart over time), or a rule sits at the wrong level.

### CONTRADICTION
Two instructions disagree.

### UNOBSERVABLE RULE
A rule is too vague for anyone to check whether it was followed.

### UNPROVEN BEHAVIOR
The project promises an important behaviour but does not show it happening in an example or a test.

### HANDOFF GAP
The project works only because important knowledge is still in the builder's head. A new person or a fresh session would not know what to do.

## 7. Testing words in plain English

### Self-review test
Cold Read reviewed its own project. This checks honesty and restraint, but it is not independent proof.

### Independent challenge test
Cold Read was given difficult sample projects in fresh sessions. Its first answers were saved and checked against expected results.

### Fresh-project test
A brand-new Claude Project with no earlier conversation and no hidden background. This test is still deferred and must not be presented as completed.

### Sample project
A project made specifically for testing, with known problems built in.

### Public file list
The exact list of files allowed in the clean public release.

### Digital fingerprint
A long value used to check whether a file has changed. Its technical name is SHA-256.
