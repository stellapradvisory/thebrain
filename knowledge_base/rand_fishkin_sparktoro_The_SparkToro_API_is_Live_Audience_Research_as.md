# The SparkToro API is Live: Audience Research as Infrastructure

*Source: Rand Fishkin / SparkToro*
*URL: https://sparktoro.com/blog/the-sparktoro-api-is-live-audience-research-as-infrastructure/*
*Date: Wed, 08 Jul 2026 15:58:39 +0000*
*Added to knowledge base: August 2026*
*Trust level: High — trusted source for SEO and AI search strategy*

---

## Summary

I have a confession. For years, my least favorite customer question was “Does SparkToro have a public API?”



Not because it was a bad question. But, because the answer was always “not yet, we still have other, higher priorities,” which is… a pretty deflating answer to have to give.” SparkToro was built as a web app: a research tool marketers…

## Full Content

Casey Henry
Casey Henry is the co-founder and CTO of SparkToro, where he builds the platform end to end - from the data pipeline to the public API and MCP server. He writes about the engineering behind audience research and what it takes to ship product.
I have a confession. For years, my least favorite customer question was “Does SparkToro have a public API?”
Not because it was a bad question. But, because the answer was always “not yet, we still have other, higher priorities,” which is… a pretty deflating answer to have to give.” SparkToro was built as a web app: a research tool marketers and consultants opened, ran research with, and pulled insights from. If you wanted the data in your CRM, your SaaS product, or your own tools, you were up a creek.
That ends today. The SparkToro API gives developers, agencies, and technical marketers direct access to
the same audience-intelligence data that powers our web app
, with the shape, speed, and predictability real production systems need.
Why Now
Two things pushed us to build this.
First,
our MCP server
(the natural-language interface to SparkToro that plugs into Claude, ChatGPT, Cursor, and any other Model Context Protocol client) has been on fire since launch. Customers are using it to build audience reports, explore section data, and reason over their audiences in plain English. That validated something we already suspected: people don’t just want to
see
SparkToro data, they want to
use
it — in the tools they already work in.
Second, the space around us has changed. LLMs, workflow tools like Zapier and n8n, AI agent builders, and modern data warehouses have all made the “pipe data between things” problem an order of magnitude easier, as long as the source has an API. Every workflow, every AI agent, every automation now assumes it can call any tool it needs. Making SparkToro one of those tools was overdue.
We’re not the first product to add an API. But we’re the first to make
behavioral audience data a building block any workflow can call on demand
: where a defined group of people spend time online, what they read, watch, listen to, and engage with.
The API is its own product, not a subscription add-on
One thing to be clear about up front: the SparkToro API is
a separate product from the SparkToro web app
. If you’re a Personal, Business, or Agency subscriber today, you’re getting a hands-on research tool tuned for the individual and team analyst use case. The API is priced and delivered independently.
We chose this split deliberately. App subscribers and API customers are two different kinds of people, using the data in two different ways:
The web app is for research.
A marketer sits down, defines an audience, explores the results, exports a slide, closes the tab. Bounded sessions. A human drives every step. Priced monthly because that’s how work like this gets budgeted.
The API is for infrastructure.
A developer wires SparkToro into a pipeline, a product, or a workflow that runs continuously and at scale. Unbounded volume. It runs whether or not anyone is watching. Priced per call because that’s the only pricing model that works when usage patterns range from “a few reports a month” to “a thousand a day.”
Trying to serve both with a single subscription would compromise both. So the API is standalone: your own credits, your own billing, your own dashboard.
What you can build with it
Here are the three starting points we think are most interesting. These all can be what happens  when this data becomes something you can compose.
1. Land the account: automated new-business pitches for agencies
Let’s say you run a marketing agency and a prospect just filled out your contact form. You’ve got 48 hours to deliver a standout, homerun pitch. Every other agency will show up with “here’s who we are and what we do.” You want to show up with “we already know your customers and how to reach them.”
Feed the prospect’s audience description into the API, pulled from their intake form or revers

---

## Relevance to Stella's Work

This insight is from **Rand Fishkin** at **SparkToro** — a trusted source for SEO and AI search strategy. Apply to:

- Brand Visibility Across Search & AI layer of the Modern Earned Media Measurement Framework
- Client strategy recommendations on AI visibility and GEO
- Supporting evidence for the earned-first proposition

## Related Files

- [Modern_Earned_Media_Measurement_Framework.md](./Modern_Earned_Media_Measurement_Framework.md)
- [RRF_AI_Visibility_Non_Determinism_Trusted_Insight.md](./RRF_AI_Visibility_Non_Determinism_Trusted_Insight.md)
- [AI_Visibility_LLM_Fan_Out_Research_LinkedIn_Post.md](./AI_Visibility_LLM_Fan_Out_Research_LinkedIn_Post.md)
