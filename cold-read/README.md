# Cold Read — Operating Manual

Cold Read is an editor for the context architecture of folder-based AI specialists. You give it a project you have built — a folder that turns a model into a coach, researcher, operator, or the like — and it tells you the few things most likely to break when someone other than you tries to use it. It reviews **how the project is built**, not what it is about, and it **never rewrites or restructures your work** — it hands the decisions back to you.

This folder *is* the editor. Drop it into a Claude Project and Claude becomes Cold Read.

---

## Setup (about 60 seconds)

1. Create a new Claude Project.
2. Add the five files in this `cold-read/` folder as the project's knowledge: `identity.md`, `rules.md`, `examples.md`, and both files in `reference/`. (This operating manual is optional as knowledge — it is for you, not the editor.)
3. That is the whole install. The editor is now the project's context.

**Keep your own project out of the knowledge base.** The thing you want reviewed is not uploaded — you paste it into the chat (next section). That keeps your files and Cold Read's own files cleanly separate, even when they share names.

---

## How to hand Cold Read a project

Paste the project you want reviewed into the chat as one block, in this shape:

```
PROJECT PURPOSE: <one plain sentence — what the project is for>
AI-OPERATING INTENT: <how AI is meant to run this work>
PROJECT TREE: <the folder tree, with paths>

# TARGET: path/to/first-file.md
<the file's contents>

# TARGET: path/to/second-file.md
<the file's contents>
```

The `# TARGET:` header before each file matters — the path is part of what Cold Read judges (a rule in your root means something different from the same rule in a sub-folder), and the headers keep files distinct even if two of them share a name. Include as much of the project as is relevant; you do not have to paste everything.

Then send this prompt:

> **Review this project's context architecture for cold-use readiness. Do not rewrite or redesign it. Give me only the highest-leverage findings.**

---

## What you get back

A short review in a fixed shape:

- **Readiness** — one of `CANNOT REVIEW`, `OUT OF SCOPE`, `PARTIAL EVIDENCE`, `REVISION REQUIRED`, or `READY FOR COLD TEST`. Cold Read never declares your project "done" — whether it is finished enough to rely on is your call.
- **Scope & review depth** — what it looked at, what it inferred, what it could not verify.
- **Necessity read** — the smallest architecture it judged your project actually needs, plus any real strengths (including "this is correctly minimal").
- **Findings** — at most three, most important first. Each names the exact place, the consequence in use, the decision that is yours to make, and a revision target that tells you what the next version must achieve — never the words to achieve it.
- **Missing decisions** and a **next test** to run after you revise.

If your project is sound, you will get few findings or none. That is a real result, not a lazy one — Cold Read is built not to invent problems.

---

## What it will and will not do

- It **will** point at exact weak lines, explain why they break for a stranger, and hand back the decision.
- It **will** refuse to rewrite your files, lay out a folder structure, or give you paste-ready fixes — even if you ask directly. That refusal is the point: an editor that does the work for you leaves you owning nothing.
- It **will** tell you plainly when a question is outside its scope.

- It is **not** a validator of your subject matter. It does not check whether your legal, medical, security, or financial content is correct — it has no standing there and will say so.
- It is **not** a builder. If you need something constructed rather than critiqued, that is a different tool.
- It reviews **context architecture**, not application code quality, UI, or business viability.

---

## Getting a useful review

- Always state the **purpose** and the **AI-operating intent**. Without them, Cold Read cannot tell whether your project is meant to be AI-run at all, and may return `OUT OF SCOPE` or ask you to clarify.
- Paste files **with their paths**. Placement is evidence; a flattened dump of same-named files loses the very thing being judged.
- You do not have to paste everything. Leaving out ordinary implementation, content, or input files — a script, a data file, a notes doc — will not block a verdict: Cold Read judges your architecture, not those contents, and notes them as immaterial omissions. But if you omit files that carry the architecture itself — a routing file, or a context whose contents decide the question — you will get an honest `PARTIAL EVIDENCE` review of what is present rather than a guess about what is not. When in doubt, say what you left out and why.
