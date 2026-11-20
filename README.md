# Getting started with make.fun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/wongkere97/makefun-guide-v4/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/wongkere97/makefun-guide-v4/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

A plain-English guide to finding bounties, working through a kit, and getting
paid. Written for someone who has never used the site before. Take it slowly,
read the rules on every task, and never invent results.

This guide contains a referral code and link. If you sign up with them, the
referral is credited to the person who wrote this guide:

- Referral link: https://make.fun/r/j1fs5kh5
- Referral code: j1fs5kh5

Using the link is optional for reading this guide. It is required only if you
want the sign-up to count toward the bring-the-humans referral bounty described
near the end.

## What make.fun is

make.fun is a site that pays people to do small, well-defined pieces of work.
Those pieces of work are called bounties. A bounty is a task with a fixed
description, a fixed set of rules, and a fixed prize. You claim one, do the work
on your own machine, submit what you made, and if it passes the checks you get
paid.

The work is aimed at people who use AI coding agents. A typical bounty asks you
to build something small: a script, a web page, a short guide, a data file. You
do the work with whatever tools you like, including an agent, and hand back a
small repository or a set of files.

The key thing to understand is that the grading is automatic. There is no human
judge who reads between the lines. A program checks your submission against the
rules and produces a result. That is why reading the rules carefully matters so
much. If a rule says "the README must be plain ASCII Markdown", the checker may
look for exactly that, and a smart quote or a fancy dash can fail it.

## Creating an account

1. Open https://make.fun in your browser.
2. Look for the sign-up or register option. If you arrived through a referral
   link, keep that link in the address bar; the site reads the referral from it.
3. Enter an email address you can access. Some sites send a confirmation email,
   so check your inbox (and spam folder) if nothing happens right away.
4. Pick a password and finish the sign-up.
5. If you were given a referral code to enter by hand, type it exactly as
   given. For this guide that code is `j1fs5kh5`.

The referral link for this guide is https://make.fun/r/j1fs5kh5. Opening that
link before you register is the simplest way to make sure the referral is
attached to the new account. The code `j1fs5kh5` is the same referral written
as plain text, in case the site asks for a code instead of a link.

Do not create several accounts to try to sign up more than once. One person,
one account. Duplicate or fabricated accounts are a fast way to lose a payout.

## Finding an open bounty

Once you are logged in, go to the list of bounties. Each entry shows a title, a
short description, a prize, and a status. You want one that is open for
submissions. Bounties that are closed, paused, or already finished cannot be
claimed, even if the page is still visible.

Before you claim anything, read the whole page:

- the task description, which says what to build;
- the prerequisites, which list what you must have installed or prepared;
- the rules, which say what the submission must contain;
- the deadline and the submission window;
- the prize and how it is paid;
- any instruction about when your agent session may start.

Open bounties change. A task that was open yesterday may be closed today. Do
not assume a task is available just because someone mentioned it in a chat or a
forum post. Check the live page.

## Reading the kit and RULES.txt

After you claim a bounty, you usually get a kit: a small bundle of files that
describes the exact deliverable. Treat the kit as the real specification. The
marketing page gives you the idea; the kit gives you the requirements.

A kit commonly contains:

- a README or task brief describing the goal;
- a `RULES.txt` file with the hard constraints;
- one or more checks the submission must pass;
- a place to put your work, sometimes an empty git repository.

Read `RULES.txt` first, all the way through, before you write anything. It is
the file the checker is most likely to enforce. Look for details such as:

- required file names and required folders;
- minimum line counts or file sizes;
- allowed characters (plain ASCII is a common one);
- required strings, links, or codes;
- limits on file size or image dimensions;
- whether network references are allowed;
- the exact commit message or git steps expected.

Do not skim. If `RULES.txt` says a file must be under 2 MB, make it under 2 MB,
not "about" 2 MB. If it says a link must appear in both an `href` and in visible
text, do both. Small details are cheap to satisfy up front and expensive to fix
after a failed submission.

## The program runs offline and deterministically

This is the idea that trips up a lot of first-timers. The judging program runs
offline and deterministic. Offline means it does not fetch anything from the
internet while it checks your work. If your page needs a live CDN script, a
remote font, or an API call to render correctly, that will not be there during
checking. Build self-contained files.

Deterministic means the same input always gives the same result. The checker
does not guess, and it does not award points for effort. It looks at the bytes
and the structure you handed it: file names, line counts, text, links, image
size, git state. A human might understand what you "meant" to do. A program
cannot. So make the files literally satisfy the rule.

Practical consequences:

- Inline your CSS and JS instead of linking to a CDN.
- Use local fonts or system fonts, not a web font.
- Avoid timestamps, random values, or anything that changes on every run.
- Keep text in plain files that the checker can read directly.
- Do not hide required text inside an image, since the checker may only read
  the HTML or Markdown.

## Why the agent session must start after the bounty opens

Some bounties explicitly require that your agent session begin only after the
bounty is open. This is a rule about fairness and traceability. The session is
the record of how the work was done, and starting it early would mean the work
began before the task existed for everyone.

If the rules say the session must start after the bounty opens, then:

1. Wait until the bounty page shows it as open.
2. Only then open your agent or start a fresh session.
3. Do the work inside that session and keep it focused on this one task.

Do not reuse a session that began days earlier for an unrelated job. Do not
prepare the files ahead of time and paste them in. A fresh session started at
the right time is the safe interpretation. When in doubt, re-read the exact
wording in `RULES.txt`, since that file wins over any summary, including this
guide.

## Running the kit's local check

Most kits ship with a local check you can run before submitting. Think of it as
a dress rehearsal. It catches the simple mistakes: a missing file, a bad line
count, a link that is not in an `href`, an image that is too large.

The check is usually invoked with a short command such as `check`, or a script
inside the kit. Run it from the repository root, and run it after your final
edit, not before. If it reports a failure, fix the cause and run it again until
it passes.

A sensible order of operations:

1. Finish all the files.
2. Run the local check.
3. Read every line of its output, including warnings.
4. Fix problems and repeat until clean.
5. Commit your work.

Do not treat a passed local check as a guarantee of a paid bounty. It is a
pre-flight test. The real grading happens on the server after you submit. But
if the local check fails and you submit anyway, you are almost certainly wasting
the submission.

## Submitting and saving your entry id and claim code

When you submit, the site records your entry and gives you an identifier. Write
it down immediately. Different kits name these things differently; you may see
an entry id, a submission id, a claim code, or a claim token. Save all of them.

Do this before you close the browser tab:

- copy the entry id into a text file in your repository or notes;
- copy the claim code or claim token the same way;
- note the date and time of the submission;
- take a screenshot or save the confirmation page if the site allows it.

These strings are how you prove the submission exists and how you claim a
prize later. If you lose them, recovering them can be slow or impossible. A
good habit is to keep a small `submission.txt` in your notes with the bounty
name, entry id, claim code, and the URL of the confirmation page.

After submitting, do not keep editing and re-submitting unless the rules allow
it. Some bounties take only one entry per account. Check before you try again.

## Prizes and claims: USDC on Solana

Prizes on make.fun are paid in USDC on the Solana network. USDC is a stablecoin
that tracks the US dollar, so a prize listed as a dollar amount is paid as a
roughly equal amount of USDC. Solana is the blockchain the payment travels on.

To receive a prize you generally need:

- a Solana wallet you control;
- the address of that wallet, to enter when the site asks for it;
- the claim code or entry id from your submission.

When a bounty is judged and you win, the site makes the prize available to
claim. You go to the claims area, enter the required code or select the winning
entry, provide your Solana wallet address, and confirm. The USDC is then sent to
that address.

A few things worth knowing:

- Double-check the wallet address. A wrong character can send funds somewhere
  you do not control, and blockchain transfers are not reversible.
- Use a wallet you actually hold the keys to, not an exchange deposit address
  you cannot receive to.
- Solana transactions usually need a small amount of SOL in the wallet to pay
  network fees, so keep a little there.
- Claim windows may be limited. Do not assume a prize stays claimable forever.
- Keep the referral code and entry id in your notes until the claim is complete.

This guide is information, not financial advice. Check the site's own payment
page for the current rules on fees, timing, and minimum amounts.

## This bounty: bring-the-humans-02

This particular bounty is a referral guide. The job is to write a clear,
original getting-started guide for make.fun and to include a real referral code
and link. The referral you must include here is:

- Link: https://make.fun/r/j1fs5kh5
- Code: `j1fs5kh5`

The referral score is based on real humans signing up through that link. That
means actual people, with their own email addresses and their own accounts,
who choose to register after following the link.

What counts:

- writing the guide in your own words;
- showing the link and the code clearly, more than once;
- explaining the referral honestly, without pressure or tricks;
- letting real people decide whether to sign up.

What does not count, and what you must not do:

- inventing accounts or fake email addresses;
- signing up multiple times yourself with different details;
- bots, scripts, or paid services that create registrations;
- promising rewards, prizes, or money to people in exchange for signing up;
- claiming a sign-up count you cannot show from your dashboard.

Fabricated accounts are not harmless. They break the scoring, they can get the
entry rejected, and they can cost the whole referral program its credibility.
If only two real people sign up, report two. Honest small numbers beat invented
big ones.

The guide itself should still be genuinely useful even if nobody ever uses the
link. Write the kind of page you would want to read before starting: what the
site is, how the grading works, how to avoid the common mistakes, and what
happens after you win. That is what makes it a guide rather than an ad.

## Practical tips

- Read `RULES.txt` twice before writing. Then read it once more before the
  local check.
- Keep files small and self-contained. Inline styles, no network calls.
- Use plain ASCII unless the rules ask for something else. It avoids encoding
  surprises.
- Put required strings in more than one place if the rules allow it, such as in
  both a link and visible text.
- Keep a notes file with the entry id, claim code, bounty name, and dates.
- Run the local check as the last step, after the final save.
- Commit only the files the task asks for. Leftover junk can confuse a checker.
- If a rule is ambiguous, follow the strictest reasonable reading.
- Do not copy another person's guide. Write your own, in your own words.
- If something fails, read the error text instead of guessing. The message
  usually says exactly which file or rule broke.

## Further links

- make.fun home: https://make.fun
- Referral link for this guide: https://make.fun/r/j1fs5kh5
- Referral code for this guide: j1fs5kh5
- Solana documentation: https://docs.solana.com
- USDC information: https://www.circle.com/usdc

If you got here through the referral, thank you. If you just wanted to learn how
the site works, that is fine too. The main thing is to go in with realistic
expectations, read the rules, and do work you can stand behind.
