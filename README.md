# CLIP Few-Shot Adaptation

**Authors:** Enrico Ferrari, Sebastiano Turco

## Overview

This project explores **efficient strategies to fine-tune CLIP** while preserving its strong zero-shot capabilities. Instead of full retraining, we focus on **Parameter-Efficient Fine-Tuning (PEFT)** methods and introduce a **distillation-based regularization** to improve generalization on unseen classes.

## Methods

We implemented and compared several approaches:

* Fine-tuning projection layers
* Fine-tuning LayerNorm parameters
* **CLIP-Adapter** (lightweight MLP on top of frozen CLIP)

To address overfitting on base classes, we introduce a **distillation loss** that keeps the fine-tuned model aligned with the original CLIP predictions.

We also experimented with an **ensemble strategy**, where multiple models trained on different splits contribute to the final prediction.

## Key Results

* Standard fine-tuning methods tend to **overfit base classes**, hurting performance on novel ones
* **Distillation significantly improves generalization**, slowing the drop in novel accuracy
* Best performance achieved with **KL divergence distillation**
* **CLIP-Adapter + distillation** provides the best trade-off
* Ensemble methods further improve robustness

## Repository Structure

* `notebook.ipynb` – main notebook containing all experiments and results

## Conclusion

Distillation proves to be a simple yet effective way to balance **adaptation vs generalization** in CLIP fine-tuning. Future work could explore combining this approach with **prompt learning techniques**.

