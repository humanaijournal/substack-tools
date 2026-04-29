# Substack Tools

> Tools for publishing to Substack from outside the website — short notes, full newsletter issues, and the one login that powers both.

<br>

The code behind [AI Working Notes](https://aiworkingnotes.substack.com) — the Substack publication of [The Human AI Journal](https://github.com/humanaijournal).

---

## The Problem

If you write on Substack and want to publish without going through their website, you're stuck. Substack doesn't offer an **API** (a standardized way for outside software to talk to a website — for example, when WordPress lets you publish from a phone app, or when Mailchimp lets your website automatically add new subscribers, that works because those services offer APIs. Substack offers nothing equivalent for publishing).

The community has built workarounds. Two of them, working together, cover most of what a writer needs:

- One tool ([`python-substack`](https://github.com/ma2za/python-substack)) is written in **Python** (a programming language popular for scripting and data work) — it handles full newsletter issues beautifully.
- Another tool ([`substack-api`](https://github.com/jakub-k-slys/substack-api)) is written in **TypeScript** (a different programming language popular for building web apps) — it handles short notes beautifully.

The catch: those two tools live in completely separate technical worlds. Using both means installing and maintaining two programming environments on your computer just to publish to one website. Two installations, two languages to debug, two sets of documentation to keep up with. That's friction nobody needs.

---

## The Solution

A single set of tools, written in one language, that does both jobs and shares one login.

- **A notes publisher.** Write a short note in plain text. Run one command. The note appears on Substack with all formatting intact — bold, italic, links, bullet lists, even link preview cards. Exactly the way it would look if you'd typed it into Substack's web editor by hand.
- **A posts publisher.** Same idea, but for full newsletter issues. Same login, same workflow.
- **A one-time login.** Sign into Substack once. After that, everything happens from your computer for months at a time, even if your account uses two-factor authentication.

When it ships, publishing a note will look something like this:

```bash
notes publish "Just figured out how to publish Substack notes from Python. Full writeup →" \
  --link https://aiworkingnotes.substack.com/p/notes-from-python
```

Run that anywhere code runs — your terminal, a Python script, an AI assistant like Claude Code, or any automation tool that can execute a command. Ten seconds later, the note is live on Substack.

---

## Status

**Building in public. Nothing is shipped yet.** This README is the first commit. Everything else is on its way.

If you want to follow the build process as it happens, the working notes live at [AI Working Notes](https://aiworkingnotes.substack.com).

---

## How This Works (And Why It Could Break)

Substack does not officially support publishing from outside their website. The community has figured out how Substack's own web editor talks to Substack's servers behind the scenes, and these tools use the same conversation.

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
