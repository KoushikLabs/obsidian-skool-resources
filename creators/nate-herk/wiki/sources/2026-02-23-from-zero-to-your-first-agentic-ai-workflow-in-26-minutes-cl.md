---
title: "From Zero to Your First Agentic AI Workflow in 26 Minutes (Claude Code)"
date: 2026-02-23
creator: nate-herk
youtube: https://youtu.be/tDGiWn0flK8
source_url: https://drive.google.com/drive/folders/1vBWsH1jwku4DdTsb8AqLgXAkeLFdyYe1
type: source
concepts:
  - agentic-workflows
  - planning-mode
  - bypass-permissions
  - context-management
  - workflow-automation
  - web-scraping
  - content-creation
  - design-systems
entities:
  - nate-herk
  - anthropic
  - claude-code
  - claude-models
  - n8n
  - openai
  - google
---

# From Zero to Your First Agentic AI Workflow in 26 Minutes (Claude Code)

> Build your first agentic AI workflow from scratch in 26 minutes

## Links
- Watch: https://youtu.be/tDGiWn0flK8
- Original source bundle: https://drive.google.com/drive/folders/1vBWsH1jwku4DdTsb8AqLgXAkeLFdyYe1
- Raw artefacts: `../../raw/from-zero-to-your-first-agentic-ai-workflow-in-26-minutes-cl/` (2 files)
- Creator: [[nate-herk-profile]]

## Cross-references
**Concepts:** [[agentic-workflows]], [[planning-mode]], [[bypass-permissions]], [[context-management]], [[workflow-automation]], [[web-scraping]], [[content-creation]], [[design-systems]]
**Entities:** [[nate-herk]], [[anthropic]], [[claude-code]], [[claude-models]], [[n8n]], [[openai]], [[google]]

## Files
- [`CLAUDE (1).md`](../../raw/from-zero-to-your-first-agentic-ai-workflow-in-26-minutes-cl/CLAUDE (1).md) — 3.9 KB
- [`From Zero to Your First Agentic AI Workflow in 26 Minutes (Claude Code).pdf`](../../raw/from-zero-to-your-first-agentic-ai-workflow-in-26-minutes-cl/From Zero to Your First Agentic AI Workflow in 26 Minutes (Claude Code).pdf) — 185.2 KB

---

## From Zero to Your First Agentic AI Workflow in 26 Minutes (Claude Code).pdf
_PDF, 9 pages — [open](../../raw/from-zero-to-your-first-agentic-ai-workflow-in-26-minutes-cl/From Zero to Your First Agentic AI Workflow in 26 Minutes (Claude Code).pdf)_

### Page 1

From Zero to Your First Agentic AI Workflow in 26 Minutes (Claude Code)

This guide covers everything you need to know about agentic workflows, including what they are, how they differ from traditional automation, and a complete step-by-step walkthrough of building your first agentic workflow using Claude Code in VS Code.

By: Nate Herk I. What Are Agentic AI Workflows? Agentic workflows represent a fundamental shift in how we build AI automations. Instead of manually configuring every step, you describe the outcome you want and the agent figures out the rest.

Traditional Automation (tools like Make or n8n): You drag nodes onto a canvas, configure each one, connect them, pass variables, test, fix errors, and repeat.

You are building the entire thing manually, and if it breaks, you go back in and fix it yourself.

Agentic Workflows: You explain the problem and describe the outcome. The system reasons, adapts, asks clarifying questions, makes decisions, fixes itself when something breaks, and does research -- all to achieve the end goal you described.

Think of it like hiring a talented developer. You don't walk them through code line by line. You explain the problem, describe the desired outcome, and ask, "What else do you need from me?"

The Navigation Analogy Traditional automation is like using a paper map and compass. You figure out routes yourself, choose which streets to walk, and if you make a wrong turn, you course-correct manually.

Agentic workflows are like pulling out your phone, searching for a destination, and following the blue line.

If you go off path, it recalculates and gets you back on track.

Both get you to the same destination, but the experience is completely different.

II. Key Concepts: Deterministic vs. Non-Deterministic

### Page 2

These are two critical terms in the AI automation space: Deterministic means predictable. In automation, predictable is beautiful. Boring is beautiful. You know exactly what will happen every single time the automation runs.

Traditional automation excels here for repetitive, predictable tasks.

Non-deterministic means that given an input, you don't know exactly what the output will be. There's variability, judgment, and AI.

AI is non-deterministic by nature.

Your job as an AI automation builder is to make a non-deterministic process as deterministic as possible, because business processes are typically pretty deterministic (or at least aim to be).

Agentic workflows shine when tasks are too variable for traditional automation -- things that need judgment calls, dynamic decision-making, research, content creation, customer support, or lead generation.

These are messy processes with lots of moving pieces, and the system actually gets better over time.

III. The WAT Framework The WAT Framework gives your agent structure. Without it, things get messy fast. Think of it like a school locker. If you threw every piece of paper from every subject into a locker with zero organization, you could still get straight A's, but it would be tough.

Binders, shelves, and folders make everything easier.

WAT is that structure for your agent.

W -- Workflows (The Instructions) Workflows are instruction files written in markdown (natural language with formatting like pound signs for headers and asterisks for bold text).

Think of a workflow like a job description or an SOP -- it tells the agent what to do.

Example -- Competitor Analysis Workflow: 1. Research businesses 2. Gather data from five competitor sources 3. Analyze findings 4. Analyze our business 5. Create a PDF report The agent uses these guidelines to figure out how to achieve the end goal. As the agent works and gives you outputs, you can provide feedback ("I liked this but not that" or "change this"), and it will update the workflow file so it does better next time.

### Page 3

A -- Agent (The Coordinator) This is the actual AI -- Claude Code itself. It's the brain. It reads your workflows, looks at available tools, and makes decisions about which tool to use and when.

If something breaks, it handles the error, researches the fix, and adapts.

Think of this as a project manager. You hand them instructions and they delegate tasks to the right tools and workflows.

You don't have to figure out sequencing or logic.

T -- Tools (The Workers) Tools are Python scripts that do the actual work. Each tool has one specific job (scraping a website, generating a PDF, etc.).

The agent calls these tools when needed based on the workflow instructions.

Example tools for a research workflow: ● Scrape a website ● Analyze findings ● Generate a PDF Tools are automatically built by Claude Code, and if they fail, they get automatically updated and fixed.

They're modular, so you can reuse a tool across different workflows.

How WAT Works Together When you give the agent a task like "research Company X's pricing and create a PDF report": 1. The agent reads the workflow (instructions) 2. It looks at available tools and decides the sequence 3. Calls web search tool to find relevant info 4. Calls scrape website tool to pull content from URLs 5. Calls analyze findings tool to synthesize everything 6. Calls generate PDF tool to create the branded report The agent reasons and makes decisions the whole time based on what the workflow says. You're not mapping it out step by step.

IV. Setting Up Your Environment Step 1: Install Visual Studio Code (VS Code)

### Page 4

Go to Google and search for "VS Code" or "Visual Studio Code." Download and install it. This is where you'll use Claude Code.

Step 2: Install the Claude Code Extension 1. Open VS Code 2. Go to the left-hand menu bar and click on Extensions 3. Search for "Claude Code" 4. Click on it and hit Install 5. It will prompt you to sign in with your Anthropic/Claude subscription Important: You need a paid Claude subscription (Pro or Max) to use Claude Code with Opus 4.5.

Step 3: Create a Project Folder 1. Go to the Explorer on the left-hand side 2. Click Open Folder 3. Create or select a blank folder (e.g., "first-agentic-workflow") 4. Close any extra panels and open Claude Code from the top menu Your workspace should now have: files on the left side, and the Claude Code chat interface on the right.

Think of the chat as your typical ChatGPT or Claude interface -- this is where the agent lives.

The left side is where workflows and tools will appear.

V. Initializing Your Project The CLAUDE.md File This is your onboarding document for the agent. It catches Claude Code up to speed on how you want to work.

It explains the WAT Framework structure and includes:

● How to operate: First look in existing tools, then learn and adapt when things fail (read errors, fix scripts,

reset) ● Self-improvement loop: When errors occur (e.g., rate limiting on an API), the agent digs into the docs, discovers solutions like batch endpoints, refactors the tool, verifies it works, and updates the workflow so the error never happens

again ● File structure: Folders for temporary files, tools, and workflows To initialize: Drag the CLAUDE.md file into your project's left-hand panel, then tell Claude Code:

### Page 5

"Hey Claude, I just dropped in a CLAUDE.md file that explains how I want you to work in this project.

Go ahead and initialize the project and get everything set up and ask me any questions if you have any."

Claude Code will read the file, create your folder structure (temporary, tools, workflows), and ask any clarifying questions.

Understanding Permission Modes Claude Code has four permission modes: Mode Description Bypass Permissions Agent executes everything without asking (enable in Settings > Claude Code > "Allow dangerously bypass permissions") Ask Before Edits Agent asks before making changes Edit Automatically Agent edits files without asking Plan Mode Agent builds a plan and asks questions before executing Recommended flow: Start in Plan Mode to build a solid plan with questions. Once you're confident, switch to Bypass Permissions to let it execute.

VI. Building a Workflow: Competitor Research (Full Walkthrough)

Phase 1: Planning (Use Plan Mode) Start in Plan Mode and describe what you want in natural language: "Hey Claude, I've got an idea for a workflow. I want a branded PDF at the end -- I'll give you my company logo and brand guidelines, and the output should have my logo, colors, and typography.

It's a competitor analysis and research workflow.

I want to give you information about my business, and based on that, you need to find competitors, find areas to improve my business, see what's working well for them, and build me a good way to keep tabs on the market."

Claude Code will think, research, and then ask clarifying questions.

### Page 6

Phase 2: Answering Agent Questions The agent asked about four areas: 1. Discovery: How should competitors be identified? (Provided list / Auto-discover based on business info / Hybrid) -- chose

Auto-discover 2. Business Information: What to collect? (Company description, products/pricing, target market, key features) -- chose

All 3. Analysis: What aspects to analyze? (Products, pricing, marketing, messaging) -- chose All 4. Branding: Use existing assets or provide new ones? -- chose Provide new branding Additional follow-up questions included frequency ( monthly ), output format ( PDF only ), and API cost budget ( recommended/middle approach ).

Phase 3: Reviewing the Plan Claude Code produced a comprehensive implementation plan including: Tech Stack: ● Claude Sonnet for AI processing ● Firecrawl and Perplexity for web research ● ReportLab for PDF generation ● Matplotlib for chart generation Folder Structure: ● brand_assets/ -- for logo and brand guidelines ● workflows/ -- competitor analysis workflow file ● tools/ -- five Python tools Five Tools to Be Built: 1. Collect business info 2. Discover competitors 3. Research competitors 4. Analyze competitors 5. Generate competitor PDF Edge Case Handling: Blocked scraping, insufficient competitors, rate limiting, invalid brand assets, data completeness issues

Cost Estimates: First run approximately $1.50, subsequent runs cheaper due to caching, adding new competitors approximately $0.50

### Page 7

Phase 4: Adding Brand Assets Before executing, drag your logo and brand guidelines files into the left-hand panel, then tell Claude:

"That plan looks good. The only change I want to make is about the brand guidelines and assets.

I just dropped in two files -- [logo file] and [brand guidelines file].

Those are the ones I want you to use for the branded PDF.

Look at those, extract the information, and make sure the logo and colors appear on the final output."

Claude Code will extract colors, typography, and logo info, then update the plan accordingly. Phase 5: Execution (Switch to Bypass Permissions) Accept the plan and let Claude Code build everything. It will create a to-do list and start building all scripts, workflows, and tools, then test the workflow.

VII. Running the Workflow Setting Up API Keys The workflow requires two API keys: 1. Anthropic API Key: Go to your Claude Developer Platform, create a new key 2. Firecrawl API Key: Go to Firecrawl's dashboard and grab your API key Place both keys in the.env file that Claude Code creates (copy from.env.example). Installing Dependencies Ask Claude Code to install the required dependencies -- it can run the commands directly for you.

Context Management Watch the context indicator at the bottom of Claude Code. When it goes over 60%, clear the conversation

using /clear to avoid context rot (the model's quality degrades as conversations get too long).

Running the Analysis

### Page 8

After clearing, give Claude Code a prompt with basic business info: "Hey Claude, I need you to help me run a competitor analysis. My business is called [Business Name] and we basically help you [description].

We're starting to see competitors pop up, so I want to understand our opportunities and what we need to be doing better."

Claude Code will automatically find the competitor analysis workflow, read it, and start executing.

It will ask follow-up questions to build a complete business profile, which it stores in

a business_profile.json file for future reference. Self-Healing in Action During execution, the agent may encounter errors (e.g., unicode encoding issues). It reads the error, identifies the fix, updates the tool script, and continues -- all without your intervention.

This is the self-improvement loop at work.

Output Files Created ● business_profile.json -- all saved business information ● competitors/ folder -- individual files for each competitor ● analysis_history/ folder -- data from each analysis run ● Final branded PDF report

VIII. Iterating and Improving The first run won't be perfect. In the demo, the logo wasn't visible because it was white on a white background, and charts had similar issues.

The fix was simple:

"That's great, but we can't see the charts or logos. I'm assuming because they're the same color as the background.

Investigate and fix these issues."

Claude Code identified multiple problems in the PDF generator, fixed them, and regenerated the report using cached data (no new research needed).

The improved report included visible logos, proper color contrast, and readable charts.

Key takeaway: You have to run the workflow a few times to discover holes. Once discovered, Claude Code fixes them, and you get to a battle-tested workflow.

Each iteration makes it smarter and more reliable.

### Page 9

IX. Key Takeaways The initial setup takes effort, but it pays off. Yes, the agent asks a lot of questions upfront. But think about how good it gets once it has all that information.

Each run makes it smarter.

You don't need to know code. You never had to look at API documentation, figure out how to prompt a competitive analysis, or learn how to generate PDFs or charts.

The agent handled all of that.

Caching saves time and money. After the first run, the agent saves competitor data and business profiles.

Future runs only need to check for new information, dramatically reducing cost and time.

Natural language is all you need. Every interaction -- from planning to execution to debugging -- happened through plain conversational language.

Plan first, execute second. Use Plan Mode to build a solid plan with questions, then switch to Bypass Permissions to let it run.

This keeps you in control while still moving fast.

Want to connect with others building and monetizing AI automation? Become an AIS Plus Member
