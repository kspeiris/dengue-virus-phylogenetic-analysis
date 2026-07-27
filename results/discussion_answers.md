# Discussion Questions & Answers

This document lists the official answers to the five core discussion questions outlined in Task 6 of the phylogenetic analysis assignment.

---

### Question 1: Why is sequence alignment required before phylogenetic analysis?

**Answer:**
Multiple Sequence Alignment (MSA) is required to establish **positional homology** across the genomes.
- **Establishing Equivalence**: Alignment ensures that nucleotides appearing in the same column (site) across different sequences share a common evolutionary origin.
- **Handling Insertion/Deletion (Indel) Events**: Viral genomes accumulate insertions and deletions over time. Alignment inserts gaps (`-`) to represent these events, preserving the relative coordinates of the remaining functional elements.
- **Preventing Errors**: If sequences are not aligned, simple deletions or insertions would cause frameshifts or position shifts. Phylogenetic tools would then compare non-homologous nucleotide sites, falsely interpreting positional differences as multiple substitutions (mutations). This would lead to highly inaccurate genetic distances, incorrect tree topologies, and distorted branch lengths.

---

### Question 2: What is the purpose of bootstrap analysis?

**Answer:**
The purpose of bootstrap analysis is to **statistically assess the reliability and robustness of the tree branches (nodes)**.
- **Resampling Method**: It generates pseudo-replicate alignments (typically 100 or 1,000) of the same length by randomly sampling columns from the original alignment with replacement.
- **Topology Verification**: For each pseudo-replicate alignment, a separate phylogenetic tree is reconstructed. 
- **Support Values**: The bootstrap value assigned to a node represents the percentage of replicate trees in which that specific clade/branch was resolved. High bootstrap support (typically $\ge 70\%$ for standard bootstrap or $\ge 95\%$ for Ultrafast Bootstrap UFBoot) gives researchers statistical confidence that a resolved grouping is stable and not an artifact of random sampling in the sequence data.

---

### Question 3: How does the Maximum Likelihood approach differ from distance-based methods?

**Answer:**
Maximum Likelihood (ML) and distance-based methods (such as Neighbor-Joining) differ fundamentally in their input data processing, model integration, and evaluation criteria:

1. **Data Utilization**: ML evaluates the alignment site-by-site, retaining all evolutionary information at each column. Distance-based methods collapse the entire alignment into a single pairwise distance matrix, discarding column-specific character patterns.
2. **Model of Evolution**: ML utilizes sophisticated, explicit probabilistic models of sequence evolution (e.g., transition/transversion ratios, empirical base frequencies, and site rate variation parameters). Distance methods calculate a simplified genetic distance correction (e.g., Jukes-Cantor or Kimura 2-Parameter) to fill the matrix.
3. **Optimality Criterion**: ML searches for the tree topology and branch lengths that maximize the likelihood of obtaining the observed sequence data given the evolutionary model ($P(\text{Data} \mid \text{Tree}, \text{Model})$). Distance-based methods rely on clustering algorithms (like Neighbor-Joining) to find a single tree that minimizes total branch length or fits the pairwise distance calculations, making them faster but less statistically robust.

---

### Question 4: What biological conclusions can be drawn from the generated tree?

**Answer:**
Several important epidemiological and biological conclusions can be drawn:
1. **Antigenic Grouping (Serotypes)**: The 28 genomes resolve into four clear monophyletic serotype groups (DENV-1 to DENV-4) with **100% bootstrap support**, confirming the historical divergence of these distinct immunological groups.
2. **Transnational Transmission Pathways**: 
   - A direct link is identified between **KM403622.1 (Singapore, 2013)** and **PV083756.1 (Guangzhou, China, 2014)** with **100% support**, indicating that international travel or trade likely introduced this strain from Singapore to Guangzhou, seeding the 2014 outbreak.
   - A similar international transmission event is evident between **PV752120.1 (Sri Lanka, 2017)** and **MH110586.1 (China, 2017)** which cluster together with **100% support**.
3. **Endemic Maintenance**: Distinct South Asian sub-lineages (containing isolates from India, Pakistan, and Bangladesh) group together within DENV-2 and DENV-3, indicating that regional viral reservoirs exist and evolve locally under endemic transmission dynamics.

---

### Question 5: What are the limitations of this analysis?

**Answer:**
1. **Sampling Representation**: With only 28 genomes representing the vast diversity of Dengue virus in Asia, the dataset is highly under-sampled. This limits the precision of transmission tracing and ancestral reconstruction.
2. **Recombination Incompatibility**: Maximum Likelihood methods assume a simple branching tree. However, RNA viruses can undergo recombination. Recombination events violate this assumption and can distort branch lengths or result in incorrect tree topologies.
3. **Absence of Epidemiological Metadata**: The analysis relies primarily on genomic sequences. Without detailed clinical records, patient travel history, or high-resolution sample dates, we cannot establish direct transmission links or clinical associations.
4. **Outgroup Selection**: Phylogenetic trees constructed from Dengue genomes are drawn as unrooted trees. While we can use a serotype (like DENV-1) as an artificial root for visualization, determining the true root of the tree requires outgroups (such as Zika virus or other flaviviruses), which were not included in this dataset.
