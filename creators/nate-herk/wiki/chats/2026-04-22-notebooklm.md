---
title: "2026-04-22-notebooklm"
date: 2026-04-22
creator: nate-herk
kind: chats
type: kortex-chat
---
# AI and Automations - Nate Herk - NotebookLM

Exported on: 4/22/2026, 4:43:39 PM

---

### User

How do I build a self-healing multi-agent system in n8n?

---

### Model

To build a self-healing multi-agent system in n8n, you need to combine a **multi-agent orchestrator architecture** for task delegation with **Claude Code** to automatically debug and fix your n8n workflows when they break.

Here is the step-by-step process for building this system:

1\. Build the Multi-Agent Swarm (Orchestrator Architecture)

Instead of forcing one AI agent to handle every tool and system prompt, you should separate your system into a "parent" orchestrator agent and specialized "child" sub-agents \[Source: 1: Build & Sell n8n AI Agents (8+ Hour Course, No Code)\] \[Source: 2: Multi-Agent Systems Have NEVER Been EASIER to Build (n8n, no code)\] .

-   **Create Specialized Sub-Agents:** Build separate n8n workflows for specific tasks (e.g., an email agent, a calendar agent, a contact agent) \[Source: 3: Build & Sell n8n AI Agents (8+ Hour Course, No Code)\] more\_horiz. Because they are isolated, you can give each agent its own chat model and highly specific system prompt, which increases the consistency and quality of their outputs \[Source: 3: Build & Sell n8n AI Agents (8+ Hour Course, No Code)\] more\_horiz.-   **Create the Orchestrator Agent:** Build a main parent agent whose sole job is to interpret the user's intent and delegate the task to the right sub-agent \[Source: 1: Build & Sell n8n AI Agents (8+ Hour Course, No Code)\] more\_horiz.-   **Connect Them:** In the parent agent, use the **"Call n8n workflow"** tool to give it access to your sub-agents \[Source: 10: Build your first NO CODE AI Agent in n8n (for beginners)\] more\_horiz. Write clear descriptions for each sub-agent tool so the orchestrator knows exactly when to route data to them \[Source: 13: Build & Sell n8n AI Agents (8+ Hour Course, No Code)\] more\_horiz.-   **Agent-to-Agent Correction:** To make the agents resilient, go into your sub-agent settings and select **"Continue Using Error Output"** on failure \[Source: 16: Make Your Agents Communicate Better in n8n (Feedback, Specifying Inputs, Agent Logs)\] \[Source: 17: Make Your Agents Communicate Better in n8n (Feedback, Specifying Inputs, Agent Logs)\] . If a sub-agent fails a task, this setting splits the output into an error branch, allowing the sub-agent to send a message back to the parent agent (e.g., "unable to perform task, please try again") \[Source: 18: I Built the Ultimate Team of AI Agents in n8n With No Code (Free Template)\] more\_horiz. The parent agent can then automatically adjust its query and try again without halting the entire workflow \[Source: 18: I Built the Ultimate Team of AI Agents in n8n With No Code (Free Template)\] \[Source: 20: I Built the Ultimate Team of AI Agents in n8n With No Code (Free Template)\] .

2\. Implement the Self-Healing Infrastructure

Even with good prompting, n8n workflows can fail due to empty arrays, null data, or expression typos \[Source: 21: I Will Never Fix Another n8n Workflow (Claude Code)\] . You can connect n8n to Claude Code so that it acts as a self-healing developer that fixes your workflows for you \[Source: 22: I Will Never Fix Another n8n Workflow (Claude Code)\] \[Source: 23: I Will Never Fix Another n8n Workflow (Claude Code)\] .

-   **Set up an Error Workflow:** In the settings of your active n8n workflows, configure a designated "error workflow" that triggers automatically whenever the main workflow fails \[Source: 23: I Will Never Fix Another n8n Workflow (Claude Code)\] more\_horiz.-   **Create a Communication Tunnel:** In your error workflow, use an HTTP request to send the failed execution data (including the workflow ID, the failed node's name, and the exact error message) through a tunnel service like Ngrok \[Source: 26: I Will Never Fix Another n8n Workflow (Claude Code)\] more\_horiz.-   **Trigger Claude Code:** The tunnel feeds this error data directly into a local terminal where Claude Code is running \[Source: 27: I Will Never Fix Another n8n Workflow (Claude Code)\] \[Source: 30: I Will Never Fix Another n8n Workflow (Claude Code)\] .-   **Equip Claude with n8n Tools:** To give Claude Code the ability to fix the issue, you must provide it with the **n8n MCP Server** and **n8n skills** \[Source: 30: I Will Never Fix Another n8n Workflow (Claude Code)\] \[Source: 31: I Will Never Fix Another n8n Workflow (Claude Code)\] . The MCP server allows Claude to securely access, search, and edit the JSON of your n8n environment \[Source: 30: I Will Never Fix Another n8n Workflow (Claude Code)\] more\_horiz. The n8n skills are a set of markdown files that teach Claude n8n's expression syntax, node configurations, and workflow patterns \[Source: 30: I Will Never Fix Another n8n Workflow (Claude Code)\] more\_horiz.-   **The Self-Healing Loop:** When a workflow breaks, Claude Code wakes up, looks up the broken workflow via MCP, identifies the root cause of the bug, and applies the code or logic fix directly into your n8n instance \[Source: 26: I Will Never Fix Another n8n Workflow (Claude Code)\] more\_horiz. It will then send you a notification (e.g., via Slack or ClickUp) detailing the fix it applied so you can confidently re-run the workflow \[Source: 22: I Will Never Fix Another n8n Workflow (Claude Code)\] more\_horiz.

*Note: Claude Code can fix bugs related to logic, code nodes, data types, and syntax, but it cannot fix issues that require human authorization, such as expired API keys or service outages* \[Source: 21: I Will Never Fix Another n8n Workflow (Claude Code)\] \[Source: 37: I Will Never Fix Another n8n Workflow (Claude Code)\] *. In these cases, Claude will send you a notification outlining the manual steps you must take to restore the connection* \[Source: 38: I Will Never Fix Another n8n Workflow (Claude Code)\] \[Source: 39: I Will Never Fix Another n8n Workflow (Claude Code)\] *.*

---

### User

How to manage tokens well on Claude code?

---

### Model

**Understanding how tokens compound is the first step to managing them.** Every time you send a message, Claude rereads the entire conversation history, meaning a later message costs exponentially more than the first \[Source: 1: 18 Claude Code Token Hacks in 18 Minutes\] . To effectively manage your token usage, follow these strategies from the sources:

**Conversation & Command Management**

-   **Start fresh conversations** and use the `/clear` command between unrelated tasks to prevent context from bleeding over \[Source: 2: 18 Claude Code Token Hacks in 18 Minutes\] \[Source: 3: 18 Claude Code Token Hacks in 18 Minutes\] .-   **Batch your prompts** into a single message rather than sending multiple separate instructions \[Source: 4: 18 Claude Code Token Hacks in 18 Minutes\] .-   **Edit instead of correcting:** If Claude makes a mistake, edit your original message and regenerate the response instead of sending a new follow-up correction, which permanently stacks onto your history \[Source: 4: 18 Claude Code Token Hacks in 18 Minutes\] .-   **Use visibility commands:** Run `/context` to see exactly what is eating your tokens (such as loaded files or skills) and `/cost` to track your actual usage and estimated spend \[Source: 5: 18 Claude Code Token Hacks in 18 Minutes\] .-   **Manually compact your session:** Run `/compact` when your context reaches around 60% capacity \[Source: 6: 18 Claude Code Token Hacks in 18 Minutes\] . After using it three or four times, ask for a session summary, run `/clear`, and paste the summary into the new session to continue cleanly \[Source: 6: 18 Claude Code Token Hacks in 18 Minutes\] .

**Optimizing Files & Context**

-   **Disconnect unused MCP servers.** Every connected server invisibly loads all of its tool definitions into your context on every single message \[Source: 3: 18 Claude Code Token Hacks in 18 Minutes\] .-   **Keep your** **claude.md** **file lean.** Limit this file to under 200 lines and treat it as an index that points Claude to other reference files, rather than dumping all your information directly into it \[Source: 7: 18 Claude Code Token Hacks in 18 Minutes\] \[Source: 8: 18 Claude Code Token Hacks in 18 Minutes\] .-   **Save your architectural decisions** in the `claude.md` file so you never have to waste tokens re-explaining them in future sessions \[Source: 9: 18 Claude Code Token Hacks in 18 Minutes\] .-   **Be surgical with file references.** Point Claude to specific functions or files (using `@filename`) instead of asking it to search your entire repository \[Source: 6: 18 Claude Code Token Hacks in 18 Minutes\] . Similarly, only paste the exact section of a document Claude needs instead of the whole file \[Source: 10: 18 Claude Code Token Hacks in 18 Minutes\] .-   **Watch out for command output bloat.** The full output of shell commands enters your context window, so you should deny permissions for commands that produce massive amounts of unnecessary data \[Source: 11: 18 Claude Code Token Hacks in 18 Minutes\] \[Source: 12: 18 Claude Code Token Hacks in 18 Minutes\] .

**Strategic Planning & Execution**

-   **Always use plan mode** before executing a real task \[Source: 5: 18 Claude Code Token Hacks in 18 Minutes\] . This allows Claude to map out an approach and ask clarifying questions, which prevents the massive token waste of going down the wrong coding path \[Source: 5: 18 Claude Code Token Hacks in 18 Minutes\] .-   **Actively watch Claude work.** Don't just fire off a prompt and walk away; monitor the session so you can stop it immediately if it gets stuck in a loop \[Source: 7: 18 Claude Code Token Hacks in 18 Minutes\] \[Source: 10: 18 Claude Code Token Hacks in 18 Minutes\] .-   **Avoid taking short breaks mid-task.** Claude uses prompt caching to save tokens, but this cache has a 5-minute timeout. If you step away longer than that, your next message will reprocess everything from scratch at full cost \[Source: 11: 18 Claude Code Token Hacks in 18 Minutes\] .

**Model Selection & Scheduling**

-   **Pick the right model for the job.** Use **Sonnet** for your default coding work, **Haiku** for simple tasks or formatting, and reserve the expensive **Opus** model strictly for deep architectural planning \[Source: 13: 18 Claude Code Token Hacks in 18 Minutes\] .-   **Use sub-agents sparingly.** Agent workflows use roughly 7 to 10 times more tokens than a standard session because each sub-agent has to load its own full context window \[Source: 14: 18 Claude Code Token Hacks in 18 Minutes\] . When you do use them, try to run them on the cheaper Haiku model \[Source: 14: 18 Claude Code Token Hacks in 18 Minutes\] \[Source: 15: 18 Claude Code Token Hacks in 18 Minutes\] .-   **Run heavy tasks during off-peak hours.** Schedule massive refactors or multi-agent sessions for afternoons, evenings, or weekends to maximize how long your session allocation lasts \[Source: 15: 18 Claude Code Token Hacks in 18 Minutes\] \[Source: 16: 18 Claude Code Token Hacks in 18 Minutes\] .