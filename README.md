# -osteogenesis-gene-expression
# Transcriptomic Analysis of Osteogenic Differentiation in hMSC

## Overview

This project investigates gene-expression changes during osteogenic
differentiation of human mesenchymal stromal cells using the GEO dataset GSE185951.

## Research question

How does gene expression change during osteogenic differentiation,
and which biological processes are consistently associated with this transition across donors?

## Dataset

- GEO accession: GSE185951
- Organism: Homo sapiens
- Cell type: human mesenchymal stromal cells
- Donors: 5
- Time points: day 0, day 7, day 14
- Samples: 15
- Data type: RNA-seq

## Methods

- Gene annotation using GENCODE v37
- Log-transformed expression analysis
- Principal component analysis
- Cross-donor consistency analysis
- Gene Ontology and Reactome enrichment analysis

## Main findings

Preliminary analysis identified a clear transcriptional shift between
undifferentiated cells at day 0 and cells undergoing osteogenic
differentiation at days 7 and 14.

Principal component analysis showed that PC1 explained 27.57% of the
total variance and PC2 explained 15.14%. Day-0 samples were generally
separated from day-7 and day-14 samples, while one day-14 sample from
donor 7083 showed strong donor-specific variation.

A cross-donor consistency analysis identified:

- 1,215 consistently upregulated genes;
- 736 consistently downregulated genes.

The upregulated genes were enriched in biological processes related to
osteogenesis, including ossification, osteoblast differentiation, bone
mineralization, bone development, extracellular matrix organization,
and cell adhesion. BMP- and Wnt-related signaling processes were also
enriched.

Inflammatory, cytokine-related, and lipid-metabolic processes were
additionally enriched, indicating that osteogenic differentiation
involves broader transcriptional changes beyond bone-related pathways.

These findings are preliminary and will be complemented by the analysis
of downregulated-gene enrichment, additional visualizations, and more
formal statistical testing.

## Repository structure

- `GSE185951_analysis.ipynb` — analysis notebook
- `results/` — figures and tables
- `research_notes.md` — research documentation

## Limitations

This is an exploratory analysis based on a normalized expression matrix.
The cross-donor consistency analysis is not a replacement for formal
differential-expression modelling.
