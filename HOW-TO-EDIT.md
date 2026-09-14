# How to edit cortex-docs

The public Mintlify docs site. This repository is PUBLIC. Every tracked file is world-readable the moment it is pushed. Read `CLAUDE.md` first, then `CONTEXT.md`.

## Where each change goes

| Change | Go to |
| --- | --- |
| A dashboard page | `dashboard/overview.mdx` and its siblings in `dashboard/` |
| A voice or agent page | `voice-core/overview.mdx` and its siblings in `voice-core/` |
| An ordering or menu page | `orders/menu.mdx` and its siblings in `orders/` |
| The API reference | `api-reference/coming-soon.mdx` |
| The landing page of the docs | `introduction.mdx` |
| The getting-started guide | `quickstart.mdx` |
| A common question | `faq.mdx` |
| Navigation, theme, or site config | `docs.json` |
| Styling | `style.css` |
| A file the site must not publish | `.mintignore` |

## The redaction rule

This repository is public. Write for a restaurant operator, not for an engineer with access.

Never write any of these here:

- A box or server hostname.
- An IP address, including a hostname that encodes one.
- An internal or staging URL.
- A vendor account name, a project id, or a tenant id.
- An environment variable name that names internal infrastructure.
- A credential of any kind, in any form.

A `redaction` job in CI greps for these terms on every pull request. It plants a canary first, so a broken grep fails the job instead of passing it silently.

## Before you open a PR

1. `git branch --show-current` and `git status --short`. Branch off the origin main branch.
2. Add every new page to the navigation in `docs.json`. A page missing from navigation fails the build.
3. Run `mint validate` locally, or let CI run it. It runs in strict mode and fails on a warning.
4. Re-read your diff for the redaction rule above. A public repo keeps no history secret.
5. Stage only your own paths. Never `git add -A`.

## Deploy path

A merge to `main` publishes the site through Mintlify. There is no manual deploy step. `.mintignore` decides which files stay unpublished; it does not hide them on GitHub.

## Never touch

- A credential, in any file, in any form.
- Any term in the redaction rule above.
- The `redaction` job in CI. It is the only automated check for the rule.
- `docs.json` navigation entries for pages you did not change.
- A production system. A docs change never needs one.
