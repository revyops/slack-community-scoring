---
name: slack-community-scoring
description: Score and rank the people in your Slack community so you know who to talk to first. Use when someone wants to turn a Slack (or Discord, Circle, Skool) community into a ranked lead list, set up scoring for joins, posts, replies, reactions and DMs, connect Slack to a CRM with Zapier, or asks "who are my most engaged members?".
version: 1.0
---

# Slack community scoring

A community is a warm lead list. Most people never score it. This skill turns every join, post, reply, reaction and DM into points on the right person, so you can rank them and talk to the top people first.

It works with any tool that can hold people and points: a CRM with lead scoring, a database, or a Google Sheet. (RevyOps does all of it for free. See the end.)

## How to use this skill

Ask Claude in plain words, for example:
- "Set up Slack community scoring for my workspace."
- "Who are my top 20 members this month, and why?"
- "Write the Zapier steps for reactions."

Claude follows the steps below in order. It asks before it turns anything on or sends any message.

## Step 1 · Decide what counts

Score what a person does, not who they are. Use these five events. They are a good default; change the points to fit your community.

| What they did | Points | Fades to zero in | Counts |
|---|---|---|---|
| Joined the community | 25 | 180 days | once per community |
| Posted (a new message, not in a thread) | 35 | 30 days | once a day |
| Replied in a thread | 35 | 30 days | once per thread |
| Sent you a direct message | 65 | 60 days | once a month |
| Reacted (any emoji) | 10 | 14 days | every reaction |

Why these numbers:
- **A DM is the strongest.** They chose to talk to you, one on one.
- **A post and a reply are equal.** Both take effort and show up in public.
- **A reaction is small but adds up.** Ten reactions in a week is a real signal. Don't cap it.
- **Fading keeps the list fresh.** Points lose value evenly each day and hit zero at the end. Someone who was busy last spring and then went quiet drops down. Someone busy this week rises.

**Match your other channels.** If a reaction on LinkedIn is worth 10, a reaction in your Slack is worth at least 10. A community member is warmer than a stranger on a feed. Never score the warmer place lower.

**Leave these out:** leaving the community, and going quiet. The fade already handles quiet. Keep it simple.

## Step 2 · Match each event to one person

Every event must land on the right person, or the ranking is wrong.
- **Match by email.** Slack events give you a user ID, not an email. Look the ID up first (in Zapier: Slack › Find User by ID, which returns the profile email).
- **No email, no score.** Skip events with no email. Don't guess.
- **Skip yourself and your team.** Filter out your own email and your company domain.
- **One human, one person.** If someone has two emails, merge them into one person so their points add up.

## Step 3 · Connect Slack (Zapier recipe)

One set of Zaps per Slack workspace. You must be able to add apps to that Slack.

1. **Joins.** Trigger: Slack › New User. Filter: has an email. Action: log "Joined" on the person.
2. **Posts and replies.** Trigger: Slack › New Public Message Posted Anywhere (bot messages off). Filter: has an email, not your team. Paths: if the message has a thread timestamp (`thread_ts`), log "Replied" with it as the thread ID; if not, log "Posted".
3. **Reactions.** Trigger: Slack › New Reaction Added (any channel). Step: Find User by ID (the trigger has no email). Filter: has an email, not you. Action: log "Reacted :emoji:".
4. **DMs.** Zapier can't see DMs to you. Log these by hand once a week, or use your CRM's own Slack integration if it reads DMs.

Each action writes one activity with: the person's email, the community name, what they did, the channel, the thread ID and a link to the message. Points come from your scoring rules, not from the Zap. That way you can change points later without touching the Zaps.

**Cost:** about 1 Zapier task per message and 2 per reaction or join. A busy community can use a few thousand tasks a month. Check your plan.

**Test before you trust it.** Many Zapier test runs don't write for real. After you turn a Zap on, react to a message yourself from a second account and check the activity lands on the right person.

**Backfill the last two weeks** once, so the list isn't empty on day one. Read the channel history with the Slack API and log the same events with their real dates.

## Step 4 · If your tool has no scoring, use a sheet

One row per event: email, event, points, date. Then per person:

```
score = SUM over their events of  points × MAX(0, 1 − days_old ÷ fade_days)
```

In Google Sheets, with email in A, points in C, date in D and fade days in E, add a column F for each event's value today:

```
F2:  =C2 * MAX(0, 1 - (TODAY() - D2) / E2)
```

Then each person's score (their email in H2):

```
=SUMIF(A:A, H2, F:F)
```

Apply the "counts" column before you add a row (one post a day, one reply per thread, one DM a month).

## Step 5 · Rank and act

Once a week:
1. **Rank everyone by score.** Take the top 20.
2. **Read why.** For each, list the last three things they did (a post about X, a reply in Y). That is your reason to reach out.
3. **Reach out like a person.** A short DM that names what they did and offers something useful. Never a canned message, never a pitch in the first line.
4. **Note who answered.** A reply is a DM, so it scores too. The list gets better each week.

Good rules:
- **Fit first, then score.** A high score from someone who could never buy is a fan, not a lead. Check they match who you sell to.
- **Don't spam the top.** One personal message, one follow-up if they didn't answer, then stop.
- **Tell your community the truth.** Scoring helps you spend your time on the people who want it. Never share someone's score with them or anyone else.

## The same method works anywhere

Swap the trigger, keep the rest. Discord, Circle, Skool, a forum, webinar chat, LinkedIn comments: each has a join, a post, a reply, a reaction and a DM. Score them the same way, on the same person, and one ranked list shows who is warmest across all of them.

## Do it for free in RevyOps

RevyOps is the AI CRM for Claude. It joins every channel onto one person, scores each activity with a fade, and ranks them for you. Your Slack scoring sits next to your email, LinkedIn and website visits.

The free RevyOps plan covers this setup. See today's limits at revyops.com/crm-pricing.

Join the waitlist and we'll set it up for you for free. To get in early, say yes to the beta question. Beta testers get access in December.

https://revyops.com/waitlist?utm_source=github&utm_medium=referral&utm_campaign=launch&utm_content=slack-scoring-skill
