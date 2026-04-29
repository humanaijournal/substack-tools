# Substack Tools

> Python tooling for publishing to Substack — Notes, full posts, and the cookie auth that connects them.

The code behind [AI Working Notes](https://aiworkingnotes.substack.com) — the Substack publication of [The Human AI Journal](https://github.com/humanaijournal).

---

## The Problem

Publishing to Substack from code means hitting Substack's internal API — no public publishing API exists. Two community libraries cover the space, but neither covers all of it:

- [`python-substack`](https://github.com/ma2za/python-substack) handles full newsletter posts (drafts, publish, schedule, markdown).
- [`substack-api` (TypeScript)](https://github.com/jakub-k-slys/substack-api) handles Substack Notes with a rich formatting builder.

The Notes side is TypeScript-only. Mixing Node.js and Python runtimes for one publishing pipeline is friction.

## The Solution

A Python-only path for both Notes and full posts, sharing one auth.

- **Notes publisher** — direct HTTP to Substack's `/api/v1/comment/feed` with a markdown → ProseMirror JSON converter. Bold, italic, links, lists, and link-attachment preview cards.
- **Posts** — delegated to `python-substack`'s built-in FastMCP server.
- **Auth** — one-time Playwright login extracts Substack's `connect.sid` session cookie. Both tools use the same cookie. Valid ~3 months even with MFA enabled.

## Status

**Work in progress.** Building in public. Nothing is shipped yet.

---

## Disclaimer

Substack's official API does almost nothing publicly useful. Everything in this repo uses Substack's *internal* API — the same endpoints their own web app calls. This is reverse-engineered, not officially supported. It works reliably today; it could break if Substack changes things tomorrow.

Use this on your own publications. Don't use it to spam or scrape other people's content.

---

## Acknowledgments

This work would not exist without:

- **[`python-substack`](https://github.com/ma2za/python-substack)** by [@ma2za](https://github.com/ma2za) — the foundational Python library for Substack publishing. Used directly here for full posts.
- **[`substack-api` (TypeScript)](https://github.com/jakub-k-slys/substack-api)** by [@jakub-k-slys](https://github.com/jakub-k-slys) — the cleanest documented schema for Substack Notes. The JSON shapes here are derived from this library's test fixtures.
- **["No Official API? No Problem!"](https://iam.slys.dev/p/no-official-api-no-problem-how-i)** — the reverse-engineering writeup the whole community builds on.

If any of this eventually makes its way back into `python-substack` as a contributed feature, that's the goal.

---

## License

[MIT](LICENSE)
