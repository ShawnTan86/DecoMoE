# DecoMoE

**DecoMoE: Decoupling Visual Propagation and Expert Computation for Efficient Multimodal MoE Inference**

DecoMoE is an efficient inference framework for multimodal Mixture-of-Experts (MoE) models. It targets two major sources of redundant computation in multimodal MoE inference: prolonged visual-token propagation and excessive expert computation.

DecoMoE introduces two complementary components:

- **Sample-Adaptive Visual Boundary (SAVB):** dynamically determines when visual tokens can stop propagating through deeper decoder layers.
- **Routing-Calibrated Expert Prefix (RCEP):** calibrates a text-aligned expert order and dynamically retains a compact contiguous expert prefix during inference.

Together, DecoMoE performs structured compression along both the **token** and **expert** dimensions, reducing computation while preserving model performance.

## Overview

[DecoMoE Motivation and Structured Compression](https://github.com/ShawnTan86/DecoMoE/blob/main/DecoMoE_Figure1_v2.pdf)

[DecoMoE Method Pipeline](https://github.com/ShawnTan86/DecoMoE/blob/main/DecoMoE_Method_Pipeline.pdf)

## Code

The implementation and evaluation code for DecoMoE will be released soon.

## Citation

Citation information will be updated after the paper is publicly available.
