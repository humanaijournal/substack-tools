# substack-tools

> Python tooling for publishing to Substack — Notes, posts, and the cookie auth that ties them together.

Part of [The Human AI Journal](https://github.com/humanaijournal) — an open documentation of what happens when human direction meets AI capability.

---

## Status

**Work in progress.** Building in public.

This repo will hold a small, focused set of Python tools for publishing to Substack from the command line or from Claude Code:

- **Cookie extractor** — one-time Playwright script to extract a Substack session cookie and store it in `.env`
- **Notes publisher** — Python module that publishes Substack Notes (with bold, italic, links, lists, and link-attachment preview cards) directly via Substack's internal API
- **Posts via python-substack** — uses [`python-substack`](https://github.com/ma2za/python-substack)'s built-in MCP server for full newsletter posts

Nothing is shipped yet. Watch this space.

---

## Why this exists

The Human AI Journal is a publication about turning ideas into finished work using AI. Its writing process involves Substack — for both Notes (short daily posts) and full newsletter issues.

The existing Python ecosystem covers full posts well ([`python-substack`](https://github.com/ma2za/python-substack)). It does not cover Notes. The TypeScript ecosystem covers Notes well ([`jakub-k-slys/substack-api`](https://github.com/jakub-k-slys/substack-api)), but mixing TypeScript and Python runtimes for one publishing pipeline is friction.

This repo closes that gap: a Python-only path for both Notes and Posts, using the same session cookie for auth.

The build process itself is content for the publication. If you're following along, you'll see the working notes there.

---

## Approach

- **Auth:** Substack's `connect.sid` session cookie, extracted once via Playwright, stored in `.env`. Valid for ~3 months even with MFA enabled.
- **Notes:** Direct HTTP to Substack's internal `/api/v1/comment/feed` endpoint. JSON schema (ProseMirror) is fully documented in this repo's `docs/` directory.
- **Posts:** Delegated to `python-substack`'s built-in FastMCP server.

No reverse-engineering surprises here — the schema and endpoints have been documented by the community over years. See acknowledgments below for sources this work builds on.

---

## Disclaimer

Substack's official API does almost nothing publicly useful. Everything in this repo uses Substack's *internal* API — the same endpoints their own web app calls. This is reverse-engineered, not officially supported. It works reliably today; it could break if Substack changes things tomorrow.

Use this on your own publications and at your own risk. Don't use it to spam or scrape other people's content.

---

## Acknowledgments

This work would not exist without:

- **[`python-substack`](https://github.com/ma2za/python-substack)** by [@ma2za](https://github.com/ma2za) — the foundational Python library for Substack publishing. Used directly here for full posts.
- **[`substack-api` (TypeScript)](https://github.com/jakub-k-slys/substack-api)** by [@jakub-k-slys](https://github.com/jakub-k-slys) — the cleanest documented schema for Substack Notes. The JSON shapes used here are derived from this library's test fixtures.
- **["No Official API? No Problem!"](https://iam.slys.dev/p/no-official-api-no-problem-how-i)** — the reverse-engineering writeup that the whole community builds on.

If anything in this repo eventually makes its way back into `python-substack` as a contributed feature, that's the goal.

---

## License

[MIT](LICENSE)
