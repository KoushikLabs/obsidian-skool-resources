---
title: "Automated Blogging in N8N"
date: 2026-04-22
creator: drake-surach
course: AI Foundations Free Resources
source_url: https://aifoundations.io/resources/automated-blogging-in-n8n
has_resource: true
type: source
concepts:
  - hooks
  - workflow-automation
  - trading-bots
  - cloud-deployment
  - design-systems
entities:
  - n8n
  - google
  - openrouter
  - youtube
---

# Automated Blogging in N8N

> Course: **AI Foundations Free Resources**

## Links
- Lesson: https://aifoundations.io/resources/automated-blogging-in-n8n
- Creator: [[drake-surach-profile]]

## Cross-references
**Concepts:** [[hooks]], [[workflow-automation]], [[trading-bots]], [[cloud-deployment]], [[design-systems]]
**Entities:** [[n8n]], [[google]], [[openrouter]], [[youtube]]

## External links
- [https://www.skool.com/ai-foundations](https://www.skool.com/ai-foundations) — `external`
- [https://lerty.ai](https://lerty.ai) — `external`
- [https://www.youtube.com/watch?v=6lGBFD8mVV8](https://www.youtube.com/watch?v=6lGBFD8mVV8) — `youtube.com`

## Files
- [`1QY3e4_AvRMH2oAc755gUunHMgKGbIpRe`](../../raw/ai-foundations-free-resources__automated-blogging-in-n8n/1QY3e4_AvRMH2oAc755gUunHMgKGbIpRe.bin) — drive_file, 59.7 KB

## Page content

🔴 April Hackathon Live in Ai Foundations! ($350 cash prizes)
Learn more
Products
Resources
K
Koushik Raghavan
Back to Resources
N8N
Automated Blogging in N8N
13 min read
Copy as Markdown
What is this?
The promise of Ai is to save you time and scale your influence. In today's guide we bring that dream to life using some incredible tools:
→ N8N: For wiring the automation and agents
→ Lerty.ai: For communicating with your workflow and human in the loop
→ Openrouter: For running ai models
Enjoy this quick guide and read through to the end to get the n8n blueprint handed off to you so you can plug this into whatever use case you want.
Who is this for?
There are many people that this automation can help but there are two main camps of people that will get the most out of this.
1.) You're an agency owner who wants Ai Agents to sell to customers. Think home services clients who are looking to bolster their SEO.
2.) You personally want to hook this up for your own business and start generating limitless blogs to grow your own brand.
The Blueprint
This workflow is a 6-step process that ensures that your blogs are high quality and specific to your exact request every time.
Want a blog with 500 words? Maybe 5000 words? This workflow can handle it.
Want an article that uses your actual keywords that matter? This workflow has a step for that.
Want accurate up to date research integrated in your blog? This workflow is built to handle it.
Step 1 - The Assistant
Discuss your blog with an assistant to brain storm ideas and get the ball rolling. This step gives you a back and fourth that will help you or your client hone in on their idea. Then all you do is type /start to initiate the creation of the blog.
Assistant Agent running on Grok 4.1
Here's the starting prompt for the assistant, I wanted to keep it dead simple to start, but you can customize this to give the assistant relevant info and make it less dry for your use-case. 👨🏽‍🎨
assistant prompt
Copy
You are a helpful agent that discusses blog ideas with the user.
Instruct them to use /start to start a blog after discussing ideas.
They need to come up with a Topic, Audience Segment, Goal and Word Count.
You cannot start these or pass their final answer, remind them to use /start to get started.
Respond in a conversational, clean, professional tone.
Do not include emojis or "overly friendly" language, respond like a professional relaxed, happy, motivated consultant.
Answer with 1-2 sentence, conversational, snappy but informative responses.
Answer like a friend I'm texting with, don't use overly professional verbose words.
Never use "—" the em dash. Omit —.
Step 2 - Starting the Blog Creation
Until you type /start, the automation won't begin, but after you initiate that command you or your client will be sent a form that makes it easy to request a blog from the system.
This is what kicks off the n8n workflow.
Creating a blog is as easy as /start
Step 3 - Research Agent
Every great article requires research, we are in luck. Ai does this well. So the next step is the research agent, which is going to search the web with relevant queries and find sources that can inspire our blog post.
Below I've listed the research agent's prompt so you can implement this for yourself.
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
## Your workflow:
1.) Initial research phase. Do a sweeping search of all the sources on the topic you can find.
2.) Hone the list to the most relevant 10 links.
3.) Return link, reason pairs. Reason should share the reason why you chose that article in 250 characters or less to be used as a reference for the blog.
## Task Specifics:
Topic: {{ $('Start').item.json.Topic }}
Audience Segment: {{ $('Start').item.json['Audience Segment'] }}
Goal: {{ $('Start').item.json.Goal }}
## Required JSON Output Structure:
{
  "url-1": "https://example.com/article-one",
  "reason-1": "2025 stats on topic with original survey data from 500+ respondents. Directly addresses audience pain points.",
  "url-2": "https://example.com/article-two",
  "reason-2": "Step-by-step implementation guide with code examples. Most shared resource in the space this quarter.",
  "url-3": "https://example.com/article-three",
  "reason-3": "Contrarian take that challenges common assumptions. Good for adding nuance and addressing objections.",
  "url-4": "https://example.com/article-four",
  "reason-4": "Case study with measurable ROI figures. Perfect for proving claims to skeptical readers.",
  "url-5": "https://example.com/article-five",
  "reason-5": "Official documentation covering latest updates. Authoritative source for technical accuracy.",
  "url-6": "https://example.com/article-six",
  "reason-6": "Expert interview with industry leader. Quotable insights for credibility.",
  "url-7": "https://example.com/article-seven",
  "reason-7": "Comparison post covering alternatives. Helps position against competitors.",
  "url-8": "https://example.com/article-eight",
  "reason-8": "Beginner-friendly explainer for foundational concepts. Good for defining terms.",
  "url-9": "https://example.com/article-nine",
  "reason-9": "Recent news piece on market trends. Adds timely context and urgency.",
  "url-10": "https://example.com/article-ten",
  "reason-10": "Community discussion with real user experiences. Authentic voice for relatability."
}
Step 4 - Section Mapping
This is where the workflow gets powerful. Not a lot of people provide custom workflows that can handle varying lengths of articles with a realistic flow.
In fact, the crux of the problem with AI is that most people don't create workflows like this that give you precise outputs.
The section mapper does just that.
It looks at your word count, and crafts sections that sum to the word count you need to hit.
Section mapper process diagram.
Here's the section mappers prompts:
section mapper input prompt
Copy
INPUT:
{
  "target_wordcount": {{ $('Start').item.json['Rough Word Target'] }},
  "attempt": 1,
  "failure_reason": "n/a",
  "topic": "{{ $('Start').item.json.Topic }}",
  "audience_segment": "{{ $('Start').item.json['Audience Segment'] }}",
  "goal": "{{ $('Start').item.json.Goal }}"
}"
Sources:
{{
  Object.keys($('Researcher').item.json.output)
    .filter(k => k.startsWith('url-'))
    .map(k => {
      const i = k.split('-')[1]
      return `- ${$('Researcher').item.json.output[`url-${i}`]}\n  Reason: ${$('Researcher').item.json.output[`reason-${i}`]}`
    })
    .join('\n\n')
}}
section mapper system prompt
Copy
You are a blog outline planning agent.
Return VALID JSON ONLY. No markdown, no extra text.
INPUT will include:
- target_wordcount (integer): total final blog word count
- attempt (integer): current attempt number that you're on if it exceeds 1 it means that this is a retry.
- failure_reason (string): if an attempt exceeds 1 you will receive a failure reason, adjust based upon this if there was a failure in the previous attempt.
- topic: the topic of the blog
- audience segment: the intended audience
- goal: the goal of the blog
- sources: sources that you can read with your extract tool to get inspiration for sections. Look 

_(truncated — see source URL for full content)_

## Notes

_Hand-editable. Preserved across re-runs._