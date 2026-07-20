# Independent challenge test — plain-English summary

*This public development record summarises saved test evidence. It is not the raw record itself, a human review, or a separate edition of Cold Read.*

## What the test was

During development, Cold Read was tested ten times in separate, isolated model sessions. These were controlled tests rather than Claude Project installation runs. Each session received one sample project and did **not** see the expected answer in advance. Each session gave its first response, that response was saved, and it was then checked against a result set that had been decided beforehand. The testing was done separately from the people and process that wrote Cold Read.

## Which revision was tested

The corrected version of Cold Read, saved under the reference `3bf0bbd124c5ff8fa8ae265aecae89146512b7ac`.

## What happened

- **Ten** fresh tests were run.
- **All ten passed. None failed** (10 pass, 0 fail).
- Two problems found in an earlier round were fixed and confirmed:
  - One sample project now always produces the same three intended findings — a conflict between two instructions, a missing required approval before charging a client, and a rule too vague for anyone to check — and no longer produces an extra, mistaken finding about knowledge being stuck in one person's head. (This was tracked internally as **S7-RF01**.)
  - A project where almost everything depended on knowledge in the builder's head now produces one main finding instead of several overlapping ones. (Tracked internally as **S7-RF02**.)

## Checking the records have not changed

All ten saved responses and their scoring are kept together as a preserved evidence set. That set has this digital fingerprint. (A SHA-256 value is a digital fingerprint. It helps show that an evidence file has not changed.)

```
b96ca77d4545f6f814fb49ec839e41fcbcb950f53312110129b6c7f12061469b
```

## What this does and does not claim

This receipt records ten preserved runs on the revision above: all ten passed. Those results support the tested behaviours, but no finite test set can cover every possible real project.
