# Substack Tools

> Tools for publishing to Substack from outside the website — short notes, full newsletter issues, one shared login.

<br>

The code behind [AI Working Notes](https://aiworkingnotes.substack.com) — the Substack publication of [The Human AI Journal](https://github.com/humanaijournal).

---

## The Problem

If you write on Substack and want to publish without going through their website, you're stuck. Substack doesn't offer an **API** (a standard way for outside software to talk to a website — like the one that lets WordPress publish from a phone app).

The community has built workarounds. Two of them together cover most of what a writer needs:

- [`python-substack`](https://github.com/ma2za/python-substack), written in **Python** (popular for scripting and data work) — handles full newsletter issues beautifully.
- [`substack-api`](https://github.com/jakub-k-slys/substack-api), written in **TypeScript** (popular for building web apps) — handles short notes beautifully.

The catch: they live in completely different technical worlds. Using both means maintaining two programming environments on your computer for one website. Two installations, two languages, two sets of documentation. Friction nobody needs.

---

## The Solution

A single set of tools in one language. Both jobs, one login.

- **A notes publisher.** Write a short note in plain text. Run one command. The note appears on Substack with all formatting intact — bold, italic, links, bullet lists, link preview cards. Indistinguishable from one typed directly on Substack.
- **A posts publisher.** Same idea, for full newsletter issues.
- **A one-time login.** Sign into Substack once. The session stays valid for months — even with two-factor authentication enabled.

When it ships, publishing a note will look something like this:

```bash
notes publish "Just figured out how to publish Substack notes from Python. Full writeup →" \
  --link https://aiworkingnotes.substack.com/p/notes-from-python
```

Run that anywhere code runs — your terminal, a Python script, an AI assistant like Claude Code, or any automation tool. Ten seconds later, the note is live on Substack.

---

## Status

**Building in public. Nothing is shipped yet.** This README is the first commit. Everything else is on its way.

Follow the build at [AI Working Notes](https://aiworkingnotes.substack.com).

---

## How This Works (And Why It Could Break)

Substack doesn't officially support outside publishing. The community has reverse-engineered how its web editor talks to its servers, and these tools use the same conversation.

This works reliably today. It could break if Substack changes its internals. If it does, expect a fix here within a few days.

Use this on your own publications. Don't use it to spam or scrape other people's content.

---

## Credit Where Credit Is Due

This exists because three other people did the hard work first:

- **[`python-substack`](https://github.com/ma2za/python-substack)** by [@ma2za](https://github.com/ma2za) — the Python library this repo uses for full newsletter posts. Without it, half of what's here wouldn't exist.
- **[`substack-api` (TypeScript)](https://github.com/jakub-k-slys/substack-api)** by [@jakub-k-slys](https://github.com/jakub-k-slys) — figured out exactly how Substack notes are structured behind the scenes. The notes side here is built on that work.
- **["No Official API? No Problem!"](https://iam.slys.dev/p/no-official-api-no-problem-how-i)** — the original writeup that explains how Substack's hidden interface works.

If anything here eventually makes its way back into `python-substack`, that's the goal.

---

## License

[MIT](LICENSE) — use it however you want.
