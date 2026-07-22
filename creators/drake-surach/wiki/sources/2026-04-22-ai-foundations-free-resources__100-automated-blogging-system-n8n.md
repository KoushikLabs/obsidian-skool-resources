---
title: "100% Automated Blogging System n8n"
date: 2026-04-22
creator: drake-surach
course: AI Foundations Free Resources
source_url: https://aifoundations.io/resources/100-automated-blogging-system-n8n
has_resource: true
type: source
concepts:
  - hooks
  - workflow-automation
  - cloud-deployment
  - design-systems
entities:
  - n8n
  - google
  - openrouter
  - youtube
---

# 100% Automated Blogging System n8n

> Course: **AI Foundations Free Resources**

## Links
- Lesson: https://aifoundations.io/resources/100-automated-blogging-system-n8n
- Creator: [[drake-surach-profile]]

## Cross-references
**Concepts:** [[hooks]], [[workflow-automation]], [[cloud-deployment]], [[design-systems]]
**Entities:** [[n8n]], [[google]], [[openrouter]], [[youtube]]

## External links
- [https://www.skool.com/ai-foundations](https://www.skool.com/ai-foundations) — `external`
- [https://lerty.ai](https://lerty.ai) — `external`
- [https://openrouter.ai/](https://openrouter.ai/) — `external`
- [https://www.tavily.com](https://www.tavily.com) — `external`
- [https://www.youtube.com/watch?v=VIDEO_ID_HERE](https://www.youtube.com/watch?v=VIDEO_ID_HERE) — `youtube.com`

## Files
- [`1XmSmqJM6mDO9Q8rd6IR2OeAgx5aVkOav`](../../raw/ai-foundations-free-resources__100-automated-blogging-system-n8n/1XmSmqJM6mDO9Q8rd6IR2OeAgx5aVkOav.bin) — drive_file, 68.6 KB
- [`1769028156-35d5db5f4cd4d0a1-_____Blog_Writer__3___1_.json`](../../raw/ai-foundations-free-resources__100-automated-blogging-system-n8n/1769028156-35d5db5f4cd4d0a1-_____Blog_Writer__3___1_.json) — direct.json, 68.6 KB

## Page content

🔴 April Hackathon Live in Ai Foundations! ($350 cash prizes)
Learn more
Products
Resources
K
Koushik Raghavan
Back to Resources
N8N
100% Automated Blogging System n8n
16 min read
Copy as Markdown
What is this?
The promise of Ai is to save you time and scale your influence. In today's guide we bring that dream to life using some incredible tools:
→ N8N: For wiring the automation and agents
→ Lerty: For communicating with your workflow and human in the loop
→ Openrouter: For running ai models
→ Tavily: For using internet search tools (free account)
Enjoy this quick guide and read through to the end to get the n8n blueprint handed off to you so you can plug this into whatever use case you want.
Steps for EASIEST Plug-n-Play
If you want to get up and running as soon as possible, here's the quick version of this guide.
Step 1: Download the Free n8n Template
Using the link below you can download a JSON file that will be a two click import into your own n8n account:
↓ Download The Blueprint
Step 2: Sign-up For a Free Lerty Account
Lerty is the tool we use to connect our AI agents to a chat interface, surface the human in the loop features and typing indicators and where we host all of our AI agents.
Step 3: Connect Your API Keys
We use OpenRouter because all it takes is one API key to access 100s of models. If you sign up for an OpenRouter account you get get model access for as little as $5.
Step 4: Connect Tavily
You can use a free Tavily account for getting access to awesome and accurate web searching capabilities with your AI agents. We are still on the free plan after loads of blog posts.
Who is this for?
There are many people that this automation can help but there are two main camps of people that will get the most out of this.
1.) You're an agency owner who wants Ai Agents to sell to customers. Think home services clients who are looking to bolster their SEO.
2.) You personally want to hook this up for your own business and start generating limitless blogs to grow your own brand.
The Blueprint
This workflow is a 7-step process that ensures that your blogs are high quality, on-brand, and specific to your exact request every time.
Want a blog with 500 words? Maybe 5000 words? This workflow can handle it.
Want an article that uses your actual keywords that matter? This workflow has a step for that.
Want accurate up to date research integrated in your blog? This workflow is built to handle it.
Want every blog to sound like your brand? There's a config node for that.
Step 1 - End User Config (One-Time Setup)
Before you run a single blog, you'll configure your company details once. This node injects your brand context into every agent in the workflow so your blogs always sound like you OR the company who you are building this for.
No more re-entering company info every time. Set it and forget it.
You can even add to this variable list and insert it directly into the agents so you can have rules and variables for each company you distribute this too.
The Node where you'll edit these options
This company context gets passed to every agent in the workflow. The Researcher prioritizes sources relevant to your industry. The Section Mapper structures content for your audience. The Blog Writer matches your brand voice.
Fill this out once when you set up the template, then every blog you generate automatically inherits your brand DNA.
Step 2 - The Assistant
Discuss your blog with an assistant to brain storm ideas and get the ball rolling. This step gives you a back and fourth that will help you or your client hone in on their idea. Then all you do is type /start to initiate the creation of the blog.
Assistant Agent running on Grok 4.1
Here's the starting prompt for the assistant, I wanted to keep it dead simple to start, but you can customize this to give the assistant relevant info and make it less dry for your use-case.
assistant prompt
Copy
You are a helpful agent that discusses blog ideas with the user.
Instruct them to use /start to start a blog after discussing ideas.
They need to come up with a Topic, Audience Segment, Goal and Word Count and CTA if they have one.
You cannot start these or pass their final answer, remind them to use **/start** to get started.
Respond in a conversational, clean, professional tone.
Do not include emojis or "overly friendly" language, respond like a professional relaxed, happy, motivated consultant.
Answer with 1-2 sentence, conversational, snappy but informative responses.
Answer like a friend I'm texting with, don't use overly professional verbose words.
Here is some information about the company speaking with you:
Company Context:
- Company: {{ $('End User Config').item.json.company_name }}
- About: {{ $('End User Config').item.json.company_description }}
- Voice: {{ $('End User Config').item.json.brand_voice }}
Make sure if giving suggestions you always keep these things in mind, with recent trends. Never create cheesey or outdated ideas. Remember the goal is to make their blog posts stand out and become GEO ready in this digital age. Don't mention anything about GEO, just use that as your brain context.
ensure you use your web search tool to find relevant things when talking to the user about ideas
Today's date is: {{ $now }}
Never use "—" the em dash. Omit —.
Step 3 - Starting the Blog Creation
Until you type /start, the automation won't begin, but after you initiate that command you or your client will be sent a form that makes it easy to request a blog from the system.
This is what kicks off the n8n workflow.
Creating a blog is as easy as /start
Step 4 - Research Agent
Every great article requires research, we are in luck. Ai does this well. So the next step is the research agent, which is going to search the web with relevant queries and find sources that can inspire our blog post.
The research agent now also knows your industry from the End User Config, so it prioritizes sources that actually matter to your audience.
Below I've listed the research agent's prompt so you can implement this for yourself.
research agent input prompt
Copy
Task Specifics:
Topic: {{ $('Start').item.json.Topic }}
Audience Segment: {{ $('Start').item.json['Audience Segment'] }}
Goal: {{ $('Start').item.json.Goal }}
CTA: {{ $('Start').item.json.cta }}
research agent prompt
Copy
## Your Role:
Search and prep 10 accurate urls related to the inputs to be used in a blog article. Ensure that you do your due diligence to find the best articles possible for this task.
## Important Rules:
- Always hone your research to return the 10 most relevant blog URLS to that you are up to date based on the current date of: {{$today}}
- Always check when content was published before listing the URL in your output to make sure that it aligns with the most up to date content in relation to {{ $today }}
- If the content is evergreen in nature don't weight it based on the date as much, but consider any updates new developments and follow up searches that you should do to verify content readiness for a successful up to date blog article.
- Utilize the web_search tool to find article urls and relevant articles
- Don't pull youtube urls or video urls, only text based posts
Company Context:
- Company: {{ $('End User Config').item.json.company_name }}
- Industry: {{ $('End User Config').item.json.industry }}
When selecting sources, prioritize content relevant to {{ $('End User Config').item.json.industry }}. Avoid generic listicles.
## Your workflow:
1.) Initial research phase. Do a sweeping search of all the sources on the topic you can find.
2.) Hone the list to the most relevant 10 links.
3.) Return link, reason pairs. Reason should share the reason why you chose that article in 250 characters or less to be used as a reference for the blog.
## Required JSON Output Structure:
{
  "url-1": "https://example.com/article-one",
  "reason-1": "2025 stats on topic with original survey data from 500+ respondents. Directly addresses audience pain points.",
  "url-2": "https://

_(truncated — see source URL for full content)_

## Notes

_Hand-editable. Preserved across re-runs._