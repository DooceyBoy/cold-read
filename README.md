# Cold Read — ICM Project Editor

Cold Read is a helper that reviews the **context architecture** of an AI project — the files, instructions, examples, and reference material that tell an AI how to do its job (for example, the `CLAUDE.md` or `CONTEXT.md` files that turn a model into a coach, researcher, operator, or specialist). You give it a project you built; it reads that project the way a stranger or a fresh session would, and points out everything material most likely to break when someone other than you tries to use it, at whichever depth you ask for. It looks at **how the project is built, not what it is about**, and it **only critiques and advises — it never rewrites, restructures, or redesigns your work.** You keep the pen.

Created by **Jude Doocey** as a first competition entry and shared with the community.

New to this? Start with the **[plain-English guide](PLAIN_ENGLISH_GUIDE.md)** — it explains everything below in everyday words.

**Version:** v0.1.2.

## What's in the public package

The editor you install is the [`cold-read/`](cold-read/) folder. It contains exactly the competition's five required parts: `identity.md`, `rules.md`, `examples.md`, `reference/`, and `README.md`. The **public package** is that seven-file editor plus this main README, the public file list, judge guide, plain-English guide, license, one sample project, and three short public evidence summaries — exactly 16 files. The exact paths are in [`PUBLIC_PACKAGE_MANIFEST.md`](PUBLIC_PACKAGE_MANIFEST.md). For the full manual see [`cold-read/README.md`](cold-read/README.md); for a one-minute try-it see [`JUDGE_GUIDE.md`](JUDGE_GUIDE.md).

## Fastest route: Claude Code (no download)

Open the AI project you want reviewed in Claude Code and paste:

```text
The open folder is the AI project I want reviewed.

Clone Cold Read from https://github.com/DooceyBoy/cold-read into a temporary folder outside my project. Use all seven Markdown files inside cold-read/ as the review instructions, with rules.md as final authority.

Do not copy anything into, edit, or rewrite my project. Ask whether I want a Quick Review or Full Review.
```

Approve GitHub access if asked, then choose **Quick Review** or **Full Review**. This loads Cold Read for the current session; it does not install a permanent command.

## How to run it in Claude Projects

This is the competition's intended route: put the Cold Read editor folder into a Claude Project, then give that Project something to critique.

**1. Download the editor folder.**

Open `https://github.com/DooceyBoy/cold-read/tree/main/cold-read`. To download just that folder, open `https://download-directory.github.io/`, paste the GitHub folder address into the box, press Enter, and extract the downloaded ZIP.

The extracted editor must keep this exact five-part shape:

```text
cold-read/
├── identity.md
├── rules.md
├── examples.md
├── reference/
│   ├── architecture-judgments.md
│   ├── findings-and-labels.md
│   └── intake-and-review-modes.md
└── README.md
```

**2. Create a new Claude Project.**

Add the `cold-read/` folder to the Project's knowledge. If the interface asks you to select files rather than a folder, add all seven Markdown files shown above and keep the three reference filenames identifiable.

Each part has one job: identity defines the editor, rules own the critique procedure, examples demonstrate good critique, reference holds the frameworks used during judgment, and README explains use. `rules.md` is the final authority on behaviour.

**3. Give Cold Read the project you want reviewed.**

Make a copy of the project you want reviewed so the original stays safe, but **keep its normal folder name** — do not rename it. Keep that copy separate from the `cold-read/` editor folder and from Cold Read's Project knowledge. For example:

```text
your-normal-project-name/
├── CLAUDE.md
├── context/
└── reference/
```

Attach or paste that project into the chat while preserving its normal top-level folder name, tree, and file paths. [`cold-read/README.md`](cold-read/README.md) shows the path-preserving packet format when you need to paste the files as one block.

**4. Ask for the review.**

> Review this project's context architecture for cold-use readiness.

Cold Read will ask whether you want a **Quick Review** or a **Full Review** if you have not already said. It critiques and advises; it does not rewrite the project.

## Quick Review or Full Review

Whichever way you run it, Cold Read offers the same choice when you have not already said which you want:

- **Quick Review** — inspects the complete relevant project, then reports the five most consequential findings.
- **Full Review** — inspects the complete relevant project, reports every distinct material finding, and includes the complete architecture assessment.

Both modes look at your whole project either way — the choice only changes how much of the finding set is detailed back to you. If you already know which you want, just say so in your first message and Cold Read will skip the question.

## What you get back

A review in a fixed shape, opening with one of **five possible results**:

- **CANNOT REVIEW** — there is no project to inspect and no stated purpose; the review names the least it would need to begin.
- **OUT OF SCOPE** — either nothing shows the project is meant to be run by AI, or the whole request was a specialist-fact question (medical, legal, security, financial) that Cold Read has no standing to answer.
- **PARTIAL EVIDENCE** — enough of the setup is missing that a whole-project verdict would be irresponsible; the review covers what is present and names what is missing.
- **REVISION REQUIRED** — one or more material problems were found; the review names every one (Full Review) or the five most consequential (Quick Review), each with its place, its consequence, and the decision you must make.
- **READY FOR COLD TEST** — the best result. Cold Read never declares a project "done" — whether it is finished enough to rely on is your call.

Below the result you get a coverage note on what was inspected and what was excluded, a plain read of the smallest setup your project actually needs (plus any real strengths), findings ranked by named severity (Critical, High, Medium, Low — never a numeric score, never silently capped), any open decisions, and one next thing to try. A Full Review adds the complete architecture read: agent/ownership analysis, routing and handoff analysis, and a prioritized action plan.

## What it changes — and what it leaves to you

Cold Read points at the exact place something breaks, explains the consequence, names the decision, and — where your project's real needs earn it — recommends the conceptual shape a fix should take (which relationship, ownership, or gate is missing). It stops there. It will **not** hand back a rewritten file, a replacement line, a finished agent prompt, or a folder layout to paste in, even if you ask directly. **It points out problems and advises on shape, but leaves the fix to you** — an editor that does the work for you leaves you owning nothing. Cold Read also does not check whether your medical, legal, security, or financial content is factually correct — it reviews the setup, not the subject matter, and says so plainly.

## Try it yourself

[`JUDGE_GUIDE.md`](JUDGE_GUIDE.md) gives a self-contained one-minute test using the sample project [`test-fixtures/nested-specialist.md`](test-fixtures/nested-specialist.md), with clear results you can check.

## Development evidence

These public records summarise checks completed while building Cold Read. They are supporting evidence, not unfinished builds, separate editions, or demo downloads. The editor users install is the seven-file bundle in [`cold-read/`](cold-read/).

- [Independent challenge test](receipts/public/independent-challenge-test.md) — ten independently scored, isolated runs; all ten passed.
- [Self-review test](receipts/public/self-review-test.md) — Cold Read reviewing its own six-file editor and holding its read-only, no-invented-findings boundary.
- [Originality check](receipts/public/originality-check.md) — a recorded wording comparison against the 508-file reference collection; no distinctive copied wording was found.

Each receipt states exactly what its saved evidence covers. Cold Read is an AI review aid, so the builder still checks its findings and makes the final decisions.

## License

[MIT](LICENSE) © 2026 Jude Doocey.
