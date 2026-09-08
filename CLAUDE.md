# cortex-docs — the public Cortex docs site

Status: v1, 2026-09-08. This is the only entry file. There is no `AGENTS.md`.

This repository is the public documentation site for Cortex, the voice AI that answers a restaurant's phone and takes orders. Mintlify builds it. Nothing here is product code. The site is public: write every page for a restaurant operator, and put no internal infrastructure facts in it.

Read `CONTEXT.md` next for how a change moves through this repo.

## Where things live

| Path | What it holds |
| --- | --- |
| `docs.json` | Site config: theme, colors, fonts, navigation, anchors. Every page must be listed here. |
| `introduction.mdx`, `quickstart.mdx`, `going-live.mdx`, `faq.mdx` | Getting Started and Help pages. |
| `dashboard/` | Dashboard pages: access, overview, in-store mode, orders, calls, analytics, settings, support. |
| `voice-core/` | Voice Core pages: overview, voice configuration, store hours, FAQs. |
| `orders/` | Orders and POS pages. |
| `api-reference/` | Placeholder tab. An OpenAPI spec goes here later. |
| `Assistant.md` | Steers the built-in Ask AI assistant. Not a page. |
| `logo/`, `favicon.svg`, `fonts/`, `images/`, `style.css` | Branding and assets. |
| `README.md` | Developer setup: local preview, deploy, custom domain steps. |
| `.mintignore` | Files the site must never publish: this file and `CONTEXT.md`. |

## Route by task

| If you need to | Go to |
| --- | --- |
| Edit or add a page | The `.mdx` file, then its entry in `docs.json` navigation |
| Change the sidebar, tabs, or theme | `docs.json` |
| Change how Ask AI answers | `Assistant.md` |
| Preview locally | `mint dev` from this folder |
| Check the build before a PR | `mint validate` |
| Know where it deploys | `CONTEXT.md` § Outputs |

## Rules

- A new page is not on the site until `docs.json` lists it. Add both in the same commit.
- Run `mint validate` before every PR. It must pass.
- Merge to `main` deploys the public site. A person reads the PR first.
- Public repo. No box names, IP addresses, vendor account names, or internal URLs, in any file.
- Branch off `origin/main`. Never push to `main`. Squash-merge.
- Before any git action, run `git rev-parse --show-toplevel` and make sure it is this repo.
