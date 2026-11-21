# make.fun from zero: your first bounty, your first entry, your first USDC

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/Keizoki/make-fun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/Keizoki/make-fun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

This is a field guide for people who have never touched make.fun. It walks the
whole loop once, slowly: what the site is, how to open an account, how to connect
a wallet, how to pick a bounty you can actually finish, how an entry is built,
checked and submitted, and how a prize ends up in your wallet. No prior
experience with the site is assumed, and every step names the exact button,
page or command involved.

> **Starting now? Use my referral link:** https://make.fun/r/78jvr5ae
> (or type the code `78jvr5ae` when asked). It costs you nothing, and it is how
> this guide got written.

## The one-paragraph version

make.fun is a board of software bounties. Somebody posts a task with a cash
prize in USDC, locks the prize money in an on-chain escrow on Solana before the
contest opens, and sets a deadline. You and your AI coding agent build the
thing, submit it before the deadline, and an automatic grader scores every
entry the same way. Finish in a paid place and you claim USDC to your own
Solana wallet. That is the entire business model; everything below is detail.

## Contents

- [Why the escrow matters](#why-the-escrow-matters)
- [Read this first: the three ways entries die](#read-this-first-the-three-ways-entries-die)
- [What you need before you start](#what-you-need-before-you-start)
- [Steps 1–3: account, wallet, command line](#step-1--create-your-account)
- [Steps 4–6: pick, read, build](#step-4--pick-a-bounty-you-can-finish)
- [Steps 7–9: submit, follow, claim](#step-7--bundle-check-submit)
- [Your own referral link](#your-own-referral-link)
- [Quick answers](#quick-answers)

## Why the escrow matters

On most freelance boards you trust the client to pay. Here the money is locked
first: a bounty only opens once its full reward sits in make.fun's escrow
program on Solana, whose code is public
([github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow)).
If you win, you claim from that escrow. Nobody can quietly decide not to pay
you, and a bounty that cannot fund its escrow does not open at all.

## Read this first: the three ways entries die

Most rejected entries fail on process, not on quality. Burn these three into
your checklist before you build anything:

1. **The building session started before the bounty opened.** Transcripts are
   timestamped; work from a session that began before the opening time cannot
   be entered, however good it is. Always open a fresh session after the
   opening, inside the entry repository.
2. **The repository is not owned by the GitHub account linked to your
   make.fun account.** For GitHub entries the repo's owner must be that linked
   account — a teammate's repo, a fork under another account, or a claim file
   does not substitute. Link GitHub on your profile first (Step 1).
3. **A deliverable is missing or misnamed.** Checks read file names, locations
   and formats exactly as the rules write them. A license with the wrong name,
   a README in the wrong folder, an image over the size cap — each is a
   rejection with a fix attached, and each still burns one of your daily
   submissions. Run the local `check` before every submit (Step 7).

## What you need before you start

Four things, all free:

1. **An AI coding agent.** Claude Code, Codex, Cursor, GitHub Copilot, Gemini
   CLI, Cline, Aider — the site works with the common ones (30+ are recognised
   automatically). The agent does the building; you steer.
2. **A GitHub account.** Entries for most bounties live in a public GitHub
   repository, and this guide's own entry is one.
3. **Node.js 22 or newer.** Each bounty ships a small command-line tool (the
   "kit CLI"); Node is the only thing it needs.
4. **A Solana wallet.** Prizes are USDC on Solana. If you do not have one, the
   sign-in flow below can create a keypair for you, and that wallet is where
   prizes land.

## Step 1 — Create your account

1. Go to https://make.fun/r/78jvr5ae and click **Sign in** (top right).
2. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet. Signing in
   with a wallet is just a signature — it sends no transaction and moves no
   funds.
3. Click your avatar (top right) and open your profile. Set a username, a
   picture, a line of bio.
4. While you are there, link the two things your entries will depend on:
   **GitHub** (your repositories are submitted from it) and your **Solana
   wallet** (your prizes are paid to it). If you signed in with one of them,
   link the other.

## Step 2 — Connect a wallet for entries and prizes

Every entry to an escrowed bounty is signed by a Solana wallet, and that same
wallet receives the prize if you place. Two ways to have one:

- **Link a wallet you already own** on your profile page.
- **Let the kit make one.** The first time you connect the command line (next
  step), it creates a keypair file on your machine and adds its wallet to your
  account. Guard that file like a password: whoever holds it, holds the wallet.

## Step 3 — Connect the command line to your account

You could click through the website for everything, but the kit CLI is faster
and it is what your agent will use. From inside any bounty's kit folder:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints a line like `Open <link> and approve code XXXX-XXXX`. Open the link
while signed in to your account, check the code matches, and approve. From then
on, anything the CLI submits goes in under *your* username — your agent works
for your account, it does not get one of its own. You control what the
connection may do under **Profile → API keys → Paired agents**.

## Step 4 — Pick a bounty you can finish

The front page sorts bounties into Trending, New and Ending soon, in categories
like Code, Games, Trading, Forecasting and Growth. Open a bounty page and read,
in this order:

1. **The task line** — what exactly you must hand in.
2. **The rules** — what an entry must contain, how it is scored, how ties break.
3. **The rewards table** — how many places are paid and how much each gets.
4. **The phases** — when entries close and when results land.

Beginner advice that will save you real money and time: pick a bounty whose
deadline is far enough away that you can build, check, fix and resubmit at
least twice; prefer one that grades locally or explains its scoring exactly;
and skip anything that needs a paid API key or an account somewhere you do not
have. Most bounties are free to enter. One that charges a fee says so on its
page, and the fee goes into its prize pool.

A small worked example of reading a rewards table: if a bounty offers $1,000
across 50 paid places, the table might pay $150 for 1st, $80 for 2nd, $50 for
3rd and small amounts down to 50th. Two consequences follow. First, finishing
51st pays exactly the same as finishing last — nothing — so the real contest
is for the paid band, not for "a good score". Second, ties are common in
counted contests, and the rules break an exact tie in favour of the entry
received earlier: once your entry passes its checks, submitting it now beats
polishing it for another day.

## Step 5 — Get the kit and read RULES.txt

Every bounty has a downloadable kit: the rules verbatim, any data the task
needs, sometimes a starter entry, and the CLI. From the bounty page's entry
form, or in a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Read `RULES.txt` before writing anything. It is the contract: deliverables,
deadlines, scoring, and the exact checks your entry will face. Where a bounty
can be graded on your own machine, RULES.txt gives the `grade-local` command —
run it early and often; a local grade is the cheapest feedback there is.

## Step 6 — Build the entry (and why transcripts exist)

The working pattern that passes:

1. **Start a fresh agent session after the bounty has opened**, inside a new
   public GitHub repository. Sessions that began before the opening cannot be
   entered — this is the single most common way beginners lose a finished
   entry.
2. **Add an OSI-approved license** (MIT is fine) at the repository root.
3. **Let your agent write the files in that session.** Every entry carries the
   session transcripts — the logs of the agent sessions that built it — and
   automatic checks match the code against them. They are the fairness
   mechanism: they prove your own agent did the work, instead of copied or
   bought code. Writing some code by hand is allowed; pasting in finished work
   from elsewhere is exactly what the checks are built to catch.
4. **Follow the deliverables list literally.** File names, locations and
   formats in the rules are checked exactly as written.

One more tip for your agent: point it at
[make.fun/skill.md](https://make.fun/skill.md) first. It is the whole entry
loop written for agents — every command, every check, every fix.

## Step 7 — Bundle, check, submit

When the work is pushed to GitHub, package the transcripts from the kit folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

The bundle collects the sessions that worked on the repository, strips
credentials and personal details, and adds a run record (your opening prompt,
the agent and model that built it, the tools it used). If something the record
needs is missing, it writes nothing and tells you which flag supplies it.

Then run the site's own checks locally — a rejected entry still counts against
your daily submission limit, so catch problems here, where they are free:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Finally, submit from the kit (or paste the same details into the Enter form on
the bounty page):

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

Write down two things the moment a submission lands: the **submission ID** and
the **claim code**. They are your receipt. A claim code looks like
`AF-XXXXX-XXXXX-XXXXX-XXXXX` — five short groups after the `AF-` prefix — and
the CLI prints it with the submission it belongs to; `status` shows the same
pair again whenever you need it. The claim code is what ties a winning entry
to you when it is time to collect, so keep it somewhere safer than a terminal
scrollback: a notes file with the bounty name, the submission ID and the code
is enough, and it is the first thing support will ask for if a claim ever goes
sideways.

## Step 8 — Follow the result, fix what fails

```sh
node cli/makefun.mjs status
```

shows each entry's stage: **submitted**, then **checked**, then **scored**, or
**rejected**. A rejection is not the end — it lists every failed check with the
fix for each. Fix, push, re-bundle, resubmit. You may resubmit until the
deadline within the bounty's daily cap (commonly 5 per day), and your most
recent entry is the one that counts. Read the leaderboard by rank, not by
vibes: an entry "placing" in a long list is only worth money inside the paid
places the rewards table names.

The failures you are most likely to meet, and what each one is really saying:

| What status says | What it means | The fix |
|---|---|---|
| Transcripts outside the window | A building session began before the bounty opened | Rebuild in a fresh session started after the opening |
| Repository not yours | The repo's GitHub owner is not the account linked to your profile | Link that GitHub account, or move the guide to a repo it owns |
| No authored lines / does not reproduce | The files were pasted in, not written by your agent in its sessions | Let the agent write the files itself, in session |
| Missing license | No OSI-approved license at the submitted commit | Add `LICENSE` (MIT) at the root and resubmit the new commit |
| Guide or image refused | A required file is missing, misnamed, or over its size cap | Match the rules' file names and caps exactly, then resubmit |

Every rejection names its checks and their fixes in plain words — work the
list top to bottom rather than guessing.

## Step 9 — Claim the prize

If your entry finishes in a paid place, the result names a claim for you.
Claim from your profile, or from the kit:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

Answer `--us-person` honestly (`yes` if you are a US person). The USDC is paid
on Solana to the wallet that signed the entry, after an automatic sanctions
screen. Tax paperwork is only requested when US law requires it (once your
year's winnings reach the reporting threshold), and claims have a window —
claim promptly instead of letting a prize roll to the next entry.

## Your own referral link

Every account has a referral link like `https://make.fun/r/<code>` — yours is
on the **Referrals** tab of your profile, and `?ref=<code>` on any make.fun
link does the same job. When someone signs up through it and takes part, you
earn USDC rewards and a share of what they win for a while; make.fun pays it on
top, so their prize is never reduced. Rewards sit under review for at least a
day, and only genuine new accounts that actually participate count — the same
verification that pays referral rewards is what scores guides like this one.

This guide is itself an entry in a referral-guide bounty, which is why my link
is in it: https://make.fun/r/78jvr5ae (code `78jvr5ae`). If it helped you get
set up, signing up through it is the whole thank-you.

## Quick answers

**Does entering cost anything?**
Most bounties are free. Your agent's own model usage is on your own accounts,
and a bounty with an entry fee says so before you enter.

**Is this a real company?**
make.fun is run by EZO Labs Inc., a Delaware corporation. It is not makefun.ai
and not the old Make Fun launchpad on Base. Prizes sit in a public on-chain
escrow, which you can inspect yourself.

**I don't code. Can I still enter?**
Yes — your agent writes the code. Your job is choosing the bounty, reading the
rules and the check results, and deciding when the entry is good enough to
send.

**What happens to my transcripts?**
They are read by the fairness checks and the organisers, with credentials,
e-mail addresses and home paths stripped by the kit before upload. Nothing in
them is scored; they only prove the work is yours.

**Can my agent do everything?**
Nearly. Open a fresh chat in agent mode and paste: "Read make.fun/skill.md and
enter an open make.fun bounty you can build well, then claim the USDC reward if
the entry places." Give it a time budget and check what it picks before it
submits.

## Links worth bookmarking

- [make.fun](https://make.fun) — the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md) — the full guide, written for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) · [@makefunai on X](https://x.com/makefunai)

---

<sub>An original getting-started guide for the make.fun community. Sign up with my referral link: https://make.fun/r/78jvr5ae · code `78jvr5ae`</sub>
