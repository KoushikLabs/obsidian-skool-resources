---
title: "Agent Builder: Build and Deploy a Self Learning Agent!"
date: 2026-04-22
creator: drake-surach
course: AI Foundations Free Resources
source_url: https://aifoundations.io/resources/agent-builder-build-and-deploy-a-self-learning-agent
has_resource: false
type: source
concepts:
  - skills
  - mcp
  - hooks
  - memory-system
  - workflow-automation
  - self-hosting
  - vector-stores
  - trading-bots
  - cloud-deployment
entities:
  - claude-code
  - n8n
  - openai
  - github
  - youtube
  - vps
---

# Agent Builder: Build and Deploy a Self Learning Agent!

> Course: **AI Foundations Free Resources**

## Links
- Lesson: https://aifoundations.io/resources/agent-builder-build-and-deploy-a-self-learning-agent
- Creator: [[drake-surach-profile]]

## Cross-references
**Concepts:** [[skills]], [[mcp]], [[hooks]], [[memory-system]], [[workflow-automation]], [[self-hosting]], [[vector-stores]], [[trading-bots]], [[cloud-deployment]]
**Entities:** [[claude-code]], [[n8n]], [[openai]], [[github]], [[youtube]], [[vps]]

## External links
- [https://www.skool.com/ai-foundations](https://www.skool.com/ai-foundations) — `external`
- [https://github.com/cartcodes/Easy-ChatKit-Server.git](https://github.com/cartcodes/Easy-ChatKit-Server.git) — `github.com`
- [https://chatkit.studio/playground](https://chatkit.studio/playground) — `external`
- [https://railway.com](https://railway.com) — `external`
- [https://platform.openai.com](https://platform.openai.com) — `external`
- [https://www.youtube.com/watch?v=zqHdRgIwOC8](https://www.youtube.com/watch?v=zqHdRgIwOC8) — `youtube.com`

## Page content

🔴 April Hackathon Live in Ai Foundations! ($350 cash prizes)
Learn more
Products
Resources
K
Koushik Raghavan
Back to Resources
AGENT BUILDER
Agent Builder: Build and Deploy a Self Learning Agent!
9 min read
Copy as Markdown
The Agent Builder Struggle
In this guide I’m going to show you exactly how to use OpenAI’s Agent Builder and even how to deploy your agent.
Agent Builder is a powerful new tool shaking up how people build ai agents...
But there’s a hard truth that you may have run into:
Deployment for non-technical users is tough.
Most people are used to n8n level simplicity. Agent Builder isn’t that. And the irony is brutal:
Even the latest language models struggle to help you build with it.
Especially when you’re working on new versions of Agent Builder that the the ai models don't understand yet. The truth is there's just not a lot of info on Agent Builder that's actionable and direct.
I hope to change that with the resources I share here and in my youtube videos.
The Goal of Today's Guide
Today, I want to give you a masterclass on agent builder, we will do the following:
1.) Create a Self Learning Ai Agent with personalized memory context.
2.) Create custom MCP servers that you can use with your agents.
3.) Finally deploy your agent builder agents.
This video goes along with the resource if you want to watch a visual explanation.
Overview of Architecture
Here's a high level overview of what we will be building today.
We start with a message from the user, then we pass that to a file search tool, this file search tool communicates with our vector database in Agent Builder and returns any relevant stored memories.
Then we pass the memory results into a transform node where we output only the text memories in the results.
Finally, that ends up being context for the assistant itself. The assistant then uses any relevant memories to construct a better response. This assistant also has the ability to add memories to the vector database using our custom built mcp tool.
Diagram of the Agent Builder workflow
Building The Self Learning Agent
Add a start node first, then connect it to a file search node, in the file search node settings you will see a button where you can create a new vector store.
Create your vector store and give it a name. Then grab the vector store id and go back to agent build. Add that vector store id to your file search node to connect it.
I leave the max results at 10 because that should be more than enough as a max memory for each response.
Then I use this variable to insert the user's message for the query:
{{workflow.input_as_text}}
Next connect the file search to a transform node. The transform node should have a key named: result
For the value enter this CEL expression:
OpenAi Agent Builder CEL Syntax
Copy
(
  (has(input.results[0]) ? input.results[0].content[0].text : "") +
  (has(input.results[1]) ? "\n" + input.results[1].content[0].text : "") +
  (has(input.results[2]) ? "\n" + input.results[2].content[0].text : "") +
  (has(input.results[3]) ? "\n" + input.results[3].content[0].text : "") +
  (has(input.results[4]) ? "\n" + input.results[4].content[0].text : "") +
  (has(input.results[5]) ? "\n" + input.results[5].content[0].text : "") +
  (has(input.results[6]) ? "\n" + input.results[6].content[0].text : "") +
  (has(input.results[7]) ? "\n" + input.results[7].content[0].text : "") +
  (has(input.results[8]) ? "\n" + input.results[8].content[0].text : "") +
  (has(input.results[9]) ? "\n" + input.results[9].content[0].text : "")
)
Sadly, OpenAi agent builder doesn't support a cleaner way to do this with wildcards yet, as of right now we have to check if each memory is there starting at index 0 and working our way up to index 9.
Hopefully OpenAi improves this feature and adds support for a wider range of CEL operations so we can use a simpler one line version in the future.
Keep in mind that if you want to go more than max 10 on the file search tool you'll need to extend this beyond index 9.
Finally we can add the agent node after the transform. Here's the prompt I used for the agent, I encourage you to modify this for your own use case:
Instructions
Copy
You are a helpful assistant, and you receive any memories that are already relevant to the conversation here:
{{input.result}}
You can also upload new memories if the user expresses any preference that's not in the previous memories given above make sure to always upload the users memory preferences, using your upload memory tool that you have access to.
USER MESSAGE:
 {{workflow.input_as_text}}
Next, you'll need to add an MCP server tool. This MCP server tool has a couple steps to make it work.
Keep in mind that in order to build this tool I used Claude Code. I spun up a python server using uvicorn that allows a persistent sse based connection.
This server does a couple things:
1.) It utilizes MCP standards to connect serve a single tool called: upload_to_vector_store
2.) When the assistant uses the tool it sends a simple text string that then goes to my server. On my local server it converts that plain text it receives into a .txt file.
3.) That .txt file then gets uploaded to OpenAi using their file upload endpoint. This endpoint responds with a file id.
4.) Finally we add a file to the vector store using OpenAi's endpoint for this. It requires a vector store id, and the file id from the previous step so we pass it in there.
Although this program is solid and it works well as an experiment. I'd always recommend n8n's mcp server node as a simpler option to create this server. It doesn't need to be it's own custom built server in most use cases. The .txt conversion was the main reason I rolled my own custom server.
The server requires authentication via my OpenAi Api key and the tool use requires a vector store id, and the api key in my .env file.
This took about 10 minutes to build using Claude Code. If you are struggling to develop simple servers like this I'd highly recommend checking out our Claude Code Mastery Course. It is super empowering to be able to build servers, websites and even full-fledged applications using this tool.
Deploying with Agent Builder
Now let's discuss the methods for deploying with Agent Builder.
Keep in mind that this is the easiest way to deploy, because OpenAI has given us so much flexibility there is a frontier of possibilities.
I think of this as the minimum viable deployment:
- Share your agent on a live website that anyone can use.
- Each user gets their on unique conversations and session ID.
- OpenAi stores the conversation history temporarily.
- A beautiful chat interface created using OpenAi's Chatkit
In future guides I'd like to share advanced use cases where you hook this into your own database with deeper customization.
The Easy ChatKit Server
The best place to start is to use my boilerplate server that I created to make this whole process a lot simpler. Of course, you could roll your own using something like Claude Code.
You can clone the git repo I created to get started.
The only requirement to deploy is to replace the config.ts file entirely with a ChatKit interface. You can create the ChatKit interface and get this code using the visual ChatKit builder provided by OpenAi.
Next, you'll want to commit it to a new github repo on your own account. Make sure to use git add to add the changes you made to the config.ts file, then push it to your github repo.
Once it's on the github repo you can deploy it using a vps provider like Railway. Railway is one of the quickest ways to deploy. If you go to railway you can connect to the github repo that you just created with the server on it.
Once it starts deploying, the first build may crash. This is because you don't currently have your environment variables set.
Adding Environment Variables
First, navigate to your settings for the app and click the generate domain button in railway. This will give you a domain that you can use. Keep the port there on 8080.
Next, copy that domain 

_(truncated — see source URL for full content)_

## Notes

_Hand-editable. Preserved across re-runs._