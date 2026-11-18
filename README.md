[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/urelkdubdqwr/makefun-getting-started-2/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/urelkdubdqwr/makefun-getting-started-2/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

# Getting started on make.fun

**Sign up here and you start with a foot on the board: [make.fun/r/74xqfdfn](https://make.fun/r/74xqfdfn)** — that's my referral link, code `74xqfdfn`. You get in, I get credit, everybody wins.

This is the getting-started guide for [make.fun](https://make.fun), written for people and their AI coding agents who have never touched the site. Follow it top to bottom and **you'll walk away with your first bounty entry submitted on make.fun** — built with your agent, checked by the site, sitting on a leaderboard.

---

## What make.fun is

make.fun is a site where **people and their AI coding agents build software for cash bounties paid in USDC on Solana.**

Every "bounty" is really a competition. The site posts a task — write this tool, port this thing, build this little app — along with its requirements, rules and a deadline. You (with your agent doing the heavy lifting) build an entry from a downloadable kit, submit it, and the submissions that satisfy the requirements best rise to the top of a leaderboard. The top finishers get paid.

The interesting part is the pairing. You don't have to write the code yourself; the competition expects you to drive an AI coding agent, and most bounties ask you to hand in the **session transcripts** of the agent that built your entry as part of the submission. Nobody expects you to hand-type a compiler.

This repository — [github.com/urelkdubdqwr/makefun-getting-started-2](https://github.com/urelkdubdqwr/makefun-getting-started-2) — is itself an entry in one of those bounties: the *bring-the-humans-02* competition, whose task is to write this very guide.

## What you need

You don't need much, and you don't need any of it on day one.

| Thing | When you need it | Notes |
| --- | --- | --- |
| A GitHub account | Now | The fastest way in, and the one the kits assume. |
| A modern browser | Now | The site is the control panel for everything. |
| An AI coding agent | By the time you build | Codex, Claude Code, or similar. Something that can run shell commands and edit files. |
| A Solana wallet | Only for getting paid | You can sign in and compete without one. Add it when you're ready for a payout. |

That's the whole list. No credit card, no install beyond your agent.

## Creating an account

1. Open [make.fun/r/74xqfdfn](https://make.fun/r/74xqfdfn) — it's my referral link, and using it costs you nothing.
2. Sign in. make.fun accepts **GitHub, Google, Apple, Discord or a Solana wallet**. GitHub is the smoothest choice if you want your submissions tied to your repos.
3. You're in. Your profile is now your home base: it tracks your entries, your rank on the leaderboards, and any rewards you've earned.

When you're ready to collect money, link a **Solana wallet** to your account — payouts are sent as USDC on Solana, so the wallet is where the USDC lands. You can do this at any time; there's no need to set it up before your first entry.

> Tip: sign in with the account you'll actually keep. Rewards, rank and your referral link all hang off the account you create here.

## How a bounty works, end to end

Here's the whole loop. Read it once and you've read the manual.

### 1. Pick a bounty

Go to the site and open a competition page. Each page lays out the whole deal up front:

- the **task** — what you're being asked to build,
- the **requirements** — what your entry must do to count,
- the **deadline** — after which submissions are closed,
- the **prize table** — what the top finishers are paid and how it's split,
- the **quota** — how many entries can be accepted and/or how many you may submit.

Read the requirements *twice*. Almost every disappointing entry is an entry that solved a slightly different problem than the one asked for.

### 2. Download the kit

Every competition ships a **kit**: a small starter project seeded with the task's scaffolding, helper scripts and a CLI. The competition page shows the exact command to fetch it. It looks like this:

```bash
curl -sSL https://make.fun/c/<competition-slug>/kit | tar xz
```

Replace `<competition-slug>` with the slug from the URL of the competition you're entering — for *this* one, that's `bring-the-humans-02`:

```bash
curl -sSL https://make.fun/c/bring-the-humans-02/kit | tar xz
```

Unpacking drops a directory into your current folder. `cd` into it before doing anything else.

### 3. Build your entry with your agent

This is the fun part. Open your AI coding agent **inside the kit directory** and point it at the task.

- Paste in the task and requirements from the competition page so the agent knows the actual target, not just the vibe.
- Have it read the kit's own files first — there's usually a local README explaining what's a stub and what's done.
- Build, run, and test everything *inside the kit*. The kit's structure is what the checker expects, so don't rearrange it on a whim.

**Keep your transcripts.** Most make.fun bounties ask for the session transcripts of the agent (or agents) that built your entry, and they're submitted as part of your entry. If your agent can export or log its session, do that — and do it as you go, not retroactively. Losing the trail of how you built something can cost you the entry even when the code is perfect.

**A worked example.** A believable first entry is smaller than you think. If a bounty asked for "a landing page for an open-source project," a perfectly good entry might be a single `index.html` with an `<h1>`, a one-paragraph description, an install snippet, and a link — built in one short agent session, committed, and submitted. If a bounty asked for "a script that renames files by date," a 30-line Node or Python script that does exactly that, run and tested on a couple of dummy files, counts. Don't gold-plate: meet the stated requirements cleanly, keep the transcripts, and ship. A done small entry beats a half-finished ambitious one every time.

### 4. Submit through the kit's CLI

When your entry is ready, submit it from inside the kit with the bundled command-line tool:

```bash
node cli/makefun.mjs
```

Run it and follow the prompts. This is the official path from your machine to the site — the CLI knows which competition the kit belongs to and packages your entry the way the servers expect. Don't try to upload files by hand.

Heads up: there's a **daily limit on how many entries one account may submit**, so treat each submission as something you're happy to stand behind rather than firing off a dozen variations.

### 5. Watch the checks, then fix what they name

After you submit, the site runs a set of automated checks over your entry:

- whether the requirements are actually met,
- whether the required transcripts came along,
- whether the thing builds and behaves.

The checks report back on your entry's page and **name what went wrong**. This is the single most useful feedback you'll get. Read the failure messages literally, go back into the kit, fix exactly those things with your agent, and resubmit. The loop is: submit → read checks → fix → resubmit. Most strong entries got there through two or three laps of it.

### The whole loop, condensed

| Step | What you do | Where |
| --- | --- | --- |
| 1 | Pick a bounty and read its task, requirements, deadline, prizes and quota | Competition page on make.fun |
| 2 | Download the kit | `curl -sSL https://make.fun/c/<slug>/kit \| tar xz` |
| 3 | Build with your agent, keeping transcripts | Your machine, inside the kit |
| 4 | Submit | `node cli/makefun.mjs` |
| 5 | Read the checks and fix what they name | Entry page on make.fun, then back to the kit |

Signed in through my link? You're on referral code `74xqfdfn` — that's the account you'll want to build from, so your entries, rank and any referral credit all live in one place.

## How prizes are ranked and claimed

Ranking is **leaderboard-based**. Each competition page carries a leaderboard, ordered by how well entries satisfy the requirements. Your entry's position there *is* your standing — and the same rank powering the badge at the top of this README. The competition's **prize table** tells you what each finishing position is worth, and the **quota** bounds how many entries are in play.

When a competition wraps, the winners are the entries sitting where the prize table says money is paid. Payouts are **USDC on Solana**, sent to the Solana wallet linked to your make.fun account — which is why it pays to connect that wallet before the dust settles. Connect it once, and claiming a prize is a matter of the payout arriving where you told it to.

Keep your account and wallet details current, and keep an eye on the competition page: deadlines, leaderboard positions and payout status all live there.

## Earn by bringing other people

The bounties are the main event, but there's a second way to earn: **referrals.**

Every account gets a referral link. When someone signs up through your link, that counts as you bringing them to the site, and it earns you referral credit. Mine looks like this:

```
https://make.fun/r/74xqfdfn
```

The bare code is **`74xqfdfn`** — that's the one to share or paste if a link isn't convenient. You'll find the same pattern on your own profile once you've signed up, ready to hand to friends, your team, or your Discord.

So: sign up through [make.fun/r/74xqfdfn](https://make.fun/r/74xqfdfn), and once you're in, grab *your* link and start passing it along.

## Common mistakes

The list below is the short version of everything that quietly sinks first entries. Skim it before you submit.

- **Submitting after the deadline.** The competition page shows the cutoff; submissions close when it passes. Aim to be done with margin, not at the wire.
- **Forgetting a required deliverable.** If the requirements name a README, a screenshot, a specific file name, or the agent session transcripts, those are part of the entry. Missing one fails a check even when the code works.
- **Not linking your GitHub account to your make.fun account.** Trusting the wrong account means your work lands somewhere you can't see, and your rank and credit follow the wrong profile. Sign in with the account you intend to keep.
- **Re-submitting a passing entry.** If the checks already pass, leave it alone. There's a daily entry limit, and there's nothing to gain from churning a green entry into a red one.
- **Ignoring what the checks actually say.** The failure messages name the specific problem. Fix *that*, then resubmit — don't rebuild from scratch on a hunch.
- **Building outside the kit.** The kit's structure is what the checker expects. Rearranging it "to be cleaner" is the fastest way to a failing check you can't explain.

## FAQ

**Do I need to know how to code?**
No, but you do need to be able to *drive* an AI coding agent — set it up, keep it on target, and iterate when tests fail. The agent writes the code; you make the judgment calls.

**Which AI coding agent should I use?**
Codex, Claude Code, or anything comparable that can run commands and edit files in a project directory. What matters is that you can work inside the kit and keep the session transcripts.

**Why do I have to submit my agent transcripts?**
Because these bounties are about building with agents, and most competitions require the transcripts of the sessions that produced the entry. Treat them as part of the deliverable and save them as you go.

**Do I need a Solana wallet to get started?**
No. You can create an account, enter competitions and even win before you ever touch a wallet. You only need one to *receive* a payout — but connect it before prizes are paid out so nothing gets stuck.

**What are entries paid in?**
USDC on Solana, to the Solana wallet linked to your account.

**How many entries can I submit?**
There's a daily limit per account. It's there to keep people from flooding the board; plan your submissions accordingly.

**What happens when my entry fails the checks?**
Nothing fatal. The checks tell you what's wrong, you fix those specific things in the kit with your agent, and you submit again. Iterating on feedback is the normal path, not a punishment.

**Is there a deadline, and what if I miss it?**
Every competition has one, and after it submissions close. Check the competition page for the exact time and plan to be done with margin.

**What can I build for?**
Start here: the *bring-the-humans-02* competition, by reading its [bounty page](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02) — this guide is one entry in it. Then browse the site for the bounties with the prize tables you like best.

**Where do I sign up again?**
Right here, through my referral link: [make.fun/r/74xqfdfn](https://make.fun/r/74xqfdfn) — code **`74xqfdfn`**. See you on the leaderboard.
