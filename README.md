# docs-privacycommand

Source for the [privacycommand](https://github.com/privacykey/privacycommand)
documentation site, built with [Mintlify](https://mintlify.com).

Production is a Cloudflare Worker serving the static export as assets
([`wrangler.jsonc`](wrangler.jsonc)). `just deploy` builds and publishes it.
**Hostname:** `docs.privacycommand.privacykey.org` *(DNS not configured yet)*

## Local preview

```bash
npm run dev      # mint dev, on http://localhost:3000
npm run check    # validate docs.json navigation against the files on disk
npm run llms     # regenerate llms.txt and llms-full.txt after editing a page
```

`npm run check` is the fast gate — it catches a page listed in `docs.json` with
no matching file, and a file that exists but isn't in the navigation. Run it
before pushing; CI runs a link check on top.

## Layout

```
docs.json          navigation, theme, SEO
introduction.mdx   … the Guide tab, one file per page
develop/           the Develop tab
images/  logo/     assets
scripts/           check-docs.mjs, build-llms.mjs
llms.txt           AI-readable index of every page (generated, committed)
llms-full.txt      the whole site as one Markdown file (generated, committed)
```

## AI-readable copies

The site follows the [llms.txt](https://llmstxt.org) convention. `llms.txt` at the
repository root indexes every page with its one-line description, and
`llms-full.txt` is the whole site as one Markdown file. Both are committed, so
they read fine straight from GitHub, and both are served from the site root. The
build also writes every page as plain Markdown beside its HTML, so appending
`.md` to any page URL returns the Markdown.

`scripts/build-llms.mjs` generates all of it from `docs.json` and each page's
frontmatter, using only Node built-ins. Run `npm run llms` after editing a page
and commit the result; `npm run check` fails when the committed copies are out
of date.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). Docs for the app itself live in the
[privacycommand](https://github.com/privacykey/privacycommand) repo — this repo
is the site only.

## Licence

MIT, matching privacycommand. See [LICENSE](LICENSE).
