# Materials and Methods

## 1. Sequence Retrieval and Dataset Selection
Complete genome sequences of the Dengue virus (DENV) were retrieved from the National Center for Biotechnology Information (NCBI) Virus database (https://www.ncbi.nlm.nih.gov/labs/virus/). The retrieval was performed using the following standardized search filters:
- **Taxonomy**: Dengue virus (taxid:11053)
- **Sequence Type**: Complete genome
- **Host**: *Homo sapiens* (Human)
- **Isolation Source**: Blood
- **Geographic Region**: Asia
- **RefSeq status**: All sequences (including GenBank)

A total of 28 representative complete genome sequences covering all four serotypes (DENV-1, DENV-2, DENV-3, and DENV-4) were selected for analysis. The dataset represents various Asian nations—including Singapore, Vietnam, China, India, Thailand, Myanmar, Pakistan, Sri Lanka, Bangladesh, Malaysia, Indonesia, Cambodia, and the Philippines—with collection dates ranging from 1999 to 2023.

---

## 2. Multiple Sequence Alignment (MSA)
Multiple sequence alignment of the 28 full-length genomes was carried out using the **MAFFT** tool (Multiple Alignment using Fast Fourier Transform) integrated within the **Galaxy** web-based platform. 
- **Methodology**: The alignment was executed using default parameters, which automatically selects the appropriate alignment strategy (typically FFT-NS-2 or L-INS-i depending on sequence size and count).
- **Quality Control**: The output alignment was downloaded in FASTA format and checked for alignment length uniformity (10,825 bp across all sequences) and gap distribution.

---

## 3. Model Selection and Phylogenetic Reconstruction
Phylogenetic tree reconstruction was performed using **IQ-TREE 2.4.0** (within the Galaxy platform) via the Maximum Likelihood (ML) method.

```
┌─────────────────┐       ┌─────────────────┐       ┌──────────────────┐
│   NCBI Virus    │  ──>  │ MAFFT Alignment │  ──>  │    ModelFinder   │
│ (28 DENV Genomes)│       │   (Galaxy)      │       │ (TIM2+F+I+R3 selected)
└─────────────────┘       └─────────────────┘       └────────┬─────────┘
                                                             │
                                                             ▼
┌─────────────────┐       ┌─────────────────┐       ┌──────────────────┐
│    Final Tree   │  <──  │  UFBoot Support │  <──  │    IQ-TREE ML    │
│  Interpretation  │       │ (100 vs 1000)   │       │ Reconstruction   │
└─────────────────┘       └─────────────────┘       └──────────────────┘
```

### A. Model Selection
Before tree search, **ModelFinder** (integrated in IQ-TREE) was used to determine the optimal nucleotide substitution model for the dataset. The selection was based on the Akaike Information Criterion (AIC), corrected AIC (AICc), and Bayesian Information Criterion (BIC) scores. The model **`TIM2+F+I+R3`** was selected as the best-fit model.

### B. Maximum Likelihood Tree Search and Bootstrapping
- **Likelihood Search**: The tree search was performed using the ML criterion to optimize topology and branch lengths.
- **Robustness assessment**: Ultrafast Bootstrap (UFBoot2) approximation was executed to evaluate the reliability of the nodes. To satisfy the assignment's bonus challenge, two distinct bootstrap runs were performed and compared:
  1. A low-replicate run with **100 bootstrap replicates**.
  2. A high-replicate run with **1,000 bootstrap replicates**.
- **Outgroup Rooting**: The resulting tree was drawn as an unrooted tree and visualized with `FJ639691.1` (DENV-1 isolate from Cambodia) as a reference outgroup node for presentation purposes.
