# CONTEXT — cortex-docs root

Status: v2, 2026-09-14. Folder: the repository root. One job: publish the public Cortex docs site.

## Inputs
- Product facts from the Cortex team: what the dashboard, voice agent, and ordering do today.
- `docs.json`: the navigation that decides which pages exist on the site.
- Branding assets in `logo/`, `fonts/`, `images/`.
- The Cabinet Grotesk font face. This repo holds a COPY at `fonts/CabinetGrotesk-Variable.woff2`. The `landing-page` repo is the one home for that font (decision E11, Hamoodey 2026-09-13). Copy a new version from `landing-page/public/fonts/`; never edit the copy here as if it were the source.

## Process
1. Branch off `origin/main`.
2. Edit or add an `.mdx` page. Add a new page to `docs.json` navigation in the same commit.
3. Run `mint dev` to preview. Run `mint validate`; it must pass. CI runs `mint validate` again on the pull request.
4. Open a PR. A person reads it.
5. Merge to `main`. The Mintlify GitHub app deploys the site.

## Outputs
- The live site at `https://cortex.mintlify.app`. Push-to-deploy from `main`.
- `docs.json` sets the canonical URL to `https://cortex.mintlify.app` (the live site). The custom domain `docs.cor-tex.solutions` is NOT wired: it has no DNS record as of 2026-09-14. `README.md` § Deploy holds the steps to wire it.

## Human check
A person reads every PR before merge, because merge publishes. The check: the page is in `docs.json`, `mint validate` passed, and nothing internal is on the page.

## Folders
- `dashboard/`: eight pages on the operator dashboard.
- `voice-core/`: four pages on the voice agent.
- `orders/`: three pages on ordering and POS.
- `api-reference/`: one placeholder page until an OpenAPI spec exists.
- `logo/`: one file, `cortex-mark.svg`. `docs.json` points both the light and the dark logo key at it. The mark reads on the cream background and on the espresso one, so there is no second file to keep in step.
- `fonts/`: one file, the Cabinet Grotesk variable face. A copy; see Inputs.
- `images/`: dashboard screenshots, shot June 2026. Re-shoot them when the dashboard UI changes.
- `.github/workflows/`: one job, `validate.yml`. It runs `mint validate` on every pull request and every push to `main`.

## Support addresses
Two addresses are in use. Both stay. (Hamoodey, 2026-09-14: "theyre both used".)

| Address | Purpose | Where it appears |
| --- | --- | --- |
| `cortextechnologyai@gmail.com` | The operator inbox. A reader of a page emails this one for help, access, or a POS question. | `dashboard/support.mdx`, `dashboard/getting-access.mdx`, `going-live.mdx`, `faq.mdx`, `orders/pos.mdx`, `api-reference/coming-soon.mdx` |
| `office@cor-tex.solutions` | The company address. It is the Support anchor in the site chrome and the address the Cortex legal documents name. | `docs.json` § navigation.global.anchors |

Do not merge the two. The split is deliberate.

## Config
Rule R11: name every config file and its consumer.

| File | Consumer | What it sets |
| --- | --- | --- |
| `docs.json` | Mintlify, on every build | Theme, colors, the font, navigation, anchors, the navbar, and the canonical URL. A page is not on the site until this file lists it. |
| `.mintignore` | Mintlify, on every build | The files the site must never publish. |
| `style.css` | Mintlify, by convention | The custom navbar CSS. No key names it; the file name and the root location are the wiring. |
| `.github/workflows/validate.yml` | GitHub Actions | Runs `mint validate` on every pull request and every push to `main`. |

## Generated
Rule R3: nothing in this repo is generated. There is no build step that writes a tracked file, no lockfile, and no build output. Mintlify builds the site on its own infrastructure from the tracked sources.

## Not pages
- `CLAUDE.md`, `CONTEXT.md`, `AGENTS.md`: agent entry files, excluded by `.mintignore`.
- `Assistant.md`: the Ask AI steering text.
- `README.md`: developer setup. Excluded by `.mintignore` and not in the navigation.
