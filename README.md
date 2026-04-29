# Substack Tools

> Tools for publishing to Substack from outside the website — short notes, full newsletter issues, one shared login.

<br>

The code behind [AI Working Notes](https://aiworkingnotes.substack.com) — the Substack publication of [The Human AI Journal](https://github.com/humanaijournal).

---

## The Problem

If you write on Substack and want to publish without going through their website, you're stuck. Substack doesn't offer an **API** (a standard way for outside software to talk to a website — like the one that lets WordPress publish from a phone app).

The developer community has built workarounds. Two of them together cover most of what a writer needs:

- [`python-substack`](https://github.com/ma2za/python-substack), written in **Python** (popular for automation and data work) — handles full newsletter issues beautifully.
- [`substack-api`](https://github.com/jakub-k-slys/substack-api), written in **TypeScript** (popular for building web apps) — handles short notes beautifully.

The catch: they live in completely different technical worlds — one is in Python, the other in TypeScript. Using both means maintaining two programming environments on your computer just to publish to one website. Two installations, two languages, two sets of documentation. An unnecessary headache.

---

## The Solution

A single set of tools, written in one language, that handles both full newsletter issues and short notes (with all their formatting) — all from one shared login.

- **A notes publisher.** Write a short note in plain text. Run one command. The note appears on Substack with all formatting intact — bold, italic, links, bullet lists, link preview cards. Indistinguishable from one typed directly on Substack.
- **A posts publisher.** Same idea, for full newsletter issues.
- **A one-time login.** Sign into Substack once. Your login stays valid for months — even on accounts that use **two-factor authentication** (the extra security step that asks for a code from your phone or an app at sign-in).

When it ships, publishing a note will look something like this:

```bash
notes publish "Just figured out how to publish Substack notes from Python. Full writeup →" \
  --link https://aiworkingnotes.substack.com/p/notes-from-python
```

Run that from anywhere code runs — your **terminal** (the place on your computer where you type commands directly), a Python script, an AI assistant like Claude Code, or any automation tool. Ten seconds later, the note is live on Substack.

---

## Status

**Built in public** — every step of the development is shared as it happens, not after it's done. **Nothing is shipped yet.** This README is the starting point. Everything else is on its way.

Follow the build at [AI Working Notes](https://aiworkingnotes.substack.com).

---

## How This Works (And Why It Could Break)

Substack doesn't officially support outside publishing. The developer community has reverse-engineered how its web editor talks to its servers, and these tools use the same conversation.

This works reliably today. It could break if Substack changes how things work on their end. If that happens, we'll try to push a fix within a few days. But use this at your own risk — we take no responsibility if anything goes wrong.

Use it on your own publications, and use it responsibly.

---

## Credit Where Credit Is Due

This exists because three other people did the hard work first:

- **[`python-substack`](https://github.com/ma2za/python-substack)** by [@ma2za](https://github.com/ma2za) — the Python library this project uses for full newsletter posts. Without it, half of what's here wouldn't exist.
- **[`substack-api` (TypeScript)](https://github.com/jakub-k-slys/substack-api)** by [@jakub-k-slys](https://github.com/jakub-k-slys) — figured out exactly how Substack notes are structured behind the scenes. The notes side here is built on that work.
- **["No Official API? No Problem!"](https://iam.slys.dev/p/no-official-api-no-problem-how-i)** — the original writeup that explains how Substack's hidden interface works.

---

## License

[MIT](LICENSE) — use it however you want.
