---
title: "Choose Your Own Adventure: The Saga of Serving LLM Inference"
aspectRatio: 16/9
theme: eloc
colorSchema: light
fonts:
  sans: Inter
  weights: '400,700'
qr: false
---

# Choose Your Own Adventure

The Saga of Serving LLM Inference

<img src="/vote-qr.png" alt="QR code to vote" style="height: 340px; margin: 24px auto 0;" />

<!--
Before AI, we served our applications on Kubernetes in a distributed way, and we were happy as clams.

We had it all figured out! We knew how to optimize our applications to get answers to our users as quickly as possible.

But now we're running Large Language Models on Kubernetes and serving our users' interactions with those models. And we have a whole new set of concerns in addition to the ones we had before.

That's what we're exploring today. We're going to give you three inference-serving challenges, let you choose how to solve each one, and then put your decisions to the test. Let's do it!

-->

---

# The goal

<p class="hide">Serve models on Kubernetes</p>
<p class="hide">Performant, cost effective, high quality</p>

<!--

The goal of what we're doing today is...
-->

---

# The goal

<p>Serve models on Kubernetes</p>
<p class="hide">Performant, cost effective, high quality</p>

<!--

...running models on Kubernetes in a distributed way and serving requests to the end users...

-->

---

# The goal

<p>Serve models on Kubernetes</p>
<p>Performant, cost effective, high quality</p>

<!--

... in a cost effective, performant, and high quality way. FAST CHEAP GOOD

So first, let's vote.

-->

---
qr: false
---

# Vote

<img src="/vote-qr.png" alt="QR code to vote" style="height: 420px; margin: 0 auto;" />

<!--

We need to hurry up and vote right now, though, so Viktor can start deploying an inference engine that's configured with YOUR CHOICES.

It takes quite a long time to get the inference engines up and running.

If you don’t understand these concepts that you’re voting about, don’t worry. I’ll explain everything later. Use your gut!

And so with that, we'll go to Viktor.

-->

---

# What is an inference engine?

<p class="hide">Runs the model and serves requests</p>
<p class="hide">vLLM</p>

<!--
Okay, so what is an inference engine? 

-->

---

# What is an inference engine?

<p>Runs the model and serves requests</p>
<p class="hide">vLLM</p>

<!--
An INFERENCE ENGINE is the software that runs an LLM and serves requests to it.
-->

---

# What is an inference engine?

<p>Runs the model and serves requests</p>
<p>vLLM</p>

<!--
For the demo we're using vLLM
-->

---

# What is a model?

<!--
First, let's talk about what a model is. A model is basically a prediction engine. Its whole goal is to predict the next token.
-->

---

# Model inputs

<ol>
  <li class="hide">Instructions</li>
  <li class="hide">The conversation so far</li>
</ol>

<!--
As input, the model receives two things.
-->

---

# Model inputs

<ol>
  <li>Instructions</li>
  <li class="hide">The conversation so far</li>
</ol>

<!--
...its instructions

This could be system prompts, tool descriptions, your rules file, saved memories, etc...
-->

---

# Model inputs

<ol>
  <li>Instructions</li>
  <li>The conversation so far</li>
</ol>

<!--
And it also receives every word that's happened in the conversation so far, all the tokens in the conversation.

That includes everything an agent did, like the history of its tool calls and their results, not just the tool descriptions.

So now what does it do with these inputs?
-->

---

# Process

<p class="hide">Math</p>
<p class="hide">Math</p>
<p class="hide">Math</p>
<p class="hide">Math</p>

<!--

-->

---

# Process

<p>Math</p>
<p class="hide">Math</p>
<p class="hide">Math</p>
<p class="hide">Math</p>

<!--

-->

---

# Process

<p>Math</p>
<p>Math</p>
<p class="hide">Math</p>
<p class="hide">Math</p>

<!--

-->

---

# Process

<p>Math</p>
<p>Math</p>
<p>Math</p>
<p class="hide">Math</p>

<!--

-->

---

# Process

<p>Math</p>
<p>Math</p>
<p>Math</p>
<p>Math</p>

<!--
There's a lot of complex math
-->

---

# Model outputs

<p class="hide">A score for every possible next token</p>
<p class="hide">The inference engine picks one</p>

<!--
Then the model outputs the next token!

Actually, that isn't quite right...
-->

---

# Model outputs

<p>A score for every possible next token</p>
<p class="hide">The inference engine picks one</p>

<!--
...strictly speaking, the model scores every possible next token.

A model like the one we're using for this demo will score something like 150,000 possible next tokens.
-->

---

# Model outputs

<p>A score for every possible next token</p>
<p>The inference engine picks one</p>

<!--
Then the inference engine, not the model, chooses the next token from that scored list of tokens.

Okay. But what is the substance of a model?
I kind of glossed over that math part.
-->

---

# A model is made up of two things

<ol>
  <li class="hide">Architecture</li>
  <li class="hide">Weights</li>
</ol>

<!--
First, a model is its...

-->

---

# A model is made up of two things

<ol>
  <li>Architecture</li>
  <li class="hide">Weights</li>
</ol>

<!--
...architecture. 

The architecture of the model answers the question: what math needs to be done at what point of the prediction process?

It defines the strategy for how the model performs all the complex math needed to predict the next token. 

The architecture itself doesn't know anything. So where's the knowledge that a model has?
-->

---

# A model is made up of two things

<ol>
  <li>Architecture</li>
  <li>Weights</li>
</ol>

<!--
That is encoded in its weights. So weights are the mechanism of how that knowledge is saved and used.

A model is made up of billions and billions of weights.

-->

---

# Billions of weights

<p class="hide">Qwen3-8B: 8 billion parameters</p>
<p class="hide">Largest open models: hundreds of billions of parameters</p>
<!--
Models come in all shapes and sizes. We talk about model sizes in terms of parameters.

"Parameter" is another word for weight. 

The model that we're using for this demo is an open-weight model called Qwen3-8B. It has...
-->

---

# Billions of weights

<p>Qwen3-8B: 8 billion parameters</p>
<p class="hide">Largest open models: hundreds of billions of parameters</p>

<!--
...8 BILLION parameters

And the largest open models have...
-->

---

# Billions of weights

<p>Qwen3-8B: 8 billion parameters</p>
<p>Largest open models: hundreds of billions of parameters</p>

<!--
...hundreds of billions of parameters.

That is a lot of weights!!!

Let me show you a weight.
-->

---

# 0.72834164


<!--
That's it. It is just a number. 

So a 300-billion-parameter model has 300 billion of those numbers. 

Billions and billions of these numbers that represent information that was learned during training.

What the model "knows" falls under two umbrellas.
-->

---

# What the weights know

<ol>
  <li class="hide">Language</li>
  <li class="hide">The world</li>
</ol>

<!--

-->

---

# What the weights know

<ol>
  <li>Language</li>
  <li class="hide">The world</li>
</ol>

<!--
It knows everything about human language: grammar, tone, social context, how to mirror the person it's interacting with, and when to be formal, when to be casual, that sort of thing.
-->

---

# What the weights know

<ol>
  <li>Language</li>
  <li>The world</li>
</ol>

<!--
Second, it knows things about the world. It knows most of the fish species of the Great Lakes. It knows what different types of cold medicines cause what side effects. It knows the tourist attractions here in Salt Lake City. It knows how quantum mechanics works.

It's pretty wild that all that information can be packed into a bunch of numbers!

-->

---

# Almost every weight

<p class="hide">For every prediction</p>

<!--
So here's what surprised me when I did my own deep dive into how all this works.

Of those billions and billions of weights, it's not like we can isolate the weights that encode the knowledge about fish, and the cold medicine weights are over here. Everything it knows is distributed across almost all of its weights.

Because of this, the model uses almost all of the weights...
-->

---

# Almost every weight

<p>For every prediction</p>

<!--
...every single time it makes a prediction. Every time it generates a token.

Okay. Now I think we're finally ready to discuss the inference serving decisions that you voted about. Now what was vote one again?
-->

---

# Vote 1

---

# Vote 1
What do you care about more?

- A. Keep the model as precise as it was trained.
- B. Make room for more conversations at the same time.

<!--
You voted about this

Without even understanding how it works, you could probably sniff out that we're asking you to make a quality versus a performance trade-off.

The important thing to know here is that weights take up space in the GPU memory.
-->

---

# Weights take up space in GPU memory

<p class="hide">Billions of numbers</p>

<!--
The model's BILLIONS of weights all live in the GPU memory, where the GPU can access them easily.
-->

---

# Weights take up space in GPU memory

<p>Billions of numbers</p>

<!--
Sure, they're just numbers, but when there are billions and billions of them, they can take up real resources.

But weights aren't the only thing taking up space in GPU memory.

Conversations also live in GPU memory.
-->

---

# Conversations also live in GPU memory

<p class="hide">Computing a token is expensive</p>
<p class="hide">Each new token looks at every token before it</p>
<p class="hide">That work stays in GPU memory</p>

<!--
-->

---

# Conversations also live in GPU memory

<p>Computing a token is expensive</p>
<p class="hide">Each new token looks at every token before it</p>
<p class="hide">That work stays in GPU memory</p>

<!--
Computing a token is expensive. The hardware has to do real work for just one token.
-->

---

# Conversations also live in GPU memory

<p>Computing a token is expensive</p>
<p>Each new token looks at every token before it</p>
<p class="hide">That work stays in GPU memory</p>

<!--
Every time a model does the work of computing a new token, it's looking at all of the other tokens that came before it in the conversation.
-->

---

# Conversations also live in GPU memory

<p>Computing a token is expensive</p>
<p>Each new token looks at every token before it</p>
<p>That work stays in GPU memory</p>

<!--
The work the model already did on those earlier tokens needs to be available in the GPU memory when the model is generating the next token.

And that is what we call the KV cache.
-->

---

# KV cache

<!--
We don't want our compute to have to do it more than once. So we save some of those intermediate calculations in the KV cache, and reuse them for every token after.
-->

---
class: diagram
---

# GPU memory competition

<div class="gpu">
  <div class="gpu-bar">
    <div class="gpu-seg weights" style="width:50%">Weights</div>
    <div class="gpu-seg kv" style="width:32%">KV Cache</div>
    <div class="gpu-seg other" style="width:18%">Overhead</div>
  </div>
</div>

<!--
There's this constant struggle between the amount of GPU memory that the weights take up and the amount of GPU memory that the KV cache takes up.

If you have a model with higher fidelity, then there's less room for conversations. If you have more conversations, there's less room for the model.

But we thought, as humans, we can do better, right? So we decided we're going to figure out a way to make the model weights take up less space in GPU memory.
-->

---

# Quantization

<p class="hide">0.72834164 → 0.75</p>

<!--
This clever strategy is called quantization.

So here's what you do.
-->

---

# Quantization

<p>0.72834164 → 0.75</p>

<!--
Just store each weight at less fidelity.

When you do that with billions and billions of weights, it can drastically reduce your model's memory footprint.

It's a way to make your model take up less space in GPU memory by sacrificing some of its precision.

How much does that affect model performance? Probably not that much, right? It is probably fine.

How much it affects the model depends on how far you quantize. When we quantize, there are different levels of precision.
-->

---

# Levels of precision

<div class="ladder">
<p class="hide"><span class="rung">32-bit</span> → <span class="bits">00111111001110100111010010011001</span> → 0.72834164</p>
<p class="hide"><span class="rung">16-bit</span> → <span class="bits">0011111100111010</span> → 0.7265625</p>
<p class="hide"><span class="rung">8-bit</span> → <span class="bits">00110100</span> → 0.75</p>
<p class="hide"><span class="rung">4-bit</span> → <span class="bits">0001</span> → 0.5</p>
</div>

<!--
Until now, I've been misrepresenting weights a bit because the values are stored in binary, which doesn't translate neatly into decimal digits...
-->

---

# Levels of precision

<div class="ladder">
<p><span class="rung">32-bit</span> → <span class="bits">00111111001110100111010010011001</span> → 0.72834164</p>
<p class="hide"><span class="rung">16-bit</span> → <span class="bits">0011111100111010</span> → 0.7265625</p>
<p class="hide"><span class="rung">8-bit</span> → <span class="bits">00110100</span> → 0.75</p>
<p class="hide"><span class="rung">4-bit</span> → <span class="bits">0001</span> → 0.5</p>
</div>

<!--

Some models are created at 32-bit precision, not all of them.
This looks like this: 32 digits of ones and zeros.

-->

---

# Levels of precision

<div class="ladder">
<p><span class="rung">32-bit</span> → <span class="bits">00111111001110100111010010011001</span> → 0.72834164</p>
<p><span class="rung">16-bit</span> → <span class="bits">0011111100111010</span> → 0.7265625</p>
<p class="hide"><span class="rung">8-bit</span> → <span class="bits">00110100</span> → 0.75</p>
<p class="hide"><span class="rung">4-bit</span> → <span class="bits">0001</span> → 0.5</p>
</div>

<!--
There're 16-bit weights...

Our model Qwen3 by default has 16-bit weights. That's what it's trained at.
-->

---

# Levels of precision

<div class="ladder">
<p><span class="rung">32-bit</span> → <span class="bits">00111111001110100111010010011001</span> → 0.72834164</p>
<p><span class="rung">16-bit</span> → <span class="bits">0011111100111010</span> → 0.7265625</p>
<p><span class="rung">8-bit</span> → <span class="bits">00110100</span> → 0.75</p>
<p class="hide"><span class="rung">4-bit</span> → <span class="bits">0001</span> → 0.5</p>
</div>

<!--
...8-bit weights...

The quantized version of Qwen3 can be 8-bit weights.
-->

---

# Levels of precision

<div class="ladder">
<p><span class="rung">32-bit</span> → <span class="bits">00111111001110100111010010011001</span> → 0.72834164</p>
<p><span class="rung">16-bit</span> → <span class="bits">0011111100111010</span> → 0.7265625</p>
<p><span class="rung">8-bit</span> → <span class="bits">00110100</span> → 0.75</p>
<p><span class="rung">4-bit</span> → <span class="bits">0001</span> → 0.5</p>
</div>

<!--
And finally, there are 4-bit weights. 

Why quantize?
-->

---

# Why quantize?

<ol>
  <li class="hide">Fit the model on one GPU</li>
  <li class="hide">Room for more conversations</li>
  <li class="hide">Fewer bytes to read</li>
</ol>

<!--

-->

---

# Why quantize?

<ol>
  <li>Fit the model on one GPU</li>
  <li class="hide">Room for more conversations</li>
  <li class="hide">Fewer bytes to read</li>
</ol>

<!--
You want to quantize if you want to fit your model on one GPU.
-->

---

# Why quantize?

<ol>
  <li>Fit the model on one GPU</li>
  <li>Room for more conversations</li>
  <li class="hide">Fewer bytes to read</li>
</ol>

<!--
Maybe you want room for more conversations. Less model fidelity makes room for more KV cache.
-->

---

# Why quantize?

<ol>
  <li>Fit the model on one GPU</li>
  <li>Room for more conversations</li>
  <li>Fewer bytes to read</li>
</ol>

<!--
And third of all, each time the model uses the billions of weights to make a prediction, there's less that it has to read from memory. This makes each token calculation faster in the cases where GPU is waiting on memory.

Why might you choose not to quantize?
-->

---

# Why NOT quantize?

<p class="hide">Worse answers</p>

<!--
You can probably guess...
-->

---

# Why NOT quantize?

<p>Worse answers</p>

<!--
It makes the model's answers slightly less in sync with its training. 

To figure out whether to quantize and whether the quality trade-off is worth it, you need good observability, you need to run experiments, and then you need to figure out: does saving costs by quantizing affect our user experience, and how much?

Later, when they're deployed, you'll be able to chat directly with each model being served. Can you tell which one is quantized? Is the quality difference detectable?

Let's drive this home with a diagram.
-->

---
class: diagram
---

# GPU memory

<div class="gpu">
  <div class="gpu-label">Full Precision 16-bit</div>
  <div class="gpu-bar">
    <div class="gpu-seg weights" style="width:68.5%">Weights</div>
    <div class="gpu-seg kv" style="width:14%">KV Cache</div>
    <div class="gpu-seg other" style="width:17.5%">Overhead</div>
  </div>
</div>
<div class="gpu hide">
  <div class="gpu-label">Quantized 8-bit</div>
  <div class="gpu-bar">
    <div class="gpu-seg weights" style="width:39.4%">Weights</div>
    <div class="gpu-seg kv" style="width:42.9%">KV Cache</div>
    <div class="gpu-seg other" style="width:17.7%">Overhead</div>
  </div>
</div>

<!--
Each GPU in our demo has 24 GB of memory

At full 16-bit precision, the model takes up about 15 GB. After accounting for overhead, there's room for about 3 GB of conversations.
-->

---
class: diagram
---

# GPU memory

<div class="gpu">
  <div class="gpu-label">Full Precision 16-bit</div>
  <div class="gpu-bar">
    <div class="gpu-seg weights" style="width:68.5%">Weights</div>
    <div class="gpu-seg kv" style="width:14%">KV Cache</div>
    <div class="gpu-seg other" style="width:17.5%">Overhead</div>
  </div>
</div>
<div class="gpu">
  <div class="gpu-label">Quantized 8-bit</div>
  <div class="gpu-bar">
    <div class="gpu-seg weights" style="width:39.4%">Weights</div>
    <div class="gpu-seg kv" style="width:42.9%">KV Cache</div>
    <div class="gpu-seg other" style="width:17.7%">Overhead</div>
  </div>
</div>

<!--
Quantized, at 8-bit precision, the model takes up about 9 GB. Overhead is the same, so there's about 9.6 GB of conversations.
-->

---

# Revisit Vote 1

What do you care about more?

- A. Keep the model as precise as it was trained. → FULL PRECISION
- B. Make room for more conversations at the same time. → QUANTIZATION

<!--
So back to vote one, we're basically asking you full precision versus quantization.
-->

---

# Deployment Status Check

<p class="hide">Where quantization is set</p>

<!--
Check in with Viktor and the deployment.

He will show us the status of the deployment, plus where the model precision is set in the deployment configuration.
-->

---

# Vote 2

---

# Vote 2: What does it mean?

You have two GPUs. How do you use them?

- A. One model split across both GPUs.
- B. Two independent copies of the model, one per GPU.

<!--
So the next thing to talk about is vote two:

First let's talk about replication.
-->

---

# Replication

<!--
Replication is when an entire copy of a model is on each GPU, and each GPU can serve requests independently.

What does that look like?
-->

---
class: diagram
---

# No quantization, no sharding

<div class="flow"><div class="node">Requests</div><div class="arrow">↓</div><div class="node">Router</div><div class="arrow">↙ ↘</div><div class="lane-row"><div class="lane"><div class="node">Engine 1</div><div class="arrow">↓</div><div class="gpu-box"><div class="gpu-title">GPU 1</div><div class="gpu-bar"><div class="gpu-seg weights" style="width:68.5%">Weights</div><div class="gpu-seg kv" style="width:13.9%">KV Cache</div><div class="gpu-seg other" style="width:17.6%">Overhead</div></div></div></div><div class="lane"><div class="node">Engine 2</div><div class="arrow">↓</div><div class="gpu-box"><div class="gpu-title">GPU 2</div><div class="gpu-bar"><div class="gpu-seg weights" style="width:68.5%">Weights</div><div class="gpu-seg kv" style="width:13.9%">KV Cache</div><div class="gpu-seg other" style="width:17.6%">Overhead</div></div></div></div></div></div>

<!--
With replication, we have a complete model on each GPU.

There are two separate inference engines, and then there's a router in place that helps know which request goes to which engine.

**NO QUANTIZATION, NO SHARDING**

- **Precision:** 16-bit
- **Weights per GPU:** ~15 GB (a whole copy)
- **KV cache room:** ~3 GB per GPU
- **Conversations that fit:** ~3 per copy, ~6 total
- **GPUs talk:** never
-->

---
class: diagram
---

# Yes quantization, no sharding

<div class="flow"><div class="node">Requests</div><div class="arrow">↓</div><div class="node">Router</div><div class="arrow">↙ ↘</div><div class="lane-row"><div class="lane"><div class="node">Engine 1</div><div class="arrow">↓</div><div class="gpu-box"><div class="gpu-title">GPU 1</div><div class="gpu-bar"><div class="gpu-seg weights" style="width:39.4%">Weights</div><div class="gpu-seg kv" style="width:42.9%">KV Cache</div><div class="gpu-seg other" style="width:17.7%">Overhead</div></div></div></div><div class="lane"><div class="node">Engine 2</div><div class="arrow">↓</div><div class="gpu-box"><div class="gpu-title">GPU 2</div><div class="gpu-bar"><div class="gpu-seg weights" style="width:39.4%">Weights</div><div class="gpu-seg kv" style="width:42.9%">KV Cache</div><div class="gpu-seg other" style="width:17.7%">Overhead</div></div></div></div></div></div>

<!--
With replication, we have a complete model on each GPU.

There are two separate inference engines, and then there's a router in place that helps know which request goes to which engine.

**YES QUANTIZATION, NO SHARDING**

- **Precision:** 8-bit
- **Weights per GPU:** ~9 GB (a whole copy)
- **KV cache room:** ~9.6 GB per GPU
- **Conversations that fit:** ~8.5 per copy, ~17 total
- **GPUs talk:** never
-->

---

# Sharding

<!--
Sharding is when one copy of a model is split across multiple GPUs, and those GPUs work together to serve each request.

That looks like this...
-->

---
class: diagram
---

# No quantization, yes sharding

<div class="flow"><div class="node">Requests</div><div class="arrow">↓</div><div class="node">One engine</div><div class="arrow">↓</div><div class="shard-group"><div class="gpu-box"><div class="gpu-title">GPU 1</div><div class="gpu-bar"><div class="gpu-seg weights" style="width:34.2%">Weights</div><div class="gpu-seg kv" style="width:45.6%">KV Cache</div><div class="gpu-seg other" style="width:20.2%">Overhead</div></div></div><div class="link">⇄</div><div class="gpu-box"><div class="gpu-title">GPU 2</div><div class="gpu-bar"><div class="gpu-seg weights" style="width:34.2%">Weights</div><div class="gpu-seg kv" style="width:45.6%">KV Cache</div><div class="gpu-seg other" style="width:20.2%">Overhead</div></div></div></div></div>

<!--
When you split the model across multiple GPUs, just some of the model's weights are stored in the memory of each individual GPU. Each conversation's KV cache gets split between GPUs too.

We have only one engine, as opposed to having two separate inference engines running.

**NO QUANTIZATION, YES SHARDING**

- **Precision:** 16-bit
- **Weights per GPU:** ~7.7 GB (half)
- **KV cache room:** ~10 GB per GPU, one shared pool
- **Conversations that fit:** ~18 total
- **GPUs talk:** on every token
-->

---
class: diagram
---

# Yes quantization, yes sharding

<div class="flow"><div class="node">Requests</div><div class="arrow">↓</div><div class="node">One engine</div><div class="arrow">↓</div><div class="shard-group"><div class="gpu-box"><div class="gpu-title">GPU 1</div><div class="gpu-bar"><div class="gpu-seg weights" style="width:19.7%">Weights</div><div class="gpu-seg kv" style="width:60.2%">KV Cache</div><div class="gpu-seg other" style="width:20.1%">Overhead</div></div></div><div class="link">⇄</div><div class="gpu-box"><div class="gpu-title">GPU 2</div><div class="gpu-bar"><div class="gpu-seg weights" style="width:19.7%">Weights</div><div class="gpu-seg kv" style="width:60.2%">KV Cache</div><div class="gpu-seg other" style="width:20.1%">Overhead</div></div></div></div></div>

<!--
When you split the model across multiple GPUs, just some of the model's weights are stored in the memory of each individual GPU. Each conversation's KV cache gets split between GPUs too.

We have only one engine, as opposed to having two separate inference engines running.

**YES QUANTIZATION, YES SHARDING**

- **Precision:** 8-bit
- **Weights per GPU:** ~4.4 GB (half)
- **KV cache room:** ~13.5 GB per GPU, one shared pool
- **Conversations that fit:** ~24 total
- **GPUs talk:** on every token
-->

---

# Replication vs. sharding

<table class="compare">
<tr><th class="hide"></th><th class="hide">Replication</th><th class="hide">Sharding</th></tr>
<tr><td class="row-label hide">Weights</td><td class="hide">Whole model on every GPU</td><td class="hide">Half per GPU, more room for KV cache</td></tr>
<tr><td class="row-label hide">KV cache</td><td class="hide">A separate cache per copy</td><td class="hide">One shared cache, split per GPU</td></tr>
<tr><td class="row-label hide">GPU communication</td><td class="hide">None: GPUs work alone</td><td class="hide">On every token</td></tr>
<tr><td class="row-label hide">Model size</td><td class="hide">Must fit on one GPU</td><td class="hide">Can span GPUs</td></tr>
</table>

<!--
When we're comparing the two, we can look across four dimensions:
-->

---

# Replication vs. sharding

<table class="compare">
<tr><th></th><th>Replication</th><th>Sharding</th></tr>
<tr><td class="row-label">Weights</td><td class="hide">Whole model on every GPU</td><td class="hide">Half per GPU, more room for KV cache</td></tr>
<tr><td class="row-label">KV cache</td><td class="hide">A separate cache per copy</td><td class="hide">One shared cache, split per GPU</td></tr>
<tr><td class="row-label">GPU communication</td><td class="hide">None: GPUs work alone</td><td class="hide">On every token</td></tr>
<tr><td class="row-label">Model size</td><td class="hide">Must fit on one GPU</td><td class="hide">Can span GPUs</td></tr>
</table>

<!--
...weights, KV cache, GPU communication, and model size.
-->

---

# Replication vs. sharding

<table class="compare">
<tr><th></th><th>Replication</th><th>Sharding</th></tr>
<tr><td class="row-label">Weights</td><td>Whole model on every GPU</td><td class="hide">Half per GPU, more room for KV cache</td></tr>
<tr><td class="row-label">KV cache</td><td class="hide">A separate cache per copy</td><td class="hide">One shared cache, split per GPU</td></tr>
<tr><td class="row-label">GPU communication</td><td class="hide">None: GPUs work alone</td><td class="hide">On every token</td></tr>
<tr><td class="row-label">Model size</td><td class="hide">Must fit on one GPU</td><td class="hide">Can span GPUs</td></tr>
</table>

<!--
With replication, you have to store the full set of model weights in each GPU's memory, so there's less room for KV cache.
-->

---

# Replication vs. sharding

<table class="compare">
<tr><th></th><th>Replication</th><th>Sharding</th></tr>
<tr><td class="row-label">Weights</td><td>Whole model on every GPU</td><td>Half per GPU, more room for KV cache</td></tr>
<tr><td class="row-label">KV cache</td><td class="hide">A separate cache per copy</td><td class="hide">One shared cache, split per GPU</td></tr>
<tr><td class="row-label">GPU communication</td><td class="hide">None: GPUs work alone</td><td class="hide">On every token</td></tr>
<tr><td class="row-label">Model size</td><td class="hide">Must fit on one GPU</td><td class="hide">Can span GPUs</td></tr>
</table>

<!--
With sharding, the model's weights are split across the GPUs, leaving more room on each GPU for KV cache.
-->

---

# Replication vs. sharding

<table class="compare">
<tr><th></th><th>Replication</th><th>Sharding</th></tr>
<tr><td class="row-label">Weights</td><td>Whole model on every GPU</td><td>Half per GPU, more room for KV cache</td></tr>
<tr><td class="row-label">KV cache</td><td>A separate cache per copy</td><td class="hide">One shared cache, split per GPU</td></tr>
<tr><td class="row-label">GPU communication</td><td class="hide">None: GPUs work alone</td><td class="hide">On every token</td></tr>
<tr><td class="row-label">Model size</td><td class="hide">Must fit on one GPU</td><td class="hide">Can span GPUs</td></tr>
</table>

<!--
With replication, each copy keeps its own KV cache.
-->

---

# Replication vs. sharding

<table class="compare">
<tr><th></th><th>Replication</th><th>Sharding</th></tr>
<tr><td class="row-label">Weights</td><td>Whole model on every GPU</td><td>Half per GPU, more room for KV cache</td></tr>
<tr><td class="row-label">KV cache</td><td>A separate cache per copy</td><td>One shared cache, split per GPU</td></tr>
<tr><td class="row-label">GPU communication</td><td class="hide">None: GPUs work alone</td><td class="hide">On every token</td></tr>
<tr><td class="row-label">Model size</td><td class="hide">Must fit on one GPU</td><td class="hide">Can span GPUs</td></tr>
</table>

<!--
With sharding, there's one KV cache, split across both GPUs.
-->

---

# Replication vs. sharding

<table class="compare">
<tr><th></th><th>Replication</th><th>Sharding</th></tr>
<tr><td class="row-label">Weights</td><td>Whole model on every GPU</td><td>Half per GPU, more room for KV cache</td></tr>
<tr><td class="row-label">KV cache</td><td>A separate cache per copy</td><td>One shared cache, split per GPU</td></tr>
<tr><td class="row-label">GPU communication</td><td>None: GPUs work alone</td><td class="hide">On every token</td></tr>
<tr><td class="row-label">Model size</td><td class="hide">Must fit on one GPU</td><td class="hide">Can span GPUs</td></tr>
</table>

<!--
With replication, the GPUs don't need to communicate with one another. Each GPU can process its own requests independently.
-->

---

# Replication vs. sharding

<table class="compare">
<tr><th></th><th>Replication</th><th>Sharding</th></tr>
<tr><td class="row-label">Weights</td><td>Whole model on every GPU</td><td>Half per GPU, more room for KV cache</td></tr>
<tr><td class="row-label">KV cache</td><td>A separate cache per copy</td><td>One shared cache, split per GPU</td></tr>
<tr><td class="row-label">GPU communication</td><td>None: GPUs work alone</td><td>On every token</td></tr>
<tr><td class="row-label">Model size</td><td class="hide">Must fit on one GPU</td><td class="hide">Can span GPUs</td></tr>
</table>

<!--
With sharding, GPUs must communicate on every token, and that communication introduces overhead.

And finally, model size.
-->

---

# Replication vs. sharding

<table class="compare">
<tr><th></th><th>Replication</th><th>Sharding</th></tr>
<tr><td class="row-label">Weights</td><td>Whole model on every GPU</td><td>Half per GPU, more room for KV cache</td></tr>
<tr><td class="row-label">KV cache</td><td>A separate cache per copy</td><td>One shared cache, split per GPU</td></tr>
<tr><td class="row-label">GPU communication</td><td>None: GPUs work alone</td><td>On every token</td></tr>
<tr><td class="row-label">Model size</td><td>Must fit on one GPU</td><td class="hide">Can span GPUs</td></tr>
</table>

<!--
With replication, each GPU must fit the complete model plus its KV cache. When you're serving a large model, sometimes this just isn't possible.
-->

---

# Replication vs. sharding

<table class="compare">
<tr><th></th><th>Replication</th><th>Sharding</th></tr>
<tr><td class="row-label">Weights</td><td>Whole model on every GPU</td><td>Half per GPU, more room for KV cache</td></tr>
<tr><td class="row-label">KV cache</td><td>A separate cache per copy</td><td>One shared cache, split per GPU</td></tr>
<tr><td class="row-label">GPU communication</td><td>None: GPUs work alone</td><td>On every token</td></tr>
<tr><td class="row-label">Model size</td><td>Must fit on one GPU</td><td>Can span GPUs</td></tr>
</table>

<!--
With sharding, we can serve a large model when splitting it across GPUs is the only way we can do it.
-->

---

# Replication vs Sharding

<p class="hide">How many requests at once?</p>
<p class="hide">How are your GPUs connected?</p>

<!--
But which one is better? Replication or Sharding?

It depends.

To help figure it out, ask yourself some questions. The first one is...
-->

---

# Replication vs Sharding

<p>How many requests at once?</p>
<p class="hide">How are your GPUs connected?</p>

<!--
...How many requests are you serving at once?

If it's a lot, and each copy has plenty of room for conversations, replication is often better. Two copies serve requests at the same time, without waiting on each other.

If it's only a few, sharding can be better.

Now ask yourself...
-->

---

# Replication vs Sharding

<p>How many requests at once?</p>
<p>How are your GPUs connected?</p>

<!--
...How are your GPUs connected?

Sharding works best when your GPUs can talk to each other fast, because they need to talk on every single token. GPUs in the same server with a fast link between them are great for sharding.
-->

---

# Revisit Vote 2

You have two GPUs. How do you use them?

- A. One model split across both GPUs. → SHARDING
- B. Two independent copies of the model, one per GPU. → REPLICATION

<!--
You voted about this. Sharding vs replication.
-->

---

# Deployment Status Check

<p class="hide">Where replication or sharding is set</p>

<!--
Check in with Viktor and the deployment.

He will show us where he configured replication and/or sharding.
-->

---

# Vote 3

---

# Vote 3: What does it mean?

How should the model write its answers?

- A. One word at a time, the normal way.
- B. Guess ahead from what's already in the conversation, and let the model check.

<!--
Underneath this is a concept called speculative decoding.

But to get there, first we need to discuss...
-->

---

# Two phases of inference serving

<p class="hide">Prefill</p>
<p class="hide">Decode</p>

<!--
...the two phases of inference serving. 

To serve a request, there are two steps…
-->

---

# Two phases of inference serving

<p>Prefill</p>
<p class="hide">Decode</p>

<!--
…The first phase is prefill. In this phase, the model processes all of the previously unseen context of this request.

As I mentioned earlier, that might be system prompts, tool descriptions, or your rules file, in addition to the conversation up until this point.

Then we have step 2. This step is called… 
-->

---

# Two phases of inference serving

<p>Prefill</p>
<p>Decode</p>

<!--
Decode is the phase where the model generates a response.

We separate these two phases because they represent two different types of work for the model.

What's unique about prefill?
-->

---

# Prefill

<p class="hide">Processes all the new input</p>
<p class="hide">Every token already exists</p>
<p class="hide">Processed in parallel</p>
<p class="hide">Bottleneck: compute</p>

<!--

-->

---

# Prefill

<p>Processes all the new input</p>
<p class="hide">Every token already exists</p>
<p class="hide">Processed in parallel</p>
<p class="hide">Bottleneck: compute</p>

<!--
The model could be getting a lot of new context all at once, and it needs to process that context before it can generate a token for the user.
-->

---

# Prefill

<p>Processes all the new input</p>
<p>Every token already exists</p>
<p class="hide">Processed in parallel</p>
<p class="hide">Bottleneck: compute</p>

<!--
But these tokens all already exist. They are available to the model immediately.
-->

---

# Prefill

<p>Processes all the new input</p>
<p>Every token already exists</p>
<p>Processed in parallel</p>
<p class="hide">Bottleneck: compute</p>

<!--
The model processes all of these tokens in parallel. 

This means that every time it reads the weights from memory, it can process many tokens at once. Often thousands.
-->

---

# Prefill

<p>Processes all the new input</p>
<p>Every token already exists</p>
<p>Processed in parallel</p>
<p>Bottleneck: compute</p>

<!--
If the prefill step isn't going as fast as we'd like it to, the limiting factor is usually COMPUTE.

Now let's look closer at decode.
-->

---

# Decode

<p class="hide">Generates new tokens</p>
<p class="hide">One at a time</p>
<p class="hide">Bottleneck: memory bandwidth</p>

<!--

-->

---

# Decode

<p>Generates new tokens</p>
<p class="hide">One at a time</p>
<p class="hide">Bottleneck: memory bandwidth</p>

<!--
Decoding is about generating a response, and the way the model knows how to do this is one token at a time.

The decode phase is stubbornly sequential.
-->

---

# Decode

<p>Generates new tokens</p>
<p>One at a time</p>
<p class="hide">Bottleneck: memory bandwidth</p>

<!--
As a reminder, when a model does a single token generation, that model uses almost all of its billions of weights every time it generates a single token.

What's going on when the decode phase isn't going as fast as you wanted to? 
-->

---

# Decode

<p>Generates new tokens</p>
<p>One at a time</p>
<p>Bottleneck: memory bandwidth</p>

<!--
The limiting factor is often memory bandwidth.

The model has the power to do these computations just fine, but it can't read all of those weights from memory over and over again fast enough. It's that step of reading the weights it needs at the moment that slows things down.

So the question becomes: Is there a way to generate more than just one token each time we run through all those weights and do all that math?

And that's where speculative decoding comes in.
-->

---

# Speculative decoding

<ol>
  <li class="hide">Guess several tokens ahead</li>
  <li class="hide">Check all the guesses in one trip</li>
</ol>

<!--
Speculative decoding is a collaboration between the inference engine and the model. Here's how it works.
-->

---

# Speculative decoding

<ol>
  <li>Guess several tokens ahead</li>
  <li class="hide">Check all the guesses in one trip</li>
</ol>

<!--
The inference engine coordinates a process that drafts, say, four tokens ahead. A popular way to get these four draft tokens is to use a smaller model to generate them.

Our demo doesn't use a smaller model. It guesses ahead by using a deterministic process that looks for patterns in the text that's already happened in this conversation.

The inference engine gives all four of these draft tokens to the model all at once.
-->

---

# Speculative decoding

<ol>
  <li>Guess several tokens ahead</li>
  <li>Check all the guesses in one trip</li>
</ol>

<!--
Then the model can process these four draft tokens in just one pass through the weights.

We're essentially trading some extra compute (some work of computing 4 tokens' worth of predictions) in exchange for using less memory bandwidth (fewer reads of the weights).

It's a bit risky because those guesses can be wrong. You're not going to get 4 tokens for the price of 1 every time. 
 
But there often is a memory bandwidth gain, enough to make it worthwhile if memory bandwidth is giving you trouble.
-->

---

# Regular vs Speculative Decoding

<p class="hide">How busy is your GPU?</p>

<!--
So then why is it even a question? Why wouldn't we just always do speculative decoding?
-->

---

# Regular vs Speculative Decoding

<p>How busy is your GPU?</p>

<!--
How busy is your GPU? If you're running high load, you might not have a lot of compute to spare, so you don't want to spend that extra compute to guess ahead and get it wrong sometimes. 

That trade-off of compute for memory bandwidth may not be worth it. Under heavy load the speedup shrinks, and it can even turn into a slowdown.
-->

---

# Revisit Vote 3

How should the model write its answers?

- A. One word at a time, the normal way. → DECODE AS USUAL
- B. Guess ahead from what's already in the conversation, and let the model check. → USE SPECULATIVE DECODING

<!--
So there it is, speculative decoding.
-->

---

# Deployment Status Check

<p class="hide">Where speculative decoding is set</p>

<!--
Check in with Viktor and the deployment.

He will show us where he configured speculative decoding.
-->

---

# The results

<p class="hide">Your pick vs. its opposite</p>

<!--
Viktor talks about how quantization, sharding versus replication, and speculative decoding affect the actual performance of our two deployments.
-->

---
qr: false
---

# So many links!

<img src="/links-qr.png" alt="QR code to the talk links page" style="height: 420px; margin: 0 auto;" />

<!--
This QR code goes to whitneylee.com/KubeConNA2026, with links to:

- Session feedback form
- Demo: github.com/vfarcic/inference-vote
- Slides: wiggitywhitney.github.io/cyoa-kubecon-na-2026
- ModelPlane: github.com/modelplaneai/modelplane
- Datadog: datadoghq.com
- Whitney Lee: whitneylee.com and YouTube
- Viktor Farcic: devopstoolkit.live and YouTube
-->
