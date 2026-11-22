# Slack community scoring for Claude Code

> Built while launching [RevyOps, the AI CRM for Claude](https://revyops.com/waitlist?utm_source=github&utm_medium=referral&utm_campaign=launch&utm_content=slack-scoring-readme). **[Join the waitlist →](https://revyops.com/waitlist?utm_source=github&utm_medium=referral&utm_campaign=launch&utm_content=slack-scoring-readme)**

Your Slack community is a warm lead list. This skill turns every join, post, reply, reaction and DM into points on the right person. Then it ranks them, so you know who to talk to first, and why.

## What you get

One Claude Code skill, `slack-community-scoring`:
- **Five events with points, fades and caps.** Joined, posted, replied, sent you a DM, reacted.
- **Matching by email,** so every event lands on one person.
- **The Zapier steps** for joins, posts, replies and reactions.
- **A Google Sheets formula** if you don't have a CRM.
- **A weekly rank-and-act loop:** the top 20, the reason each one is there, and how to reach out.

## What you need

- Claude Code
- A Slack workspace where you can add apps
- Zapier (or your own Slack API script)
- Somewhere to keep people and points: a CRM with lead scoring, a Google Sheet, or RevyOps (free, see below)

## Install

**1. Add it in Claude Code:**

```
/plugin marketplace add revyops/slack-community-scoring
/plugin install slack-community-scoring@slack-community-scoring
```

Or copy `skills/slack-community-scoring` into `~/.claude/skills/`.

**2. Ask for it in plain words:** "Set up Slack community scoring for my workspace."

**3. Each week, ask:** "Who are my top 20 members, and why?"

## The flow

| Step | What happens |
|---|---|
| 1 · Decide what counts | Five events, their points, how fast they fade, how often they count |
| 2 · Match each event to one person | Look up the email, skip your own team |
| 3 · Connect Slack | One set of Zaps per workspace |
| 4 · No CRM, use a sheet | One formula adds up each person's points |
| 5 · Rank and act | The top 20, why, and one personal message each |

## Make it yours

The skill is a plain Markdown file. Change the points or the events, and Claude follows your version. The same method works for Discord, Circle, Skool or any forum.

## Run the scoring free in RevyOps

Zapier gets the events out of Slack. Scoring everyone, ranking them, and starting your outreach happen in RevyOps, next to your email, LinkedIn and website visits. The free RevyOps plan covers this setup. See today's limits at [revyops.com/crm-pricing](https://revyops.com/crm-pricing?utm_source=github&utm_medium=referral&utm_campaign=launch&utm_content=slack-scoring-readme).

Join the waitlist and we'll set it up for you for free. Beta testers get access in December.

**[Join the waitlist →](https://revyops.com/waitlist?utm_source=github&utm_medium=referral&utm_campaign=launch&utm_content=slack-scoring-readme)**

## Licence

MIT. Use it, change it and share it, including in paid work. Keep the copyright line. See [LICENSE](LICENSE).
