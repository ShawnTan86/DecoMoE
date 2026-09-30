# DecoMoE

**DecoMoE: Decoupling Visual Propagation and Expert Computation for Efficient Multimodal MoE Inference**

DecoMoE is an efficient inference framework for multimodal Mixture-of-Experts (MoE) models. It jointly reduces redundant computation along the visual-token and expert dimensions through sample-adaptive visual propagation and structured expert-prefix execution.

### Figure 1
![Figure 1](https://github.com/ShawnTan86/DecoMoE/blob/main/DecoMoE_Figure1_v2.png)

**Description:** (a) The per-layer latency profile illustrates the computation composition across one prefill pass and one decoding pass, shown as two consecutive 48-layer segments. Attention and expert-MLP computation jointly account for the majority of inference latency, motivating joint optimization of both components; (b) The comparison illustrates multimodal MoE compression along the token and expert dimensions. Existing token-pruning methods mainly reduce the token dimension, while expert-compression methods primarily reduce the expert dimension. DecoMoE instead performs structured compression along both dimensions by removing the complete visual-token block after a sample-dependent boundary and restricting subsequent MoE computation to a compact contiguous expert prefix.

### Abstract

Multimodal Mixture-of-Experts (MoE) models combine strong visual-language capabilities with sparse expert activation, yet their inference remains computationally expensive because long visual-token sequences repeatedly incur attention and expert-MLP computation across decoder layers. DecoMoE addresses this problem by decoupling visual propagation from expert computation. It introduces a **Sample-Adaptive Visual Boundary (SAVB)** to determine when visual tokens can stop propagating through the decoder, and a **Routing-Calibrated Expert Prefix (RCEP)** to organize experts using text-token routing statistics and dynamically retain a compact contiguous expert prefix during inference. By performing structured compression along both the token and expert dimensions, DecoMoE reduces multimodal MoE inference cost while largely preserving the performance of the original model.

### Figure 2
![Figure 2](https://github.com/ShawnTan86/DecoMoE/blob/main/DecoMoE_Method_Pipeline.png)

**Description:** DecoMoE consists of two complementary components. **SAVB** constructs a lightweight gating feature from the current text hidden states and predicts a sample-dependent visual-exit boundary. Its supervision is derived from forced visual-exit correctness and first-token negative log-likelihood while keeping the multimodal backbone frozen. After visual exit, **RCEP** exploits the more concentrated and recurrent routing patterns of text tokens. During offline calibration, experts are reordered according to their cross-case mean routed mass so that important experts occupy a contiguous physical prefix. During online inference, RCEP dynamically selects the shortest prefix that covers a target fraction of the current routed mass and performs native Top-k routing within the retained prefix. Together, SAVB and RCEP enable structured and adaptive compression along both computation dimensions.

### Code

The implementation and evaluation code for DecoMoE will be released soon.

**Code coming soon.**

### Citation

Citation information will be updated after the paper is publicly available.
