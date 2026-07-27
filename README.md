# Dengue Virus Phylogenetic & Evolutionary Analysis

This repository contains the complete dataset, bioinformatics workflows, computational results, and formal documentation for the phylogenetic analysis of Dengue virus (DENV) genomes. The study was conducted as part of the **CCS4082 - BioInformatics** curriculum.

---

## 1. Project Overview

The objective of this project is to analyze the evolutionary relationships and transmission dynamics of Dengue virus isolates across Asia. The workflow integrates:
*   **Sequence Retrieval**: 28 human-derived complete DENV genomes isolated from blood samples across 13 Asian countries, representing all four serotypes (DENV-1 to DENV-4, balanced with 7 sequences each).
*   **Multiple Sequence Alignment (MSA)**: Automatic sequence alignment using **MAFFT** on the Galaxy platform.
*   **Model Selection**: Automated evolutionary model selection using **ModelFinder** (recommending the **`TIM2+F+I+R3`** substitution model).
*   **Phylogenetic Reconstruction**: Maximum Likelihood (ML) tree construction using **IQ-TREE 2.4.0** with **1,000 Ultrafast Bootstrap (UFBoot2) replicates** and **100 standard non-parametric bootstrap replicates** for comparative analysis.

---

## 2. Core Repository Contents

*   [BioInformatics_Assignment.md](file:///c:/My%20KS/University/7th%20Sem/CSE4092%20-%20Bioinformatics/dengue-virus-phylogenetic-analysis/BioInformatics_Assignment.md): The final formal 18-page assignment report containing all sections (Introduction, Materials & Methods, Results, Discussion, and the Bonus Challenge).
*   [analysis.ipynb](file:///c:/My%20KS/University/7th%20Sem/CSE4092%20-%20Bioinformatics/dengue-virus-phylogenetic-analysis/analysis.ipynb): An interactive Jupyter notebook detailing data profiling, sequence statistics, transition bias, site rate heterogeneity, and bootstrap execution times.
*   `data/`: Contains raw sequence data in FASTA format.
*   `results/`: Results folder containing [alignment_statistics.md](file:///c:/My%20KS/University/7th%20Sem/CSE4092%20-%20Bioinformatics/dengue-virus-phylogenetic-analysis/results/alignment_statistics.md), [iqtree_results.md](file:///c:/My%20KS/University/7th%20Sem/CSE4092%20-%20Bioinformatics/dengue-virus-phylogenetic-analysis/results/iqtree_results.md), [tree_interpretation.md](file:///c:/My%20KS/University/7th%20Sem/CSE4092%20-%20Bioinformatics/dengue-virus-phylogenetic-analysis/results/tree_interpretation.md), and [bonus_analysis.md](file:///c:/My%20KS/University/7th%20Sem/CSE4092%20-%20Bioinformatics/dengue-virus-phylogenetic-analysis/results/bonus_analysis.md).
*   `iqtree/`: 
    *   `bootstrap_100/`: Tree files, distance matrices, and reports for the 100 standard bootstrap replicate run.
    *   `bootstrap_1000/`: Tree files and reports for the 1,000 UFBoot replicate run.
    *   `comparison/`: Comparative markdown files ([bootstrap_comparison.md](file:///c:/My%20KS/University/7th%20Sem/CSE4092%20-%20Bioinformatics/dengue-virus-phylogenetic-analysis/iqtree/comparison/bootstrap_comparison.md) and [comparison_table.md](file:///c:/My%20KS/University/7th%20Sem/CSE4092%20-%20Bioinformatics/dengue-virus-phylogenetic-analysis/iqtree/comparison/comparison_table.md)) and the comparison chart (`comparison_results.png`).

---

## 3. Key Scientific & Computational Findings

1.  **Monophyly of Serotypes**: The Maximum Likelihood tree resolved the 28 isolates into four distinct monophyletic clades representing serotypes DENV-1, DENV-2, DENV-3, and DENV-4, each supported by **100% bootstrap confidence** at their ancestral nodes.
2.  **Transition Mutation Bias (Ti/Tv)**: Quantitative analysis of substitution rates reveals a **~12.86× transition bias** ($C \leftrightarrow T$ rate = 29.41; $A \leftrightarrow G$ rate = 9.31), reflecting structural constraints during viral replication.
3.  **Site Rate Heterogeneity**: The FreeRate category model (`+R3`) shows that **30.9% of site positions in the alignment are invariable** (strong purifying selection), whereas **10.7% are highly variable** (likely antigen-binding regions under selection).
4.  **Geographic Co-circulation & Transmission**: Strains from the same country did not cluster exclusively together, indicating multiple independent viral introductions. However, significant regional clades are recovered at **100% support** (e.g., Singapore–China transmission routes in DENV-1/4, and India–Pakistan South Asian sub-lineage in DENV-2).
5.  **Bootstrap Algorithmic Comparison**: 
    *   **Standard Bootstrap (100 replicates)**: Took **48m 45s** of wall-clock time and failed to reach complete topological convergence (Robinson-Foulds distance = 2).
    *   **Ultrafast Bootstrap (1,000 replicates)**: Took only **1m 45s** (**~27.6× faster**), achieved complete convergence (RF = 0), and provided more decisive support values for deeper backbone nodes.

---

## 4. Running the Jupyter Notebook Locally

To view and run the interactive analysis notebook, ensure you have Python 3 installed alongside the required scientific libraries:

### Install dependencies
```bash
pip install pandas numpy matplotlib seaborn scipy nbformat nbconvert ipykernel
```

### Run the notebook
Launch Jupyter Notebook or JupyterLab in your terminal:
```bash
jupyter notebook
```
Open `analysis.ipynb` to view the code blocks, data tables, and pre-rendered plots.
