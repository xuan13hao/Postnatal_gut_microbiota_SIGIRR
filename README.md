# Postnatal gut microbiota succession in mice is impacted by maturation, site, injury, and single immunoglobulin interleukin-1 related receptor (SIGIRR) genotype
## Overview
This repository contains data and analysis scripts for studying postnatal gut microbiota succession in mice, focusing on how gut microbiome composition evolves over time, across different intestinal sites, in response to injury, and under the influence of host genetics. The study involves novel transgenic SigirrMut mice encoding a SIGIRR p.Y168X mutation that disrupts postnatal intestinal adaptation.

## Data Processing and Analysis
### 16S rRNA Amplicon Sequencing
The 16S rRNA amplicon sequencing data was processed using **DADA2 v1.1**, generating an **Amplicon Sequence Variant (ASV) table**. The processing pipeline included:
- Quality trimming and filtering
- Dereplication
- Error rate estimation and denoising
- Merging paired-end reads
- Screening for mismatches and chimeric sequence removal

Taxonomic classification was performed using the **SILVA 132 reference database**. Further preprocessing was conducted via **MicrobiomeAnalyst**, applying:
- A **20% prevalence filter** and **minimum count threshold of 4** for low-abundance feature removal.
- Low variance feature removal using the **interquartile range (10% cutoff)**.
- Rarefaction of all samples to the sequencing depth of the sample with the lowest sequence count.
- Normalization using **Total Sum Scaling (TSS)**.

### Diversity Analysis
- **Alpha Diversity**: Calculated to assess microbial richness and evenness.
- **Beta Diversity**: Explored via **Nonmetric Multidimensional Scaling (NMDS) ordination** to visualize microbial composition differences across groups.

### Differential Abundance Analysis
- **Kruskal-Wallis Rank Sum Test**: Used to identify statistically significant differentially abundant taxa.
- **Linear Discriminant Analysis Effect Size (LEfSe)**: Employed for biomarker discovery and group differentiation.

### Functional Profiling
- **PICRUSt2**: Used to predict metagenomic functional potential based on 16S rRNA sequencing data.
- **MetaCyc & KEGG Pathways Analysis**: Performed using **STAMP**, applying appropriate statistical tests to identify significant differences between groups.

## Repository Contents
- `OTU/` - Contains all OTU data and statistical analysis scripts.
- `Picrust2/` - Includes Picrust2 metagenomic functional and statistical analysis scripts.
- `dada2.R` - Includes raw data processing process

## Installation and Usage
### Prerequisites
Ensure you have the following tools installed:
- R (`MicrobiomeAnalystR`)
- STAMP
- PICRUSt2 (for functional predictions)

### Running the Pipeline
1. Clone the repository:
   ```bash
   git clone https://github.com/xuan13hao/Postnatal_gut_microbiota_SIGIRR.git
   cd Postnatal_gut_microbiota_SIGIRR
   ```
2. Process 16S rRNA data using `DADA2`:
   ```r
   dada2.R
   ```

## Citation
If you use this repository, please cite:
> "Postnatal gut microbiota succession in mice is impacted by maturation, site, injury, and single immunoglobulin interleukin-1 related receptor (SIGIRR) genotype."

## License
This project is licensed under the MIT License - see the `LICENSE` file for details.

