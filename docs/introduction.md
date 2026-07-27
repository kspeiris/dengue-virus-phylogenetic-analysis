# Introduction

## 1. Background and Clinical Significance of Dengue Virus
Dengue virus (DENV) is a major public health concern globally, particularly in tropical and subtropical regions. It is a mosquito-borne, single-stranded, positive-sense RNA virus belonging to the family *Flaviviridae* and the genus *Orthoflavivirus*. DENV is primarily transmitted to humans through the bites of infective female *Aedes* mosquitoes, principally *Aedes aegypti* and, to a lesser extent, *Aedes albopictus*. 

Infection with DENV can lead to a wide spectrum of clinical manifestations, ranging from mild, self-limiting dengue fever (DF) to severe, life-threatening conditions such as dengue hemorrhagic fever (DHF) and dengue shock syndrome (DSS). The virus exists as four antigenically distinct serotypes, designated as DENV-1, DENV-2, DENV-3, and DENV-4. While infection with one serotype confers lifelong immunity against that specific serotype, subsequent infection with a heterologous serotype increases the risk of severe dengue due to a immunological mechanism known as antibody-dependent enhancement (ADE).

```
                      ┌───────────────┐
                      │ Dengue Virus  │
                      └───────┬───────┘
                              │
         ┌────────────┬───────┴────┬────────────┐
         ▼            ▼            ▼            ▼
     ┌───────┐    ┌───────┐    ┌───────┐    ┌───────┐
     │DENV-1 │    │DENV-2 │    │DENV-3 │    │DENV-4 │
     └───────┘    └───────┘    └───────┘    └───────┘
```

## 2. Role of Phylogenetics in Viral Epidemiology
Phylogenetic analysis plays a critical role in molecular epidemiology and public health surveillance. Because RNA viruses exhibit high mutation rates due to the error-prone nature of their viral RNA-dependent RNA polymerase (RdRp), they evolve rapidly. By analyzing these genetic changes, researchers can reconstruct the evolutionary history of viral lineages, trace transmission pathways during outbreaks, detect the introduction of novel genotypes into a region, and monitor the geographical spread of viral strains. During epidemics, mapping these relationships helps identify the sources of outbreaks and understand how viral populations adapt to host immune pressures and vector populations.

## 3. Computational Workflow for Evolutionary Reconstruction
Modern bioinformatics relies on robust, reproducible pipelines to analyze viral genomics. The standard workflow involves:
1. **Sequence Retrieval**: Fetching complete genomes from public repositories such as the National Center for Biotechnology Information (NCBI) Virus database.
2. **Multiple Sequence Alignment (MSA)**: Aligning homologous positions across genomes. In this study, we utilize **MAFFT** (Multiple Alignment using Fast Fourier Transform), which is highly optimized for large nucleotide sequences.
3. **Phylogenetic Reconstruction**: Building tree topologies using statistical methods. We employ the **Maximum Likelihood (ML)** method implemented via **IQ-TREE**, combined with **ModelFinder** to determine the best-fit substitution model and **Ultrafast Bootstrapping (UFBoot)** to assess branch support.
4. **Galaxy Platform Integration**: Performing these analyses within the **Galaxy** platform ensures workflow reproducibility, transparency, and computational accessibility.

## 4. Study Objectives
The primary objective of this project is to construct and interpret a phylogenetic tree using 28 human-derived Dengue virus complete genome sequences isolated from clinical blood samples in Asia. Specifically, the study aims to:
- Establish the monophyletic status of the four DENV serotypes.
- Identify geographic and temporal clustering patterns among Asian isolates.
- Assess the reliability of internal nodes using 100 vs. 1,000 bootstrap replicates (Bonus Challenge).
- Discuss the evolutionary mechanisms driving Dengue virus diversity in the region.
