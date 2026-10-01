# Free-Energy-Inspired Stability Indicators and Secure Resource Orchestration for Hybrid QKD–PQC Satellite–Terrestrial Networks

This repository contains the complete, reproducible simulation behind the article. A single notebook, `FreeEnergy_QKD_PQC_STIN.ipynb`, builds a role-aware satellite–terrestrial network (10 nodes, 18 links), simulates its dynamic link process, computes the hybrid QKD–PQC security quantities and the system-level Security Criticality Index (SCI) and Security Deficit Index (SDI), runs seven allocation methods, and produces every table and figure of the article.

## What the notebook computes

- **Link model.** Per-link transmissivity, excess noise, QBER, capacity, latency and trust evolving over 24 time steps; a secret-key-rate surrogate (repeaterless loss scaling × BB84 secret fraction × noise penalty) on the nine QKD-capable space and air links, and an overhead-adjusted PQC secure rate on every link.
- **Path-level quantities.** Normalized QKD contribution Q_p and PQC contribution C_p, hybrid security level S_p, security margin M_p, QBER entropy H_p, path risk, and the free-energy-inspired operational stress score F_p = (1 − S_p) + λ_H H_p + λ_R R_p.
- **System-level indices.** SCI (normalized sum of positive margins), SDI (normalized sum of deficits) and three reserve bands (high, intermediate, low).
- **Allocation methods.** The proposed free-energy controller and six alternatives: latency-first, PQC-trust, QKD-priority, max-margin greedy, shortest-path PQC and random admissible. All share the same service-state hierarchy (secure, best-effort, degraded, blocked).
- **Experiments.** A reference run (seed 42, nominal scenario); 30 random seeds × 6 scenarios (nominal, QKD scarcity, congestion, trust degradation, link noise, traffic load); an ablation of the controller signals; one-at-a-time parameter sensitivity; a prospective evaluation of SCI as an alarm for entry into a low-feasibility state (ROC-AUC, precision, recall, lead time), with the alarm threshold selected on development seeds and tested on held-out seeds; and paired seed-wise comparisons of the methods with bootstrap intervals.

## Running

Open the notebook in Google Colab or Jupyter and run all cells. It needs Python 3 with `numpy`, `pandas`, `networkx` and `matplotlib`. The full run takes about 15 minutes on one CPU. Set the environment variable `QSCI_SEEDS` to a smaller number for a quick check.

Outputs are written to `./Outputs/quantum_secure_comm/` (in Colab, `/content/Outputs/quantum_secure_comm/`):

- `figures/`: all figures of the article (Figs. 2–22 of the article; Fig. 1 is a schematic).
- `tables/`: all result tables as CSV (reference run, method comparison, seed and scenario summaries, ablation, sensitivity, prospective evaluation).
- `others/`: the parameter configuration and the run manifest.

The `Outputs/` folder in this repository holds the results of the full 30-seed run reported in the article.
