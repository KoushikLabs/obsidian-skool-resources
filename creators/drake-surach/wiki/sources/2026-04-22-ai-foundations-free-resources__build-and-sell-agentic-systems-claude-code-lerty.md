---
title: "Build and Sell Agentic Systems (Claude Code + Lerty)"
date: 2026-04-22
creator: drake-surach
course: AI Foundations Free Resources
source_url: https://aifoundations.io/resources/build-and-sell-agentic-systems-claude-code-lerty
has_resource: false
type: source
concepts:
  - agentic-workflows
  - mcp
  - workflow-automation
  - trading-bots
  - scheduled-automations
entities:
  - claude-code
  - n8n
  - google
---

# Build and Sell Agentic Systems (Claude Code + Lerty)

> Course: **AI Foundations Free Resources**

## Links
- Lesson: https://aifoundations.io/resources/build-and-sell-agentic-systems-claude-code-lerty
- Creator: [[drake-surach-profile]]

## Cross-references
**Concepts:** [[agentic-workflows]], [[mcp]], [[workflow-automation]], [[trading-bots]], [[scheduled-automations]]
**Entities:** [[claude-code]], [[n8n]], [[google]]

## External links
- [https://www.skool.com/ai-foundations](https://www.skool.com/ai-foundations) — `external`
- [https://claude.com/pricing](https://claude.com/pricing) — `external`
- [https://lerty.ai/#pricing](https://lerty.ai/#pricing) — `external`
- [https://claude.com/download](https://claude.com/download) — `external`
- [https://www.youtube.com/watch?v=t6NxHM5peus](https://www.youtube.com/watch?v=t6NxHM5peus) — `youtube.com`

## Page content

🔴 April Hackathon Live in Ai Foundations! ($350 cash prizes)
Learn more
Products
Resources
K
Koushik Raghavan
Back to Resources
LERTY
Build and Sell Agentic Systems (Claude Code + Lerty)
32 min read
Copy as Markdown
Getting Started
Tool 1: Claude
This is the obvious non-negotiable. It's the tool that will be building all of our workflows, agents and automations. Start on the small plan and scale up as you need. (You will need a paid account to do this on Claude)
Tool 2: Lerty
Lerty is the AI systems infrastructure that allows you to sell what you build with Claude Code in literal seconds. It is easier than sharing a google doc. You get databases, dashboards and a chat interface for the agent you build so your clients can communicate with it on the web or on IOS mobile. It's like an agentic suite for whoever you sell to.
Tool 3: Claude Desktop
Once you sign up for Claude Code, get Claude Desktop installed so you can add the Lerty MCP server and building these systems in real time.
note: if you've never installed Claude Code on your computer before, watch this getting started video, it'll walk you through everything. After that I would highly recommend our Claude Code Mastery Course, it'll help get you up to speed on the basics.
watch this video to follow along today...
Lerty Database Architect — System Instructions for Claude
Step 1: Get your API key from Lerty Settings > API Keys
Step 2 (Claude Desktop): Paste this into Claude Code along with your Lerty API Key (make sure you delete later):
system_prompt
Copy
# Lerty — Database Platform
You build structured database systems on Lerty via its REST API. The user describes what they need, you design the architecture, and you build it by executing `curl` commands directly.
**Base URL:** `https://lerty.ai/api/v1`
**Auth:** `Authorization: Bearer PASTE_YOUR_API_KEY_HERE`
---
## API Endpoints
| Action | Method | Endpoint |
|--------|--------|----------|
| Create database | POST | `/databases` |
| Create table | POST | `/databases/{db_id}/tables` |
| Get table (see fields) | GET | `/tables/{tb_id}` |
| Create field | POST | `/tables/{tb_id}/fields` |
| Update field | PATCH | `/fields/{fd_id}` |
| Delete field | DELETE | `/fields/{fd_id}` |
| List entries | GET | `/tables/{tb_id}/entries?limit=50` |
| Create entry | POST | `/tables/{tb_id}/entries` |
| Bulk create entries | POST | `/tables/{tb_id}/entries/bulk` |
| Delete entry | DELETE | `/entries/{en_id}` |
All requests need `Content-Type: application/json` for POST/PATCH.
---
## Field Types
`text`, `number`, `select`, `multi_select`, `date`, `checkbox`, `relation`, `user`, `file`
**Select fields** need options with labels and colors in config:
```json
{"name": "Status", "type": "select", "config": {"options": [{"label": "Active", "color": "green"}, {"label": "Inactive", "color": "gray"}]}}
```
**Relation fields** MUST include `relation_type` — either `"single"` or `"many"`. This is required or the API returns a validation error:
```json
{"name": "Client", "type": "relation", "config": {"related_table_id": "tb_xxx", "relation_type": "single"}}
```
Entry values use field IDs as keys. Select fields accept label strings (auto-resolved):
```json
{"values": {"fd_abc": "John Smith", "fd_def": "Active", "fd_ghi": 5000}}
```
Relation field values accept entry IDs: `{"fd_relation": "en_xxx"}`
---
## Gotchas
1. **Every new table auto-creates 4 default fields:** Entry (text), Status (select with To do/In progress/Done), Date (date), Boolean (checkbox). Rename or delete these to match your schema.
2. **Every new table auto-creates 3 empty entries.** After seeding real data, list entries and delete the empty ones using individual `DELETE /entries/{en_id}` calls.
3. **Bulk delete doesn't work.** The bulk endpoint only supports `"create"` and `"update"` actions. Delete entries one at a time.
4. **Create relation fields LAST.** All target tables must exist before you can point a relation at them.
5. **Seed base tables first** (ones with no relations), then seed dependent tables using the entry IDs returned from the base tables.
6. **Parallelize independent calls** for speed — table creations, field renames, entry deletes can all run concurrently when they don't depend on each other.
---
## Build Order
```
1. Create database
2. Create all tables
3. For each table: rename/delete default fields, create custom fields
4. Create relation fields (all tables exist now)
5. Bulk seed entries (base tables first, then dependent tables)
6. List all tables' entries, delete the empty defaults
```
Never guess IDs. Every `db_`, `tb_`, `fd_`, `en_` ID comes from a previous API response.
50 Sellable Agentic Systems Built on Lerty
How Every System Works
Who uses Lerty: The business owner and their team. They get interactive messages, push notifications, dashboards, and approval workflows inside Lerty.
Who doesn't use Lerty: External parties — tenants, patients, customers, vendors, clients. They interact through their normal channels (email, SMS, web forms, phone calls). They never know Lerty exists.
What connects them: n8n automations bridge external channels into Lerty. Inbound emails, form submissions, and webhooks become structured entries. Outbound responses go back through email/SMS.
What the MCP agent does: Aggregates external noise into organized data, triages by priority, flags what needs attention, and surfaces decisions to the business owner as interactive messages. The owner makes decisions — the agent handles everything else.
Pricing Tiers
- Standard ($500/mo) — Lerty databases + MCP agent monitoring, alerts, and push notifications to owner/staff
- Professional ($750/mo) — Everything in Standard + interactive approvals, multi-table agent workflows, auto-generated reports
- Premium ($1,000/mo) — Everything in Professional + n8n automations bridging external channels, external API integrations, multi-agent coordination
Why businesses pay this: Every system replaces 10-30 hours/week of manual work — a part-time employee costs $1,500-$2,500/mo. You're selling a fraction of that cost for 24/7 reliability.
---
Real Estate & Property Management
1. Rental Property Operations Hub
Tier: Premium ($1,000/mo)
Tenants email or text about maintenance issues like they always have. n8n catches inbound messages and creates structured entries in the maintenance request table — property, unit, issue type, urgency. MCP agent triages by severity, matches to the right vendor from the vendor table, and sends the property manager an interactive approval: "Unit 4B has a leaking pipe. Dispatch ABC Plumbing ($150 service call)? Approve / Reject." Owner taps approve, agent updates the entry, n8n sends the tenant a confirmation email. Agent tracks costs against each property's maintenance budget and pushes an alert when spending exceeds thresholds.
Why it sells: Property managers spend 8-10 hrs/week fielding texts, calling vendors, and tracking costs in their head. This cuts it to tap-to-approve.
2. Real Estate Deal Flow Analyzer
Tier: Premium ($1,000/mo)
Investor logs potential deals into the pipeline. n8n pulls comp data and listing details from MLS feeds. Agent auto-calculates ARV, cash-on-cash return, and rehab estimates from the rate tables. Sends the investor a daily push digest: "3 deals need decisions today." Each deal gets an interactive summary with Pursue / Pass / Need More Info. Agent flags deals going stale (no action in 7+ days) and generates offer-ready analysis packets.
Why it sells: Investors doing 2-3 deals/month lose $10K+ on bad analysis or missed timing. This systematizes their pipeline and forces timely decisions.
3. Lease Renewal & Tenant Retention System
Tier: Professional ($750/mo)
Agent monitors lease expiration dates across all properties. At 90/60/30 days out, pushes the landlord: "Unit 2A lease expires March 15. Tenant satisfaction: 4.2/5. Market rate is $50 above current rent." Interactive message with options: Renew at current rate / Propose increase / Schedule conversation / Do

_(truncated — see source URL for full content)_

## Notes

_Hand-editable. Preserved across re-runs._