# PR-HalluX: Perception–Reasoning Hallucination XAI for MLLMs

<p align="right">
<b>English</b> | <a href="./README_ko.md">한국어</a>
</p>

## Overview

PR-HalluX is a small codebase for experiments on hallucinations in multimodal / vision-language models (MLLMs).

- separate **perception-related** and **reasoning-related** errors,
- extract internal signals (attention / features),
- implement simple evaluation and mitigation code.

## Directory layout

```text
src/
  models/        # MLLM wrapper (load model, generate)
  attribution/   # attention hooks, perception/reasoning scores
  policy/        # simple stage-aware mitigation policies
  utils/         # I/O, visualization, logging helpers
notebooks/       # Jupyter notebooks for experiments
configs/         # experiment configs
data/            # datasets (raw / processed, ignored by git)
```

## Installation

```bash
conda create -n mllm-hallu-pr-xai python=3.11
conda activate mllm-hallu-pr-xai

pip install torch torchvision --index-url https://download.pytorch.org/whl/cu121
pip install transformers datasets accelerate pillow matplotlib
```