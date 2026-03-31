## Supplementary Material for Reviewer2

---

## Table 2: Domain Number D Ablation (OCW-10, 3 Seeds)

| D (Domains) | P ↑           | F ↓            | FWT ↑         |
| ------------- | ------------- | -------------- | ------------- |
| 1             | 0.64±0.02     | −0.00±0.05     | 0.00±0.01     |
| 2             | 0.59±0.09     | 0.01±0.01      | 0.02±0.01     |
| 3             | 0.63±0.08     | 0.03±0.02      | 0.01±0.02     |
| **4 (paper)** | **0.72±0.08** | **−0.02±0.04** | **0.06±0.10** |
| 5             | 0.59±0.06     | 0.06±0.02      | 0.00±0.00     |
| 6             | 0.67±0.02     | −0.02±0.03     | 0.00±0.00     |


---

## Table S3: Task Order Robustness (OCW-10, 3 Seeds)

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



