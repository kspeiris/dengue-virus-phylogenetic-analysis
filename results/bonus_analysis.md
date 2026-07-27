# Bonus Analysis: Bootstrap Replicates Comparison (100 vs. 1000)

This document provides the comparative analysis of the phylogenetic trees reconstructed using standard bootstrap (100 replicates) and Ultrafast Bootstrap (UFBoot, 1,000 replicates), answering the Bonus Challenge from the assignment.

---

## 1. Quantitative Performance & Topology Summary

Both runs were executed on the same multiple sequence alignment of 50 Dengue virus genomes. The model selected by ModelFinder and the general Maximum Likelihood tree topology were identical between the two runs, but the computation times and bootstrap support values differed significantly:

| Evaluation Metric | Standard Bootstrap (n = 100) | Ultrafast Bootstrap (n = 1000) |
| :--- | :---: | :---: |
| **Selected Evolutionary Model** | `GTR+F+I+G4` | `GTR+F+I+G4` |
| **Log-Likelihood ($\ln L$) of ML Tree** | -73,298.52 | -73,298.51 |
| **Total Tree Length** | 4.0668 | 4.0800 |
| **Consensus Tree RF Distance to ML Tree** | 4 | 0 |
| **Total Wall-Clock Runtime** | 1 hour 1 minute 23 seconds | 5 minutes 4 seconds |
| **Mean Branch Support (47 comparable clades)** | 84.8% | 90.7% |
| **Median Branch Support** | 99.0% | 99.0% |
| **Clades with Support < 70%** | 10 / 47 | 8 / 47 |
| **Clades with Support = 100%** | 17 / 47 | 22 / 47 |

---

## 2. Key Observations and Interpretation

### A. Algorithmic Efficiency
- The **Ultrafast Bootstrap (n = 1,000)** completed in **5 minutes and 4 seconds**, representing a **~12x speedup** over the standard bootstrap (1 hour 1 minute 23 seconds), despite evaluating **10x more replicates**. 
- Standard bootstrap is computationally heavy because it performs a full Maximum Likelihood tree search from scratch for each pseudo-replicate. UFBoot accelerates this by using a candidate tree set and optimizing branch lengths heuristically without full search iterations.

### B. Topological Convergence
- The Robinson-Foulds (RF) distance between the ML tree and the consensus tree was **4** for standard bootstrap, indicating that 100 replicates were not enough to reach complete topological convergence.
- In contrast, the RF distance was **0** for UFBoot (n = 1,000), showing that the larger number of replicates successfully converged on the exact ML tree topology.

### C. Influence of Replicates on Clade Confidence
- **Decisiveness of Support**: With 1,000 replicates, more branches achieved **100% support** (22 clades vs. 17 in standard bootstrap). This indicates that increasing replicates helps stabilize support values for well-supported clades.
- **Backbone Resolution**: The number of clades with weak support ($< 70\%$) dropped from 10 to 8 when increasing replicates to 1,000. Under-sampling in standard bootstrap (n = 100) introduces statistical noise, which can artificially lower support values for genuine relationships.
- **Conservative Bias of Standard Bootstrap**: Standard bootstrap values tend to be lower because each replicate search is independent and can get trapped in local optima. UFBoot support values behave as approximate probabilities of clade occurrence, meaning they are less conservative but highly reliable when $\ge 95\%$.

---

## 3. Conclusion on Bootstrap Settings

For molecular epidemiology and outbreak tracking, **1,000 replicates via UFBoot** is superior because:
1. It achieves complete topological convergence (RF = 0).
2. It reduces statistical sampling noise, providing more accurate confidence scores.
3. It is significantly faster, enabling rapid public health responses during active viral outbreaks.
