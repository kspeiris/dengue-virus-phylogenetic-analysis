# Conclusion

The phylogenetic analysis of 28 complete Dengue virus (DENV) genomes successfully reconstructed the evolutionary relationships of human-derived isolates from Asia. The study accomplished all specified learning outcomes and objectives:

1. **Successful Workflow Implementation**: A reproducible bioinformatics workflow was executed using the Galaxy platform, combining sequence retrieval from NCBI Virus, multiple sequence alignment via MAFFT, and maximum likelihood tree construction via IQ-TREE.
2. **Clear Evolutionary Partitioning**: The resulting tree successfully resolved the 28 isolates into four distinct monophyletic serotype clades (DENV-1 to DENV-4) with **100% bootstrap support**, confirming their distinct evolutionary trajectories. DENV-2 and DENV-4 were resolved as sister serotypes.
3. **Geographic and Transmission Insights**: Detailed clade inspection revealed strong epidemiological links, particularly between Singapore and China (DENV-1 and DENV-4) and Sri Lanka and China (DENV-2), illustrating the rapid transnational spread of Dengue strains within Asia. Localized South Asian lineages (India, Pakistan, Bangladesh) were also identified, highlighting endemic maintenance.
4. **Methodological Validation**: Comparing 100 vs. 1,000 bootstrap replicates demonstrated that higher replicate runs minimize statistical noise and provide more reliable support metrics for weakly resolved nodes, validating the standard requirement of 1,000 replicates in viral phylogenetics.

In summary, this study demonstrates the power of molecular phylogenetics in viral surveillance. These computational pipelines are critical for tracking virus outbreaks, predicting the risk of severe dengue (DHF/DSS) through co-circulating serotypes, and informing public health interventions across Asia.
