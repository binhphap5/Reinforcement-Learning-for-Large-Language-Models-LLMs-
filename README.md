# 🤖 Reinforcement Learning for Large Language Models (LLMs)

This repository combines multiple research directions that use **Reinforcement Learning (RL)** and instruction fine-tuning to enhance the capabilities and alignment of Large Language Models (LLMs).

---

## 🧠 Structure

```
.
├── LLMs_reasoning/        # Enhancing LLM reasoning with GRPO
│   └── README.md          # Detailed explanation of GRPO-based approach
│
├── LLMs_preference/       # Aligning LLMs to user preferences with PPO & DPO
│   └── README.md          # Detailed explanation of PPO and DPO training
│
├── LLMs_chatbot/          # Train and deploy a chatbot using multi-turn data
│   └── README.md          # Instructions for training & launching chatbot
│
└── README.md              # (You are here) High-level summary of the entire project
```

---

## 1. 🧮 Reasoning with GRPO

Located in: `LLMs_reasoning/`

- Implements **Group Relative Policy Optimization (GRPO)**, a variant of PPO from DeepSeek.
- Targeted at improving LLM performance on **math reasoning tasks** using **Chain-of-Thought** prompting.
- Fine-tunes **Qwen2.5B-Instruct** with **QLoRA** for efficiency.
- Evaluated on a Vietnamese subset of GSM8K (`vi_gsm8k`).

📈 Highlights:
- Achieves **+20% accuracy** improvement over standard instruction tuning on math problems.

➡️ See [`LLMs_reasoning/README.md`](./LLMs_reasoning/README.md) for full details.

---

## 2. 🗣️ Preference Alignment with PPO & DPO

Located in: `LLMs_preference/`

- Uses **PPO** to fine-tune **GPT-2** for generating *negative* student feedback using a reward model (PhoBERT).
- Uses **DPO** to fine-tune **Qwen2.5B-Instruct** directly from user preference pairs without a reward model.
- Demonstrates alignment of model outputs to human-intended choices.

📌 Use Cases:
- Automatically bias outputs toward desired sentiment (e.g., negative feedback).
- Train models to prefer "chosen" over "rejected" completions from instruction datasets.

➡️ See [`LLMs_preference/README.md`](./LLMs_preference/README.md) for full details.

---

## 3. 💬 Vietnamese Multi-turn Chatbot

Located in: `LLMs_chatbot/`

- Fine-tunes **Qwen2.5B-Instruct** on the **[5CD-AI/Vietnamese-Multi-turn-Chat-Alpaca](https://huggingface.co/datasets/5CD-AI/Vietnamese-Multi-turn-Chat-Alpaca)** dataset.
- Implements a complete pipeline: multi-turn instruction fine-tuning → preference-tuning (RLHF with DPO) → inference → deployment.
- Serves the model via **[vLLM](https://github.com/vllm-project/vllm)** backend and **Gradio** frontend for real-time chat interaction.

💡 Highlights:
- Supports multiple turns of conversation with context retention.
- Demonstrates practical chatbot deployment with a Vietnamese LLM.

➡️ See [`LLMs_chatbot/README.md`](./LLMs_chatbot/README.md) for full setup and usage.

---

## 🛠️ Tech Stack

- PyTorch, Hugging Face Transformers
- PEFT (QLoRA) for memory-efficient fine-tuning
- vLLM for fast inference and deployment
- RL Algorithms: GRPO, PPO, DPO

---

## 🚀 Goals

- Understand and implement RL algorithms tailored for LLMs.
- Improve **reasoning** and **alignment** without relying on fully supervised fine-tuning (which always require many high quality instruction datasets).
- Provide reproducible baselines for RL in Vietnamese-language LLMs.