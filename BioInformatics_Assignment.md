# BioInformatics Assignment

**CCS4082 - BioInformatics**  
**Page 1**

### Faculty of Computing
### University of Sri Jayewardenepura

**Assignment:**  
**Phylogenetic Analysis of Dengue Virus Genomes Using Galaxy**

**CCS4082 - BioInformatics**

**Submitted by:**
- S. D. Suraweera - FC110567
- K. A. D. C. Perera - FC110533
- T. H. Perera - FC110564
- G. P. S. Weerakoon - FC110550

---

**CCS4082 - BioInformatics**  
**Page 2**

## Table of Contents
1. [Introduction](#1-introduction) (Page 4)
2. [Materials and Methods](#2-materials-and-methods) (Page 4)
   - 2.1 [Sequence Retrieval from NCBI Virus Database](#21-sequence-retrieval-from-ncbi-virus-database) (Page 4)
   - 2.2 [Sequence Quality Assessment and Data Preparation](#22-sequence-quality-assessment-and-data-preparation) (Page 7)
   - 2.3 [Multiple Sequence Alignment Using MAFFT](#23-multiple-sequence-alignment-using-mafft) (Page 8)
   - 2.4 [Maximum Likelihood Phylogenetic Analysis Using IQ-TREE](#24-maximum-likelihood-phylogenetic-analysis-using-iq-tree) (Page 10)
3. [Results](#3-results) (Page 12)
   - 3.1 [Phylogenetic Tree Visualization](#31-phylogenetic-tree-visualization) (Page 12)
   - 3.2 [Cluster Analysis](#32-cluster-analysis) (Page 13)
   - 3.3 [Geographic Clustering](#33-geographic-clustering) (Page 13)
   - 3.4 [Distinct Evolutionary Lineages](#34-distinct-evolutionary-lineages) (Page 13)
   - 3.5 [Bootstrap Analysis](#35-bootstrap-analysis) (Page 14)
     - Serotype-defining clades (Page 14)
     - Well-supported within-serotype and country-specific groupings (Page 14)
     - Weakly supported backbone nodes (Page 15)
4. [Discussion](#4-discussion) (Page 15)
   - Q1. What could be possible explanations for the observed clustering patterns? (Page 15)
   - Q2. Why is sequence alignment required before phylogenetic analysis? (Page 16)
   - Q3. What is the purpose of bootstrap analysis? (Page 16)
   - Q4. How does Maximum Likelihood differ from distance-based methods? (Page 16)
   - Q5. What biological conclusions can be drawn from the generated tree? (Page 16)
   - Q6. What are the limitations of this analysis? (Page 17)
5. [Bonus Challenge](#5-bonus-challenge) (Page 17)
6. [Conclusion](#6-conclusion) (Page 18)
7. [References](#7-references) (Page 18)

---

**CCS4082 - BioInformatics**  
**Page 3**

## Table of Figures
- **Figure 1**: Search Filters Used (Page 5)
- **Figure 2**: Metadata of the Downloaded 28 Genome Sequences (Page 6)
- **Figure 3**: Output From Running Fasta Statistics Tool from Galaxy on the Original FASTA file (Page 7)
- **Figure 4**: Example FASTA Entry (Page 8)
- **Figure 5**: Output From Running Fasta Statistics Tool from Galaxy on the MAFFT Aligned FASTA file (Page 9)
- **Figure 6**: MAFFT Workflow Execution (Page 10)
- **Figure 7**: Evolutionary Model Selected by IQ-TREE (Page 11)
- **Figure 8**: Bootstrap settings for IQ-TREE (Page 11)
- **Figure 9**: Resulting Phylogenetic Tree (Page 12)

## List of Tables
- **Table 1**: Parameter Selection (Page 4)
- **Table 2**: Countries Represented by the 28 Genome Sequences (Page 5)
- **Table 3**: Statistics of the Original FASTA File (Page 7)
- **Table 4**: Statistics of the Aligned FASTA File Using MAFFT (Page 9)
- **Table 5**: Parameters for Phylogenetic Reconstruction using IQ-TREE (Page 10)
- **Table 6**: Cluster Analysis of the Phylogenetic Tree (Page 13)
- **Table 7**: Bootstrap Support Values for Serotype-Defining Dengue Virus Clades (Page 14)
- **Table 8**: Bootstrap Support Values for Well-Supported Within-Serotype and Country-Specific Dengue Virus Groupings (Page 14)
- **Table 9**: Summary of 100 vs 1000 Bootstrap Replicates (Page 17)
- **Table 10**: Overall Branch Support Statistics Across 47 Comparable Clades (Page 17)

---

**CCS4082 - BioInformatics**  
**Page 4**

# Construction and Interpretation of a Dengue Virus Phylogenetic Tree Using Multiple Sequence Alignment and Maximum Likelihood Analysis

## 1. Introduction
Dengue virus (DENV) is an important mosquito-borne viral pathogen responsible for dengue fever, dengue hemorrhagic fever, and severe dengue disease. The virus belongs to the family *Flaviviridae* and contains a single-stranded positive-sense RNA genome of approximately 10.7 kb. Dengue virus is classified into four major serotypes (DENV-1 to DENV-4), which show genetic variation due to mutation and evolutionary processes.[1]

Phylogenetic analysis is widely used in virology to investigate evolutionary relationships between viral isolates, identify genetic lineages, and understand patterns of viral transmission and geographical spread. By comparing genomic sequences, researchers can determine how closely related viral strains are and identify distinct evolutionary groups.[2]

Multiple sequence alignment is an essential step in phylogenetic analysis because evolutionary relationships are inferred by comparing homologous nucleotide positions among sequences. After alignment, Maximum Likelihood approaches estimate the evolutionary tree that best explains the observed sequence data based on a nucleotide substitution model.[3]

In this study, 28 Dengue virus complete genome sequences from human-derived isolates collected from Asian regions were analyzed. Multiple sequence alignment was performed using MAFFT, followed by Maximum Likelihood phylogenetic tree construction using IQ-TREE with bootstrap analysis. The objective was to identify evolutionary relationships among Dengue virus genomes and interpret clustering patterns among viral isolates.

## 2. Materials and Methods

### 2.1 Sequence Retrieval from NCBI Virus Database
Dengue virus genome sequences were obtained from the NCBI Virus database. The following search criteria were applied:

#### Table 1: Parameter Selection
| Parameter | Selection |
| :--- | :--- |
| **Virus** | Dengue virus |
| **Sequence type** | Complete Genome |
| **Host** | Human |
| **Isolation source** | Blood |
| **Geographic region** | Asia |

---

**CCS4082 - BioInformatics**  
**Page 5**

A total of 28 complete Dengue virus genome sequences were downloaded in FASTA format, representing all four serotypes (DENV-1 to DENV-4). The dataset comprises sequences originating from 13 distinct countries. The table below outlines the breakdown of sequences by region and country:

#### Table 2: Countries Represented by the 28 Genome Sequences
| Region | Country | Number of Sequences | Percentage of Dataset (%) |
| :--- | :--- | :---: | :---: |
| Asia | Bangladesh | 1 | 4% |
| Asia | Cambodia | 2 | 7% |
| Asia | China | 5 | 18% |
| Asia | India | 4 | 14% |
| Asia | Indonesia | 2 | 7% |
| Asia | Malaysia | 2 | 7% |
| Asia | Myanmar | 1 | 4% |
| Asia | Pakistan | 1 | 4% |
| Asia | Philippines | 1 | 4% |
| Asia | Singapore | 3 | 11% |
| Asia | Sri Lanka | 1 | 4% |
| Asia | Thailand | 2 | 7% |
| Asia | Viet Nam | 3 | 11% |
| **Total** | | **28** | **100%** |

#### Figure 1: Search Filters Used

---

**CCS4082 - BioInformatics**  
**Page 6**

#### Figure 2: Metadata of the Downloaded 28 Genome Sequences

---

**CCS4082 - BioInformatics**  
**Page 7**

### 2.2 Sequence Quality Assessment and Data Preparation
The downloaded FASTA file was evaluated using the FASTA Statistics tool available in Galaxy. The dataset contained the following properties:

#### Table 3: Statistics of the Original FASTA File
| Parameter | Result |
| :--- | :--- |
| **Number of sequences** | 28 |
| **Total sequence length** | ~298,300 bp |
| **Average genome length** | ~10,654 bp |
| **Minimum length** | 10,176 bp |
| **Maximum length** | 10,735 bp |
| **GC content** | ~46.60% |
| **Ambiguous nucleotides** | 0 |

No sequences contained ambiguous nucleotide characters, indicating good sequence quality. The genome lengths were consistent with expected Dengue virus genome sizes (~10.7 kb).

#### Figure 3: Output From Running Fasta Statistics Tool from Galaxy on the Original FASTA file

---

**CCS4082 - BioInformatics**  
**Page 8**

#### Figure 4: Example FASTA Entry

```
>FJ639691.1 |Dengue virus 1 isolate DENV-1/KH/BID-V2008/2007, complete genome
-----------------------acaagaacagtttcgaatcggaagct-tgcttaacgt
agttctaacagttt--ttt-attagagagcagatctct---gatgaacaaccaacggaaa
...
```

### 2.3 Multiple Sequence Alignment Using MAFFT
The 28 Dengue virus genome sequences were aligned using MAFFT through the Galaxy platform. Default MAFFT parameters were used, with the automatic alignment strategy selected.

**Purpose:** Multiple sequence alignment was performed to identify homologous nucleotide positions among different Dengue virus genomes. This alignment step is required because phylogenetic methods compare nucleotide changes at equivalent positions.

---

**CCS4082 - BioInformatics**  
**Page 9**

The resulting aligned FASTA file was evaluated using FASTA Statistics.

#### Table 4: Statistics of the Aligned FASTA File Using MAFFT
| Parameter | Value |
| :--- | :--- |
| **Number of sequences** | 28 |
| **Alignment length** | 10,825 bp |
| **Mean length** | 10,825 bp |
| **Constant sites** | 5,068 (46.82%) |
| **Variable (Polymorphic) sites** | 5,758 (53.19%) |
| **Parsimony-informative sites** | 5,496 (50.77%) |
| **Singleton sites** | 262 (2.42%) |
| **GC content (average)** | ~46.60% |
| **Distinct site patterns** | 3,855 |

The alignment produced equal-length sequences of 10,825 bp, suitable for downstream phylogenetic analysis.

#### Figure 5: Output From Running Fasta Statistics Tool from Galaxy on the MAFFT Aligned FASTA file

---

**CCS4082 - BioInformatics**  
**Page 10**

#### Figure 6: MAFFT Workflow Execution

### 2.4 Maximum Likelihood Phylogenetic Analysis Using IQ-TREE
The MAFFT alignment was used as input for phylogenetic reconstruction using IQ-TREE 2.4.0. The analysis parameters were:

#### Table 5: Parameters for Phylogenetic Reconstruction using IQ-TREE
| Parameter | Setting |
| :--- | :--- |
| **Sequence type** | DNA |
| **Tree method** | Maximum Likelihood |
| **Model selection** | ModelFinder (AIC/AICc/BIC) followed by tree inference |
| **Bootstrap method** | Ultrafast bootstrap (UFBoot2) |
| **Bootstrap replicates** | 1000 |

IQ-TREE automatically evaluated nucleotide substitution models and selected the best-fitting model.
- **Selected evolutionary model:** `TIM2+F+I+R3`

The resulting Maximum Likelihood tree was generated in NHX format. Output files included:
- Maximum Likelihood Tree (`.nhx`)
- IQ-TREE report (`.iqtree`)
- Bootstrap occurrence frequencies (`.nex`)
- Maximum Likelihood Distance Matrix (`.mldist`)
- BIONJ Tree (`.nhx`)

---

**CCS4082 - BioInformatics**  
**Page 11**

#### Figure 7: Evolutionary Model Selected by IQ-TREE
#### Figure 8: Bootstrap settings for IQ-TREE

---

**CCS4082 - BioInformatics**  
**Page 12**

## 3. Results

### 3.1 Phylogenetic Tree Visualization
The Maximum Likelihood phylogenetic tree was visualized using a tree visualization tool such as iTOL.

#### Figure 9: Resulting Phylogenetic Tree

---

**CCS4082 - BioInformatics**  
**Page 13**

### 3.2 Cluster Analysis
The tree resolves into 4 major clusters, mapping onto the four dengue virus serotypes:

#### Table 6: Cluster Analysis of the Phylogenetic Tree
| Cluster | Serotype | Size | Position in Tree |
| :---: | :--- | :---: | :--- |
| **A** | DENV-1 | 7 seqs | Basal lineage, most divergent from DENV-2/3/4 |
| **B** | DENV-2 | 7 seqs | Clade sister to DENV-4 (100% support) |
| **C** | DENV-3 | 7 seqs | Clade sister to DENV-2/DENV-4 superclade (100% support) |
| **D** | DENV-4 | 7 seqs | Clade sister to DENV-2 (100% support) |

### 3.3 Geographic Clustering
The metadata shows partial country-specific clustering:
- **China**: Chinese isolates appear across three serotypes (DENV-1: PV083756.1; DENV-2: MH110586.1; DENV-3: GU363549.1, ON115814.1; DENV-4: KY672959.1), indicating China is a major hub of serotype co-circulation. Within DENV-1, the Singapore (KM403622.1) and China (PV083756.1) isolates cluster together with **100% bootstrap support**, strongly suggesting regional transmission linkage.
- **India**: Indian isolates are distributed across three serotypes (DENV-1: KJ755855.1; DENV-2: KY427084.1; DENV-4: MG272274.1), reflecting endemic co-circulation. Within DENV-2, India (KY427084.1) and Pakistan (KM217156.1) cluster together at **100% support**, forming a South Asian sub-lineage.
- **Singapore**: Singapore isolates appear in both DENV-1 (KM403622.1), DENV-3 (OP410995.1), and DENV-4 (KP792537.2). The DENV-4 Singapore (KP792537.2) and China (KY672959.1) isolates cluster together with **100% support**.
- **Viet Nam**: Vietnamese isolates are present in DENV-1 (FJ410280.1), DENV-2 (EU687250.1), and DENV-3 (FJ461326.1). They appear in different sub-clades, indicating introduction of different lineages.

Therefore, strains from the same country do not always cluster exclusively together. The most consistent geographic clustering is observed for proximate countries that likely share active transmission networks (e.g., Singapore–China, India–Pakistan).

### 3.4 Distinct Evolutionary Lineages
Distinct evolutionary lineages are observed at two levels:
- **Serotype-level lineages**: DENV-1, -2, -3, -4 are each monophyletic with **100% bootstrap support**. The internal branch lengths separating these four clades are very long (>0.3 to 1.0 substitutions per site), confirming deep historical divergence between serotypes.
- **Sub-lineages within serotypes**: Within DENV-2, a South Asian sub-lineage (India/Pakistan) is clearly distinguished from the Sri Lanka/China grouping. Within DENV-4, two distinct geographic sub-groups (Singapore/China vs Bali/Thailand/Malaysia) are evident, backed by high bootstrap support.

---

**CCS4082 - BioInformatics**  
**Page 14**

### 3.5 Bootstrap Analysis
Bootstrap analysis was performed using the ultrafast bootstrap method (UFBoot2) with 1000 replicates to evaluate the reliability of the inferred phylogenetic relationships among the 28 Dengue virus genome sequences. Bootstrap values greater than 70% were considered to indicate strong statistical support for a given branch.

#### Serotype-defining clades
The phylogenetic tree demonstrated very strong support for the major serotype-defining clades, confirming the monophyletic grouping of all four analyzed Dengue virus serotypes.

##### Table 7: Bootstrap Support Values for Serotype-Defining Dengue Virus Clades
| Serotype Clade | Bootstrap Support |
| :--- | :---: |
| DENV-1 clade (7 taxa) | 64–100% (internal nodes) |
| DENV-2 monophyletic clade (7 taxa) | 100% |
| DENV-3 monophyletic clade (7 taxa) | 100% |
| DENV-4 monophyletic clade (7 taxa) | 100% |
| DENV-2 + DENV-4 sister grouping | 100% |
| DENV-3 sister to DENV-2/DENV-4 superclade | 100% |

These results indicate that the major serotype groupings were recovered with near-certain confidence, demonstrating the robustness of the phylogenetic reconstruction. The Robinson-Foulds distance between the ML tree and the Consensus tree was **0**, indicating identical topologies.

#### Well-supported within-serotype and country-specific groupings
Several terminal and within-serotype clusters exhibited very strong bootstrap support, indicating highly reliable evolutionary relationships among closely related isolates.

##### Table 8: Bootstrap Support Values for Well-Supported Within-Serotype and Country-Specific Dengue Virus Groupings
| Isolate Grouping | Serotype | Bootstrap Support |
| :--- | :---: | :---: |
| KM403622.1 (Singapore) + PV083756.1 (China) | DENV-1 | 100% |
| PV752120.1 (Sri Lanka) + MH110586.1 (China) | DENV-2 | 100% |
| KY427084.1 (India) + KM217156.1 (Pakistan) | DENV-2 | 100% |
| South Asian sub-clade (India/Pakistan) + PQ465587.1 (Malaysia) | DENV-2 | 98% |
| PQ657766.1 (Bangladesh) included in DENV-2 clade | DENV-2 | 98% |
| EU687250.1 (Viet Nam) basal to DENV-2 clade | DENV-2 | 100% |
| GU363549.1 (China) + MN253125.1 (India) | DENV-3 | 100% |
| ON115814.1 + GU363549.1 + MN253125.1 sub-clade | DENV-3 | 96% |
| OP410995.1 (Singapore) + PX125311.1 (Indonesia) | DENV-3 | 95% |
| FJ461326.1 (Viet Nam) + KF955461.1 (Cambodia) | DENV-3 | 89% |
| KP792537.2 (Singapore) + KY672959.1 (China) | DENV-4 | 100% |
| MG272274.1 (India) + KP792537.2 + KY672959.1 sub-clade | DENV-4 | 99% |
| PX368925.1 (Indonesia) + PV344375.1 (Thailand) | DENV-4 | 100% |
| PQ555702.1 (Malaysia) + PX368925.1 + PV344375.1 sub-clade | DENV-4 | 95% |
| KY670635.1 (Philippines) basal to DENV-4 | DENV-4 | 100% |

---

**CCS4082 - BioInformatics**  
**Page 15**

#### Weakly supported backbone nodes
In contrast to the strongly supported terminal clusters, several deeper backbone nodes joining regional subgroups within the same serotype showed weak bootstrap support. Bootstrap values of 64%, 74%, and 75% were observed for some internal branches linking geographically distinct sub-clades.

For example, weakly supported nodes were observed in:
- The basal split within DENV-1, linking the KM403622.1/PV083756.1 sub-clade to the remaining DENV-1 sequences (bootstrap: **74%**).
- The deeper backbone node linking DENV-1 sub-clades (bootstrap: **64%**).
- The DENV-4 backbone node linking sub-group A (Singapore/China/India) and sub-group B (Indonesia/Thailand/Malaysia) (bootstrap: **75%**).

These low bootstrap values indicate uncertainty regarding the exact order of divergence among regional lineages within the same serotype.

## 4. Discussion

### Q1. What could be possible explanations for the observed clustering patterns?
The clustering patterns observed in the Maximum Likelihood phylogenetic tree can be explained by several biological, geographic, and temporal factors influencing Dengue virus evolution and transmission.
- **Serotype divergence**: The most prominent clustering pattern was the separation of all 28 isolates into four distinct serotype-specific clades (DENV-1, DENV-2, DENV-3, and DENV-4), each with **100% bootstrap support**. The deep branch lengths separating serotypes (>0.3–1.0 substitutions per site) confirm ancient independent divergence.
- **Regional transmission networks**: Within individual serotypes, geographically proximate countries show strong clustering. The Singapore (KM403622.1) and Guangzhou/China (PV083756.1, 2013–2014) pairing within DENV-1 at 100% support, and the India (KY427084.1, 2010) and Pakistan (KM217156.1, 2011) pairing within DENV-2 at 100% support, reflect active regional transmission routes between neighboring countries.
- **Weakly supported backbone nodes**: Several deeper internal branches exhibited low bootstrap support values (64–75%), indicating uncertainty in the precise evolutionary relationships among regional lineages within the same serotype. This may be due to rapid, near-simultaneous diversification of lineages, leaving insufficient phylogenetic signal along internal branches.
- **Temporal lineage replacement**: The collection dates of the analyzed isolates ranged from 1999 (KF955461.1, Cambodia) to 2023 (PQ555702.1, Malaysia). Some fine-scale clustering may reflect temporal lineage turnover, where strains from different eras belong to distinct sub-clades.

---

**CCS4082 - BioInformatics**  
**Page 16**

### Q2. Why is sequence alignment required before phylogenetic analysis?
Sequence alignment is required because phylogenetic analysis depends on comparing homologous nucleotide positions between sequences. Alignment ensures that mutations are compared at equivalent locations. Without alignment, evolutionary relationships may be incorrectly inferred due to comparison of unrelated positions.[3]

### Q3. What is the purpose of bootstrap analysis?
Bootstrap analysis estimates confidence in phylogenetic tree branches. The alignment dataset is repeatedly resampled and trees are reconstructed to determine how frequently the same relationships appear. Higher bootstrap values indicate stronger confidence in evolutionary relationships.[4]

### Q4. How does Maximum Likelihood differ from distance-based methods?
Maximum Likelihood methods evaluate possible evolutionary trees using probability models of nucleotide substitution and select the tree that best explains the observed data. Distance-based methods first calculate genetic distances between sequences and then construct a tree based on these distances. Maximum Likelihood generally provides more accurate evolutionary estimates because it considers the evolutionary process rather than only overall sequence differences.[5]

### Q5. What biological conclusions can be drawn from the generated tree?
The phylogenetic tree provides information about:[2]
- Genetic relationships between Dengue virus isolates
- Evolutionary diversification across four antigenically distinct serotypes
- Regional transmission patterns, particularly the Singapore–China (DENV-1, DENV-4) and India–Pakistan (DENV-2) linkages
- Co-circulation of multiple serotypes within countries like China, India, and Singapore, which increases the risk of severe dengue via antibody-dependent enhancement (ADE)

Closely related sequences with short branch lengths (e.g., KM403622.1/PV083756.1; KP792537.2/KY672959.1) share a recent evolutionary ancestor, while the long internal branches separating serotype clades indicate deep historical divergence.

---

**CCS4082 - BioInformatics**  
**Page 17**

### Q6. What are the limitations of this analysis?
The analysis has several limitations:
1. Limited number of genome sequences (28 sequences) relative to the true diversity of DENV across Asia
2. Geographic sampling bias — some countries (e.g., China: 5 sequences, India: 4 sequences) are over-represented compared to others (e.g., Bangladesh, Myanmar, Pakistan: 1 sequence each)
3. Lack of detailed epidemiological information (patient travel history, clinical severity)
4. Evolutionary model assumptions — TIM2+F+I+R3 assumes no recombination
5. Possible recombination events in RNA viruses that violate bifurcating tree assumptions
6. Unrooted tree — the true root of the tree requires an outgroup (e.g., Zika virus), which was not included

## 5. Bonus Challenge
Two independent IQ-TREE runs were performed on the same 28-sequence MAFFT alignment: one using standard non-parametric bootstrap (n = 100) and one using the Ultrafast Bootstrap algorithm (UFBoot2, n = 1,000). ModelFinder selected the same best-fit substitution model (`TIM2+F+I+R3`) in both runs, and the underlying ML tree topologies are identical, confirming that the choice of bootstrap method and replicate count affects only the confidence values assigned to branches, not the tree estimate itself.

#### Table 9: Summary of 100 vs 1000 Bootstrap Replicates
| Metric | n = 100 (Standard Bootstrap) | n = 1000 (UFBoot2) |
| :--- | :---: | :---: |
| **Best-fit model (ModelFinder)** | `TIM2+F+I+R3` | `TIM2+F+I+R3` |
| **Log-likelihood of ML tree ($\ln L$)** | -78,448.5459 | -78,448.5451 |
| **Total tree length (sum of branch lengths)** | 3.9970 | 3.9970 |
| **Sum of internal branch lengths** | 3.5830 (89.64%) | 3.5830 (89.64%) |
| **RF distance: ML tree vs. consensus tree** | **2** | **0** |
| **Total CPU time used** | 11,250.03 s (3h 7m 30s) | 415.99 s (6m 55s) |
| **Total wall-clock time** | 2,925.70 s (48m 45s) | 105.92 s (1m 45s) |

Despite running **10× more replicates**, UFBoot2 (n = 1,000) completed in under **2 minutes** compared to nearly **49 minutes** for the standard bootstrap — a **~27.6× wall-clock speedup** — while simultaneously achieving better topological convergence (RF = 0 vs. RF = 2).

#### Table 10: Node-Level Bootstrap Support Comparison (Key Clades)
| Clade | Standard Bootstrap (100) | UFBoot2 (1000) | Change |
| :--- | :---: | :---: | :---: |
| KM403622.1 (Singapore) + PV083756.1 (China) — DENV-1 | 100% | 100% | — |
| PV752120.1 (Sri Lanka) + MH110586.1 (China) — DENV-2 | 100% | 100% | — |
| KY427084.1 (India) + KM217156.1 (Pakistan) — DENV-2 | 100% | 100% | — |
| South Asian sub-clade + PQ465587.1 (Malaysia) — DENV-2 | 95% | 98% | **+3%** |
| OP410995.1 (Singapore) + PX125311.1 (Indonesia) — DENV-3 | 80% | 95% | **+15%** |
| GU363549.1 (China) + MN253125.1 (India) — DENV-3 | 98% | 100% | **+2%** |
| MG272274.1 (India) + KP792537.2 + KY672959.1 — DENV-4 | 94% | 99% | **+5%** |
| PX368925.1 (Indonesia) + PV344375.1 (Thailand) — DENV-4 | 94% | 100% | **+6%** |
| PQ555702.1 (Malaysia) sub-clade — DENV-4 | 89% | 95% | **+6%** |
| DENV-4 backbone node (Subgroup A vs. B) | 64% | 75% | **+11%** |
| DENV-1 deep backbone node | 41% | 64% | **+23%** |

Across key comparable clades, UFBoot2 (n = 1,000) consistently produced **equal or higher support values** than standard bootstrap (n = 100). The most notable gains were observed for moderately supported internal nodes: the DENV-3 Singapore/Indonesia cluster improved from 80% → 95%, and the uncertain DENV-1 backbone from 41% → 64%. These increases reflect better statistical sampling and reduced variance at larger replicate counts.

The standard bootstrap RF distance of 2 indicates that the consensus tree from only 100 replicates failed to converge with the ML tree topology at two low-support internal nodes. With 1,000 UFBoot replicates, the RF distance dropped to 0, confirming complete topological convergence. This demonstrates that bootstrap replicate count governs the precision and reliability of branch confidence values, and that 1,000 UFBoot replicates is the superior choice — both statistically and computationally — for Dengue virus genome-scale phylogenetics.

---

**CCS4082 - BioInformatics**  
**Page 18**

## 6. Conclusion
This study successfully reconstructed a Maximum Likelihood phylogenetic tree of Dengue virus genomes using Galaxy-based bioinformatics tools. Twenty-eight complete Dengue virus genomes, representing all four serotypes from 13 Asian countries, were aligned using MAFFT and analyzed using IQ-TREE with 1,000 ultrafast bootstrap replicates.

The best-fit substitution model selected by ModelFinder was **TIM2+F+I+R3**, reflecting strong transition bias and site rate heterogeneity in Dengue genome evolution. The analysis demonstrated clear genetic monophyly of all four serotypes (each with 100% bootstrap support), and revealed regional transmission linkages particularly between Singapore–China (DENV-1, DENV-4) and India–Pakistan (DENV-2). The use of automated model selection and ultrafast bootstrap analysis improved confidence in the reconstructed phylogenetic relationships.

## 7. References
- [1] M. E. Kelly et al., "Molecular Characterization and Phylogenetic Analysis of Dengue Fever Viruses in Three Outbreaks in Tanzania Between 2017 and 2019," *PLoS Negl. Trop. Dis.*, vol. 17, no. 4, p. e0011289, Apr. 2023, doi: 10.1371/journal.pntd.0011289.
- [2] R. Dixit, "Phylogenetic Tree | Construction and Overview," *geeksforgeeks*. [Online]. Available: https://www.geeksforgeeks.org/biology/phylogenetic-tree/
- [3] "Understanding Sequence Alignment," *Geneious Academy*. [Online]. Available: https://www.geneious.com/guides/understanding-sequence-alignment
- [4] J. Lasky, "Bootstrapping (statistics)." [Online]. Available: https://www.ebsco.com/research-starters/science/bootstrapping-statistics
- [5] S. Tamang, "Phylogenetic Tree- Definition, Types, Steps, Methods, Uses," *Microbe Notes*. [Online]. Available: https://microbenotes.com/phylogenetic-tree/