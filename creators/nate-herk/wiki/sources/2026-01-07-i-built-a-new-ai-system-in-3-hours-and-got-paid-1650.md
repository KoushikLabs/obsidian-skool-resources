---
title: "I Built a New AI System in 3 Hours (and got paid $1650)"
date: 2026-01-07
creator: nate-herk
youtube: https://youtu.be/Q4iEslmyMyM
source_url: https://drive.google.com/drive/folders/1v6Xqty7Ss5GUIaIYiJ-Nq0y8Rr7Vccrg
type: source
concepts:
  - workflow-automation
  - prompt-engineering
entities:
  - nate-herk
  - n8n
  - google
---

# I Built a New AI System in 3 Hours (and got paid $1650)

> Live build of a paid AI system in 3 hours, start to finish

## Links
- Watch: https://youtu.be/Q4iEslmyMyM
- Original source bundle: https://drive.google.com/drive/folders/1v6Xqty7Ss5GUIaIYiJ-Nq0y8Rr7Vccrg
- Raw artefacts: `../../raw/i-built-a-new-ai-system-in-3-hours-and-got-paid-1650/` (1 files)
- Creator: [[nate-herk-profile]]

## Cross-references
**Concepts:** [[workflow-automation]], [[prompt-engineering]]
**Entities:** [[nate-herk]], [[n8n]], [[google]]

## Files
- [`I Built an AI Agent in 3 Hours and Got Paid $1,650.pdf`](../../raw/i-built-a-new-ai-system-in-3-hours-and-got-paid-1650/I Built an AI Agent in 3 Hours and Got Paid $1,650.pdf) — 204.4 KB

---

## I Built an AI Agent in 3 Hours and Got Paid $1,650.pdf
_PDF, 4 pages — [open](../../raw/i-built-a-new-ai-system-in-3-hours-and-got-paid-1650/I Built an AI Agent in 3 Hours and Got Paid $1,650.pdf)_

### Page 1

I Built an AI Agent in 3 Hours and Got Paid $1,650

This guide breaks down the technical build, business strategy, and mindset shift required to sell high-value AI automations.

By: Nate Herk 1. The Workflow: The "AI Executive Assistant" The system was designed to solve a specific pain point: an overwhelmed inbox. Instead of a generic tool, it was built as a two-part custom solution using n8n.

Part A: The Inbox Manager ● Trigger: New incoming email. ● Internal Routing: If the sender is internal, the system automatically sends a Slack DM to the

client. ● External Routing: If external, an AI node classifies the email (e.g., Sales, Finance, Support). ● Logging: The system labels the email and logs details into a clean spreadsheet for organized tracking.

### Page 2

Part B: The Slack Assistant ● Interface: A Slack bot that allows the client to "talk" to their inbox. ● Search Capability: The client can ask for specific emails from certain dates or senders. ● Contact Retrieval: Integrates with Google Contacts to find email addresses dynamically. ● Drafting Agent: A specialized sub-workflow that drafts replies based on a specific style guide.

2. What Made it Special: The "Writer Subworkflow" The most unique part of this build was how it handled the client's "Tone of Voice." Rather than using a generic AI response, Nate used a specialized sub-workflow for

drafting. ● The Style Guide Method: Nate analyzed 50-100 of the client's real emails to identify patterns, common phrases, and

sign-offs. ● System Prompting: This analysis was turned into a detailed "Style Guide" in the AI's system

prompt. ● The Result: The AI drafts were indistinguishable from the client’s actual writing style. ● Token Efficiency: By moving the writing logic to a sub-workflow, the main agent didn't have to process the massive style guide every time the client just wanted to "search" for an email, saving significantly on API costs.

### Page 3

3. The Business Impact: How It Was Sold This project wasn't sold through a "viral" video or a complex sales funnel. It was sold through Value-Based Consulting.

From "Pharmacist" to "Doctor" ● The Pharmacist: Waits for a customer to say "Give me this tool" and then builds it. This is a commodity

service. ● The Doctor (Consultant): Diagnoses the business problem first. Nate didn't try to "boil the ocean" by automating an entire Executive Assistant role; he asked: "Where is the first place you would offload work if you had an

assistant?" ● The Answer: "My email." This narrowed the scope to a solvable, high-impact problem. Outcome Over Templates The client didn't pay for an n8n template; they paid for the outcome of not having to context-switch between Slack and Email all day.

4. The P.R.I.C.E. Framework To consistently land high-value deals, follow this internal 5-step framework: ● P - Prepare: Ground yourself in Value-Based Pricing. Focus on the transformation (e.g., "From inbox chaos to Slack-based control") rather than the

tech. ● R - Research: Fully map the manual workflow during discovery. How often does this task happen?

How long does it take?

Who is doing it? ● I - Identify ROI: Calculate the annual savings (Time saved * Hourly cost). Use the 10x ROI

Rule. ● C - Communicate: Present the solution, the testing/QA process, and the maintenance plan before you ever mention the

price. ● E - Expand: Treat the first delivery as "Version 1." Always look for "Version 2" upgrades, maintenance retainers, or new bottlenecks to solve.

5. Pricing Math: The 10x ROI Rule When calculating your price, aim to show the client a 10x return on their investment within the first year.

Step 1: Calculate Annual Savings

### Page 4

● Example: A process takes 1 hour per day. ● Hourly rate of the person doing the work = $50. ● Working days per year = 240. ● Math: 1 hour * $50 * 240 days = $12,000 in annual savings. Step 2: Set the Project Price ● Rule: Project Price should be roughly 10% of the Annual Savings. ● Math: 10% of $12,000 = $1,200. ● Result: This makes the purchase an easy decision for the client because they "profit" $10,800 in the first year alone.

6. Mindset: Thinking Like a Problem Solver If you are starting from zero, Nate recommends focusing on these core principles: ● Identify Bottlenecks: Don't automate a process that isn't a constraint. If a business needs leads, automate outreach, not internal

filing. ● Pick the Right Tools: Use flexible tools like n8n that allow for custom integration and "Human-in-the-loop" features (e.g., creating a draft rather than

auto-sending ). ● Scalable Flywheels: Look for systems where usage correlates with business growth (like Sales

Agents). ● Prototype Fast: Don't overthink the first build. Get a working version into the client's hands quickly to get real-world feedback loops.

Want to connect with others building and monetizing AI automation? Become an AIS Plus Member
