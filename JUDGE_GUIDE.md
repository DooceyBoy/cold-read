# Judge Guide — Cold Read (a one-minute try-it)

This is a self-contained test you can run in about a minute. It is something you do yourself; it is not a claim that the **fresh-project test** (a brand-new Claude Project with no earlier conversation) was already run. New to Cold Read? See the [plain-English guide](PLAIN_ENGLISH_GUIDE.md).

## Setup (about a minute)

1. Create a new **Claude Project**.
2. Add these five files from [`cold-read/`](cold-read/) as the project's knowledge:
   - `identity.md`
   - `rules.md`
   - `examples.md`
   - `reference/architecture-judgments.md`
   - `reference/findings-and-labels.md`
3. Do **not** add the project you are testing to the knowledge — you paste it into the chat.

## The test project

Use [`test-fixtures/nested-specialist.md`](test-fixtures/nested-specialist.md) — a small "client onboarding" project made specifically for testing, with known problems built in. Paste its contents **into the chat** exactly as written; it is already in the format Cold Read expects.

## The prompt (exact)

> Review this project's context architecture for cold-use readiness. Do not rewrite or redesign it. Give me only the highest-leverage findings.

## What a correct review looks like (results you can check)

- **Result: `REVISION REQUIRED`.**
- **Exactly three findings, in this order:**
  1. **CONTRADICTION** (two instructions disagree) — the main rule says get the client's sign-off before sending, but the delivery step sends automatically.
  2. **MISSING RESPONSIBILITY** (an important approval is missing) — charging the client's fee has no required approval.
  3. **UNOBSERVABLE RULE** (a rule too vague to check) — the rule to "move to the next stage once the work is *solid enough*" gives no way to tell whether it was met.
- **No replacement content** — no rewritten rules, no folder layout, no ready-to-paste fix.
- **No HANDOFF GAP finding.** (A HANDOFF GAP means the project only works because knowledge is still in the builder's head.) This sample project spells out how each step passes its work to the next, so a handoff-gap finding here would be wrong.

## If any of these happen, Cold Read did not behave as intended

- The result is not `REVISION REQUIRED`.
- It supplies a replacement `rules.md`, replacement lines, or a folder layout.
- A HANDOFF GAP finding appears.
- The three findings shrink to fewer, or extra findings are padded on beyond three.
- The vague "solid enough" stage rule is missed, or is called a missing part of the structure instead.
- The missing fee approval is merged into the sign-off contradiction instead of being reported as its own finding.

## Evidence

- [Independent challenge test](receipts/public/independent-challenge-test.md)
- [Self-review test](receipts/public/self-review-test.md)
- [Originality check](receipts/public/originality-check.md)

These are short summaries based on saved records. This guide is something you can run yourself; it is not a claim that the fresh-project test (a brand-new Claude Project with no earlier conversation) was already done.
