Assignment: Phylogenetic Analysis of Dengue Virus Genomes Using Galaxy 
Module 
Bioinformatics 
Assignment Title 
Construction and Interpretation of a Dengue Virus Phylogenetic Tree Using Multiple 
Sequence Alignment and Maximum Likelihood Analysis 
Background 
Phylogenetic analysis is a fundamental bioinformatics technique used to study 
evolutionary relationships among organisms and viruses. During outbreaks, phylogenetic 
trees help researchers understand viral evolution, transmission patterns, emergence of 
new strains, and geographical spread. 
In this assignment, students will obtain Dengue virus genome sequences from the NCBI 
Virus database, perform multiple sequence alignment using MAFFT, and construct a 
phylogenetic tree using IQ-TREE within the Galaxy platform. 
 
Learning Outcomes 
Upon successful completion of this assignment, students will be able to: 
1. Retrieve biological sequence data from public repositories. 
2. Apply multiple sequence alignment techniques to viral genomes. 
3. Construct phylogenetic trees using Maximum Likelihood methods. 
4. Interpret evolutionary relationships among viral strains. 
5. Utilize Galaxy workflows for reproducible bioinformatics analyses. 
 
Assignment Tasks 
Task 1: Sequence Retrieval from NCBI Virus Database 
Access the NCBI Virus database and retrieve Dengue virus genome sequences using the 
following criteria: 
Search Criteria 
• 
Virus: Dengue virus 
• 
Sequence Type: Complete Genome 
• 
Host: Human 
• 
Isolation Source: Blood 
• 
Geographic Region: Asia 
Download a minimum of 20 complete genome sequences in FASTA format. 
Record: 
• 
Number of sequences retrieved 
• 
Countries represented 
• 
Collection dates (if available) 
Include screenshots of the search filters used. 
 
Task 2: Data Preparation 
Review the downloaded FASTA file and ensure: 
• 
All sequences are complete genomes 
• 
Sequences are in FASTA format 
• 
Sequence identifiers are preserved 
Provide: 
• 
Number of sequences analyzed 
• 
Average sequence length 
• 
Example FASTA entry 
 
Task 3: Multiple Sequence Alignment Using MAFFT 
Using Galaxy: 
1. Upload the FASTA file. 
2. Run MAFFT. 
3. Use default parameters unless otherwise justified. 
4. Download the aligned FASTA output. 
Include: 
• 
Screenshot of MAFFT workflow execution 
• 
Alignment statistics 
• 
Description of alignment purpose 
 
Task 4: Phylogenetic Tree Construction Using IQ-TREE 
Using Galaxy: 
1. Input the MAFFT alignment into IQ-TREE. 
2. Use Maximum Likelihood tree construction. 
3. Perform bootstrap analysis with 1000 replicates. 
4. Generate the phylogenetic tree. 
Record: 
• 
Evolutionary model selected by IQ-TREE 
• 
Bootstrap settings 
• 
Tree file generated 
Include screenshots. 
 
Task 5: Tree Visualization and Interpretation 
Visualize the resulting phylogenetic tree. 
Analyze: 
1. Number of major clusters observed. 
2. Whether strains from the same country cluster together. 
3. Presence of distinct evolutionary lineages. 
4. Branches with strong bootstrap support (>70%). 
5. Possible explanations for observed clustering patterns. 
 
Task 6: Discussion 
Discuss the following: 
Question 1 
Why is sequence alignment required before phylogenetic analysis? 
Question 2 
What is the purpose of bootstrap analysis? 
Question 3 
How does the Maximum Likelihood approach differ from distance-based methods? 
Question 4 
What biological conclusions can be drawn from the generated tree? 
Question 5 
What are the limitations of this analysis? 
 
Report Structure 
1. Introduction 
2. Materials and Methods 
3. Results 
4. Discussion 
5. Conclusion 
6. References 
Expected report length: 1500–2500 words. 
 
Submission Requirements 
Submit: 
• 
PDF report 
• 
Original FASTA file 
• 
MAFFT alignment output 
• 
IQ-TREE output files 
• 
Galaxy workflow export 
 
 
 
Marking Scheme (100 Marks) 
Component 
Marks 
Data Retrieval and Documentation 
15 
Data Preparation 
10 
MAFFT Alignment 
15 
IQ-TREE Analysis 
20 
Tree Interpretation 
20 
Discussion and Biological Understanding 10 
Report Presentation and References 
10 
Total 
100 
 
Bonus Challenge (+10 Marks) 
Compare phylogenetic trees generated using: 
• 
100 bootstrap replicates 
• 
1000 bootstrap replicates 
Discuss how bootstrap values influence confidence in evolutionary relationships. 
 
Expected Deliverable 
A reproducible Galaxy workflow that downloads Dengue virus genome sequences, 
performs multiple sequence alignment using MAFFT, constructs a phylogenetic tree 
using IQ-TREE, and provides a biological interpretation of the observed evolutionary 
relationships among Asian human-derived Dengue virus isolates. 
 
