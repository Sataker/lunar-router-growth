# Lunar Router — All Tweets (20 Days)
## Hook forte. Resultado primeiro. Sempre.

---

# DAY 1 — LAUNCH (8 tweets)

## Thread principal

```
Tweet 1:
I was mass paying $420/month to OpenAI.

Changed one line of code.

Same app. Same quality. Bill: $73.

Here's what happened:
🧵

Tweet 2:
I put a gateway between my app and the API.

base_url = "localhost:8080" instead of "api.openai.com"

Every call now gets tracked automatically.
Model, tokens, cost, latency, full prompt/response.

[screenshot do dashboard]

Tweet 3:
After one week, the data was brutal:

38% → simple formatting ($2.50/M on GPT-4o)
24% → classification ($2.50/M on GPT-4o)
38% → actually needed GPT-4o

62% of my money was going to the wrong model.

[screenshot do cost breakdown]

Tweet 4:
The fix was embarrassingly simple:

Formatting → DeepSeek ($0.14/M)
Classification → Groq ($0.05/M, 10x faster)
Complex → stays on GPT-4o

Same SDK. Same code. Different model prefix.
$420 → $73. Overnight.

Tweet 5:
But here's the part I didn't expect.

After 10k calls, a clustering algorithm found 
5 use cases in my traffic I didn't design for.

Each one is now a clean fine-tuning dataset.
I didn't configure anything. It just happened.

[screenshot dos clusters]

Tweet 6:
The tool is called Lunar Router.

Open-source. MIT. Self-hosted.
3 commands to run. 13 providers.
Your data never leaves your machine.

github.com/lunar-org-ai/lunar-router

⭐ if it saves you money.
```

## Tweets individuais (Day 1)

```
Tweet 7:
$8.4 billion spent on LLM APIs last year.

72% of companies plan to spend more.

Most can't tell you which feature costs the most.

I couldn't either. Until I tracked every call for a week.

Tweet 8:
The gap between LLM providers is now 1,000x.

$0.02/M tokens vs $375/M tokens.

Most apps send everything to the expensive one.

That's not a strategy. That's blindness.
```

---

# DAY 2 (3 tweets)

```
Tweet 1:
24 hours since launch.

[X] GitHub stars.
[X] bugs found by strangers.
[X] bugs fixed.
[X] comments answered.

One person DMed: "found $180/mo in waste in the first 3 days."

Open source is insane.

Tweet 2:
Most asked question yesterday:

"How is this different from LiteLLM?"

LiteLLM routes to 100+ models. Great proxy.

This routes + tracks every cent + stores full traces 
+ clusters your prompts + prepares fine-tuning data.

LiteLLM = pipe.
This = cockpit.

Tweet 3:
Someone found a bug 4 hours after launch.

Fixed in 20 minutes. Shipped.

This would've taken 3 sprints at a SaaS company.

Open-source speed hits different.
```

---

# DAY 3 (3 tweets)

```
Tweet 1:
I self-hosted an LLM dashboard for free.

First thing it showed me: $347/mo going to prompts 
that don't need a premium model.

$5 VPS. One command. Zero code changes.

Found it in day one.

[screenshot]

Tweet 2:
"How much does each feature in my AI app cost?"

Before: "around $300 I think?"

After: "Feature A: $0.04/call. Feature B: $0.31/call. 
Feature C: $0.002/call and shouldn't be on GPT-4o."

That precision pays for itself.

[screenshot]

Tweet 3:
Debugging LLM responses before tracking:

"The AI said something weird"
"Which call?"
"No idea"
"What was the prompt?"
"No idea"

Debugging after:

Click. Full trace. Done.

[screenshot of trace detail]
```

---

# DAY 4 (4 tweets)

```
Tweet 1:
Switching from OpenAI to DeepSeek used to mean 
rewriting half your app.

Now it's one word:

model="openai/gpt-4o"          → $2.50/M
model="deepseek/deepseek-chat" → $0.14/M

Same SDK. Same line. 18x cheaper.

Tweet 2:
Every LLM provider goes down.

If your app is hardcoded to one, your app goes down too.

With fallback routing:
OpenAI fails → auto-retry on Anthropic → user never notices.

Zero downtime. Zero code change.

Tweet 3:
LLM pricing right now (April 2026):

GPT-5.4:      $2.50/M
Claude Sonnet: $3.00/M
Gemini Flash:  $0.30/M
DeepSeek:      $0.14/M

Most apps send everything to the top line.

Smart routing sends each prompt to the cheapest 
that delivers. Saved me 67%.

Tweet 4 (poll):
How much do you spend monthly on LLM APIs?

- Under $50
- $50-200
- $200-1000
- Over $1000
```

---

# DAY 5 (3 tweets)

```
Tweet 1:
My most expensive feature was a summarizer.

800 calls/day. $0.31 each. $248/month. On GPT-4o.

Switched to DeepSeek. $0.02/call. Same output.

From $248 to $16. One feature. One line.

How many features like this are hiding in your app?

Tweet 2:
The first week of tracking your LLM calls 
is always humbling.

"I thought I was spending wisely."

→ 62% wasted on wrong-tier models
→ Most expensive feature was a simple summarizer
→ Could've saved $150/mo from day one

You don't know until you track.

Tweet 3 (poll):
Do you know which feature in your AI app 
costs the most to run?

- Yes, to the cent
- Roughly
- No idea
- Wait, I should track that?
```

---

# DAY 6 (3 tweets)

```
Tweet 1:
The $420 → $73 breakdown:

Before:
GPT-4o for everything: $420/mo

After:
GPT-4o (complex only): $52
DeepSeek (extraction): $14
Groq (classification): $3
Other: $4

Total: $73. Same app. Same quality.

Tweet 2:
Anthropic uses a different streaming format.
Bedrock uses different auth.
Gemini has different tool calling.

Your app shouldn't care about any of that.

One gateway. One format. 13 providers.
The mess stays behind the proxy.

Tweet 3:
Load balancing LLM calls:

strategy="least-cost"     → always cheapest
strategy="lowest-latency" → always fastest
strategy="round-robin"    → distribute evenly
strategy="weighted-random" → custom split

Built-in. No code. Just config.

Pick "least-cost" and watch your bill drop.
```

---

# DAY 7 (3 tweets — thread)

```
Tweet 1:
I tracked 50k LLM calls across 13 providers.

Benchmarks said GPT-4o wins everything.

My production data disagreed.

Real numbers:
🧵

Tweet 2:
Code generation (34% of my traffic):

GPT-4o: 8.7/10 quality — $4.20/1k calls
DeepSeek: 8.2/10 — $0.52/1k calls

94% of the quality. 12% of the cost.

I was overpaying 8x on a third of my traffic.

Tweet 3:
Classification (22% of traffic):

All 3 models within 0.3 points.

GPT-4o: $4.20/1k calls
Groq: $0.18/1k calls

Same quality. 23x price difference.

This is the most wasted money in most LLM apps.

Tweet 4:
Biggest surprise: Claude beat GPT-4o on content writing.

8.9 vs 8.5 on my real prompts.

No benchmark ever showed this.

Production data > leaderboards. Every time.

Tweet 5:
Stop choosing models based on MMLU scores.

MMLU doesn't know your use case.
HumanEval doesn't know your prompts.
Arena ratings don't know your quality bar.

Run your own evals on your own data.

Tool is open-source: [link]
```

---

# DAY 8 (3 tweets)

```
Tweet 1:
Week 1 numbers:

⭐ [number] stars
🐛 [number] bugs reported by strangers
🔧 [number] fixed in <24h
💰 User-reported savings: $[total]

Best DM: "Found $180/mo waste in 3 days."

Building in public > any marketing budget.

Tweet 2:
"Why not just check my OpenAI dashboard?"

Because it only shows OpenAI.
No per-feature cost.
Can't search prompt content.
Can't compare across providers.
Can't export for fine-tuning.

That's like checking one credit card when you have five.

Tweet 3:
Things I learned from 50k tracked LLM calls:

1. Morning calls are 2x faster (US timezone)
2. 70% of "complex" prompts don't need a complex model
3. Cheapest model is often the fastest too
4. Cost per feature varies 50x in the same app

Your app has the same patterns. You just can't see them.
```

---

# DAY 9 (3 tweets)

```
Tweet 1:
Added LLM observability to our stack.

Found $200/mo in waste. First week.

The fix: one line change. 
base_url from api.openai.com to localhost:8080.

Every call tracked. Cost, latency, full content.

Runs on a $5 VPS.

Tweet 2:
One feature was making 800 LLM calls/day.

$0.31 each on GPT-4o. $248/month.

Nobody on the team knew.

Switched to DeepSeek: $0.02/call. $16/month.

We only found this because we tracked every call.

How many features like this are hiding in YOUR app?

Tweet 3 (poll):
How do you track your LLM API costs?

- Custom logging
- Provider dashboard
- I don't
- "We should probably start"
```

---

# DAY 10 (4 tweets)

```
Tweet 1:
10 days. Some real numbers.

Stars: [X]
Issues opened by strangers: [X]
Issues closed: [X]
PRs from community: [X]

One person rewrote the Bedrock integration in a weekend.

I didn't ask. They just shipped it.

Open source is wild.

Tweet 2:
Top 3 feature requests from users:

1. [feature]
2. [feature]
3. [feature]

Shipping #1 this week. PRs welcome for #2 and #3.

This is how products should be built.

Tweet 3:
Hot take: if you're spending >$100/mo on LLM APIs 
and can't answer "which feature costs the most" —

You don't have a cost problem.
You have a visibility problem.

Fix visibility. Cost fixes itself.

Tweet 4:
Someone DMed: "I set up Lunar Router in 4 minutes 
and found $180/mo in waste in the first 3 days."

Stories like this > star counts.

Every time.
```

---

# DAY 11 (3 tweets)

```
Tweet 1:
What I see for every LLM call now:

Model. Tokens in/out. Cost to the cent.
Full prompt. Full response. Latency.

All searchable.

"Show me every call where a user asked about refunds."

Boom. Every one. With cost attached.

[screenshot]

Tweet 2:
I didn't know 35% of my traffic was code generation 
until a clustering algorithm told me.

10k calls → semantic analysis → 5 clusters found.

No config. No labeling. Just patterns I never designed for.

My users found use cases I didn't even plan.

[screenshot]

Tweet 3:
Your app has hidden patterns.

Mine had 5 use cases I never designed.
Users found them. I didn't know until the data showed me.

What would YOUR traffic look like if you could see it?
```

---

# DAY 12 (3 tweets)

```
Tweet 1:
"I only use one provider, I don't need a gateway."

You also don't need to:
- Know cost per feature
- Debug bad responses
- Have fallback when OpenAI goes down
- See latency patterns
- Capture training data

...until you do. And then you wish you'd started months ago.

Tweet 2:
13 providers. One API format. One dashboard.

OpenAI ✓ Anthropic ✓ Gemini ✓ Mistral ✓ 
Groq ✓ DeepSeek ✓ Perplexity ✓ Cerebras ✓ 
SambaNova ✓ Together ✓ Fireworks ✓ Cohere ✓ 
AWS Bedrock ✓

Streaming, tool calling, vision — all translated automatically.

Your app code stays clean.

Tweet 3 (poll):
If you could cut LLM costs by 60% 
with zero code changes — would you?

- Obviously
- Too good to be true
- Already doing this
- Prove it
```

---

# DAY 13 (3 tweets)

```
Tweet 1:
$8.4 billion on LLM APIs last year.

72% of companies spending more this year.

40% spend over $250K/year.

Most can't answer one simple question:
"Which feature costs the most?"

That's not a cost problem. That's flying blind.

Tweet 2:
One team found ONE feature burning $248/mo.

800 calls/day × $0.31 on GPT-4o.

Same quality on DeepSeek: $16/mo.

$232/mo saved. One feature. One routing rule.

Now multiply that by every feature in your app.

Tweet 3:
The LLM pricing gap is now 1,000x.

Bottom: $0.02/M tokens
Top: $375/M tokens

Smart routing picks the right tier per prompt.

60-80% cost reduction. Measured. Not estimated.
```

---

# DAY 14 (4 tweets)

```
Tweet 1:
2 weeks building in public.

⭐ [X] stars
🌍 [X] countries
💰 $[X] in user-reported savings

Biggest learning: posts with real dollar amounts 
get 10x more shares than feature lists.

Nobody cares what the tool does.
Everyone cares what the tool saves.

Tweet 2:
Week 2 lesson:

"I cut my bill from $420 to $73" → 500 likes
"Open-source LLM gateway with 13 providers" → 12 likes

Same product. Different frame.

Results > features. Always.

Tweet 3:
Someone DMed yesterday:

"I found $180/mo in waste in 3 days using your tool."

This is why I wake up in the morning.

Tweet 4 (poll):
What's stopping you from tracking your LLM costs?

- Don't know how
- Seems like too much setup
- Not worth it at my scale
- Already tracking everything
```

---

# DAY 15 (3 tweets)

```
Tweet 1:
Every prompt you send to OpenAI is a fine-tuning example 
you're paying for and throwing away.

After 10k calls through my gateway:

5 use cases found automatically.
3,400 clean training pairs in one cluster.
Fine-tuned a 7B model.
Now handles 80% of that traffic at 2% of the cost.

Your production data IS your training data.

Tweet 2:
What most LLM apps do:

User → API → Response → Gone forever

What mine does:

User → Gateway → Response + trace stored 
→ Clustered by use case → Clean dataset 
→ Fine-tune my own model

Same API call. Completely different outcome.

Tweet 3:
"I don't have enough data to fine-tune."

100 LLM calls/day = 1,400 in 2 weeks.

Clustered and filtered = 200-500 quality pairs per use case.

That's MORE than enough for LoRA.

You have the data. You're just letting it disappear.
```

---

# DAY 16 (3 tweets)

```
Tweet 1:
The clustering blew my mind.

I never told it my app has 5 use cases.

It analyzed 10k prompts with semantic embeddings 
and found them on its own:

Code generation: 34%
Data extraction: 28%
Content writing: 19%
Classification: 12%
Other: 7%

Each cluster = a fine-tuning dataset. No manual work.

[screenshot]

Tweet 2:
Production → Fine-tuning pipeline:

Gateway captures everything → 
Clustering groups by use case →
Quality gates filter garbage →
Export clean pairs →
LoRA fine-tune a 7B model

Result: 5-30x cheaper inference. Comparable quality.

All automatic. All open-source.

Tweet 3 (poll):
Would you fine-tune your own model if the data 
was already organized for you?

- Absolutely
- Maybe, depends on effort
- No, I'll keep paying OpenAI
- Already doing this
```

---

# DAY 17 (3 tweets — thread)

```
Tweet 1:
The endgame for every LLM app:

Year 1: pay $X/month for GPT-4o
Year 1.5: capture and cluster all traffic
Year 2: fine-tune your own model
Year 2+: 80% of traffic at 1/50th the cost

I'm at year 2. Here's the pipeline:
🧵

Tweet 2:
Step 1: every API call goes through a gateway.

Full input/output captured. Cost tracked. Nothing lost.

This is the data pipeline most teams don't have.

The difference between "using AI" and "building an AI moat."

Tweet 3:
Step 2: semantic clustering groups traffic automatically.

10k calls → 5 clean datasets.
No manual labeling. No configuration.

AI agent labels each cluster: "Code Generation", 
"Data Extraction", etc.

Tweet 4:
Step 3: quality gates filter garbage.

Coherence scoring. Outlier detection.

10k raw pairs → 8k clean training examples.

This is what makes production data better 
than synthetic datasets.

Tweet 5:
Step 4: LoRA fine-tune.

100-500 examples is enough for straightforward tasks.
You'll have thousands.

My 7B model matches GPT-4o quality on its specific task.
At 1/50th the cost. In production right now.

The full pipeline is open-source: [link]
```

---

# DAY 18 (3 tweets)

```
Tweet 1:
"Is DeepSeek as good as GPT-4o for my use case?"

I stopped guessing and measured.

15k real prompts. Both models. LLM-as-judge scoring.

Code gen: 8.2 vs 8.7. 94% quality. 12% cost.
Classification: identical. 23x cheaper.

Your results will be different. That's the point.

Run your own evals. Not benchmarks. YOUR data.

Tweet 2:
Benchmarks told me GPT-4o wins at classification.

My production data: 3 models within 0.3 points.

GPT-4o: $4.20/1k calls
Groq: $0.18/1k calls

Same results. 23x price difference.

I was paying 23x more for nothing. For months.

Benchmarks lie. Your data doesn't.

Tweet 3:
7 AI agents running inside Lunar Router:

Cluster labeler → names your prompt groups
Coherence scorer → rates dataset quality
Outlier detector → removes bad examples
Trace scanner → finds hallucinations
Metrics suggester → creates domain-specific evals

All work automatically. All open-source. All configurable.
```

---

# DAY 19 (3 tweets)

```
Tweet 1:
Benchmarks said GPT-4o is the best at content writing.

My data: Claude scored 8.9. GPT-4o scored 8.5.

On MY prompts. With MY quality bar.

No public leaderboard showed this.

The only benchmark that matters runs on YOUR traffic.

Tweet 2:
For classification tasks specifically:

GPT-4o: $4.20/1k calls
DeepSeek: $0.52/1k calls
Groq: $0.18/1k calls

All within 0.3 quality points.

If you're paying GPT-4o prices for classification, 
you're lighting money on fire.

I was. For 6 months. Without knowing.

Tweet 3:
Stop choosing models from leaderboards.

MMLU doesn't know your use case.
HumanEval doesn't know your prompts.
Chatbot Arena doesn't know your quality bar.

Capture your real traffic.
Run your own evals.
Trust your own data.

Free tool to do it: [link]
```

---

# DAY 20 (4 tweets)

```
Tweet 1:
20 days building Lunar Router in public.

⭐ [X] stars
👥 [X] contributors
💰 $[X] user-reported savings
🌍 [X] countries

Biggest learning: "I saved $X" gets shared.
"We support 13 providers" gets ignored.

Results > features. Every single time.

Thank you all.

Tweet 2:
The full stack, one diagram:

Your App
  ↓
Go Gateway (:8080) — 13 providers
  ↓  
ClickHouse — every trace stored
  ↓
Python API (:8000) — clustering + evals
  ↓
React Dashboard (:3000) — see everything

One command: make start-full
$420/mo → $73/mo.
MIT licensed.

[link]

Tweet 3:
What the community shipped in 20 days:

- [feature from PR]
- [feature from PR]
- [feature from PR]

I didn't build these. Strangers on the internet did.

Because it's open-source and their problems became features.

That's the model.

Tweet 4 (poll):
What should we build next?

- More LLM providers
- Better dashboard
- Direct fine-tuning integration
- MCP / Claude Code plugin
```

---

# SUMMARY

**Total: 65 tweets across 20 days**
- 3 threads (Day 1, Day 7, Day 17)
- 7 polls (Day 4, 5, 9, 12, 14, 16, 20)
- 55 standalone tweets

**Hook rules applied to every tweet:**
1. First line = result or pain point, never description
2. Dollar amounts wherever possible
3. Short sentences. White space. Scannable.
4. Product mentioned at the END, never the beginning
5. Screenshots referenced on every data tweet
6. No explaining what the tool IS. Only what it DID.
