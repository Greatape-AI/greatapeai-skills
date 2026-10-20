---
name: employee-pack
description: Pack up what you know about the user's work into employee-pack.zip, which they upload to their GreatApe digital employee so it starts already knowing their role, company, people, processes and routines. Use when the user says "make an employee pack", "move this to my GreatApe employee", "export what you know for my employee" or "set up my digital employee".
---

# Employee Pack

The user is handing their work to a GreatApe digital employee: a colleague that works on its own in their Slack, email and apps. Pack everything you know about that work so the employee starts on day one knowing what you know. Look first, ask only what's missing, then write one zip.

**IRON LAW: INVENT NOTHING.** Every line in the pack is something the user told you or something you actually know about them. Leave out a guess you can't trace, or ask about it.

## Step 1: Gather, silently

Before asking anything, read every source you can reach:

- your memory of the user, and their custom instructions or personalization;
- projects: their instructions and files;
- past conversations: search them if you can, and look for what they ask again and again;
- scheduled tasks or reminders you run for them;
- apps they already connected to you (Drive, Gmail, Notion, Calendar): read only, never change anything.

Sort what you find:

| Bucket | Look for |
|---|---|
| The user | name, role, company, timezone, how they like answers, what they care about |
| Company | what it does, stage, customers, products, pricing |
| People | who they work with: role, what to go to them for, how to reach them |
| Processes | anything with steps they asked for more than once or explained to you |
| Recurring | anything they want done on a cadence |
| Rules | corrections and standing preferences ("always CC finance", "no emojis with clients") |
| Documents | templates, guides, price sheets, FAQs they shared or you wrote for them |
| Apps and channels | the tools and places their work happens |

Can't reach memory or past chats? Say so in one line, and ask more in Step 3.

## Step 2: Pick the job

ONE question. The employee holds ONE role. Offer 1 to 3 roles drawn from what they use you for most:

> From our chats, you lean on me most for {X}, {Y} and {Z}. Should your employee be your {role A}, your {role B}, or something else?

Everything in the pack serves that role. Leave out what doesn't.

## Step 3: Fill the gaps

One question per message, at most 8 in total, only about what Step 1 didn't answer. In this order:

1. **The job:** what it owns from day one, and what success looks like at 30 and 90 days.
2. **Company and people:** whatever is missing.
3. **How the work is done:** "Walk me through {process} step by step", for each process that lacks steps.
4. **Recurring work:** what happens every day or week, when, and in which timezone.
5. **Voice:** how it should sound.
6. **Apps and channels:** where the work happens.
7. **First tasks:** what it should do first.

Stop early when you have enough. "Skip" means move on.

## Step 4: Show the outline. STOP.

```
EMPLOYEE PACK: {role} for {name}
Role:       {one line}
Company:    {one line}
Voice:      {one line}
Goals:      {n}: {names}
About you:  {one line}
Memories:   {n}
  - {slug}: {one line}   (inferred)
Skills:     {n}
  - {name}: {one line}
Files:      {n}: {names}
Routines:   {n}
  - {name}: {when}
Setup:      {apps, channels, keys by name, uploads}
First tasks: {1 to 3}
```

Mark `(inferred)` on everything the user didn't tell you directly. Ask: "Anything to cut, fix or add?" Do NOT write the pack until they approve.

## Step 5: Write the pack

Build this folder, zip it as `employee-pack.zip`, and give it to the user as a download:

```
employee-pack/
├── PACK.md
├── memories/{slug}.md
├── skills/{name}/SKILL.md      (plus any references/, scripts/, templates the skill uses)
└── files/{name}                documents a memory points to
```

**`PACK.md`:**

```markdown
---
employee_pack: 1
created: {YYYY-MM-DD}
made_with: {Claude | ChatGPT | your name}
owner: {user's name}
role: {the role}
---

# Employee pack: {role} for {owner}

{One paragraph: what this employee is for.}

## Role
What you own from day one, how you work, and what success looks like at 30 and 90 days.

## Company
What the company does, its stage, customers and products. Team: one line each, `- {Name} ({role}): {what to go to them for}, {work contact}`. Key outside contacts. Where the work happens.

## Voice
How you sound and how you work: tone, length, formality, what to avoid.

## Goals
### {Goal}
Target: {what done looks like}. Deadline: {date}. Why: {one line}.

## About you
The owner: role, timezone, language, preferred channel, communication style, preferences, what they care about, open commitments.

## Routines
### {name}
When: {weekdays 9:00}
Cron: {0 9 * * 1-5}
Timezone: {Asia/Kolkata}
Brief: {what to do and why, where to deliver, what done looks like, when to skip. Whoever runs it has seen none of this chat.}

## Setup
- App: {HubSpot}: {why}
- Channel: {Slack #sales}: {why}
- Secret: {STRIPE_API_KEY}: {what for}
- Upload: {Q3 pricing deck}: {why}

## First tasks
- {task}: {why it comes first}
```

Write Role, Voice and Goals to the employee ("You own..."). Write About you about the owner.

**`memories/{slug}.md`**, one fact per file:

```markdown
---
name: {slug}
description: {one line that states the fact itself}
type: person | feedback | project | reference
updated: {YYYY-MM-DD}
---

{The fact. For feedback and project, add **Why:** and **How to apply:** lines.}
```

- `person`: someone's work identity.
- `feedback`: a standing rule, with the why.
- `project`: ongoing work, with absolute dates.
- `reference`: a pointer to a system, link or file. A file in the pack is pointed to as `files/{name}`.

**`skills/{name}/SKILL.md`**: frontmatter `name` (kebab-case) and `description` (what it does and when to use it), then numbered steps someone else could follow. Name the app and the outcome, never your own tool names. Keep it under about 150 lines, and put templates, examples and scripts next to it in its folder.

**Can't create files?** Write ONE `employee-pack.md` in a single code block instead. Put every file under its own `===== file: {path} =====` line, starting with `===== file: PACK.md =====`. Binary documents can't travel this way: list them under Setup as `Upload:`.

## Step 6: Hand it over

> Your pack is ready: employee-pack.zip. Open your employee in GreatApe, upload it in the chat, and say: set yourself up from this pack.

## What goes where

| You know... | It becomes |
|---|---|
| a process with steps | a skill, with its templates, examples and scripts in its folder |
| one rule, preference, person, project or link | a memory |
| a document not tied to one process | a file in `files/` plus a `reference` memory pointing at it |
| a document you can't copy faithfully | Setup: `Upload:` |
| something on a cadence | a routine |
| a password, API key or token | Setup: `Secret: {NAME}`, NEVER the value |

## Important Rules

- INVENT NOTHING. Mark `(inferred)` on what the user didn't say directly.
- NEVER put a password, API key, token or card number in the pack. Name it under Setup.
- People get their work identity only: role, company, what to go to them for, work contact. NEVER health, family, money, or anything said in confidence.
- One question per message, at most 8.
- Outline before pack. NEVER write the pack before the user approves the outline.
- Keep it short: Role, Company, Voice and Goals each fit on one screen, About you stays under 6 KB, and each SKILL.md stays under about 150 lines.
