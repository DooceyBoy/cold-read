# Public file list

This file is the exact list of files allowed in the public release of Cold Read. (An "allowlist" is just that: the exact list of files allowed in the public release.) A clean release is put together by taking exactly the files listed under **Allowed** and nothing else. The release itself is **not** built or published here — this file only says what a clean release may contain.

## Allowed (the whole public release)

```
README.md
JUDGE_GUIDE.md
PLAIN_ENGLISH_GUIDE.md
LICENSE
PUBLIC_PACKAGE_MANIFEST.md
cold-read/**
test-fixtures/nested-specialist.md
receipts/public/independent-challenge-test.md
receipts/public/self-review-test.md
receipts/public/originality-check.md
```

`cold-read/**` is the editor itself and follows the competition's five-part methodology exactly: `identity.md`, `rules.md`, `examples.md`, the two Markdown files in `reference/`, and `README.md`. With that folder expanded, the public package is **15 files** in total.

## Not in the public release (kept privately, never deleted)

Everything not listed under **Allowed** is left out. The rule is simply: include exactly the Allowed files; leave out everything else. In particular, the release leaves out all internal development and record-keeping material, including:

- the internal review write-ups and their receipts;
- the internal stage, correction, and audit notes;
- the internal record of file history and the detailed originality-check working;
- the internal full record of the self-review test (its short public summary is `receipts/public/self-review-test.md`);
- the private answer key for the sample projects, and any other answer-key files under `test-fixtures/`;
- the separate shared working folder used during development;
- any raw session records, internal notes, and file locations from the machine used to build it.

These files are **not** deleted — they are kept as private records. Building or publishing the release is a separate, later step and is not done here.
