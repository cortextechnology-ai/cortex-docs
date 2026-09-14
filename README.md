# Cortex Docs

The public documentation site for Cortex, built on [Mintlify](https://mintlify.com).

## Local development

```bash
npm i -g mint        # the CLI package is `mint` (not the deprecated `mintlify`)
mint dev             # preview at http://localhost:3000
mint validate        # strict build check; it must pass before you open a PR
```

Run both from this directory, where `docs.json` lives. Node.js 20.17 or newer.

## Structure

```
docs.json                  # site config: theme, colors, fonts, navigation, anchors, SEO
introduction.mdx           # homepage
quickstart.mdx
going-live.mdx
faq.mdx
dashboard/                 # 8 pages on the operator dashboard
voice-core/                # 4 pages on the voice agent
orders/                    # 3 pages on ordering and POS
api-reference/             # 1 placeholder page until an OpenAPI spec exists
Assistant.md               # steers the built-in "Ask AI" assistant. Not a page
style.css                  # custom navbar CSS. Mintlify loads it by convention
logo/cortex-mark.svg       # the brand mark. Both docs.json logo keys point here
favicon.svg                # the site favicon
fonts/                     # Cabinet Grotesk, a copy. landing-page owns the font
images/                    # dashboard screenshots used by the pages
.mintignore                # files the site must never publish
.github/workflows/         # CI: mint validate on every PR and every push to main
CLAUDE.md, CONTEXT.md      # agent entry files. Not published
AGENTS.md                  # a 3-line pointer to CLAUDE.md. Not published
README.md                  # this file. Not published
```

## Deploy

This repo is connected to Mintlify. Pushing to `main` publishes the site. There is
no manual deploy step and no build artifact to commit.

- Live site: `https://cortex.mintlify.app`. `docs.json` § seo sets it as the canonical URL.
- The custom domain `docs.cor-tex.solutions` is **not wired**. It has no DNS record as
  of 2026-09-14. To wire it: add the domain in the Mintlify dashboard, add the two TXT
  verification records it gives you at the registrar, then add `CNAME docs cname.mintlify.builders`.
  TLS provisions automatically. The free Starter tier covers a custom domain and the AI assistant.

## Adding the API Reference tab (later)

Drop an OpenAPI 3.0 or 3.1 spec at `api-reference/openapi.json`, then add a tab to
`docs.json`:

```json
{ "tab": "API Reference", "openapi": "/api-reference/openapi.json" }
```

## Rules for this repo

This repo is public. Never write a box name, an IP address, a vendor account name, or an
internal URL into any file here. Read `CLAUDE.md` before your first change.
