# IQ-TREE Phylogenetic Analysis Results (Bootstrap 1000)

This document provides a summary of the phylogenetic analysis performed on the Dengue virus sequences using **IQ-TREE 2.4.0** with **1,000 Ultrafast Bootstrap (UFBoot) replicates**.

## 1. Analysis Overview
- **Input Data**: 28 sequences with 10,825 nucleotide sites
- **Constant Sites**: 5,067 (46.82% of all sites)
- **Parsimony Informative Sites**: 5,496
- **Distinct Site Patterns**: 3,855
- **Analysis Type**: ModelFinder + Tree Reconstruction + Ultrafast Bootstrap (1000 replicates)

## 2. Substitution Model Selection
**Best-fit model:** `TIM2+F+I+R3` (selected by AIC, AICc, and BIC)

- **TIM2**: Transitional Model 2 (assumes $r_{AC} = r_{AT}$, $r_{CG} = r_{GT}$, and unequal transition rates $r_{AG}$ and $r_{CT}$)
- **+F**: Empirical state frequencies from the alignment
- **+I**: Proportion of invariable sites (fraction of site positions that do not change)
- **+R3**: FreeRate model with 3 rate categories to model rate heterogeneity across sites

### Substitution Parameters

#### A. Rate Parameters (Relative to C-G = 1.0000)
- **$r_{AC}$ (A-C)**: 2.0137
- **$r_{AG}$ (A-G)**: 9.3054
- **$r_{AT}$ (A-T)**: 2.0137
- **$r_{CG}$ (C-G)**: 1.0000
- **$r_{CT}$ (C-T)**: 29.4081
- **$r_{GT}$ (G-T)**: 1.0000

#### B. Empirical Base Frequencies
- **$\pi_A$**: 0.3203 (32.03%)
- **$\pi_C$**: 0.2071 (20.71%)
- **$\pi_G$**: 0.2587 (25.87%)
- **$\pi_T$**: 0.2139 (21.39%)

#### C. Rate Heterogeneity (Invar + FreeRate 3 categories)
- **Proportion of invariable sites ($I$)**: 30.87%
- **Rate Categories**:
  - **Category 0** (Invariable): Rate = 0.0000 (Proportion = 30.87%)
  - **Category 1**: Relative Rate = 0.1474 (Proportion = 25.76%)
  - **Category 2**: Relative Rate = 1.6740 (Proportion = 32.66%)
  - **Category 3**: Relative Rate = 3.8770 (Proportion = 10.71%)

## 3. Likelihood and Information Criteria (ML Tree)
- **Log-Likelihood ($\ln L$)**: -78,448.5451 (s.e. 627.5467)
- **Akaike Information Criterion (AIC)**: 157,025.0903
- **Corrected AIC (AICc)**: 157,025.8635
- **Bayesian Information Criterion (BIC)**: 157,491.6255
- **Total Tree Length (sum of branch lengths)**: 3.9970
- **Sum of Internal Branch Lengths**: 3.5830 (89.64% of total tree length)

## 4. Consensus Tree and Bootstrap Analysis
- **Replicates**: 1,000 Ultrafast Bootstrap replicates
- **Log-likelihood of Consensus Tree**: -78,448.5473
- **Robinson-Foulds (RF) Distance**: 0 (indicates that the Maximum Likelihood tree and the Consensus tree have identical topologies)

## 5. Execution Performance
- **Total CPU time used**: 415.99 seconds (~6 min 55 sec)
- **Wall-clock time**: 105.92 seconds (~1 min 45 sec)
