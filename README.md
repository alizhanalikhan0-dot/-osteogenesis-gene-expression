# Transcriptomic Analysis of Osteogenic Differentiation in hMSC

## Overview

This project investigates gene-expression changes during osteogenic
differentiation of human mesenchymal stromal cells using the GEO dataset
GSE185951.

The analysis focuses on transcriptional changes across three time points
and identifies biological processes that are consistently associated with
the transition toward osteogenic differentiation across multiple donors.

## Research question

How does gene expression change during osteogenic differentiation,
and which biological processes are consistently associated with this
transition across donors?

## Dataset

- GEO accession: [GSE185951](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE185951)
- Organism: Homo sapiens
- Cell type: Human mesenchymal stromal cells
- Donors: 5
- Time points: Day 0, day 7, and day 14
- Samples: 15
- Data type: RNA-seq
- Expression data: Normalized gene-expression matrix

## Methods

The analysis was performed in Python using Google Colab.

Main steps included:

- Gene annotation using GENCODE v37
- Expression-data preprocessing and filtering
- Log2-transformation of expression values
- Principal component analysis (PCA)
- Analysis of osteogenic marker genes
- Cross-donor consistency analysis
- Gene Ontology (GO) enrichment analysis
- Reactome pathway enrichment analysis
- Visualization of transcriptional patterns

## Main findings

### Global transcriptional changes

The analysis identified a clear transcriptional shift between day-0 cells
and cells collected during osteogenic differentiation at days 7 and 14.

Principal component analysis showed that:

- PC1 explained 27.57% of the total variance;
- PC2 explained 15.14% of the total variance.

Day-0 samples were generally separated from day-7 and day-14 samples,
indicating substantial changes in global gene-expression patterns during
differentiation.

One day-14 sample from donor 7083 showed strong donor-specific variation,
particularly along PC2. This suggests that the transcriptional response
at the late time point was not completely uniform across donors.

### Osteogenic marker expression

Several osteogenesis-associated genes showed increased or variable
expression during differentiation.

- `ALPL` showed a clear increase by day 7 and remained elevated.
- `RUNX2` showed a more modest and heterogeneous pattern.
- `IBSP` showed variable increases across donors.
- `SP7` displayed heterogeneous expression changes.
- `BGLAP` expression was very low or nearly absent in the analyzed matrix.

These results are consistent with activation of osteogenic transcriptional
programs, but the low expression of `BGLAP` means that strong conclusions
about fully mature mineralization cannot be made from this dataset alone.

### Cross-donor consistency

A paired comparison of day 14 versus day 0 was performed separately for
each donor.

Genes were classified as consistently regulated when they changed in the
same direction across all five donors. A stricter exploratory filter was
then applied using:

- consistent direction of change across all donors;
- mean log2 fold change of at least 1 for upregulated genes or at most -1
  for downregulated genes;
- mean expression of at least 5.

This analysis identified:

- **1,215 consistently upregulated genes**
- **736 consistently downregulated genes**

The complete gene lists and log2 fold-change values are available in the
[`results/tables/`](results/tables/) directory.

### Enrichment of upregulated genes

Upregulated genes were enriched in biological processes associated with
osteogenic differentiation and extracellular remodeling, including:

- Ossification
- Osteoblast differentiation
- Bone mineralization
- Bone development
- Extracellular matrix organization
- Cell adhesion
- BMP-related signaling
- Wnt-related signaling

Additional enrichment was observed for inflammatory, cytokine-related,
stress-response, and lipid-metabolic processes.

This indicates that the transcriptional response to osteogenic induction
involves not only bone-related pathways but also broader changes in
extracellular signaling, metabolism, and cellular stress responses.

### Enrichment of downregulated genes

Downregulated genes were enriched in processes related to:

- Anatomical structure development
- Tissue and organ development
- Cell differentiation
- Cell adhesion
- Cell communication
- Cell migration
- Extracellular matrix organization
- Blood vessel development
- Angiogenesis
- Nervous system development

These results should be interpreted as changes in the expression of genes
associated with these processes rather than proof that each entire
biological process was globally inhibited.

The presence of extracellular-matrix and cell-adhesion terms in both
upregulated and downregulated gene sets may reflect coordinated remodeling
of different components of these systems.

## Results

The main output files are organized as follows:

- [`results/tables/`](results/tables/) — processed tables and gene-level results
- [`results/figures/`](results/figures/) — PCA plots and visualizations
- [`results/enrichment/`](results/enrichment/) — GO and Reactome enrichment results

Important files include:

- `consistent_upregulated_genes.csv`
- `consistent_downregulated_genes.csv`
- `day14_vs_day0_log2FC_all_genes.csv`
- `pca_coordinates.csv`
- `pca_explained_variance.csv`
- `enrichment_upregulated_significant.csv`
- `enrichment_downregulated_significant.csv`

## Repository structure

```text
.
├── GSE185951_analysis.ipynb
├── research_notes.md
├── README.md
└── results/
    ├── tables/
    │   ├── consistent_downregulated_genes.csv
    │   ├── consistent_upregulated_genes.csv
    │   ├── day14_vs_day0_log2FC_all_genes.csv
    │   ├── pca_coordinates.csv
    │   └── pca_explained_variance.csv
    ├── figures/
    │   ├── pca_by_day.png
    │   └── pca_plot.png
    └── enrichment/
        ├── enrichment_downregulated_all.csv
        ├── enrichment_downregulated_significant.csv
        ├── enrichment_upregulated_all.csv
        └── enrichment_upregulated_significant.csv



## Limitations

This project is an exploratory analysis based on a normalized expression
matrix rather than raw sequencing reads.

The main limitations are:

- The analysis does not include raw FASTQ processing or read alignment.
- The cross-donor consistency approach is not a replacement for formal
  differential-expression modelling.
- No complete statistical model accounting for donor effects was applied.
- The gene lists were generated using exploratory fold-change and expression
  thresholds.
- Enrichment results depend on the selected gene sets and filtering criteria.
- Low expression of some late osteogenic markers limits conclusions about
  terminal differentiation and mineralization.
- The day-14 sample from donor 7083 showed substantial donor-specific
  variation.

Future improvements could include formal differential-expression analysis
using a model that accounts for donor pairing, multiple-testing correction,
and additional validation using independent datasets or experimental
measurements.

## Reproducibility

The analysis notebook and generated results are provided in this repository.

The workflow can be reproduced by running the cells in the analysis notebook:

[`GSE185951_analysis.ipynb`](GSE185951_analysis.ipynb)
