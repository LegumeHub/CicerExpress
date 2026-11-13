# CicerExpress v1.0

**CicerExpress: An interactive expression atlas for tissue-specific gene discovery, candidate-gene prioritization and functional enrichment in chickpea**

## Overview

CicerExpress is an interactive web resource for exploring gene expression across 32 chickpea tissues and developmental stages. All gene identifiers and coordinates follow the **CDC Frontier v2.0** reference genome and annotation (`cicar.CDCFrontier.gnm2.ann1.9M1L`, Legume Information System). Query the site with gene IDs such as `Ca_00001` and chromosomes Ca01–Ca08.

The website integrates expression data, gene annotations, transcription-factor information, Gene Ontology terms, InterPro and Pfam annotations, marker genes, housekeeping candidates, and chromosome information.

## Main Features

- eFP-style gene expression atlas
- Gene expression bar plots
- Mean and median expression summaries
- Multi-gene heatmaps with user-defined color-scale limits, palettes, clustering and PNG/SVG/CSV export
- GWAS candidate gene search for single SNPs or batch SNP lists, with expression class, Tau, peak tissue, marker status and TF family for each candidate, and multi-sheet Excel export
- Send GWAS candidates directly to the heatmap, enrichment modules and chromosome mapper
- Transcription-factor portal
- Gene Ontology enrichment
- InterPro and Pfam enrichment (selectable background and multiple-testing correction; raw and adjusted P-values reported)
- Editable chromosome mapper
- Downloadable tables and figures

## Transcriptomic Dataset

RNA-seq data were obtained from:

**NCBI BioProject:** PRJNA622231

https://www.ncbi.nlm.nih.gov/bioproject/PRJNA622231

Reference:

Jain M, Bansal J, Rajkumar MS, Garg R. An integrated transcriptome mapping the regulatory network of coding and long non-coding RNAs provides a genomics resource in chickpea. *Communications Biology*. 2022;5:1106.

## Transcriptomic Analysis

The analysis workflow included:

1. Download of RNA-seq reads from NCBI SRA
2. Quality assessment using FastQC
3. Adapter and quality trimming using Trimmomatic
4. Transcript quantification using Salmon
5. Gene-level summarization using tximport
6. TPM matrix generation
7. Replicate summarization across tissues (median TPM; mean TPM also provided)
8. Gene-expression classification
9. Tissue-specificity analysis
10. Marker-gene identification
11. TF-family analysis
12. GO enrichment
13. InterPro and Pfam enrichment

Gene expression was summarized across 32 tissues as the median TPM of biological replicates; all website modules use the median matrix. Gene IDs were standardized where needed for integration across expression and annotation files.

## Enrichment Analysis

GO, InterPro, and Pfam enrichment analyses use:

- One-sided Fisher’s exact test (hypergeometric upper tail), implemented in JavaScript and computed in the browser
- Multiple-testing correction within each gene set and ontology/database: Benjamini–Hochberg (default; reported as Adjusted_P), Bonferroni, or none
- Significance filter on adjusted P (default) or raw P; default cutoff 0.05
- Fold enrichment > 1
- At least three foreground genes
- At least five annotated genes in the tested set

Background options: (1) all atlas genes with at least one annotation in the selected ontology/database (default), (2) expressed atlas genes (median TPM ≥ 1 in at least one tissue) with annotation, or (3) a user-supplied list. The foreground is always restricted to the background. GO identifiers come from the CDC Frontier v2.0 GFF3; GO term names from GO.db; InterPro and Pfam assignments from the v2.0 GFF3 and InterProScan output.

## Reference Genome

CDC Frontier v2.0 genome assembly and annotation (cicar.CDCFrontier.gnm2.ann1.9M1L).

https://data.legumeinfo.org/Cicer/arietinum/annotations/CDCFrontier.gnm2.ann1.9M1L/

## Development Team

### Shubh Pravat Singh Yadav

College of Agriculture  
Tennessee State University  
Nashville, Tennessee, USA

Email: sushantpy8500@gmail.com

GitHub:  
https://github.com/sushantpy8500

ORCID:  
https://orcid.org/0000-0003-3987-5616

### Kuber Shivashakarappa

College of Agriculture  
Tennessee State University  
Nashville, Tennessee, USA

Email: kshivash@my.tnstate.edu

## Faculty Advisors

### Dr. Lyle T. Wallace

College of Agriculture  
Tennessee State University

Email: lwalla10@tnstate.edu

### Dr. Ali Taheri

College of Agriculture  
Tennessee State University

Email: ali.taheri@tnstate.edu

## Repository Structure

```text
Chickpea-Genomics-Atlas/  (CicerExpress)
│
├── index.html
├── style.css
├── app.js
├── README.md
├── LICENSE
│
├── assets/
│   ├── atlas_logo.png
│   ├── Chickpea_gene_expression_atlas_RK.svg
│   └── team/
│       ├── Shubh.jpg
│       ├── Kuber.png
│       ├── Dr. Wallace.jpg
│       └── Dr. Taheri.jpg
│
└── data/
    ├── TPM_median_RK.csv   (median TPM; used by the website)
    ├── TPM_mean_RK.csv     (mean TPM)
    ├── gene_annotation.csv
    ├── website_gene_master.csv
    ├── high_confidence_tissue_marker_genes.csv
    ├── candidate_housekeeping_genes.csv
    ├── GO_gene_mapping_with_terms.csv
    ├── combined_gene_domain_mapping.csv
    ├── interpro_pfam_domain_reference.csv
    └── chickpea_chromosome_lengths.csv

RK

## Version

### v1.0
- Expression atlas of 25,001 CDC Frontier v2.0 genes across 32 tissues (median TPM; mean TPM in Downloads).
- eFP view, bar plots, mean/median summaries and multi-gene heatmaps with user-defined color-scale limits, clustering and PNG/SVG/CSV export.
- Single and batch GWAS candidate-gene search with expression annotation and multi-sheet Excel export; send-to buttons for heatmap, enrichment and chromosome mapper.
- GO, InterPro and Pfam enrichment with selectable background and multiple-testing correction.
- TF portal (1,515 TF genes, 57 families) and an editable chromosome mapper.
