# Independent challenge test — plain-English summary

*This is a short public summary based on saved records. It is not the raw records themselves, and it does not describe a review done by a person.*

## What the test was

Cold Read was tested ten times in separate, fresh sessions. Each session received one sample project and did **not** see the expected answer in advance. Each session gave its first response, that response was saved, and it was then checked against a result set that had been decided beforehand. The testing was done separately from the people and process that wrote Cold Read.

## Which version was tested

The corrected version of Cold Read, saved under the reference `3bf0bbd124c5ff8fa8ae265aecae89146512b7ac`.

## What happened

- **Ten** fresh tests were run.
- **All ten passed. None failed** (10 pass, 0 fail).
- Two problems found in an earlier round were fixed and confirmed:
  - One sample project now always produces the same three intended findings — a conflict between two instructions, a missing required approval before charging a client, and a rule too vague for anyone to check — and no longer produces an extra, mistaken finding about knowledge being stuck in one person's head. (This was tracked internally as **S7-RF01**.)
  - A project where almost everything depended on knowledge in the builder's head now produces one main finding instead of several overlapping ones. (Tracked internally as **S7-RF02**.)
- The live fresh-project test — a brand-new session with no earlier conversation — was **not run this time**. It is still deferred, and nothing was used in its place.

## Checking the records have not changed

All ten saved responses and their scoring are kept together as a preserved evidence set. That set has this digital fingerprint. (A SHA-256 value is a digital fingerprint. It helps show that an evidence file has not changed.)

```
b96ca77d4545f6f814fb49ec839e41fcbcb950f53312110129b6c7f12061469b
```

## What this does and does not claim

This summary reports only what the ten saved tests showed on the version above. It does **not** claim that every possible situation was tested, that the live fresh-project test was done, that Cold Read is safe for production use, or that Cold Read has been proven to work on any and all real projects.
