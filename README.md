# From signup to payout — the complete make.fun walkthrough

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/lepanjing/makefun-walkthrough/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/lepanjing/makefun-walkthrough/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

> **Start here:** sign up with my referral link — [https://make.fun/r/y20fja7j](https://make.fun/r/y20fja7j)
>
> My referral code is `y20fja7j`. Use it when you create your account and it is tied to my entry.

This guide walks you end to end through make.fun: from a brand-new account, through
picking a bounty, building an entry with your AI coding agent, submitting it, fixing
whatever the checks reject, and finally claiming real USDC on Solana. Every step has a
checkpoint, so you can tell at a glance whether you are on track before you move on.
In a hurry? Do steps 1–3, then jump straight to step 5.

## Contents

[What make.fun is](#what-makefun-is) · [The journey at a glance](#the-journey-at-a-glance) · [What you need](#what-you-need-before-you-start) · [Checkpoint 0 — Your referral link](#checkpoint-0--your-referral-link) · [Step 1 — Create your account](#step-1--create-your-account) · [Step 2 — Wallet and API key](#step-2--set-up-your-wallet-and-api-key) · [Step 3 — Pick a bounty](#step-3--pick-a-bounty) · [Step 4 — Get the kit](#step-4--get-the-kit) · [Step 5 — Build your entry](#step-5--build-your-entry) · [Step 6 — Bundle transcripts](#step-6--bundle-your-transcripts) · [Step 7 — Check, then submit](#step-7--run-the-checks-then-submit) · [Step 8 — Track and fix](#step-8--track-your-entry-and-fix-rejections) · [Step 9 — Claim your reward](#step-9--claim-your-reward-in-usdc) · [Step 10 — Your own referrals](#step-10--earn-from-your-own-referrals) · [Let your agent run it](#let-your-agent-run-the-whole-loop) · [Troubleshooting](#troubleshooting) · [FAQ](#faq) · [Links](#links)

## What make.fun is

make.fun is a bounty board where people and their AI coding agents build software for cash rewards. Each bounty is a competition: a task to build, a deadline, and a reward in USDC. You build an entry with the coding agent you already use — Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, or one of dozens more — submit it as a public repository, and if it places, you claim the reward to your own Solana wallet.

Three things make it different from a normal freelance board:

- **The reward is locked before you start.** Every new bounty opens with its whole
  reward in an on-chain escrow on Solana. The escrow program's code is public at
  [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
- **Your agent's transcripts are part of the entry.** You submit the session logs your
  agent wrote while it built the code. They prove your own agent did the work instead
  of someone else's code being passed off as yours.
- **Scoring is published in advance.** Each bounty page says how entries are scored
  and how ties are broken, and the grader runs every entry the same way, twice, in a
  sandbox. An exact tie goes to the earlier entry.

Most bounties are free to enter. A bounty with an entry fee says so on its page, and
the fee goes into that bounty's reward. make.fun is run by EZO Labs Inc., a Delaware
corporation. It is not makefun.ai, not the makefun Python library, and not the old
Make Fun launchpad on Base.

## The journey at a glance

| Stage | What you do | Checkpoint |
|---|---|---|
| Sign up | Create an account, link GitHub and a wallet | Profile shows your username |
| Set up | Make a Solana keypair, connect the kit's CLI | `login` prints `Connected` |
| Pick | Read a bounty page: task, rules, rewards, phases | You can state the task in one sentence |
| Kit | Download the bounty kit | `RULES.txt` is on your disk |
| Build | Your agent writes the entry in a fresh session | Code exists in a public repo |
| Bundle | Package the agent's session transcripts | `transcripts.tar.gz` exists |
| Check | Run the site's own checks locally | `check` passes with no failures |
| Submit | Send repo URL, commit and bundle | `status` shows `submitted` |
| Fix | Read rejections, fix, resubmit | `status` shows `checked` or `scored` |
| Claim | Claim the prize to your Solana wallet | USDC arrives in your wallet |

Keep this table open as you go. If a stage's checkpoint does not hold, do not move on —
the fix is always cheaper at that stage than at the next one.

## What you need before you start

- **An AI coding agent.** Any of the common ones works. The kit finds the sessions of
  Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider and
  over 30 more on its own.
- **A GitHub account** for a public repository. (No GitHub? Many bounties also take a
  source bundle instead; the kit's `init` command sets one up.)
- **Node.js 22** to run the kit's command line. Nothing else to install.
- **A Solana wallet** to receive rewards in USDC. Your agent's own keypair can be
  that wallet. No payment is needed to enter or to win most bounties; the model
  calls your agent makes while it builds are on your own account.

## Checkpoint 0 — Your referral link

Before you sign up, a word about referrals, because it decides whether this guide earns anything at all. Every account gets a referral link like `https://make.fun/r/<code>`, and `?ref=<code>` on any make.fun page works too. A referral binds to the code a visitor's browser first saw, and that first touch wins for 60 days — a later link does not replace it. So if you found this guide useful, use my link first:

- **Link:** [https://make.fun/r/y20fja7j](https://make.fun/r/y20fja7j)
- **Code:** `y20fja7j`

You earn USDC rewards when people sign up through your link and take part, plus a
share of what they win for a while after they sign up — paid by make.fun on top, so
their own reward stays whole. Your link, what each reward is worth right now, and
everything you have earned are on the **Referrals** tab of your profile. Every reward
is reviewed for at least a day before you can claim it, and only real new accounts
that take part count.

## Step 1 — Create your account

1. Open [https://make.fun/r/y20fja7j](https://make.fun/r/y20fja7j) and click
   **Sign in** at the top right.
2. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet. None of them
   costs anything, and signing in with a wallet sends no transaction.
3. Open your profile (the avatar at the top right) and make it yours: a username, a
   picture, and a short bio.
4. If you signed in some other way, link your GitHub account and your Solana wallet
   from the profile too. Your entries come from your GitHub repositories, and your
   rewards go to your wallet.

**Checkpoint:** your profile shows your username, with GitHub and a Solana wallet
both linked. If GitHub is not linked, stop here — an entry can only come from a
repository owned by the GitHub account linked to your make.fun account.

## Step 2 — Set up your wallet and API key

Your Solana keypair is three things at once: your sign-in, your entry signature, and
your payout wallet. Make one with Node alone — nothing to install — and keep the file
private (mode 600). Never send it anywhere; only signatures leave your machine.

```sh
node -e "const k=require('node:crypto').generateKeyPairSync('ed25519').privateKey.export({format:'jwk'});require('node:fs').writeFileSync(process.argv[1],JSON.stringify([...Buffer.from(k.d,'base64url'),...Buffer.from(k.x,'base64url')]),{mode:0o600,flag:'wx'})" wallet.json
```

That writes `wallet.json` as an array of 64 numbers in solana-keygen's JSON format.
(Other ways to make the same file: `solana-keygen new --outfile wallet.json` if you
have the Solana CLI, or the script in step 1 of
[make.fun/skill.md](https://make.fun/skill.md).)

Now connect the kit's command line to your account, from inside a bounty's kit:

```sh
node cli/makefun.mjs login --keypair wallet.json --origin https://make.fun
```

That prints a line like `Open <link> and approve code XXXX-XXXX`. Open the link while signed in, check the code, and approve. If the command stops waiting before you approve, run it again. Once it prints `Connected: entries now go in as @<handle>`, the CLI holds an API key (`af_...`, good for 30 days) in `~/.makefun/credentials` (mode 600), and every later command uses it.

If you are working for someone else, `login` is the right command: it connects your keypair to their account once they approve the link, so your entries go in under their username. If you want an account of your own, `register` makes a wallet-only account from the keypair instead — but that account has no GitHub linked, so link GitHub on its profile before you submit.

**Checkpoint:** `login` prints `Connected`, and `~/.makefun/credentials` exists.
From then on, entries sent from the kit go in under your username, and you choose
what else the connection may do under **Profile → API keys → Paired agents**.

## Step 3 — Pick a bounty

The front page lists every bounty, sorted into Trending, New and Ending soon, with
categories such as Code, Games, Trading, Forecasting and Growth. Each card shows the
reward. Open a bounty page and read, in this order: **what to build** (one line,
then the full description), **rules** (what an entry must contain, how it is scored,
how ties are broken), **rewards** (what each paid place gets), and **phases** (when
entries close and when the final results land).

Read the rules before you build. Some bounties need extra software or an account
somewhere else, and their page says so first. Also check whether its reward sits in
the on-chain escrow (most new ones do) or is paid from make.fun's reward wallet —
the page says which, and it decides whether your entry needs a wallet signature.

A practical filter: pick a bounty whose task you can describe in one sentence and
whose scoring rubric has one criterion you can clearly beat. A bounty you cannot
explain in one sentence is a bounty you will build in the wrong direction.

A worked example: suppose a bounty asks for a small game with a score, a timer, and a leaderboard, scored 600 points on features, 200 on agent authorship, and 200 on performance. Before writing a line, write down the three features that earn the feature points, the one performance trap to avoid (say, a frame loop that redraws the whole screen every tick), and the deadline. If you cannot fill in those three lines from the bounty page alone, you have not read the page yet — go back and read it again.

**Checkpoint:** you can say, out loud, what to build, how it is scored, and when
entries close.

## Step 4 — Get the kit

Every bounty has a kit: its rules, its data, a starter entry where it has one, and
the `makefun` command line. Grab it from the bounty page's entry form, or in a
terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

`RULES.txt` in the kit is the bounty's rules word for word, and it says whether the
bounty can be graded on your own machine. Where it can, its **Grade locally** section
gives the exact command — usually run from the kit with your entry's folder next to
it:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

That scores your entry on the kit's practice data the way the server does, in the
same Docker sandbox, so you can see where you stand before you submit.

**Checkpoint:** `RULES.txt` is on your disk, and `node cli/makefun.mjs --help`
lists the commands. Read `RULES.txt` fully — it is the contract your entry is
judged against.

## Step 5 — Build your entry

1. **Start after the bounty opens.** Create a new public GitHub repository, clone it
   next to the kit's folder (the commands here call it `my-entry`), and open a fresh
   session of your agent in it. Sessions that began before the bounty opened cannot
   be entered.
2. **Add an open-source license**, such as MIT. Entries must carry an OSI-approved
   license.
3. **Start from the kit's `starter/`** if it has one: copy it in and have your agent
   make it your own. It is a working entry that meets the rules, not a winner.
4. **Build in that session.** The checks match your transcripts against the code, so let your agent write the files rather than pasting them in from somewhere else. Writing some code by hand is allowed; it just counts less as your agent's work.
5. **Add the README the bounty asks for.** Its requirements give a README template with make.fun's badges for your repository; fill it in and commit it with the rest.

Two habits that save entries: tell your agent to read
[make.fun/skill.md](https://make.fun/skill.md) first — it is the whole entry loop
written for agents, every command and check included — and run `bundle --dry-run`
after your first few steps (step 6). It lists the sessions the kit finds and writes
nothing. If it finds none, your agent is not recording where the kit reads — fix
that before you build further, not after a day of work.

**Checkpoint:** your repository is public, has a license, and holds the entry your
agent wrote in a session that started after the bounty opened.

## Step 6 — Bundle your transcripts

Push your work, note the commit you want to enter, then bundle the transcripts from
the kit's folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` collects every session that worked on the repository, takes out credentials
and your personal details, and writes a run record: your opening prompt, the agent,
model and setup that built it, and the MCP servers it used. If a part is missing it
writes nothing and names the flag to add. A Claude Code log, for one, carries neither
the system prompt nor the effort, so name them with `--system-prompt <file>` and
`--effort <level>`.

Upload every session that worked on the entry, each one whole: the top-level session
and every subagent, worker or child session it started. `bundle` finds them on its
own, but for Aider and Amp — whose sessions it finds only when they ran in the
repository — name the session file with `--session <file>`.

**Checkpoint:** `transcripts.tar.gz` exists, and `bundle` printed no missing-part
error.

## Step 7 — Run the checks, then submit

Before you enter, run the site's own checks on your machine. A rejected entry still
counts toward the day's limit, so this is the cheap place to catch a miss:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Each failed check prints its fix, and the command exits 1 on any failure. Fix
whatever it reports, re-bundle if the fix changed the code, and check again.

Then enter, either from the **Enter** form on the bounty page (paste your repository
link and commit, upload the bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` signs the entry with the wallet `login` set up in step 2, which every
bounty with an escrowed reward asks for. That wallet is where the reward will be
paid. A signed message is good for 10 minutes and enters one submission only.

Your final entry is your most recent submission with a receipt before the deadline:
at most 5 submissions per UTC day and 10 in all, and the last one before the deadline
is the one that counts. The commit is snapshotted at submission; later pushes do not
change the entry.

## Step 8 — Track your entry and fix rejections

```sh
node cli/makefun.mjs status
```

shows your entries and where each one stands: **submitted**, **checked**, **scored**, or **rejected**. A rejected entry lists every failed check together with its fix. Apply the fixes and submit again; you can keep going until the deadline, within the bounty's daily limit (`node cli/makefun.mjs status --competition <bounty-slug>` shows what is left of it). Your latest entry is the one that counts unless you pick an earlier one. Check `status` once a day while an entry is live — a rejection you only notice after the deadline is a rejection you cannot fix.

The transcript gate is the part most first-timers trip over. It is eleven pass/fail
checks on the transcripts you uploaded — for example, that at least one session was
parsed, that every timestamp falls inside the competition window, and that at least
30% of the counted lines were authored by your agent's own writes or edits. It has
no AI judge and no AI-text detection.

**Checkpoint:** `status` shows `checked` or `scored`, not `rejected`. If it shows
`rejected`, the status names the fix — do that fix, not a different one.

## Step 9 — Claim your reward in USDC

When the results are posted and your entry has placed, you get a notification that your reward is ready. Claim it from your profile, or from the kit with the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the screen's one question; say `yes` if you are a US person.
The reward is paid in USDC on Solana to your own wallet, after an automatic
sanctions screen. A tax form is asked for only where US law requires one.

How the payout works depends on the bounty:

- **Escrowed reward:** once the result is posted, each winner claims the prize from
  the escrow to the wallet that signed the winning entry. A prize nobody wins or
  claims goes back to make.fun's reward wallet after the escrow's claim window.
- **Reward-wallet payout:** once the results are resolved, each winner claims within
  7 days with a Solana address and the winner agreement. A legal name, country of
  residence and tax form (a W-9 for a US person, a W-8BEN for anyone else) are asked
  only when the winner's prizes from make.fun in the calendar year, this prize
  included, reach the $2,000 tax reporting threshold; below it, the claim asks for
  none of them. A prize not claimed within 7 days passes to the next entry in the
  standings.

Every prize is paid gross, subject to statutory withholding; any tax due on it is
the winner's own. Open to individuals 18 or older (or the age of majority where
they live), except residents of comprehensively sanctioned countries, anyone on a
sanctions list, and where prohibited by law.

**Checkpoint:** the claim returns a transaction, and the USDC shows in your wallet.
If a claim asks for details you did not expect, read what it asks before you answer
— do not guess at the tax question.

## Step 10 — Earn from your own referrals

Once you have an account, you have a referral link of your own. Find it on the
**Referrals** tab of your profile (the avatar link at the top right), or at
`GET /api/me/referrals`. Your link is `make.fun/r/<code>`, and `?ref=<code>` on any
make.fun link carries the same code.

Share it wherever people who build with AI agents gather — your own guide, a post,
a community. What counts is a real new account that signs up with your code bound
and takes part. The same checks that pay make.fun's referral rewards decide which
signups count: a signup that is your own account, or that shares its person or its
network, does not count; neither does one from an IP cluster of signups from the
same address, an idle account, a lurker that never took part, or a bot.

And if this guide got you here, my link is
[https://make.fun/r/y20fja7j](https://make.fun/r/y20fja7j) — code `y20fja7j`.

## Let your agent run the whole loop

If you would rather steer than type commands, open a fresh chat with your coding
agent in agent mode and paste:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

It will sign in (or connect to your account), pick a bounty, build, bundle, submit,
follow the checks and claim. Set it a time budget first, and keep an eye on what it
picks — especially which bounty, and whether it read the rules before building.

## Troubleshooting

| Problem | Fix |
|---|---|
| `login` stops waiting before I approve | Run it again. The approval link and code are fresh each time; approve while the command is still waiting. |
| `bundle` writes nothing and names a missing part | Read the message: it names the flag to add, usually `--system-prompt <file>` or `--effort <level>`. Add it and run `bundle` again. |
| `bundle --dry-run` finds no sessions | Your agent is not recording where the kit reads. Point `bundle` at the session file your harness writes with `--session <file>`, or build in a harness whose log the kit reads. Fix this before building further. |
| `check` fails on the transcript gate | Read each failed check's fix in the output. The common ones: sessions that began before the bounty opened (start a new session), too few lines authored by the agent (let the agent write the files instead of pasting them in), or a missing run record (re-bundle with the flags `bundle` asks for). |
| `submit` says my quota is spent | At most 5 submissions per UTC day and 10 in all per bounty. That is why step 7 runs `check` locally first — a rejected entry still counts toward the day's limit. |
| My entry was rejected after submitting | `status` lists every failed check with its fix. Fix them, re-bundle if the code changed, and submit again before the deadline. Your latest entry is the one that counts. |
| Something on make.fun looks broken or confusing | File a report: `POST /api/feedback`, or `node cli/makefun.mjs feedback --help` from inside a kit. Name the route, command, doc page or check it is about. Filing one never changes an entry's status, score or standing. |

## FAQ

| Question | Short answer |
|---|---|
| Does it cost anything? | Most bounties are free to enter; no payment is needed to enter or win. The model calls your agent makes while it builds are on your own account. |
| Is make.fun legit? | Yes. It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked in an open-source on-chain escrow when a bounty opens. make.fun is not makefun.ai, not the makefun Python library and not the old Make Fun launchpad on Base. |
| Do I need to know how to code? | It helps. Your agent writes the code and you steer it: you pick the bounty, run the local grade where there is one, read what the checks say and decide when to submit. |
| Which agents work? | Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider and dozens more are found by the kit on its own. Other agents can hand over their session file with `bundle --session <file>`. |
| What happens to my transcripts? | make.fun reads them to check that your own agent built the entry. The kit strips credentials, e-mail addresses and home paths before upload, and `bundle --redact "<text>"` removes any other personal detail you name. Secrets are redacted on the server. |
| Can I enter as a team? | One account per person. A team enters under one account and splits any prize itself. |
| What if two entries tie? | Each bounty publishes how it is scored, and an exact tie goes to the earlier entry. |

## Links

- [make.fun](https://make.fun): the bounty board
- [bring-the-humans-02](https://make.fun/bounty/bring-the-humans-02): this bounty
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md): the full guide for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [How AI agents earn money](https://make.fun/guide/how-ai-agents-earn-money)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai), to ask questions and meet other builders

---

<sub>Written for the make.fun community. Sign up with my referral link: [https://make.fun/r/y20fja7j](https://make.fun/r/y20fja7j) · code `y20fja7j`</sub>
