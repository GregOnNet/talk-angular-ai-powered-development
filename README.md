# talk-angular-ai-powered-development

## Start presentation

```bash
npm install
npm run dev
```

## Goal

This task tells the story of how I started to learn about AI.
How I struggled at first.
How I was fighting it.
And finally, how I started to integrate it into my work as a frontend engineer.

There is a lot to tell about AI, so I need to continuously remind myself to focus on Angular here.
Luckily the Angular team already did a great job on integrating Angular with the AI ecosystem.
There is already a lot on the official docs page: https://angular.dev/ai.

So why this talk?
I guess I want to add some background to the whole AI story.
I want to round things up for the Angular Community.

Frequently we see posts of poor quality on social media.
AI-generated content can be really annoying.
But we shall not fall into the trap of thinking of AI as a threat, only because of people seeking publicity using it in a bad way.

This being said, I will start with **building a healthy mindset when it comes to using AI professionally**.
Then, I need to shift to Angular's pre-work on integrating the platform with AI Agents (**Angular comes prepared**).
In this section, I will also explain the purpose of instructions and rules.
This is the foundation of building an agentic team taking on several tasks like coding, testing, requirements-engineering, and review.
After that I will show the Angular CLI MCP server and its capabilities.
I will record a video demonstrating how tool calls are made from the Agent to look up best practices of Angular.

## Building AI Skills
The following list holds a bunch of topics we can learn as developers to get used to AI.

- Build a healthy AI mindset
- Use an AI Chat
- Use an Agent
- Expand usage of Agents
- Include tools to your Development Workflows
- Build agentic workflows
- Understand how LLMs work
- Measure LLM output allowing evidence-based decisions

## Distillation for Angular
The following list filters topics especially for using AI with Angular.

- Build a healthy AI mindset
- Angular comes prepared
- Get started with Angular CLI MCP
- Build agentic workflows
- 🍨🍒 Measure LLM output allowing evidence-based decisions

## Build a healthy AI mindset

“AI is incapable of this.”
“AI is incapable of that.”
“Look — this is where vibe-coding leads you… straight to hell.”

I’m sure you’ve seen posts like this before — perhaps even today.
From time to time, you might also stumble across something like:

**Do we still need software developers?**
**Will UX experts and designers still have a future?**

Statements like these can trigger frustration, fear, or at least uncertainty.
Why? Because our brains tend to believe something is true the more often we read or hear it.

This was exactly the situation I faced a year ago.
I launched a new business during an unstable market period, and on top of that, AI seemed poised to eliminate the very career I had built my life around.

Bad news can hit like a massive, dark-blue wave — overwhelming and paralyzing.
But here’s the truth: we cannot control what comes from the outside.
If the waves keep crashing over us, we can learn to surf them.

And that’s what I chose to do.
And luckily the Angular team had already chosen AI as an important strategic pillar, too.

From this moment on I started recognizing that everyone was talking about fewer developers or
bad quality, BUT no one was talking about the potential if we developers start to use AI on our own
with the proficiency we already bring to the table when it comes to complex technical challenges.

I started using AI chats and soon I started working with my first coding agent and I delegated
small tasks to it.

Guess what, from that moment on I knew that 90% of the messages in social media and even in the press
were incorrect.
And from this day on, I learned. AI is yet another skill that will be added to our toolbelt, such as
testing, architecting, clean coding, automating & versioning already is.

## Angular B-AI-tteries included

### llms.txt

The `llms.txt` is a special file for AI agents.
It belongs to the same family as the robots.txt.
But whereas the robots.txt tells search engines what not to crawl,
the `llms.txt` points to pages with significant information for the models.
You can make your web-page or web-resources better to search for models if you
provide a `llms.txt` file in your web-space.

Angular.dev does the same.
It provides a `llms.txt` file to help models crawl the documentation more efficiently to
provide better and more up-to-date answers to you.

This is a very easy but effective way of providing actual information about Angular to LLMs.
Luckily, Markdown is a format most developers are familiar with.
It is very easy to write and has turned out to be consumed and processed by models due to its
structured syntax.

### rules-files

And you can use Markdown in your projects, too.
Especially if you want to ensure that certain coding styles or whole architectures are applied.

Imagine you want to start bringing a new feature to life. You need components and services for it and your prompt looks like this:

```text
- Create a component that allows to rate a product from 1-5
- Therefore, create a service that allows to update the rating
```

If you review this prompt you are absolutely right if you say:
"There is a lot of information missing."
- How should the rating be displayed?
- When shall the API be called?
- What is the API endpoint?

Yes, you are right, I hear you, and this can be improved.
But requirements change and tend to be unique up to a certain point.
What stays the same are criteria for quality and architecture.
And this is missing too, right?
But how do we fit all this information in a single prompt?
And how do we make sure that we apply our valuable standards for each
prompt?
How do we share those instructions?
Here rule- & instruction files come into play.

These are files written in Markdown.
Here you can specify your coding guides and best practices.

Coding Agents like Firebase Studio, Cursor, GitHub Copilot, Windsurf, Tabnine load these files and are able to apply those
instructions to every prompt you send to the model.
This makes sure that your standards are safely applied and recognized by the model.

The good news is, Angular gets you started quickly with a concise rule file: https://angular.dev/ai/develop-with-ai#rules-files

In this rule file you will note that a lot of the modern Angular
styles are enforced (signals APIs, `control-flow-syntax`, DI with `inject`).

**Question**: "Do you have coding standards in your company? Have you written them down? Is your project 100% in line with these standards?"
If the answer is **no**, this is absolutely fine. I never met a team that was able to apply all standards, since they evolve and change over time, too.

Now, with the help of rules or instruction files you are able to define your standards and live them
at the same time.
The LLMs will help you code along these standards. You can let models review your code to spot
mistakes and anti-patterns.
With the right prompting technique you are even able to let the model refactor your code automatically.

This is how AI makes your coding standards a living standard!

You might say now: "Gregor, thanks for mentioning it, but we already use these markdown files.
Still, it does not work for us. Sometimes the model messes things up. Sometimes we spot errors
too late that have been introduced. So, how can we escape that loop?"
And again, Angular has your back.
Here is where [web-codegen-scorer](https://github.com/angular/web-codegen-scorer) comes in handy.

### web-codegen-scorer

What is the web-codegen-scorer?
It is a CLI tool that helps you check how good your prompts and instructions perform.
To evaluate your instructions the web-codegen-scorer will be fed with
- a configuration telling which runner and model is used
- one or more of your instructions (your living coding standards)
- example prompts to create various example apps

What happens with these ingredients?
The web-codegen-scorer will by default pick 5 prompts that instruct a model to build an app.
Your instructions are mixed into each of these prompts as a system prompt.
5 Apps will be generated in parallel.
Once an app is built, it gets started in the browser.
Axe and Lighthouse tests are executed.
Failing tests such as build errors are reported.
web-codegen-scorer will make 2 attempts to fix those errors.
Based on the collected data the generated app is rated.
A report gets generated that you can inspect.
Now it's your turn: based on the findings of the report you tweak your instructions.
You let the evaluation run again.
All reports are saved in a history.
This allows you to compare the reports.
This allows you to do evidence-based testing on your AI setup ❤️.

**configuration**
```js
// config.mjs
import { getBuiltInRatings } from 'web-codegen-scorer';

export default {
  skipInstall: true,
  displayName: 'agentic-coding-scorer',
  clientSideFramework: 'angular',
  sourceDirectory: 'project',
  ratings: [...getBuiltInRatings()],
  generationSystemPrompt: './<your-instructions>.md',
  executablePrompts: ['./example-prompts/**/*.md'],
}
```

**evaluate**

```bash
export GEMINI_API_KEY="..🤖.." && web-codegen-scorer eval --env=angular-example;
# OR - setup your own environment
export GEMINI_API_KEY="..🤖.." && web-codegen-scorer eval --env=./config.mjs;
```

**report**

```bash
web-codegen-scorer report
```

**test generated apps manually**

```bash
web-codegen-scorer run --prompt=<generated-app> --env=<path>
```

- Your Playground: https://github.com/GregOnNet/angular-web-codegen-scorer-playground

Now, you have a tool that can proof how well your generated code performs.
This enables you to take the next step in agentic coding: orchestrating not one but multiple
agents in a workflow.

## Agentic Workflows

Since Angular gives you the ability you need to build apps supported by AI with confidence,
you are now able to delegate recurring tasks to your CI/CD-Pipeline.
Workflows bring everything together, that we have learned so far.
Workflows allow to orchestrate multiple Agents to reach a specific goal.

But why shall we do it.
So currently, we are trapped in the quality triangle of software engineering.
There is quality, cost, time. You cannot optimize all three aspects.
My personal goal is to let AI help to automatically optimise these aspects where it is ever possible.
- Quality -> Let AI Ensure Coding Standards and correctly applied architecture
- Cost -> Let AI lift heavy, recurring tasks that would take hours and days for us to do manually
- Time -> Let AI generate code, scripts, tests after ensuring the correct setup (e.g. with web-codegen-scorer)

You can use a command line agent or an AI SDK to call your model.
- With CLIs
  - Gemini CLI
  - Claude Code
  - Cursor CLI
  - ...
- With AI SDKs
  - Vercel

Based on your CI/CD you can use various triggers to let your agentic workflows run
- issue created/edited
- issue labelled
- pull request opened
- cron schedule

What about starting with a supportive Agentic Team:
- Requirements-Review
- Coding-Explorer
- PR-Reviewer

- Your Playground: https://github.com/GregOnNet/agentic-workflow-claude

## Backup

### MCP Server

- Angular CLI lets you install an MCP Server
- The Angular CLI MCP Server is a bridge between your AI Model and https://angular.dev
- It allows tool calls to search the Angular Documentation
- I also allows to get most up to date best practices from https://angular.dev
- In the near future we can expect even more tools... maybe modernizing our Angular App with one tool call, that executes all the migration schematics for us to migrate to the latest Anuglar-APIs

### My personal AI roadmap

1. Mindset Shift - AI & Developer = 💪⚡
2. Chat with LLMs
3. Let an Agent Code
   3.1 often found myself in an endless loop debugging and fixing stuff
   3.2 felt lost in fixing recursion bugs AI had solved before
4. Understand how LLMs work (good enough)
   4.1 Learned about capabilities of agentic coding
   4.2 learned how to prevent these issues
5. Expand usage of Agents
6. Include tools to your Development Workflows
7. Build agentic workflows
8. ✨ Measure LLM output allowing evidence-based decisions
