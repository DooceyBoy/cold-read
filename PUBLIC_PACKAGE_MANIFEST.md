# Public file list

This file records the exact 16-file public package for Cold Read. Every allowed path is listed explicitly; anything not listed stays private.

## Allowed (the whole public release)

```
README.md
JUDGE_GUIDE.md
PLAIN_ENGLISH_GUIDE.md
LICENSE
PUBLIC_PACKAGE_MANIFEST.md
cold-read/README.md
cold-read/examples.md
cold-read/identity.md
cold-read/rules.md
cold-read/reference/architecture-judgments.md
cold-read/reference/findings-and-labels.md
cold-read/reference/intake-and-review-modes.md
test-fixtures/nested-specialist.md
receipts/public/independent-challenge-test.md
receipts/public/self-review-test.md
receipts/public/originality-check.md
```

The seven `cold-read/` paths are the editor itself and follow the competition's five-part methodology exactly: `identity.md`, `rules.md`, `examples.md`, `reference/`, and `README.md`. The complete public package is **16 files** in total.

## Not in the public release (kept privately, never deleted)

Everything not listed under **Allowed** is left out. The rule is simply: include exactly the Allowed files; leave out everything else. In particular, the release leaves out all internal development and record-keeping material, including:

- the internal review write-ups and their receipts;
- the internal stage, correction, and audit notes;
- the internal record of file history and the detailed originality-check working;
- the internal full record of the self-review test (its short public summary is `receipts/public/self-review-test.md`);
- the private answer key for the sample projects, and any other answer-key files under `test-fixtures/`;
- the separate shared working folder used during development;
- any raw session records, internal notes, and file locations from the machine used to build it.

These files are **not** deleted — they remain private records outside the public repository and release.
