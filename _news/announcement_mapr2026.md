---
layout: post
date: 2026-07-21 10:00:00-0400
inline: true
related_posts: false
---

**Paper accepted at MAPR 2026:** *Retrieval-Augmented Fine-Tuning with Reasoning Distillation for Vietnamese Medical Question Answering*.

The paper proposes a retrieval-augmented fine-tuning (RAFT) pipeline for Vietnamese medical QA that distills Chain-of-Thought rationales from a large language model into LLaMA-3-8B via Low-Rank Adaptation (LoRA). Using oracle-and-distractor contexts built from VMHQA and a fixed oracle-context protocol for retrieval-independent evaluation, the fine-tuned model reaches 93.64% accuracy and 93.56% macro-F1, outperforming both the provided-context baseline and zero-shot LLaMA-3-70B while remaining competitive with prior VMHQA results including fine-tuned GPT-4o.