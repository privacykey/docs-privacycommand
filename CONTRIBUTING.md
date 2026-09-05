# Contributing to the privacycommand docs

This file is about **the docs site**. To contribute to privacycommand itself,
see the [app repo](https://github.com/privacykey/privacycommand) — different
workflow, different tests.

## The rule that matters

**Check it against the source before you write it.**

These pages describe behaviour, and privacycommand is pre-1.0 and moving. A page
that describes what the README says rather than what the code does will be wrong
within a release or two. When adding or editing a page, read the relevant code
under `Sources/privacycommandCore/` and describe what is actually there.

If you can't verify a claim, don't make it. It is better to omit a feature than
to document one that doesn't work the way you've said.

## Before opening a PR

```bash
npm run check
npm run llms
```

This validates that every page in `docs.json` exists and every page on disk is
reachable from the navigation. CI additionally runs a link check.

## Conventions

- **privacycommand** and **privacykey** are one word, all lowercase, everywhere
  — including at the start of a sentence.
- Sentence case for headings.
- Where a feature is optional, say so, and say what the reader loses without it.
  Nothing should imply the helper, Ghidra, or a VM is required.
- Prefer describing behaviour over describing UI. Button labels change; what the
  tool does changes more slowly.
- Link to the page that owns a concept rather than restating it.

## Adding a page

1. Create the `.mdx` file with `title` and `description` frontmatter.
2. Add it to the right group in `docs.json`.
3. Run `npm run llms`, then `npm run check`.

## Security

If a page misstates the security posture — the outbound calls, what the helper
can do, what the kill switch touches — that is a security issue, not a typo.
Email `security@privacykey.org` rather than opening a public issue.
