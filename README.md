# Substack Tools

> Tools for publishing to Substack from your computer instead of from Substack's website — short notes, full newsletter issues, and the one-time login that powers both.

The code behind [AI Working Notes](https://aiworkingnotes.substack.com) — the Substack publication of [The Human AI Journal](https://github.com/humanaijournal).

---

## What This Is

If you write on Substack, this is the thing that lets you publish from your own computer instead of from Substack's web editor.

Type a short note in plain text. Run one command. Done — the note is live on Substack with all the formatting intact: bold, italic, links, bullet lists, even link preview cards. Exactly the way it would look if you'd typed it into Substack's web editor by hand.

The same set of tools handles full newsletter issues too. Same login, same workflow.

You sign into Substack once. After that, everything happens from your computer.

---

## Why This Exists

I write on Substack. Substack doesn't give writers an official way to publish from outside their website — there's no app, no API, no command line tool.

The community has figured out how to do it anyway. Two existing tools do most of the work:

- One tool ([`python-substack`](https://github.com/ma2za/python-substack), written in Python) handles full newsletter posts beautifully.
- Another tool ([`substack-api`](https://github.com/jakub-k-slys/substack-api), written in TypeScript) handles short notes beautifully.

The catch: those two tools are written in different programming languages. Using both means running two separate technical setups on your computer just to publish to one website. That's friction nobody needs.

This repo fixes that. Everything's in one language, sharing one login, doing both jobs.

---

## What's In Here

When this is finished, here's what you'll find:

- **A login extractor.** A small program that opens a browser, lets you sign into Substack once, and saves your session so you don't have to sign in again for months.
- **A notes publisher.** Write a note in markdown (the same plain-text formatting used in regular text files), run the publisher, and your note appears live on Substack with all formatting preserved.
- **A posts publisher.** Same idea, but for full newsletter issues. Built on top of the existing `python-substack` library.

---

## Status

**Building in public. Nothing is shipped yet.** This README is the first commit. Everything else is on its way.

If you want to follow the build process as it happens, the working notes live at [AI Working Notes](https://aiworkingnotes.substack.com).

---

## How This Works (And Why It Could Break)

Substack does not officially support publishing from outside their website. The community has reverse-engineered how Substack's own web editor talks to Substack's servers, and we use the same conversation here.

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
