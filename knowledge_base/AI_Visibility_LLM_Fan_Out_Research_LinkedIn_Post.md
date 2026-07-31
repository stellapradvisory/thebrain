# AI Visibility Is Not One Thing — LLM Fan-Out Query Research

*Source: LinkedIn post (screenshot saved July 2026)*
*Topic: AI visibility, LLM search behaviour, fan-out queries, ChatGPT vs Claude vs Gemini*

---

One of my biggest bugbears working in the AI Search space is that people talk about 'AI visibility' like it's one thing... when it isn't.

I ran 200 identical prompts (a mix of ecommerce, travel, services and pure informational questions) through Ebb (our proprietary AI visibility tracking tool) to scrape the fan-out queries (both what they were and how many there were) run by ChatGPT, Claude and Gemini before answering. The different approaches between each LLM were super interesting...

**ChatGPT** ran NO searches on 96% of factual questions (things like, 'what causes hay fever?' and 'how does compound interest work?') and answered straight from its memory/training data. But it searched every single time the prompt had a commercial angle (e.g. 'best company for X' and 'where to buy Y').

**Claude** searched on both types of prompt, but ran an average of 1 search, regardless of whether the question was factual, commercial, broad or specific.

**Gemini** searched on almost everything, and the number massively spiked when a prompt combined multiple details ('noise-cancelling wireless earbuds under £100' triggered 18 searches). A less specific version of a similar prompt triggered 2 or 3.

Sooooo... we have three engines, with three different research strategies and none of them match. See why I'm struggling with bland 'AI Visibility'? If you're collapsing that into one number, I really think it's hiding more than it's showing.

We need to be understanding what fan-out queries are and paying proper attention to them, but more than that, we need to know which LLM we're actually reporting on before deciding what to do about it. The tactics aren't the same; chasing Gemini means chasing a model that searches constantly and reacts to specific, stacked detail — so structure and specificity in your content is key. Chasing ChatGPT on a factual, brand-related question is often a different job entirely, since it's not searching at all, it's answering from what it already learned, which means you're trying to shape the training data and the knowledge base, not rank for a live query.

And underneath all of that is the question: which LLM should you even be reporting and focusing on?! Market share still says ChatGPT by a distance, but Gemini's growing fast and closing the gap. If your audience is B2B, Claude's the one punching above its user numbers (smaller by usage volume but disproportionately the one professional and technical audiences reach for).

In the name of transparency, I should flag that this is a single snapshot, with all 200 prompts run at the same time, not repeated. I'll be rechecking weekly to see how consistent these patterns actually are.

---

## Key Data Points from the Research

**Tool used:** Ebb — proprietary AI visibility tracking tool

**Fan-Out Query Distribution (200 sample prompts):**

| LLM | Mean Fan-Out Count | Behaviour |
|---|---|---|
| **ChatGPT** | 2.24 | No search on 96% of factual questions; always searches on commercial prompts |
| **Claude** | 1.10 | Searches on all prompt types, consistently ~1 search regardless of type |
| **Gemini** | 3.21 | Searches on almost everything; spikes dramatically with specific/stacked prompts |

**Prompt types tested:** Commercial (best/where to buy/find) and Informational

---

## Key Takeaways

- **"AI visibility" is not a single metric** — each LLM has a fundamentally different search strategy
- **Collapsing AI visibility into one number hides more than it shows**
- **Gemini strategy:** Structure and specificity in content is key — it reacts to stacked detail
- **ChatGPT strategy (factual/brand):** You're shaping training data and knowledge base, not ranking for a live query
- **Audience matters for LLM choice:** B2B audiences disproportionately use Claude; ChatGPT still leads on market share; Gemini is growing fast
- This is a single snapshot — patterns to be rechecked weekly for consistency

---

## Related Topics in This Knowledge Base

- [Transcript_Splendid_Comms_Followup_Meeting.md](./Transcript_Splendid_Comms_Followup_Meeting.md) — AI visibility strategy discussion with Splendid Comms
- [AMEC_Global_Summit_2026_PRs_Data_Structure_Problem.md](./AMEC_Global_Summit_2026_PRs_Data_Structure_Problem.md) — PR data structure and measurement
