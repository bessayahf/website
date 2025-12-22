

---
title: "My LLM Cheatsheet: Concepts, Training, and Best Practices 🧠✨"
date: 2025-12-22
draft: false
description: ""
tags: [
    "LLM",
    "RAG",
  "AI",
  "Machine Learning",
  "Transformers",
  "LLM Engineering",
  "AI Fundamentals"
]

categories: ["Blog"]
---


Large Language Models (LLMs) are everywhere now — chatbots, copilots, search, coding, writing, and reasoning.  
This is my **personal LLM cheatsheet**: concise notes I use to refresh core concepts, training ideas, and practical techniques without diving back into papers or long courses.
<!--more-->


---

## 1. Core Concepts

### What is an LLM?
An **LLM (Large Language Model)** is a neural network trained on massive text corpora to **predict the next token**.  

With enough scale, this simple objective unlocks:
- Text generation
- Reasoning
- Translation
- Summarization
- Q&A

By learning to predict the next word in sentences over billions of examples, LLMs implicitly learn grammar, facts, reasoning patterns, and even some world knowledge.

---

### Tokenization
LLMs don’t read text — they read **tokens**.

Tokenization is how text becomes numeric input. Smaller tokens give flexibility but increase sequence length, while larger tokens are faster but less flexible.

- Text → tokens → numbers
- Tokens can be words, subwords, or characters
- Example:  
  `cryptocurrency → crypto + currency`

**Why it matters:**
- Handles rare / new words
- Controls vocabulary size
- Impacts cost (more tokens = more compute)


---

### Context Window
The **context window** is the model’s working memory. LLMs can only “see” a limited number of tokens at a time. Anything beyond the window is ignored, so long documents may need special handling.

- Measured in tokens (4k, 8k, 32k, 128k…)
- Bigger window = more context, better coherence
- Trade-off: **cost & latency**

---

## 2. Transformer Fundamentals

### Attention (The Secret Sauce)
Attention lets the model decide **what matters most** in a sequence. It allows the model to focus on relevant words regardless of their position, enabling it to capture complex relationships in language.

Instead of reading text left-to-right only, the model:
- Looks at all tokens
- Assigns importance weights
- Builds context dynamically

This is why transformers scale so well.

---

### Self-Attention Formula (High Level)

Self-attention computes a weighted sum of all words in a sequence, where weights measure relevance to each word.

Attention(Q, K, V) = softmax(QKᵀ / √dₖ) · V

- **Q**: What I’m looking for  
- **K**: What I have  
- **V**: The actual information  

---

### Multi-Head Attention
Multi-head attention allows the model to capture multiple perspectives simultaneously, improving understanding of complex sentences.

- Each head focuses on different patterns:
  - Syntax
  - Semantics
  - Long-range dependencies

---

### Positional Encoding
Attention alone has **no sense of order**. Positional encodings give the model information about word order.

Positional encodings inject:
- Token position
- Sequence structure

Without them, word order wouldn’t matter.

---

## 3. Training Paradigms

### Autoregressive vs Masked Models

**Autoregressive (GPT-style)**
- Predict next token
- Best for generation

**Masked (BERT-style)**
- Predict hidden tokens
- Best for understanding & classification

Autoregressive models excel at producing coherent text, while masked models excel at understanding context for tasks like classification or QA.

---

### Pretraining Objectives
- **Next-token prediction**
- **Masked Language Modeling (MLM)**
- **Next Sentence Prediction (NSP)** (less common now)

These objectives define what the model learns during pretraining, shaping whether it is better at generating or understanding text.

---

### Loss Function
**Cross-entropy loss** measures how well the predicted probability distribution matches the true tokens. Lower loss = better predictions.

Most LLMs optimize **cross-entropy loss** by:
- Penalizing wrong token predictions
- Encouraging probability mass on correct tokens


---

## 4. Generation Controls (Very Practical)

### Temperature
Controls randomness:
- `0.2` → deterministic
- `0.7–0.9` → balanced
- `>1.0` → creative / risky

Temperature scales the probability distribution of the next token. Low temperature = safe predictions, high = more diverse output.

---

### Top-K Sampling
- Sample only from the top `K` tokens
- Prevents weird low-probability outputs
- Limits the choice to the most likely tokens, reducing nonsensical text while keeping some randomness.

---

### Top-P (Nucleus) Sampling
- Sample from tokens whose cumulative probability ≥ `p`
- More adaptive than Top-K
- Dynamically chooses a subset of probable tokens so that rare but important words can still be selected.
- Best choice for creative tasks

---

### Beam Search
Beam search explores several paths at once, picking the most probable sequence, which improves fluency but reduces diversity.

- Keeps multiple candidate sequences
- Improves coherence
- Less creative, more “safe”

---

## 5. Fine-Tuning & Efficiency

### Catastrophic Forgetting
When fine-tuning overwrites prior knowledge.

Mitigations:
- Mix old + new data
- Freeze most weights
- Use adapters

Without precautions, fine-tuning can erase the general knowledge learned during pretraining.

---

### PEFT (Parameter-Efficient Fine-Tuning)
PEFT methods let you adapt huge models to new tasks without retraining everything, saving resources.

Popular techniques:
- **LoRA**
- **QLoRA** (LoRA + quantization)

Benefits:
- Lower memory usage
- Cheaper training
- Works on large models with limited hardware

---

### Model Distillation
Train a small model to mimic a large one.

Distillation transfers knowledge from a big model to a smaller one, keeping most capabilities but reducing compute needs.
- Faster
- Cheaper
- Great for edge devices

---

## 6. Retrieval & Reasoning

### RAG (Retrieval-Augmented Generation)
LLMs don’t “know” facts — they **predict text**.

RAG pipeline:
1. Retrieve documents
2. Rank relevance
3. Generate using retrieved context

This:
- Reduces hallucinations
- Improves factual accuracy

By combining LLMs with external knowledge, RAG ensures outputs are grounded in real data rather than just model memorization.

---

### Chain-of-Thought (CoT)
Encourages step-by-step reasoning.

Useful for:
- Math
- Logic
- Multi-step questions

CoT prompts make the model “think out loud,” improving multi-step reasoning performance.

---

### Zero-Shot & Few-Shot Learning
- **Zero-shot**: Just instructions
- **Few-shot**: Add 2–5 examples

Prompt quality often matters more than model size.

LLMs can perform tasks without explicit training, but giving examples usually boosts accuracy.

---

## 7. Scaling Tricks

### Mixture of Experts (MoE)
- Many expert sub-models
- Only a few activate per input

Result:
- Massive models
- Lower inference cost

MoE allows enormous models to exist without making every computation expensive by activating only relevant “experts” for each input.

---

### Adaptive Softmax

It speeds up prediction for frequent words while using fewer resources for rare ones.

- Optimizes large vocabularies
- Faster training
- Lower memory usage

---

## 8. Challenges & Limitations
LLMs are powerful tools but come with technical, ethical, and operational challenges that must be managed.

- High compute cost
- Bias from training data
- Hallucinations
- Limited interpretability
- Privacy & data leakage risks

---

## Final Thoughts

This cheatsheet is **not exhaustive**, but it covers:
- How LLMs work
- How they’re trained
- How to control them
- How to deploy them wisely

Mastering these concepts is often enough to reason effectively about LLM behavior, limitations, and trade-offs in real systems.