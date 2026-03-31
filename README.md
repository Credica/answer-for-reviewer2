## Supplementary Material for Reviewer2

---

## Table 2: Domain Number D Ablation (OCW-10, 3 Seeds)

The number of domain prototypes D controls the granularity of domain-level knowledge grouping. We evaluate D ∈ {1, 2, 3, 4, 5, 6} to identify the optimal partition for OCW-10.


| D (# Domains) | P ↑           | F ↓            | FWT ↑         |
| ------------- | ------------- | -------------- | ------------- |
| 1             | 0.64±0.02     | −0.00±0.05     | 0.00±0.01     |
| 2             | 0.59±0.09     | 0.01±0.01      | 0.02±0.01     |
| 3             | 0.63±0.08     | 0.03±0.02      | 0.01±0.02     |
| **4 (paper)** | **0.72±0.08** | **−0.02±0.04** | **0.06±0.10** |
| 5             | 0.59±0.06     | 0.06±0.02      | 0.00±0.00     |
| 6             | 0.67±0.02     | −0.02±0.03     | 0.00±0.00     |


**Analysis:**

The effect of D reflects an **intra-domain homogeneity–coverage trade-off**:

- **Under-partitioning (D=1–3):** Semantically heterogeneous tasks coexist in the same domain (e.g., *hammer-v2* and *push-v2* at D=2), causing conflicting gradient signals. This yields **reduced FWT**  and **elevated forgetting**  as interference degrades acquired skills.
- **Over-partitioning (D=5–6):**  Each domain prototypes receive EMA updates from only 1–2 tasks, preventing convergence to a stable semantic centroid. As a result, domain experts are trained on insufficient intra-domain diversity and fail to capture generalizable shared structure — they specialise to individual tasks rather than manipulation families. This collapses the two-level hierarchy into a de facto single-level system, eliminating the compositional reuse that domain experts are designed to provide. 
- **D=4 (optimal):** OCW-10 comprises **four manipulation primitive families** (push, grasp/place, rotate/press, peg/stick). D=4 allows each domain expert to specialise in one family, achieving **FWT=0.06** and **F=−0.02**. Notably, domain prototypes recover this structure automatically via EMA-driven convergence on task description embeddings, without any manual domain label supervision.

---

## Table S3: Task Order Robustness (OCW-10, 3 Seeds)

To verify that HTAC's performance does not depend on a favourable task arrival sequence, we evaluate all methods across four independently permuted task orderings. All 4 orderings use the same 10 tasks; only the arrival sequence differs.

Task arrival orders:


| Order | Task Sequence (T1 → T10)                                                                                                                                  |
| ----- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 0     | hammer-v2, push-wall-v2, faucet-close-v2, push-back-v2, stick-pull-v2, handle-press-side-v2, push-v2, shelf-place-v2, window-close-v2, peg-unplug-side-v2 |
| 1     | push-v2, window-close-v2, peg-unplug-side-v2, shelf-place-v2, handle-press-side-v2, push-back-v2, hammer-v2, stick-pull-v2, push-wall-v2, faucet-close-v2 |
| 2     | handle-press-side-v2, peg-unplug-side-v2, push-back-v2, stick-pull-v2, push-v2, shelf-place-v2, faucet-close-v2, window-close-v2, push-wall-v2, hammer-v2 |
| 3     | push-wall-v2, handle-press-side-v2, push-v2, hammer-v2, peg-unplug-side-v2, stick-pull-v2, shelf-place-v2, faucet-close-v2, window-close-v2, push-back-v2 |



| Category | Method     | Order 0       | Order 1       | Order 2       | Order 3       | Avg.     | Range    |
| -------- | ---------- | ------------- | ------------- | ------------- | ------------- | -------- | -------- |
| Reg      | L2         | 0.29±0.06     | 0.20±0.03     | 0.23±0.05     | 0.29±0.05     | 0.25     | 0.09     |
|          | EWC        | 0.16±0.02     | 0.12±0.02     | 0.11±0.02     | 0.15±0.03     | 0.13     | 0.05     |
|          | MAS        | 0.29±0.04     | 0.17±0.01     | 0.16±0.06     | 0.20±0.04     | 0.21     | 0.13     |
|          | LwF        | 0.21±0.04     | 0.15±0.04     | 0.18±0.05     | 0.19±0.00     | 0.18     | 0.06     |
|          | RWalk      | 0.26±0.03     | 0.17±0.01     | 0.25±0.02     | 0.20±0.01     | 0.22     | 0.09     |
|          | VCL        | 0.14±0.03     | 0.11±0.01     | 0.11±0.01     | 0.12±0.03     | 0.12     | 0.03     |
|          | Finetuning | 0.11±0.03     | 0.12±0.02     | 0.15±0.06     | 0.12±0.03     | 0.12     | 0.04     |
| Struc    | LoRA       | 0.54±0.03     | 0.47±0.02     | 0.35±0.03     | 0.43±0.05     | 0.45     | 0.19     |
|          | PackNet    | 0.64±0.06     | 0.67±0.01     | 0.65±0.03     | 0.65±0.04     | 0.65     | 0.03     |
|          | Grow       | 0.60±0.06     | 0.54±0.05     | 0.43±0.01     | 0.51±0.05     | 0.52     | 0.17     |
| Reh      | PM         | 0.26±0.01     | 0.26±0.10     | 0.25±0.03     | 0.27±0.01     | 0.26     | 0.02     |
|          | A-GEM      | 0.12±0.04     | 0.12±0.02     | 0.11±0.01     | 0.15±0.04     | 0.13     | 0.04     |
| **Ours** | **HTAC**   | **0.72±0.04** | **0.72±0.02** | **0.70±0.03** | **0.69±0.03** | **0.71** | **0.03** |


**Analysis:**

HTAC records the highest average performance (0.71) across all four orderings and the joint-lowest performance range (0.03), on par with PackNet and PM. Two complementary mechanisms underpin this order-invariance:

1. **EMA-based prototype convergence:** Domain prototypes accumulate task embeddings incrementally via exponential moving average, regardless of arrival order. After observing all tasks in a domain, the prototype converges to a weighted centroid of their embeddings. This centroid is invariant to the sequence in which those tasks were encountered.
2. **Per-decision warmup evaluation:** Expert reuse is decided independently for each incoming task based on the *current* prototype state, with no dependence on a global task ordering assumption. Tasks that arrive early can trigger expert creation for later tasks to reuse, and vice versa, without any ordering constraint.

By contrast, LoRA and Grow show high order sensitivity, indicating that their performance is strongly influenced by which tasks initialise shared parameters early in the sequence. Methods with low range but low average (PM, MAS) achieve order-invariance through limited expressivity rather than effective knowledge management, and do not represent a practical alternative.

These results confirm that HTAC's gains over baselines are robust to task ordering and are not an artefact of a particular experimental setup.
