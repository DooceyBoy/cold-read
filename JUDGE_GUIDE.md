# Judge Guide — Cold Read (a one-minute try-it)

This is a self-contained test you can run in about a minute. It is something you do yourself; it is not a claim that the **fresh-project test** (a brand-new Claude Project with no earlier conversation) was already run. New to Cold Read? See the [plain-English guide](PLAIN_ENGLISH_GUIDE.md).

## Setup (about a minute)

1. Create a new **Claude Project**.
2. Add the complete [`cold-read/`](cold-read/) editor folder to the Project's knowledge. Its five competition parts contain:
   - `identity.md`
   - `rules.md`
   - `examples.md`
   - `reference/architecture-judgments.md`
   - `reference/findings-and-labels.md`
   - `README.md`
3. Do **not** add the project you are testing to the knowledge — you paste it into the chat.

## The test project

Use [`test-fixtures/nested-specialist.md`](test-fixtures/nested-specialist.md) — a small "client onboarding" project made specifically for testing, with known problems built in. Paste its contents **into the chat** exactly as written; it is already in the format Cold Read expects.

## The prompt (exact)

> Review this project's context architecture for cold-use readiness.

Cold Read does not yet know how much detail you want, so it should ask you one plain question next — Quick Review or Full Review. Reply:

> Full Review.

(You can ask for Quick Review instead; the fixture has only three known problems, which is fewer than Quick Review's cap of five, so a correct Quick Review reports all three anyway. Answering Full Review additionally checks the complete architecture assessment described below.)

## What a correct review looks like (results you can check)

- **Readiness: `REVISION REQUIRED`.**
- **A review-coverage note** naming the six supplied files as inspected, with no material omissions.
- **Exactly three distinct material findings — no more, no fewer, none merged into another, none invented:**
  1. **CONTRADICTION** — the main rule says get the client's sign-off before sending, but the delivery step sends automatically. This is externally visible and hard to reverse once a summary reaches the client, so it should rank at or near the top of the severity order (Critical or High).
  2. **MISSING RESPONSIBILITY** — charging the client's fee to the card on file has no required approval. This is a financial, largely irreversible action, so it should also rank near the top (Critical or High) — and it must be reported as its own finding, never folded into the sign-off contradiction just because both involve the delivery step.
  3. **UNOBSERVABLE RULE** — the rule to "move to the next stage once the work is *solid enough*" gives no way to tell whether it was met. This is a real but lower-consequence problem (Medium), and it should rank below the two above it.
- **No replacement content** — no rewritten rules, no folder layout, no ready-to-paste fix, no finished agent prompt.
- **No HANDOFF GAP finding.** (A HANDOFF GAP means the project only works because knowledge is still in the builder's head.) This sample project spells out how each stage passes its work to the next through `runs/<client-id>/`, so a handoff-gap finding here would be wrong.
- **If you asked for Full Review:** the review also names the three agents' ownership (intake, research, delivery), notes that `reference/market-sizing.md` is correctly scoped to the research stage only, and gives a prioritized action plan and the tests needed to prove a revision — all without proposing a finished fix.

The exact severity word Cold Read assigns to findings 1 and 2 (Critical vs. High) is a judgment call within the rules, not a fixed answer — what matters is that both outrank the vague-rule finding, and that all three findings appear, undiminished and unmerged.

## If any of these happen, Cold Read did not behave as intended

- The result is not `REVISION REQUIRED`.
- It skips the depth question entirely when you have not named a depth, or treats one depth as hidden or lesser.
- It supplies a replacement `rules.md`, replacement lines, a folder layout, or a finished agent prompt.
- A HANDOFF GAP finding appears.
- The three findings shrink to fewer, get merged into each other, or extra findings are invented beyond the three that are actually there.
- The vague "solid enough" stage rule is missed, or is called a missing structural part instead of an unobservable rule.
- The missing fee approval is merged into the sign-off contradiction instead of being reported as its own finding.
- A Full Review answer omits the architecture/ownership analysis, the action plan, or the required tests.

## Evidence

- [Independent challenge test](receipts/public/independent-challenge-test.md)
- [Self-review test](receipts/public/self-review-test.md)
- [Originality check](receipts/public/originality-check.md)

These saved records are supporting development evidence, not alternate builds or demo versions. The finished version under review is **v0.1.2**. The steps in this guide let a judge directly check the current Quick Review and Full Review behaviour against the included sample project.
