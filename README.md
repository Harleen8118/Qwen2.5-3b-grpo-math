# GRPO-Math 🧠➕: Direct Reinforcement Learning for Compact AI Mathematical Reasoning

Teaching compact AI to reason step-by-step — without the crutch of supervised fine-tuning.

![GRPO-Math](https://img.shields.io/badge/Math%20Reasoning-RL--Only-blueviolet)
![Qwen-2.5-3B](https://img.shields.io/badge/Base%20Model-Qwen--2.5%203B-informational)
![Accuracy](https://img.shields.io/badge/GSM8K%20Accuracy-61.33%25-brightgreen)
![LoRA](https://img.shields.io/badge/LoRA-enabled-blue)
![Quantized](https://img.shields.io/badge/4--bit%20Quantization-Yes-success)

---

## 🧩 Overview

**GRPO-Math** introduces a novel, efficient approach to teach compact language models mathematical reasoning using **Reinforcement Learning only**, bypassing traditional **Supervised Fine-Tuning (SFT)**.

We show that intelligent training — not just massive scale — can lead to **precise, logical reasoning** in smaller models like **Qwen-2.5 3B Instruct**. With the help of our custom RL method (**GRPO**) and a smart reward system, our model achieves **61.33% accuracy** on GSM8K — a **+6.67% absolute improvement** over the baseline.

---

## 🔍 Key Contributions

- ✅ **RL-Only Training:** No supervised fine-tuning required. Pure reinforcement learning for better generalization and exploration.
- 🚀 **GRPO Algorithm:** Group Relative Policy Optimization — compares multiple outputs, learns from the best, and improves stability.
- 🎯 **Reward Design:** 
  - High reward for correct final numerical answers.
  - Shaping reward for clear step-by-step reasoning using `<reasoning>` and `<answer>` tags.
- 🧠 **Compact Model, Big Results:** Uses Qwen-2.5 3B Instruct with LoRA and 4-bit quantization.
- 📈 **Performance:** 61.33% on GSM8K — a **12.2% relative improvement** over baseline (54.66%).

---

## 🏗️ Architecture

```text
           ┌────────────────────────────────────┐
           │         Input Math Problem         │
           └────────────────────────────────────┘
                          │
                          ▼
         ┌───────────────────────────────────┐
         │   Qwen-2.5 3B Instruct (LoRA + 4bit)│
         └───────────────────────────────────┘
                          │
                          ▼
         ┌────────────────────────────────────┐
         │   Generate Multiple Candidate Traces │
         └────────────────────────────────────┘
                          │
                          ▼
         ┌────────────────────────────────────┐
         │  GRPO: Select + Learn from Best Outputs │
         └────────────────────────────────────┘
                          │
                          ▼
         ┌────────────────────────────────────┐
         │    Reward Signal: Accuracy + Clarity   │
         └────────────────────────────────────┘
                          │
                          ▼
           Model Learns to Reason Mathematically!

Model	Accuracy on GSM8K
Baseline (Qwen-2.5 3B)	54.66%
GRPO-Math (Ours)	61.33%
