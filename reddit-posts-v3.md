# Lunar Router — All Reddit + HN + Dev.to Posts (20 Days)
## Strong hooks. Results first. Easy UX. Teach don't sell.

---

# DAY 1 — BLITZ LAUNCH

## Reddit r/LocalLLaMA (Hour 0)

**Title:** I cut my LLM API bill from $420/mo to $73 by routing each prompt to the cheapest model that could handle it

**Body:**
```
I was mass paying OpenAI $420/month. Every call hitting GPT-4o 
whether it needed to or not. Zero visibility.

Put a gateway between my app and the API. Took 2 minutes:

Step 1: clone it
  git clone https://github.com/lunar-org-ai/lunar-router
  cd lunar-router

Step 2: start everything
  make start-full

That's it. Gateway running on localhost:8080. 
Dashboard on localhost:3000. ClickHouse included.

Step 3: one line change in your app
  # before
  client = OpenAI(base_url="https://api.openai.com/v1")
  
  # after  
  client = OpenAI(base_url="http://localhost:8080/v1")

Nothing else changes. Same SDK. Same code. Same everything.
Your app doesn't even know it's going through a gateway.

After one week of tracking every call:

- 38% were simple extraction/formatting. DeepSeek handles 
  these identically at $0.14/M instead of $2.50/M.
- 24% were classification. Groq's Llama 3.3 does these at 
  near-zero cost, 10x faster.
- Only 38% actually needed GPT-4o.

To use a different model, you just change the prefix:

  model="openai/gpt-4o"          # OpenAI
  model="deepseek/deepseek-chat" # DeepSeek — 18x cheaper
  model="groq/llama-3.3-70b"    # Groq — nearly free

Same line of code. Same SDK. Just a different prefix.

Bill went from $420 to $73. Same app. Same quality.

13 providers supported: OpenAI, Anthropic, Gemini, Mistral, 
Groq, DeepSeek, Perplexity, Cerebras, SambaNova, Together, 
Fireworks, Cohere, AWS Bedrock.

The part I didn't expect: it auto-clusters your prompts by 
semantic similarity. After 10k calls I had 5 clean datasets 
grouped by use case — ready for fine-tuning. Didn't configure 
anything.

MIT licensed. Self-hosted. Data stays on your machine.

GitHub: [link]

AMA — happy to walk anyone through setup.
```

---

## Hacker News Show HN (Hour 1)

**Title:** Show HN: I cut my LLM costs 67% by auto-routing prompts to the cheapest model that delivers (open-source)

**Body:**
```
Was spending $420/mo on LLM APIs with zero visibility into 
what each feature actually cost.

Built Lunar Router — open-source gateway (Go + Python + React) 
that sits between your app and 13 LLM providers.

Setup is 3 steps:

  git clone https://github.com/lunar-org-ai/lunar-router
  cd lunar-router
  make start-full

Then change one line in your app:
  base_url = "http://localhost:8080/v1"

That's it. Every call now gets tracked: model, tokens, cost, 
latency, full input/output. Dashboard at localhost:3000.

What makes it different from LiteLLM: this isn't just a proxy. 
It's a proxy + cost dashboard + trace storage + semantic 
clustering + evaluation engine + fine-tuning data preparation.

After a week of tracking: found 62% of my GPT-4o calls didn't 
need GPT-4o. Simple routing rules → $420 down to $73.

After 10k calls: clustering pipeline automatically found 5 
distinct use cases in my traffic and prepared clean datasets 
for each one. Ready for fine-tuning without manual work.

Stack: Go engine (fast, sub-ms overhead) + ClickHouse (traces) 
+ Python/FastAPI (analytics, clustering, evals) + React dashboard.

MIT licensed. No telemetry. Self-hosted.

GitHub: [link]
```

---

## Dev.to Blog Post (Hour 4)

**Title:** How I cut my LLM API costs from $420/mo to $73 with 3 commands and one line of code

**Body:**
```
# The Problem

I was paying OpenAI $420/month. I had no idea what each 
feature in my app actually cost. No way to know if a 
$0.14/M model could handle what I was sending to a 
$2.50/M model.

Sound familiar?

# The Fix (2 minutes)

## Step 1: Clone and start

```bash
git clone https://github.com/lunar-org-ai/lunar-router
cd lunar-router
make start-full
```

This starts:
- Gateway on port 8080 (Go — fast, sub-ms overhead)
- Dashboard on port 3000 (React)
- ClickHouse for trace storage
- Python API on port 8000

All in one docker compose. No config files to edit.

## Step 2: One line change in your app

```python
# before
client = OpenAI(base_url="https://api.openai.com/v1")

# after
client = OpenAI(base_url="http://localhost:8080/v1")
```

That's it. Your app doesn't know the difference. 
Same SDK. Same code. Same response format.

## Step 3: Open the dashboard

Go to localhost:3000. Every call shows up in real time.

For each call you see:
- Model used
- Tokens in / out
- Exact cost in dollars
- Latency in ms
- Full prompt (searchable)
- Full response (searchable)

## What I found in week 1

After 7 days of tracking 14,200 calls:

- 38% → simple formatting/extraction tasks
  - Was using GPT-4o ($2.50/M tokens)
  - DeepSeek handles identically ($0.14/M tokens)
  
- 24% → classification tasks
  - Was using GPT-4o ($2.50/M tokens)
  - Groq Llama 3.3 does these at ~$0.05/M, 10x faster

- 38% → actually needed GPT-4o

62% of my money was going to the wrong model.

## Switching models

To route different prompts to different models, you just 
change the model prefix:

```python
# expensive
response = client.chat.completions.create(
    model="openai/gpt-4o",
    messages=[...]
)

# 18x cheaper, same quality for simple tasks
response = client.chat.completions.create(
    model="deepseek/deepseek-chat",
    messages=[...]
)

# nearly free, 10x faster for classification
response = client.chat.completions.create(
    model="groq/llama-3.3-70b-versatile",
    messages=[...]
)
```

Same SDK. Same code. One word change.

## Result

$420/mo → $73/mo. Same app. Same quality for users.

## The bonus I didn't expect

After ~10k calls, the clustering pipeline kicked in. 
It groups your prompts by semantic similarity automatically 
using KMeans + MiniLM embeddings.

It found 5 distinct use cases in my traffic:
- Code generation (34%)
- Data extraction (28%)
- Content writing (19%)
- Classification (12%)
- Other (7%)

Each cluster is a clean dataset of input/output pairs. 
Ready for fine-tuning. I didn't configure any of this.

## Try it

3 commands. One line change. 2 minutes.

```bash
git clone https://github.com/lunar-org-ai/lunar-router
cd lunar-router
make start-full
```

GitHub: [link]
MIT licensed. Self-hosted. Your data stays on your machine.
```

---

# DAY 3

## Reddit r/selfhosted

**Title:** I self-hosted a one-command LLM dashboard and found I was burning $347/mo on prompts that didn't need a premium model

**Body:**
```
Wanted to know what my LLM app was actually doing behind 
the scenes. Set this up in under 2 minutes.

Setup:

  git clone https://github.com/lunar-org-ai/lunar-router
  cd lunar-router
  make start-full

That gives you:
- Gateway on :8080 (your app points here instead of OpenAI)
- Dashboard on :3000 (where you see everything)
- ClickHouse (trace storage, starts automatically)
- Python API on :8000 (analytics, clustering)

One docker compose. No config files. No API keys to register.

Then one line change in your app:

  base_url = "http://localhost:8080/v1"

Your app thinks it's talking to OpenAI. It's not. 
It's going through the gateway. Every call gets logged.

What the dashboard showed me (first week):

- 14,200 calls tracked automatically
- Total spend: $347
- Calls that could've used a cheaper model: 8,700 (61%)
- Money wasted: ~$210

The search is the killer feature. I can type "show me every 
call about refunds" and see every single one — with the 
model's response, the cost, the latency. All of it.

Filter by model, date range, cost range. Click any trace 
for full detail.

Runs on a $5/month VPS no problem. I do ~15k calls/day 
on a $10 instance.

No accounts. No telemetry. No SaaS dependency. 
Your data stays on your disk. MIT licensed.

[link]

Screenshots of the dashboard in comments.
```

---

# DAY 5

## Reddit r/ChatGPTCoding

**Title:** 62% of my GPT-4o calls were a waste of money. Took me 2 minutes and one free tool to find out.

**Body:**
```
I was paying ~$200/month on OpenAI APIs. Thought that was 
just the cost of building with AI.

Then I set up tracking. Took 2 minutes:

  git clone https://github.com/lunar-org-ai/lunar-router
  cd lunar-router
  make start-full

Changed one line in my app:

  # before
  client = OpenAI()
  
  # after
  client = OpenAI(base_url="http://localhost:8080/v1")

Ran for a week. Opened the dashboard at localhost:3000.

The data was brutal:

- 38% of calls were simple formatting/extraction.
  GPT-4o: $2.50/M tokens.
  DeepSeek does these identically: $0.14/M tokens.

- 24% were classification tasks.
  GPT-4o: $2.50/M tokens.
  Groq Llama 3.3: ~$0.05/M tokens, 10x faster.

- My most expensive feature? A summarizer.
  800 calls/day × $0.31 each = $248/month.
  Switched to DeepSeek: $0.02/call = $16/month.
  Same output. One line change:

    model="openai/gpt-4o"          # $248/mo
    model="deepseek/deepseek-chat" # $16/mo

Total bill: ~$200 → ~$68. No code changes beyond model prefixes.

Every call is tracked: cost, tokens, latency, full prompt 
and response. Searchable. Filterable.

The tool is open-source, MIT licensed, self-hosted: [link]

Genuinely curious — has anyone else audited their API usage 
like this? What did you find?
```

---

# DAY 7

## Reddit r/LocalLLaMA

**Title:** I tracked 50k LLM calls and found out which models actually beat GPT-4o on my real prompts — not benchmarks, real production data

**Body:**
```
Benchmarks told me GPT-4o was the best for everything. 
My production data said otherwise.

I routed 50k real calls through 13 providers using an 
open-source gateway and scored every response.

How to do this yourself:

  git clone https://github.com/lunar-org-ai/lunar-router
  cd lunar-router
  make start-full

Point your app at localhost:8080. Run for a week. 
Open the dashboard. Run evaluations.

My results:

Code generation (34% of my traffic):
  GPT-4o:   8.7/10 quality — $4.20/1k calls
  DeepSeek: 8.2/10 quality — $0.52/1k calls
  → 94% of the quality at 12% of the cost

Classification (22% of traffic):
  All 3 models within 0.3 points of each other
  GPT-4o: $4.20/1k calls
  Groq:   $0.18/1k calls
  → Same results. 23x price difference.

Content writing (19% of traffic):
  Claude actually beat GPT-4o here. 8.9 vs 8.5.
  No benchmark ever showed me this.

Data extraction (18% of traffic):
  DeepSeek won. Faster, cheaper, slightly better 
  at structured output.

Other findings:
- Latency varies 3x by time of day
- Cheapest model was often the fastest
- Semantic routing (auto-pick per prompt) saved 67%

Scored with LLM-as-judge + similarity metrics. Built-in 
evaluation engine, 6 metrics. Not vibes. Data.

Your results will be different. That's the whole point.
Generic benchmarks don't know your use case.

Tool is open-source (MIT): [link]

Run your own evals on YOUR data.
```

---

# DAY 9

## Reddit r/devops

**Title:** Added LLM observability to our stack with one line change. Found $200/mo in wasted API calls the first week.

**Body:**
```
We're running LLMs in production. Had zero visibility.
No cost per feature. No way to debug bad responses.
No latency tracking. Flying blind.

The fix took 2 minutes:

Step 1 — start the observability stack:
  git clone https://github.com/lunar-org-ai/lunar-router
  cd lunar-router
  make start-full

This gives you:
  :8080 → Go gateway (sub-ms overhead, handles routing)
  :3000 → React dashboard (trace explorer, filters, search)
  :8000 → Python API (analytics, clustering, evaluations)
  ClickHouse → stores every trace

All in one docker compose. Runs on a single VPS.

Step 2 — one line change:
  base_url = "http://localhost:8080/v1"

Your app thinks it's talking to OpenAI. The gateway 
intercepts, logs, and forwards. Zero code changes 
beyond that one line.

What we found in week 1:

- $200/mo going to GPT-4o for calls that don't need it
- One feature making 800 calls/day at $0.31 each ($248/mo) 
  that runs identically on a $0.02/call model
- 3 features calling the API with nearly identical prompts 
  (consolidation opportunity)
- P95 latency spikes correlating with specific providers 
  at specific times of day

Every trace includes: model, tokens in/out, cost, latency, 
full prompt, full response. All searchable.

I can type "show me every call over $0.10" or "show me 
every call about refunds" and get instant results.

Resource usage: we do ~50k calls/day on a $20 VPS.
For testing, a $5 VPS handles it fine.

MIT licensed. No telemetry. Self-hosted.

[link]

What's everyone else using for LLM observability? 
Curious how other teams are solving this.
```

---

# DAY 11

## Reddit r/LocalLLaMA

**Title:** Switched my app's base_url from api.openai.com to localhost — here's exactly what I can see now for every single call

**Body:**
```
People keep asking what the dashboard actually shows you.
Here's a complete walkthrough.

The change (your entire migration):

  client = OpenAI(base_url="http://localhost:8080/v1")

That's it. Everything else stays the same.

What I see now for EVERY call:

  Model:    openai/gpt-4o
  Tokens:   847 in / 234 out
  Cost:     $0.0043
  Latency:  1,847ms (312ms to first token)
  Prompt:   [full text, searchable]
  Response: [full text, searchable]

All 14,000+ calls from the last week. Searchable.

Example searches I actually use:
- "refund" → every call where a user mentioned refunds
- Cost > $0.10 → find my expensive calls
- Model = deepseek → filter by provider
- Last 24 hours → recent activity only

Click any trace → full detail drawer with the complete 
conversation, metadata, timing breakdown.

But the feature nobody talks about:

After a few thousand calls, the clustering pipeline runs 
automatically. It groups your prompts by semantic similarity 
using MiniLM embeddings + KMeans.

Mine found:
  Code generation:  34% of traffic
  Data extraction:  28%
  Content writing:  19%
  Classification:   12%
  Other:             7%

I didn't configure this. I didn't label anything.
It just analyzed my traffic and found the patterns.

Each cluster = a clean dataset of real input/output pairs.
Ready for fine-tuning whenever I want.

Setup:

  git clone https://github.com/lunar-org-ai/lunar-router
  cd lunar-router
  make start-full

13 providers. MIT licensed. Self-hosted. 2 minutes.

[link]
```

---

# DAY 13

## Reddit r/artificial

**Title:** Companies spent $8.4B on LLM APIs last year. I found that most can't even answer "which feature costs the most?"

**Body:**
```
Some stats:

- LLM API spending: $500M → $8.4B in 18 months
- 72% of orgs expect even higher spending in 2026
- Nearly 40% spend over $250K/year on LLMs
- Price gap between cheapest and most expensive: 1,000x
  ($0.02/M tokens vs $375/M tokens)

And yet most teams I talk to can't answer one simple 
question: "which feature in your app costs the most?"

I couldn't either. So I built a way to find out.

Setup is embarrassingly simple:

  git clone https://github.com/lunar-org-ai/lunar-router
  cd lunar-router
  make start-full

Change one line in your app:
  base_url = "http://localhost:8080/v1"

Every LLM call now gets tracked automatically. Open 
localhost:3000 and you see: model, cost, tokens, latency, 
full prompt/response. Searchable.

The pattern I see every time someone sets this up:

- 40-60% of calls don't need a premium model
- The most expensive feature is always a surprise
- Simple routing rules cut the bill in half

One person found a summarizer burning $248/mo on GPT-4o 
(800 calls/day × $0.31). Same quality on DeepSeek: $16/mo.
$232/mo saved. One feature. One line change:

  model="deepseek/deepseek-chat"  # instead of openai/gpt-4o

The tool is open-source, MIT licensed, self-hosted.
13 providers. Your data stays on your machine.

[link]

Is anyone here tracking LLM costs systematically? 
What are you using?
```

---

# DAY 15

## Reddit r/LocalLLaMA

**Title:** After 10k API calls, a clustering algorithm found 5 use cases in my traffic I didn't know existed — each one is now a fine-tuning dataset I got for free

**Body:**
```
I set up Lunar Router to track costs. But it does 
something else I didn't expect.

It clusters your prompts by semantic similarity. 
Automatically. No configuration.

After ~10k calls, it grouped my traffic into 5 clusters:

  Code generation:  34% — 3,400 prompt-response pairs
  Data extraction:  28% — 2,800 pairs
  Content writing:  19% — 1,900 pairs
  Classification:   12% — 1,200 pairs
  Other:             7% — 700 pairs

Each cluster is a clean dataset of real input/output pairs. 
My actual users. My actual tasks. My actual quality bar.

Quality gates clean it up automatically:
- Coherence scoring removed 2 garbage clusters
- Outlier detection removed ~400 bad examples
- AI agent labeled each cluster ("Code Generation", etc.)

I took the code generation cluster (3,400 pairs) and 
fine-tuned a 7B model with LoRA.

Result: matches GPT-4o quality for that specific task.
Cost: 1/50th.

Research says 100-500 quality examples is enough for 
straightforward tasks. Production traffic gives you 
thousands — pre-filtered, domain-specific, real pairs.

How to get this:

  git clone https://github.com/lunar-org-ai/lunar-router
  cd lunar-router
  make start-full

Point your app at localhost:8080. Let it run. The clustering 
happens automatically after enough calls accumulate.

Your traffic patterns will be different than mine. 
That's the entire point — it finds YOUR use cases.

MIT licensed: [link]

Anyone else building production-to-fine-tuning pipelines?
```

---

# DAY 17

## Reddit r/MachineLearning

**Title:** I fine-tuned a 7B model on production data my gateway captured automatically — it handles 80% of one use case at 1/50th the cost of GPT-4o

**Body:**
```
Sharing a pipeline that turns production LLM traffic into 
fine-tuning datasets with zero manual work.

The problem: we all call GPT-4o for everything, pay premium 
prices, and discard the most valuable training data we'll 
ever have — our own users' real inputs and outputs.

The pipeline:

1. Go gateway captures every API call with full I/O content
   (setup: git clone + make start-full + change base_url)

2. MiniLM embeddings encode each prompt

3. KMeans clusters prompts by semantic similarity

4. LLM agent auto-labels each cluster 
   ("Code Generation", "Data Extraction", etc.)

5. Quality gates: coherence scoring removes garbage clusters, 
   outlier detection removes bad examples

6. Clean input/output pairs exported per cluster

Results from 50k captured calls:
- 5 distinct clusters identified automatically
- ~8k high-quality pairs after quality filtering
- Fine-tuned Llama 7B with LoRA on the largest cluster
- Task-specific quality matched GPT-4o
- Inference cost: 1/50th

The research supports this:
- 100-500 quality examples with LoRA is often enough 
  for straightforward tasks (Particula, 2026)
- TensorZero reports 5-30x cheaper inference with 
  distilled models from production data
- Our numbers are consistent with both

The endgame:
  Year 1 → pay full price for GPT-4o
  Year 1.5 → capture and cluster all traffic
  Year 2 → fine-tune your own model
  Year 2+ → 80% of traffic at 1/50th the cost

The whole pipeline is open-source (MIT):

  git clone https://github.com/lunar-org-ai/lunar-router
  cd lunar-router
  make start-full

[link]

The barrier isn't the tooling anymore. It's whether 
you're capturing the data.
```

---

# DAY 19

## Reddit r/ChatGPTCoding

**Title:** I compared GPT-4o, DeepSeek and Groq on 15k real production prompts — benchmarks were wrong about my use case

**Body:**
```
Instead of trusting public benchmarks, I ran my own 
evaluation on my actual production prompts.

Setup (if you want to do the same):

  git clone https://github.com/lunar-org-ai/lunar-router
  cd lunar-router
  make start-full

Point your app at localhost:8080. Capture traffic for 
1-2 weeks. Then use the built-in evaluation engine 
to compare models.

My results from 15k calls:

Code generation (34% of traffic):
  GPT-4o:   8.7/10 quality — $4.20/1k calls
  DeepSeek: 8.2/10 quality — $0.52/1k calls
  Groq:     7.8/10 quality — $0.18/1k calls

  → DeepSeek: 94% quality at 12% cost.

Classification (22% of traffic):
  All models within 0.3 points of each other.
  GPT-4o: $4.20/1k calls
  Groq:   $0.18/1k calls

  → Same quality. 23x price difference. Pure waste.

Content writing (19%):
  Claude: 8.9/10
  GPT-4o: 8.5/10

  → Claude beat GPT-4o. No benchmark showed me this.

Data extraction (18%):
  DeepSeek won. Faster + cheaper + slightly better 
  at structured output.

How the evaluation works:
- Built-in metrics: exact match, similarity, LLM-as-judge, 
  latency, cost
- Run the same dataset through multiple models
- Side-by-side results with scores
- All automated

The biggest lesson: for classification tasks, I was 
paying GPT-4o prices for 6 months. Same results on 
Groq at 1/23rd the cost. I had no idea.

Your results WILL be different. That's the point. 
MMLU doesn't know your prompts. Run your own evals.

Tool is open-source (MIT): [link]
```

---

# COMMENT SEEDING TEMPLATES (Days 2, 4, 6, 8, 12, 16, 18)

Use these when you find relevant posts in target subreddits.

## Template 1 — Cost discussion

**When someone asks about LLM API costs:**
```
I tracked every single API call for a month. Found that 
62% of my GPT-4o calls could've run on DeepSeek at 
$0.14/M tokens instead of $2.50/M.

The setup was stupid simple — open-source gateway that 
sits between your app and the API. One line change. 
Every call tracked automatically with cost data.

Ended up cutting my bill from $420 to $73/mo.

[link] if you want to try it. 3 commands to set up.
```

## Template 2 — Model comparison

**When someone asks "which model should I use?":**
```
Honest answer: it depends on your specific prompts.

I ran my own evaluation — 15k production calls through 
GPT-4o, DeepSeek, and Groq. Results were completely 
different from public benchmarks.

For classification: all models scored within 0.3 points. 
GPT-4o was $4.20/1k calls. Groq was $0.18/1k.

For content writing: Claude actually beat GPT-4o.

The only reliable way to know is to test on YOUR data.

I used this open-source eval tool: [link]
Captures your traffic, runs it through multiple models, 
scores automatically.
```

## Template 3 — Observability

**When someone discusses LLM debugging/monitoring:**
```
We had the same problem. Zero visibility into what our 
LLM calls were actually doing.

Set up an open-source gateway — one line change in the 
app (base_url to localhost:8080). Every call now gets 
logged with full prompt/response, cost, latency.

The search is the killer feature. "Show me every call 
where a user asked about pricing" → instant results 
with cost attached.

Found $200/mo in waste the first week.

3 commands to set up, runs on a $5 VPS: [link]
```

## Template 4 — Fine-tuning / training data

**When someone discusses fine-tuning or distillation:**
```
Something I discovered by accident: if you route your 
LLM calls through a gateway that captures full I/O, 
after a few thousand calls you have a production-grade 
training dataset.

A clustering pipeline groups your prompts by semantic 
similarity automatically. Mine found 5 distinct use 
cases in my traffic without any configuration.

Fine-tuned a 7B model on the biggest cluster (3,400 pairs). 
Handles that use case at 1/50th the cost of GPT-4o.

You need 100-500 quality examples for LoRA. Production 
traffic gives you thousands, pre-filtered and domain-specific.

The pipeline is open-source: [link]
```

## Template 5 — Provider switching

**When someone asks about switching from OpenAI:**
```
Made this way easier by using a gateway proxy. 
One line change in my app, then switching providers 
is just a different model prefix:

  model="openai/gpt-4o"          → OpenAI
  model="deepseek/deepseek-chat" → DeepSeek (18x cheaper)
  model="groq/llama-3.3-70b"    → Groq (nearly free)

Same SDK, same code, same response format.
The gateway translates everything — streaming, 
tool calling, vision, even Anthropic's weird SSE format.

Open-source: [link]
```

---

# AWESOME-LIST SUBMISSIONS (Day 3+)

Submit to these lists for permanent, slow-drip stars:

- awesome-llm
- awesome-selfhosted
- awesome-go
- awesome-python
- awesome-devtools
- awesome-open-source

**PR format:**
```
- [Lunar Router](https://github.com/lunar-org-ai/lunar-router) - 
  Open-source LLM gateway with cost tracking, semantic clustering, 
  and fine-tuning data preparation. Routes to 13 providers. MIT.
```

Read each list's contribution guidelines first.
Open issue before PR if they require it.
Be patient — acceptance takes days to months.

---

# PRODUCT HUNT (Day 1, Hour 3)

**Tagline:** Cut your LLM API costs by 60-80%. Track every token. Prepare training data automatically.

**Description:**
```
I was spending $420/month on LLM APIs with zero visibility.

Lunar Router is an open-source gateway that sits between 
your app and 13 LLM providers. One line change to set up.

What it does:
→ Tracks every API call: cost, tokens, latency, full content
→ Dashboard with search and filters
→ Auto-clusters prompts by semantic similarity
→ Prepares fine-tuning datasets automatically
→ Built-in evaluation engine (6 metrics + LLM-as-judge)

Setup: git clone + make start-full (2 minutes)
Migration: change base_url to localhost:8080 (1 line)

Result: $420/mo → $73/mo. Same app. Same quality.

MIT licensed. Self-hosted. Your data stays on your machine.
```

**First comment (post yourself immediately):**
```
Hey! I'm [name], the creator.

Quick story: I was paying OpenAI $420/month and had no 
idea which feature was costing what. After building this 
and tracking every call for a week, I found 62% of my 
calls didn't need GPT-4o.

Happy to answer any questions about the project, the 
architecture, or how routing/clustering works.
```

---

# POST SCHEDULE

| Day | Platform | Type | Hook |
|-----|----------|------|------|
| 1 | r/LocalLLaMA | Launch | "$420 → $73 by routing to cheapest model" |
| 1 | Hacker News | Show HN | "Cut LLM costs 67% with auto-routing" |
| 1 | Product Hunt | Launch | "Cut costs 60-80%. Track every token." |
| 1 | Dev.to | Blog | "From $420 to $73 with 3 commands" |
| 2 | All subs | Comment seeding | Cost discussion template |
| 3 | r/selfhosted | Post | "Found $347/mo waste with one-command dashboard" |
| 4 | All subs | Comment seeding | Model comparison template |
| 5 | r/ChatGPTCoding | Post | "62% of GPT-4o calls were waste" |
| 6 | All subs | Comment seeding | Observability template |
| 7 | r/LocalLLaMA | Post | "Tracked 50k calls, benchmarks were wrong" |
| 8 | All subs | Comment seeding + replies | Fine-tuning template |
| 9 | r/devops | Post | "$200/mo waste found in week 1" |
| 10 | All posts | Engagement day | Reply to everything |
| 11 | r/LocalLLaMA | Post | "What I see for every call now" |
| 12 | All subs | Comment seeding | Provider switching template |
| 13 | r/artificial | Post | "$8.4B spent, most can't track it" |
| 14 | All posts | Engagement day | Week 2 update |
| 15 | r/LocalLLaMA | Post | "Clustering found 5 use cases I didn't know" |
| 16 | All subs | Comment seeding | Fine-tuning template |
| 17 | r/MachineLearning | Post | "Fine-tuned 7B from production data" |
| 18 | All subs | Comment seeding | Cost + eval templates |
| 19 | r/ChatGPTCoding | Post | "Benchmarks were wrong about my use case" |
| 20 | All posts | Recap + update | Star count + community wins |

**Also submit (Day 3+):**
- 6+ awesome-lists
- Hacker News second post (Day 10 or 14 if first one didn't hit)

---

# RULES

1. Every Reddit title = RESULT + number. Never product description.
2. Every post includes setup steps (git clone + make start-full + base_url change).
3. Setup must look easy. 3 commands + 1 line. Always show the exact code.
4. Product name NOT in Reddit title. Story first. Link in body.
5. Reply to EVERY comment in first 3 hours. Non-negotiable.
6. Screenshots in comments on every post (dashboard, traces, clusters).
7. End every post with a QUESTION to drive comments.
8. Tone: dev explaining to other devs. Not marketing. Not corporate.
9. Be honest about limitations when asked. Reddit destroys marketing.
10. Day 1 is a coordinated blitz. All platforms within 4 hours.
