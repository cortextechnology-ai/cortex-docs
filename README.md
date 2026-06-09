# Cortex Docs

Documentation site for Cortex, built on [Mintlify](https://mintlify.com).

## Local development

```bash
npm i -g mint        # the CLI package is `mint` (not the deprecated `mintlify`)
mint dev             # preview at http://localhost:3000
```

Run from this directory (where `docs.json` lives). Requires Node.js ≥ 20.17.

## Structure

```
docs.json              # site config: theme, colors, nav, AI features
introduction.mdx       # homepage
quickstart.mdx
going-live.mdx
voice-core/            # Voice Core pages
orders/                # Ordering + POS pages
faq.mdx
Assistant.md           # steers the built-in "Ask AI" assistant
logo/ , favicon.svg    # branding (placeholders — swap for real assets)
api-reference/         # (optional) OpenAPI tab — add openapi.json + a tab in docs.json
```

## Deploy

1. Push this folder to a GitHub repo.
2. Go to [mintlify.com/start](https://mintlify.com/start), connect GitHub, install
   the Mintlify app. Push-to-deploy is automatic thereafter.
3. Add the custom domain `docs.cor-tex.solutions` in the Mintlify dashboard:
   - Add the two TXT verification records it gives you at GoDaddy first.
   - Then add: `CNAME  docs  cname.mintlify.builders`
   - TLS provisions automatically.

Free (Starter) tier covers custom domain + AI assistant. See
`../docs/research/2026-06-09-mintlify-docs-build-recipe.md` for the full recipe.

## Adding the API Reference tab (later)

Drop an OpenAPI 3.0/3.1 spec at `api-reference/openapi.json`, then add a tab to
`docs.json`:

```json
{ "tab": "API Reference", "openapi": "/api-reference/openapi.json" }
```
