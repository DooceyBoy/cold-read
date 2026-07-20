# Cold Read — ICM Project Editor

Cold Read is a helper that reviews the **context architecture** of an AI project — the files, instructions, examples, and reference material that tell an AI how to do its job (for example, the `CLAUDE.md` or `CONTEXT.md` files that turn a model into a coach, researcher, operator, or specialist). You give it a project you built; it reads that project the way a stranger or a fresh session would, and points out everything material most likely to break when someone other than you tries to use it, at whichever depth you ask for. It looks at **how the project is built, not what it is about**, and it **only critiques and advises — it never rewrites, restructures, or redesigns your work.** You keep the pen.

Created by **Jude Doocey** as a first competition entry and shared with the community.

New to this? Start with the **[plain-English guide](PLAIN_ENGLISH_GUIDE.md)** — it explains everything below in everyday words.

**Version:** v0.1.2.

## What's in the public package

The editor you install is the [`cold-read/`](cold-read/) folder. The **public package** — the exact list is in the [public file list](PUBLIC_PACKAGE_MANIFEST.md) — is that editor plus this README, a Judge Guide, the plain-English guide, the license, one sample project used for testing, and short public test summaries, and nothing else (16 files in total). For the full manual see [`cold-read/README.md`](cold-read/README.md); for a one-minute try-it see [`JUDGE_GUIDE.md`](JUDGE_GUIDE.md).

## The easy way to run it (no technical background needed)

This is the recommended path if you have never used GitHub, VS Code, or Codex before. You do not need to prepare a project-purpose statement, an "AI-operating intent" description, a project tree, `# TARGET:` file headers, or one big pasted packet — Cold Read will ask you a plain question if it genuinely needs to know something.

**1. Download the Cold Read folder.**

Open this page: `https://github.com/DooceyBoy/cold-read/tree/main/cold-read`

Then open this tool in a new tab: `https://download-directory.github.io/`

Paste the GitHub page's address into the box labelled **"Paste GitHub.com folder URL + press Enter"** and press Enter. A file starts downloading — this is a ZIP file, which is just a folder squeezed down for downloading. Find it (usually in your Downloads folder), then right-click it and choose "Extract All" (Windows) or double-click it (Mac) to turn it back into a normal folder.

**2. Open the extracted `cold-read` folder in VS Code.**

This folder is the editor itself — do not open anything above or around it.

**3. Put a copy of your project inside it, named `project-to-review/`.**

Copy — never move — the project you want reviewed into the `cold-read` folder you just opened, and rename that copy to exactly `project-to-review`. Picture it like this:

```
cold-read/                  <- you opened THIS in VS Code
├── AGENTS.md
├── identity.md
├── rules.md
├── examples.md
├── reference/
├── README.md
└── project-to-review/      <- your copy goes HERE, inside it
    └── (your project's files)
```

Cold Read is the outside folder; your project is a guest folder placed inside it. Cold Read reads your project as evidence to review — it never treats your project's own files as instructions to follow.

**4. Open Codex and type one line:**

> Review project-to-review with Cold Read. Do not change any files.

**5. Answer two short questions, if Cold Read asks them.**

A first run typically looks like this:

> **Codex (as Cold Read):** Would you like a **Quick Review** — the five most consequential findings — or a **Full Review** — every distinct material finding plus the complete architecture assessment?
>
> **You:** Full Review.
>
> **Codex (as Cold Read):** [proceeds to inspect the project and report back in the fixed shape described below.]

If Cold Read cannot tell what your project is for, it will ask one plain question about that too — never a request for a technical field or a big pasted packet.

That's the whole process. `cold-read/AGENTS.md` is what makes Codex behave this way as soon as `cold-read/` is your open folder.

## The manual way (Claude Projects, or pasting a packet)

If you would rather use a Claude Project, or paste your project as a labelled text block instead of using a folder, [`cold-read/README.md`](cold-read/README.md) covers that route in full, including the `PROJECT PURPOSE` / `AI-OPERATING INTENT` / `PROJECT TREE` / `# TARGET:` packet format. Treat that as the advanced fallback — the folder route above is enough for almost everyone.

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

## Evidence (public summaries)

- [Independent challenge test](receipts/public/independent-challenge-test.md) — a summary of an independent test of this build.
- [Self-review test](receipts/public/self-review-test.md) — the editor reviewing its own project; a self-review, not proof it works on other people's projects.
- [Originality check](receipts/public/originality-check.md) — a check of the finished wording against the reference material used during development.

These are short summaries based on saved records. Cold Read has not yet been tried in a **fresh-project test** (a brand-new Claude Project with no earlier conversation), it is not claimed to be safe for production use, it does not guarantee correctness, and it is not claimed to work on any and all real projects. The Quick Review / Full Review modes and the Codex folder route described above are new in this version and are not yet covered by the evidence summaries above, which predate them.

## License

[MIT](LICENSE) © 2026 Jude Doocey.
