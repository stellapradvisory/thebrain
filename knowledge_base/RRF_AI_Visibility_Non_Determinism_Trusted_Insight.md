# Reciprocal Rank Fusion (RRF) & AI Visibility Non-Determinism

*Source: Trusted industry expert (via LinkedIn post) — included as reference insight to inform Stella's advice where relevant*
*Date added: August 2026*
*Relevance: High — directly supports and extends Stella's Modern Earned Media Measurement Framework*

---

## The Core Argument

> "If your AI visibility reporting is built *entirely* on a handful of sampled responses, you're blindly reporting on noise."

This post makes a critical and well-reasoned argument about the limits of standard AI visibility tracking, and introduces **Reciprocal Rank Fusion (RRF)** as a more stable upstream metric.

---

## The Non-Determinism Problem

The Rand Fishkin / SparkToro research found:

- **Less than 1 in 100 chance** of two runs of the same prompt returning the same list of brands
- **Less than 1 in 1,000 chance** of the same order of brands

This means a single sampled AI response tells you almost nothing on its own. The inconvenient truth: most AI tracking tools give clients a clean citation count, a ranking position, a tidy chart — but a huge chunk of that is noise.

> "It's not that AI is a bit inconsistent — it's actually the case that a single sampled response tells you almost nothing on its own."

The reason this finding was widely shared but then ignored: **admitting the noise doesn't give clients confidence**, and confidence is what agencies are paid to provide.

---

## What RRF Is and Why It Matters

**Reciprocal Rank Fusion (RRF)** is a metric that sits *upstream* of the actual LLM response itself.

Instead of chasing a position in one sampled answer, RRF looks at:
- Your **ranking for the fan-out queries** behind a prompt
- The **underlying SEO-style search signal** that exists before the LLM ever generates a response

| Metric Type | What It Measures | Stability |
|---|---|---|
| LLM response position / citation | Position in one sampled AI answer | Low — highly non-deterministic |
| **RRF Score** | Ranking across the fan-out queries behind a prompt | Higher — based on search rankings, an older and more stable signal |

> "It's not a workaround for the problem the study exposed, but a different layer entirely, sitting further back in the pipeline, where we can be a little bit more confident in what we're measuring — because let's face it, it's an old-school SEO metric!"

The reasoning: a Google or Bing ranking for a fan-out query is plausibly more stable and consistent than a single AI response.

---

## The Ebb Tool Dashboard (Screenshot Evidence)

The screenshot shows an Ebb dashboard for the prompt: **"Where can I buy a good quality cheap bed online?"**

| Metric | Value | Change |
|---|---|---|
| LLM Prominence | 0.00 | 0.00 vs prev run |
| Mentions | 0 | 0 vs prev run |
| Citations | 0 | 0 vs prev run |
| **RRF Score** | **80.0%** | ↓ -8.4% vs prev run |
| Fan-out Queries | 8 | — |

This illustrates the key point: a brand can have **zero LLM mentions or citations** in a sampled response, yet have a strong **RRF Score of 80%** — meaning it ranks well across the 8 fan-out queries that the LLM ran before answering. The upstream signal is strong even when the downstream response doesn't surface the brand.

---

## How This Connects to Stella's Framework

This insight directly supports and extends the **Modern Earned Media Measurement Framework** in two ways:

**1. It validates the framework's distinction between layers**
The framework separates PR Coverage Performance from Brand Visibility Across Search & AI. RRF sits within the Search Visibility layer — specifically as a more robust signal than raw LLM mention/citation counts.

**2. It reinforces Stella's measurement cautions**
Stella's framework already includes the caution: *"A single sampled response tells you almost nothing on its own."* RRF provides a practical answer to that problem — measure the fan-out query rankings, not just the final response.

**3. It connects to Stella's own fan-out research**
Stella's research (see `AI_Visibility_LLM_Fan_Out_Research_LinkedIn_Post.md`) found that different LLMs run wildly different numbers of fan-out queries. RRF aggregates across those queries into a single, more stable score.

---

## How to Use This in Client Advice

When advising clients on AI visibility measurement, use this to:

**Explain why sampled response counts are not enough:**
> "The Rand Fishkin research found less than a 1 in 100 chance of two runs of the same prompt returning the same brand list. A citation count from a handful of sampled responses is directional at best — it's not a reliable absolute."

**Introduce RRF as the more stable upstream signal:**
> "We also look at RRF — Reciprocal Rank Fusion — which measures how well your brand ranks across the fan-out queries that LLMs run before generating a response. This sits upstream of the AI answer itself, in territory closer to traditional search rankings, which are more stable and consistent."

**Set appropriate expectations:**
> "We treat LLM response tracking as directional samples, not absolutes. The RRF score gives us a more robust signal to track over time."

---

## Key Terminology

| Term | Definition |
|---|---|
| **RRF (Reciprocal Rank Fusion)** | A metric measuring brand ranking across the fan-out queries run by an LLM before generating a response. Sits upstream of the final AI answer. |
| **Fan-out queries** | The background searches an LLM runs before answering a prompt. Different LLMs run different numbers (ChatGPT: avg 2.24, Claude: avg 1.10, Gemini: avg 3.21 per Stella's research). |
| **Non-determinism** | The property of LLM responses whereby the same prompt run twice produces different outputs. Makes single-sample tracking unreliable. |
| **LLM Prominence** | A composite score measuring how prominently a brand appears in LLM responses. |

---

## Related Files in This Knowledge Base

- [Modern_Earned_Media_Measurement_Framework.md](./Modern_Earned_Media_Measurement_Framework.md) — Stella's core framework (Brand Visibility Across Search & AI layer)
- [AI_Visibility_LLM_Fan_Out_Research_LinkedIn_Post.md](./AI_Visibility_LLM_Fan_Out_Research_LinkedIn_Post.md) — Stella's own fan-out query research (200 prompts across ChatGPT, Claude, Gemini)
- [AI_Visibility_LLM_Citation_Behaviour_LinkedIn_Post.md](./AI_Visibility_LLM_Citation_Behaviour_LinkedIn_Post.md) — Stella's citation overlap research (36,128 citations)
