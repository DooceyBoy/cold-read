# Cold Read — ICM Project Editor

Cold Read is a helper that reviews the **context architecture** of an AI project — the files, instructions, examples, and reference material that tell an AI how to do its job (for example, the `CLAUDE.md` or `CONTEXT.md` files that turn a model into a coach, researcher, operator, or specialist). You give it a project you built; it reads that project the way a stranger or a fresh session would, and points out the few things most likely to break when someone other than you tries to use it. It looks at **how the project is built, not what it is about**, and it **only points out problems — it never rewrites, restructures, or redesigns your work.** You keep the pen.

Created by **Jude Doocey** as a first competition entry and shared with the community.

New to this? Start with the **[plain-English guide](PLAIN_ENGLISH_GUIDE.md)** — it explains everything below in everyday words.

**Version:** v0.1.1 candidate — this is a candidate build; a final version tag is not yet assigned.

## What's in the public package

The editor you install is the [`cold-read/`](cold-read/) folder — five files plus its own short manual. The **public package** — the exact list is in the [public file list](PUBLIC_PACKAGE_MANIFEST.md) — is that editor plus this README, a Judge Guide, the plain-English guide, the license, one sample project used for testing, and short public test summaries, and nothing else. For the full manual see [`cold-read/README.md`](cold-read/README.md); for a one-minute try-it see [`JUDGE_GUIDE.md`](JUDGE_GUIDE.md).

## Install and run

Cold Read runs inside a **Claude Project** — that is where it is meant to be used.

1. Create a new Claude Project.
2. Add the five files in [`cold-read/`](cold-read/) as the project's **knowledge**: `identity.md`, `rules.md`, `examples.md`, and both files in `reference/`. That is the whole install — the project is now Cold Read.
3. **Keep the project you want reviewed out of the knowledge.** You paste it into the chat instead (next step), so the editor's own files and your files stay separate and never mix up, even if they share names.

### Give Cold Read a project to review

Paste the project **into the chat** as one block — never as project knowledge — in this shape:

```
PROJECT PURPOSE: <one plain sentence — what the project is for>
AI-OPERATING INTENT: <how AI is meant to run this work>
PROJECT TREE: <the folder tree, with paths>

# TARGET: path/to/first-file.md
<the file's contents>

# TARGET: path/to/second-file.md
<the file's contents>
```

The `# TARGET:` line before each file matters — where a file sits is part of what Cold Read judges, and these lines keep files separate even when two share a name.

### The exact first prompt

> Review this project's context architecture for cold-use readiness. Do not rewrite or redesign it. Give me only the highest-leverage findings.

## What you get back

A short review in a fixed shape, opening with one of **five possible results**:

- **CANNOT REVIEW** — there is no project to inspect and no stated purpose; the review names the least it would need to begin.
- **OUT OF SCOPE** — either nothing shows the project is meant to be run by AI, or the whole request was a specialist-fact question (medical, legal, security, financial) that Cold Read has no standing to answer.
- **PARTIAL EVIDENCE** — enough of the setup is missing that a whole-project verdict would be irresponsible; the review covers what is present and names what is missing.
- **REVISION REQUIRED** — an important problem was found; the review names the place, the consequence, and the decision you must make.
- **READY FOR COLD TEST** — the best result. Cold Read never declares a project "done" — whether it is finished enough to rely on is your call.

Below the result you get a short note on what was looked at, a plain read of the smallest setup your project actually needs (plus any real strengths), up to three important findings, any open decisions, and one next thing to try.

## What it changes — and what it leaves to you

Cold Read points at the exact place something breaks, explains the consequence, and names the decision — and stops there. It will **not** hand back a rewritten file, a replacement line, or a folder layout to paste in, even if you ask directly. **It points out problems but leaves the fixes to you** — an editor that does the work for you leaves you owning nothing. Cold Read also does not check whether your medical, legal, security, or financial content is factually correct — it reviews the setup, not the subject matter, and says so plainly.

## Try it yourself

[`JUDGE_GUIDE.md`](JUDGE_GUIDE.md) gives a self-contained one-minute test using the sample project [`test-fixtures/nested-specialist.md`](test-fixtures/nested-specialist.md), with clear results you can check.

## Evidence (public summaries)

- [Independent challenge test](receipts/public/independent-challenge-test.md) — a summary of an independent test of this build.
- [Self-review test](receipts/public/self-review-test.md) — the editor reviewing its own project; a self-review, not proof it works on other people's projects.
- [Originality check](receipts/public/originality-check.md) — a check of the finished wording against the reference material used during development.

These are short summaries based on saved records. Cold Read is a candidate build: it has not yet been tried in a **fresh-project test** (a brand-new Claude Project with no earlier conversation), it is not claimed to be safe for production use, it does not guarantee correctness, and it is not claimed to work on any and all real projects.

## License

[MIT](LICENSE) © 2026 Jude Doocey.
