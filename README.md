# docs-privacycommand

Source for the [privacycommand](https://github.com/privacykey/privacycommand)
documentation site, built with [Mintlify](https://mintlify.com).

Published at `docs.privacycommand.privacykey.org`.

## Local preview

```bash
npm run dev      # mint dev, on http://localhost:3000
npm run check    # validate docs.json navigation against the files on disk
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
scripts/           check-docs.mjs
```

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). Docs for the app itself live in the
[privacycommand](https://github.com/privacykey/privacycommand) repo — this repo
is the site only.

## Licence

MIT, matching privacycommand. See [LICENSE](LICENSE).
