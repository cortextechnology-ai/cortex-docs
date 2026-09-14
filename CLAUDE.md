# cortex-docs — the public Cortex docs site

Status: v2, 2026-09-14. This is the entry file. `AGENTS.md` is a three-line pointer here for tools that load that name.

This repository is the public documentation site for Cortex, the voice AI that answers a restaurant's phone and takes orders. Mintlify builds it. Nothing here is product code. The site is public: write every page for a restaurant operator, and put no internal infrastructure facts in it.

Read `CONTEXT.md` next for how a change moves through this repo.

Trunk: this repo is one of six clones inside the private `cortex-phone-agents` repo. Cross-repo rules, plans, decisions, and the system map live there. Read its `CLAUDE.md` for anything that spans repos.

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
| `logo/cortex-mark.svg`, `favicon.svg` | The brand mark. `docs.json` points both the light and the dark logo key at this one file: the mark reads on the cream background and on the espresso one. |
| `fonts/CabinetGrotesk-Variable.woff2` | The site face, named by `docs.json` § fonts. It is a copy. `landing-page` owns the font (decision E11, 2026-09-13); copy a new version from there. |
| `images/` | Dashboard screenshots used by the pages. Shot in June 2026. Re-shoot them when the dashboard UI changes. |
| `style.css` | The custom navbar stylesheet. Mintlify loads a root `style.css` by convention; no `docs.json` key names it. Read the header comment in the file before you rename or move it. |
| `README.md` | Developer setup: local preview, the deploy path, and the custom-domain steps. Not published. |
| `.mintignore` | Files the site must never publish: `CLAUDE.md`, `CONTEXT.md`, `AGENTS.md`, `README.md`. |

## Route by task

| If you need to | Go to |
| --- | --- |
| Edit or add a page | The `.mdx` file, then its entry in `docs.json` navigation |
| Change the sidebar, tabs, or theme | `docs.json` |
| Change how Ask AI answers | `Assistant.md` |
| Preview locally | `mint dev` from this folder |
| Check the build before a PR | `mint validate`. CI runs the same command in `.github/workflows/validate.yml` |
| Know where it deploys | `CONTEXT.md` § Outputs |

## Rules

- A new page is not on the site until `docs.json` lists it. Add both in the same commit.
- Run `mint validate` before every PR. It must pass.
- Merge to `main` deploys the public site. A person reads the PR first.
- Public repo. No box names, IP addresses, vendor account names, or internal URLs, in any file.
- Two support addresses are in use and both stay. `cortextechnologyai@gmail.com` is the operator inbox that the pages give a reader. `office@cor-tex.solutions` is the Support anchor in the site chrome (`docs.json` § navigation.global.anchors) and the address the legal documents name. Do not merge them. (Hamoodey, 2026-09-14: "theyre both used".)
- The public page `orders/pos.mdx` names Clover, Toast, and Square as the supported systems. Keep it as written and do not soften the supported-POS list. The middleware Cortex uses to reach them is internal and must stay out of every public page. (Hamoodey, 2026-09-11.)
- Branch off `origin/main`. Never push to `main`. Squash-merge.
- Before any git action, run `git rev-parse --show-toplevel` and make sure it is this repo.
