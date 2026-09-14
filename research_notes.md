# Transcriptomic Analysis of Osteogenic Differentiation in hMSC

## 1. Research Question

How does gene expression change during osteogenic differentiation of human
mesenchymal stromal cells, and which biological processes are consistently
associated with this transition across donors?

## 2. Dataset

The analysis used the GEO dataset GSE185951, which contains RNA-seq
expression data from human mesenchymal stromal cells undergoing
osteogenic differentiation.

| Parameter | Value |
|---|---|
| GEO accession | GSE185951 |
| Organism | Homo sapiens |
| Cell type | Human mesenchymal stromal cells |
| Donors | 5 |
| Time points | Day 0, Day 7, Day 14 |
| Total samples | 15 |
| Data type | RNA-seq |
| Expression matrix | Normalized counts |
| Gene annotation | GENCODE v37 |

## 3. Methods

## 3. Data Preprocessing

The normalized expression matrix was loaded and inspected for its
dimensions, gene identifiers, sample columns, and missing values.

Ensembl gene identifiers contained version suffixes, such as
`ENSG00000000003.15`. These suffixes were removed to obtain base Ensembl
gene identifiers for annotation.

Gene identifiers were matched to gene symbols and gene types using
GENCODE v37 annotation. Duplicate or alternative annotation entries
were checked, and a unique gene-level annotation table was prepared.

The final annotated dataset contained 60,607 genes and 19 columns,
including gene annotation fields and sample expression values.

## 4. Exploratory Analysis

To reduce the influence of genes with very low expression, genes were
filtered by requiring expression greater than 1 in at least three samples.

The expression values were transformed using:

`log2(expression + 1)`

Principal component analysis (PCA) was then performed on the filtered,
log-transformed expression matrix to examine overall sample structure
and variation between differentiation stages and donors.

The filtered matrix contained 25,840 genes.

## 5. PCA Results

The first principal component (PC1) explained 27.57% of the total
variance, while the second principal component (PC2) explained 15.14%.

Day-0 samples were generally separated from day-7 and day-14 samples,
indicating a substantial transcriptional change during osteogenic
differentiation.

The day-14 sample from donor 7083 showed a pronounced deviation along
PC2. This pattern may reflect donor-specific transcriptional variation.
However, the PCA result alone is insufficient to classify this sample
as a technical failure or to determine the biological cause of the
deviation.

## 6. Osteogenic Marker Analysis

The expression of selected osteogenesis-related genes was examined,
including `ALPL`, `RUNX2`, `IBSP`, `SP7`, and `BGLAP`.

`ALPL` showed an increase during differentiation, particularly by day 7.
The patterns of `RUNX2`, `IBSP`, and `SP7` were more variable across
donors.

`BGLAP` showed low expression in the analyzed samples. Therefore, the
results support the activation of an osteogenic transcriptional program,
but they do not establish that all samples reached a fully mature,
mineralizing osteoblast state.

## 7. Cross-Donor Consistency Analysis

To identify gene-expression changes that were consistent across donors,
day-14 expression was compared with day-0 expression separately for
each donor.

For each gene and donor, the change was calculated as:

`log2(expression_day14 + 1) - log2(expression_day0 + 1)`

Genes were classified as consistently upregulated when:

- the log2 expression change was positive in all five donors;
- the mean log2 change was at least 1;
- the mean expression across samples was at least 5.

Genes were classified as consistently downregulated when:

- the log2 expression change was negative in all five donors;
- the mean log2 change was at most -1;
- the mean expression across samples was at least 5.

This approach focuses on reproducible directional changes across donors.
It is a consistency-based exploratory analysis and does not provide
formal gene-level statistical significance.


## 8. Consistent Gene-Expression Changes

Using the cross-donor consistency criteria, 1,215 genes were identified
as consistently upregulated between day 0 and day 14.

A total of 736 genes were identified as consistently downregulated.

The most prominent upregulated genes included genes associated with
extracellular matrix organization, stromal-cell biology, osteogenesis,
inflammatory signaling, and lipid metabolism.

Examples of highly upregulated genes included `SAA1`, `SAA2`, `OMD`,
`ZBTB16`, `CHRDL1`, `LBP`, `OGN`, `FRZB`, `PRELP`, and `RSPO3`.

The downregulated gene set included several keratin-associated genes,
regulatory genes, and genes involved in signaling and extracellular
matrix-related processes.


## 9. Functional Enrichment Analysis

Functional enrichment analysis was performed using g:Profiler with
Gene Ontology Biological Process and Reactome sources.

### 9.1 Upregulated genes

The consistently upregulated gene set showed significant enrichment
for several processes related to osteogenic differentiation and
extracellular matrix remodeling.

The most relevant enriched processes included:

- Cell adhesion
- Ossification
- Extracellular matrix organization
- Osteoblast differentiation
- Bone mineralization
- BMP signaling
- Wnt signaling
- Bone development
- Response to cytokines
- Inflammatory response
- Lipid metabolic processes

The enrichment of ossification, osteoblast differentiation, bone
mineralization, and bone development is consistent with the expected
biological direction of osteogenic differentiation.

At the same time, enrichment of inflammatory, cytokine-related, and
lipid-metabolic processes indicates that the transcriptional response
involves additional cellular programs beyond osteogenesis alone.



### Selected enriched processes among consistently upregulated genes

| Biological process | Gene overlap | Adjusted p-value |
|---|---:|---:|
| Cell adhesion | 152 | 1.68 × 10⁻¹⁸ |
| Ossification | 65 | 1.13 × 10⁻¹⁵ |
| Extracellular matrix organization | 53 | 6.82 × 10⁻¹⁵ |
| Osteoblast differentiation | 41 | 1.31 × 10⁻¹¹ |
| Bone mineralization | 27 | 8.28 × 10⁻¹⁰ |
| BMP signaling pathway | 30 | 2.10 × 10⁻⁹ |
| Bone development | 31 | 5.62 × 10⁻⁷ |
| Wnt signaling pathway | 50 | 5.33 × 10⁻⁷ |
