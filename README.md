# GRPO-Math: Direct Reinforcement Learning for Enhanced Mathematical Reasoning in Compact LLMs

## Description

Mathematical reasoning – solving problems step-by-step – is a tough challenge for Artificial Intelligence. Typically, making AI good at this involves multiple complex training stages, including a step called Supervised Fine-Tuning (SFT) where the AI learns to mimic specific answer formats. While helpful, this SFT step can sometimes limit the AI's ability to find creative or truly logical solutions and often requires massive computational resources.

Project GRPO-Math explores a more direct and efficient path. We hypothesized that we could skip the SFT stage entirely and use a smarter training method called Reinforcement Learning (RL) to teach the AI mathematical reasoning directly.

### Key Innovations

**RL-Only Approach**: We bypassed the conventional SFT step, training the AI model directly using RL. This allows the AI more freedom to explore different reasoning pathways towards the correct answer, rather than just copying formats.

**Advanced RL Technique (GRPO)**: We employed Group Relative Policy Optimization (GRPO), a sophisticated RL algorithm designed to effectively train AI models by comparing multiple generated answers and learning from the best ones within that group. This provides more stable and effective learning signals, especially for complex tasks like math.

**Smart Reward System**: We guided the AI's learning with carefully designed rewards. The AI was strongly rewarded for getting the final numerical answer correct. It also received smaller rewards for structuring its reasoning clearly (using simple tags like `<reasoning>` and `<answer>`), making its thought process understandable.

**Efficiency First**: Crucially, this was achieved using a relatively compact AI model (Qwen-2.5 3B Instruct) with only 3 billion parameters. While giants like ChatGPT leverage hundreds of billions of parameters, our research demonstrates that significant reasoning improvements are possible on much smaller, more accessible models through advanced training strategies. We further enhanced efficiency using techniques like LoRA (updating only small parts of the model) and 4-bit quantization (reducing memory usage).

## Results

### Overall Performance

Our GRPO-trained model achieved **61.33% accuracy** on the challenging GSM8K math benchmark, a substantial **+6.67% absolute improvement** (a **12.2% relative jump**) over the baseline model's 54.66%.

| Model | Parameters | Method | GSM8K Accuracy | Improvement |
|-------|------------|--------|----------------|-------------|
| Qwen-2.5 3B (Baseline) | 3B | Standard | 54.66% | - |
| **GRPO-Math** | 3B | RL-Only + GRPO | **61.33%** | **+6.67%** |

### Performance by Problem Type

| Problem Type | Baseline | GRPO-Math | Improvement |
|--------------|----------|-----------|-------------|
| Basic Arithmetic | 78.5% | 84.2% | +5.7% |
| Word Problems | 52.3% | 60.1% | +7.8% |
| Multi-step Reasoning | 41.2% | 49.8% | +8.6% |
| Geometry | 38.9% | 45.3% | +6.4% |

### Training Efficiency

- **Model Size**: 3 billion parameters (compact)
- **Training Time**: 6 hours on 2x A100 GPUs
- **Memory Usage**: ~24GB with 4-bit quantization
- **Convergence**: Stable improvement after 2 epochs

## Impact

This project demonstrates a powerful and potentially more resource-efficient way to build AI capable of precise, complex reasoning. By focusing on smarter training algorithms (like GRPO) and targeted rewards, we can unlock impressive capabilities even in smaller AI models, making advanced AI problem-solving more accessible and potentially leading to more adaptable and logical AI systems in the future. It suggests that sheer size isn't the only path to capable AI; intelligent training design matters significantly.
