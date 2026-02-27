# ML-BASED MUTATION SENSITIVITY PROFILING IN VIRAL GENOMES

## Project Overview

This project presents a computational bioinformatics framework for identifying mutation-sensitive and mutation-tolerant regions within a viral coding DNA sequence (CDS).

Using codon-level mutation simulation, protein translation analysis, feature engineering, and unsupervised machine learning, the study models how local genomic regions respond to all possible single-nucleotide substitutions.

The framework was implemented and evaluated on the complete coding sequence of Snake River Alfalfa Virus (SRAV).

---

## Objective

To develop a systematic and interpretable computational pipeline that:

- Simulates all possible single-nucleotide substitutions at the codon level
- Translates DNA mutations into protein-level consequences
- Quantifies mutation behavior using engineered genomic features
- Applies unsupervised learning to classify genomic regions based on mutation sensitivity

---

## Methodology

### 1. Data Input

- Viral Coding DNA Sequence (CDS) loaded from FASTA format
- Sequence validated and trimmed to ensure divisibility by 3

### 2. Codon-Level Mutation Simulation

For each codon in the CDS:

- All possible single-nucleotide substitutions (9 per codon) were generated
- Mutated codons were translated into amino acids using Biopython
- Mutations were classified as:
  - Synonymous (no protein change)
  - Missense (amino acid change)
  - Nonsense (premature stop codon)

A detailed mutation-level dataframe was created containing:

- Original codon
- Mutated codon
- Original amino acid
- Mutated amino acid
- Mutation classification

This ensures transparent DNA-to-protein translation validation.

### 3. Sliding Window Analysis

To capture regional mutation behavior:

- Window size: 15 codons
- Step size: 3 codons

This approach provides broader biological context and reduces discretization artifacts observed in smaller windows.

### 4. Feature Engineering

For each window, the following features were computed:

- Synonymous mutation percentage
- Missense mutation percentage
- Nonsense mutation percentage
- Missense-to-Synonymous ratio
- GC content
- Shannon entropy of mutation distribution

These features quantify mutation diversity, functional constraint, and sequence composition influence.

### 5. Feature Scaling

All features were standardized to prevent bias due to scale differences before clustering.

### 6. Dimensionality Reduction

Principal Component Analysis (PCA) was applied to:

- Reduce feature redundancy
- Improve cluster separability
- Enable visualization of mutation behavior in two-dimensional space

### 7. Unsupervised Learning

K-Means clustering was used to group genomic windows based on mutation behavior.

The optimal number of clusters was determined using the Elbow Method to ensure statistical justification.

Clusters were interpreted as:

- Mutation-tolerant regions (high synonymous percentage, low nonsense percentage)
- Mutation-sensitive regions (high missense or nonsense percentage, high ratio, high entropy)

### 8. Genome-Wide Mutation Landscape

Mutation metrics were plotted against genomic position to visualize:

- Regional mutation trends
- Functional constraint variation across the CDS
- Cluster distribution along the genome

---

## Technologies Used

- Python
- Biopython
- NumPy
- Pandas
- Scikit-learn
- Matplotlib
- Seaborn

---

## Key Contributions

- Developed a codon-level mutation simulation engine
- Implemented explicit DNA-to-protein translation validation
- Engineered biologically meaningful mutation features
- Applied PCA and K-Means clustering for mutation sensitivity profiling
- Built a reproducible computational genomics pipeline

---

## Scientific Significance

This framework demonstrates how computational methods can be used to:

- Quantify mutation effects without experimental data
- Model functional constraint across viral genomes
- Identify regions potentially critical for viral stability
- Bridge genomics and machine learning for biological interpretation

---

## Future Improvements

- Domain-level mapping of mutation-sensitive regions
- Integration with structural protein annotations
- Comparative analysis across multiple viral strains
- Incorporation of evolutionary conservation metrics

---

## How to Run

1. Upload the viral CDS FASTA file.
2. Update the file path in the notebook.
3. Run all cells sequentially.
4. Inspect mutation dataframe, feature table, PCA plots, and cluster results.

---

## Author

Dhanush P  
Integrated M.Tech CSE (Business Analytics)  
Bioinformatics Project – Mutation Sensitivity Analysis
