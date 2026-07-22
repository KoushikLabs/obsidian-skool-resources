---
title: "How to Manage Your Claude Limits Better Than 99% of People"
date: 2026-04-20
creator: nate-herk
youtube: https://youtu.be/_qZvORxGqI0
source_url: https://drive.google.com/drive/folders/1Gec-42rgEGFXpktKAwWLAqvaU--OuAhZ
type: source
concepts:
  - skills
  - mcp
  - subagents
  - planning-mode
  - memory-system
  - token-optimization
  - context-management
  - workflow-automation
  - plugins
  - rewind-history
entities:
  - nate-herk
  - anthropic
  - claude-code
  - github
---

# How to Manage Your Claude Limits Better Than 99% of People

> Session-limit and token hygiene deep dive: context rot, /rewind, manual session handoff, markdown conversion, and a custom token dashboard

## Links
- Watch: https://youtu.be/_qZvORxGqI0
- Original source bundle: https://drive.google.com/drive/folders/1Gec-42rgEGFXpktKAwWLAqvaU--OuAhZ
- Raw artefacts: `../../raw/how-to-manage-your-claude-limits-better-than-99-of-people/` (3 files)
- Creator: [[nate-herk-profile]]

## Cross-references
**Concepts:** [[skills]], [[mcp]], [[subagents]], [[planning-mode]], [[memory-system]], [[token-optimization]], [[context-management]], [[workflow-automation]], [[plugins]], [[rewind-history]]
**Entities:** [[nate-herk]], [[anthropic]], [[claude-code]], [[github]]

## Files
- [`How to Never Hit Your Claude Limit Again.pdf`](../../raw/how-to-manage-your-claude-limits-better-than-99-of-people/How to Never Hit Your Claude Limit Again.pdf) — 167.6 KB
- [`README - Links.md`](../../raw/how-to-manage-your-claude-limits-better-than-99-of-people/README - Links.md) — 0.4 KB
- [`session-handoff-SKILL.md`](../../raw/how-to-manage-your-claude-limits-better-than-99-of-people/session-handoff-SKILL.md) — 4.4 KB

---

## How to Never Hit Your Claude Limit Again.pdf
_PDF, 7 pages — [open](../../raw/how-to-manage-your-claude-limits-better-than-99-of-people/How to Never Hit Your Claude Limit Again.pdf)_

### Page 1

How to Never Hit Your Claude Limit Again This guide summarizes the key concepts, habits, and tools for managing Claude Code sessions efficiently so you stop burning tokens and stop hitting your session limit.

By: Nate Herk I. What Is Context? Context is everything Claude Code can see at one time. It's Claude's current working memory. This includes: ● The system prompt ● Your full conversation history ● Every tool call and tool output ● Every file Claude has read ● Every skill, MCP server, or agent in your project Key stat: Claude Code has a 1 million token context window, but before you even type anything you're already burning ~8,000 tokens of startup overhead (sometimes 62,000+).

Action step: In a fresh session, run /context to see how many tokens you're at before sending anything.

This reveals invisible tokens from unused files, MCPs, or skills you can trim.

II. How Tokens Actually Work (The Critical Concept) A token is the smallest unit of text an AI reads and charges you for (roughly 1 word = 1 token). The Compounding Problem Every time you send a message, Claude rereads the entire conversation from the beginning.

Message 1, reply 1, message 2, reply 2, all the way up to your latest prompt.

Every single time.

This means your cost isn't adding. It's compounding exponentially: ● Message 1 might cost 500 tokens

### Page 2

● Message 30 might cost 15,500 tokens (31x more) ● After 30 messages, you could be at ~250,000 cumulative tokens Case study: A developer tracked a 100+ message chat and found 98.5% of tokens were spent just rereading old chat history.

III. Context Rot & Auto Compaction Context Rot (a.k.a. "AI Dementia") As your session grows, the model's attention spreads across every token and performance degrades.

Claude starts to:

● Forget things ● Contradict itself ● Edit files without reading them first ● Get vague and noticeably worse Retrieval accuracy drops from 92% at 256K tokens to 78% at 1M tokens. As the model degrades, you spend more tokens to get worse outputs (e.g., 500K tokens for something that should've taken 200K).

Auto Compaction Kicks in automatically at ~95% of your window, but this is way too late: ● You only keep 20-30% of the original detail ● The model is compacting at its least intelligent point (peak context rot) ● It's like packing for a trip 5 minutes before you leave The fix: Manual compaction at ~60% through the window always beats waiting for auto compaction.

IV. The 5 Options After Every Claude Response After Claude responds, you always have five choices: 1. Continue (send another message, easy to over-use) 2. /rewind (jump back to a previous message and drop everything after) 3. /clear (start completely fresh)

### Page 3

4. /compact (summarize the session and replace history with the summary) 5. Sub-agent (delegate work to a fresh context window) /rewind is Anthropic's #1 Recommended Habit Double-tap Escape or run /rewind to jump back to any previous message; everything after gets dropped.

Why this matters: When Claude messes up and you just say "that didn't work, try this instead," the failed attempt, broken code, and wrong approach all stay in your context, polluting every future response.

Rewinding keeps context clean.

Bonus: The /rewind menu has a "summarize from here" option that creates a handoff message, like a note from Claude's future self to its past self saying "here's what we figured out, do it this way."

/compact vs. /clear and Nate's Preferred Method The documentation says: ● Starting a new task → /clear ● Continuing same task → /compact Nate's method (he stops using /compact entirely): 1. When Opus hits ~120K tokens (~12% of a 1M window), ask Claude: "Give me a full summary of everything we've done and the current status of what we're about to do

next." 2. Copy the summary 3. Run /clear 4. Paste the summary and keep going Critical supporting practice: Store key data in files like tracking sheets, activity logs, task lists, and decision files.

That way a reset doesn't feel like a reset (it's like closing all your Chrome tabs but keeping your bookmarks).

Nate also built a custom /session-handoff skill that automates this process, outputting a structured handoff with decisions locked, files shipped, state verification, open questions, and next steps.

Sub-Agents ● Each sub-agent gets its own fresh context window ● Does its own research, synthesizes, and returns only the result

### Page 4

● Think of it as a research intern. You don't watch them read 50 articles, you just want the summary

Pro tip: Sub-agents can run on cheaper models (e.g., Haiku) while your main session runs on Opus.

Same quality for summarization tasks at a fraction of the cost.

The key is knowing which tasks to delegate.

V. Practical Token-Saving Tips 1. Watch Your Session Limit Constantly Keep the limit visible (second monitor if possible). Be strategic: if you're near the limit, take a break.

If you're at 50% with 30 minutes until reset, abuse it on heavy work.

2. Convert Everything to Markdown Markdown is dramatically cheaper: ● HTML to Markdown: ~90% fewer tokens ● PDF to Markdown: ~65-70% fewer tokens ● DOCX to Markdown: ~33% fewer tokens Use a tool like Docling to convert in seconds. A 40-page PDF takes the same space as a 130-page markdown file.

(Exception: if you need OCR/vision, keep the original.)

3. Use /btw for Side Questions Opens a quick overlay for side questions that don't enter your conversation history. Perfect for quick questions during deep work.

4. Start Every Session in Plan Mode Boris Churnney (creator of Claude Code) does this every time. Spending tokens upfront to get the plan right means Claude can one-shot the implementation, cheaper in the long run.

Recommended tools: Ultra Plan and Superpowers.

5. claude.md Discipline ● Keep it under 200 lines / ~2,000 tokens (loads every session) ● Only include what Claude actually needs ● Move specialized instructions into context files or skills that load on demand ● Use a.claudeignore file to exclude large folders/files

### Page 5

6. Understand Output vs. Input Tokens Output tokens cost more than input tokens, but telling Claude "be concise" won't save as much as you'd think, because many output tokens are invisible (file writes, etc.).

The caveman plugin experiment confirmed the savings are smaller than expected.

Focus on context management, not response length.

VI. The Token Dashboard Nate built a free custom dashboard (available in his free School community) that shows: ● Sessions, turns, input/output tokens, cache read/create ● Usage over 7 or 30 days across models, projects, and tools ● Your most expensive prompts (so you can analyze what happened and why) ● A projects view and a sessions view ● Most-invoked skills ● Most-opened files and most-run bash commands, so you can spot patterns you didn't realize were happening

Setup: Drop the GitHub repo URL into Claude Code and ask it to help you set it up.

VII. Why You Probably Don't Need the 1M Token Window Three Stats to Internalize 1. Analysis of 18,000 thinking blocks across 7,000 sessions: thinking depth dropped 67% as sessions got longer.

Edits-without-reading jumped from 6% to 34%.

Longer sessions = lazier, sloppier

Claude. 2. One user went from $345/month to $42,000/month on tokens with the same output quality.

Pure bad context management. 3. Retrieval accuracy: 92% at 256K drops to 78% at 1M. Just because you can fill the window doesn't mean you should.

The Philosophy When people hear "1 million tokens," they get wasteful. They stop using sub-agents, stop being intentional, and offload everything into one giant session.

The 1M window is insurance, not a goal. The first 0-20% of your session is prime time when claude.md is freshest and the model is most primed.

### Page 6

Nate's Personal Rule Never go above ~120K tokens (~12% of a 1M window). The number comes from the old 200K context era, when 60% ≈ 120K was his compact trigger.

Treat it as a baseline mindset, not a hard limit.

Sometimes a big coding or video task will push past it.

Session Chaining For big projects, don't do everything in one session. Chain them like an assembly line: ● Session 1, Discovery: Claude reads PDFs and the codebase, produces a summary doc ● Session 2, Planning: reads the summary, creates a plan ● Session 3, Execution: reads the plan, builds If You're Just Starting Out Stick with the 200K window, learn the discipline of being intentional, then graduate to 1M if you actually need it.

More space invites worse habits, like leaving cookies on your desk when you're trying to lose weight.

VIII. 10 GitHub Frameworks for 60-90% Token Savings Community-built tools that each tackle context and token management differently. Don't install all of them.

Analyze which one fits your specific project.

1. Rust Token Killer (CLI proxy that filters terminal output before it hits context) 2. Context Mode (sandboxes raw tool output into SQLite instead of dumping into context) 3. Code Review Graph 4. Token Savior 5. Caveman (makes Claude talk like a caveman, saves less than expected) 6. Claude Token Efficient (a single claude.md file that keeps responses terse) 7. Token Optimizer MCP 8. Claude Token Optimizer 9. Claude Context 10. (Plus one more from the linked community tweet) Best approach: Feed all of them to Claude Code and ask: "Based on what we're doing in this specific project with this specific end goal, which of these would help us most?"

### Page 7

IX. Final Thoughts If a session feels off, repetitive, going in circles, or off the rails, just clear it or open a new one. Both for your sanity and for Claude's.

Do these things consistently and you'll get more out of your Claude Code subscription than 99% of users.

Want to connect with others building and monetizing AI automation? Become an AIS Plus Member
