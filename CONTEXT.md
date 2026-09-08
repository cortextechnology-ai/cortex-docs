# CONTEXT — cortex-docs root

Status: v1, 2026-09-08. Folder: the repository root. One job: publish the public Cortex docs site.

## Inputs
- Product facts from the Cortex team: what the dashboard, voice agent, and ordering do today.
- `docs.json`: the navigation that decides which pages exist on the site.
- Branding assets in `logo/`, `fonts/`, `images/`.

## Process
1. Branch off `origin/main`.
2. Edit or add an `.mdx` page. Add a new page to `docs.json` navigation in the same commit.
3. Run `mint dev` to preview. Run `mint validate`; it must pass.
4. Open a PR. A person reads it.
5. Merge to `main`. The Mintlify GitHub app deploys the site.

## Outputs
- The live site at `https://cortex.mintlify.app`. Push-to-deploy from `main`.
- `docs.json` names `https://docs.cor-tex.solutions` as the canonical URL. That domain was not wired as of 2026-09-08. `README.md` § Deploy has the custom-domain steps.

## Human check
A person reads every PR before merge, because merge publishes. The check: the page is in `docs.json`, `mint validate` passed, and nothing internal is on the page.

## Folders
- `dashboard/`: eight pages on the operator dashboard.
- `voice-core/`: four pages on the voice agent.
- `orders/`: three pages on ordering and POS.
- `api-reference/`: one placeholder page until an OpenAPI spec exists.
- `logo/`, `fonts/`, `images/`: assets referenced by `docs.json` and pages.

## Not pages
- `CLAUDE.md`, `CONTEXT.md`: agent entry files, excluded by `.mintignore`.
- `Assistant.md`: the Ask AI steering text.
- `README.md`: developer setup. Not in the navigation.
