# Substack Tools

> Tools for publishing to Substack from your computer instead of from Substack's website — short notes, full newsletter issues, and the one-time login that powers both.

The code behind [AI Working Notes](https://aiworkingnotes.substack.com) — the Substack publication of [The Human AI Journal](https://github.com/humanaijournal).

---

## The Problem

If you write on Substack and want to publish without going through their website, you're stuck. Substack doesn't give writers an official way to publish from outside — no app, no automated tool, no way to do it from your own computer.

The community has built workarounds. Two of them cover most of what's needed:

- One tool ([`python-substack`](https://github.com/ma2za/python-substack), written in Python) handles full newsletter issues beautifully.
- Another tool ([`substack-api`](https://github.com/jakub-k-slys/substack-api), written in TypeScript) handles short notes beautifully.

The catch: those two tools are written in different programming languages. Using both means running two separate technical setups on your computer just to publish to one website. That's friction nobody needs.

## The Solution

A single set of tools, written in one language, that does both jobs and shares one login.

- **A notes publisher.** Write a short note in plain text. Run one command. The note appears on Substack with all formatting intact — bold, italic, links, bullet lists, even link preview cards. Exactly the way it would look if you'd typed it into Substack's web editor by hand.
- **A posts publisher.** Same idea, but for full newsletter issues. Same login, same workflow.
- **A one-time login.** Sign into Substack once. After that, everything happens from your computer for months at a time, even if your account uses two-factor authentication.

---

## Status

**Building in public. Nothing is shipped yet.** This README is the first commit. Everything else is on its way.

If you want to follow the build process as it happens, the working notes live at [AI Working Notes](https://aiworkingnotes.substack.com).

---

## How This Works (And Why It Could Break)

Substack does not officially support publishing from outside their website. The community has figured out how Substack's own web editor talks to Substack's servers, and these tools use the same conversation.

This works reliably today. It could break the day Substack changes how their own site works internally. If that happens, expect a fix here within a few days.

Use this on your own publications. Don't use it to spam or scrape other people's content.

---

## Credit Where Credit Is Due

This whole thing exists because three other people did the hard work first:

- **[`python-substack`](https://github.com/ma2za/python-substack)** by [@ma2za](https://github.com/ma2za) — the Python library this repo uses for full newsletter posts. Without this library, half of what's here wouldn't exist.
- **[`substack-api` (TypeScript)](https://github.com/jakub-k-slys/substack-api)** by [@jakub-k-slys](https://github.com/jakub-k-slys) — figured out exactly how Substack notes are structured behind the scenes. The notes side of this repo is built on that work.
- **["No Official API? No Problem!"](https://iam.slys.dev/p/no-official-api-no-problem-how-i)** — the original writeup that explains how Substack's hidden interface works.

If anything in this repo eventually makes its way back into `python-substack` as a contributed feature, that's the goal.

---

## License

[MIT](LICENSE) — use it however you want.
