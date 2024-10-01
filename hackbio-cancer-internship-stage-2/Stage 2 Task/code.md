<h1 align="center"> Visualization, Differential Expression Analysis and Downstream Analysis of Glioma Transcriptomics Count Data </h1>

The whole analysis will use a [count dataset of glioblastoma transcriptomic samples](https://raw.githubusercontent.com/HackBio-Internship/public_datasets/main/Cancer2024/glioblastoma.csv).
# Installing gplots for visualization
```{r, echo=TRUE, message=FALSE, warning=FALSE, results='hide'}
install.packages("gplots")
library("gplots")
```
# Generating Matrix from a CSV file
```{r}
gene_data <- read.csv('https://raw.githubusercontent.com/HackBio-Internship/public_datasets/main/Cancer2024/glioblastoma.csv', row.names=1)
mat <- as.matrix(gene_data)
#log_data_matrix <- log2(mat+1) #log transformation of matrix as data range is too broad
#head(log_data_matrix)
```
# Heatmap using diverging color palette
```{r, fig.width=10, fig.height=10}
col_palette <- colorRampPalette(brewer.pal(11, "RdBu"))(100)
heatmap.2(x=mat, col = col_palette, 
          density.info = 'none', dendrogram = 'both',
          scale = 'row', trace = 'none')
```
# Heatmap using sequential color palette
```{r, fig.width=10, fig.height=10}
col_palette <- colorRampPalette(brewer.pal(9, "Blues"))(100)
heatmap.2(x=mat, col = col_palette, 
          density.info = 'none', dendrogram = 'both',
          scale = 'row', trace = 'none')
```
# Clustering Genes (rows) Alone
```{r, fig.width=10, fig.height=10}
col_palette <- colorRampPalette(brewer.pal(11, "RdBu"))(100)
heatmap.2(x=mat, col = col_palette, 
          density.info = 'none', dendrogram = 'row',
          scale = 'row', trace = 'none',
          Romv = TRUE, Colv = FALSE)
```
# Clustering Samples (columns) Alone
```{r,fig.width=10, fig.height=10}
col_palette <- colorRampPalette(brewer.pal(11, "RdBu"))(100)
heatmap.2(x=mat, col = col_palette, 
          density.info = 'none', dendrogram = 'col',
          scale = 'row', trace = 'none',
          Romv = FALSE, Colv = TRUE)
```
# Clustering both Genes and Samples
```{r,fig.width=10, fig.height=10}
col_palette <- colorRampPalette(brewer.pal(11, "RdBu"))(100)
heatmap.2(x=mat, col = col_palette, 
          density.info = 'none', dendrogram = 'both',
          scale = 'row', trace = 'none',
          Romv = TRUE, Colv = TRUE)
```
# Calculate fold change
```{r, echo=TRUE, message=FALSE, warning=FALSE, results='hide'}
# group samples using index positions
group1 <- c(1,2,3,4,5)
group2 <- c(6,7,8,9,10)
# separate treatment and control data
group1_data <- gene_data[, group1]
group2_data <- gene_data[, group2]
# Calculate the mean for control and treatment groups
group1_mean <- rowMeans(group1_data)
group2_mean <- rowMeans(group2_data)
# Calculate log2 fold change
log2_fold_change = log2(group1_mean/group2_mean)
log2_fold_change
```
# Preparation for Differential Expression Analysis
```{r}
# Calculate the pvalues of fold changes
pvalues <- apply(gene_data, 1, function(row) {
  t.test(row[1:5], row[6:10])$p.value
})
pvalues
```

# Filtering out Significant Genes (padj <0.05 and fold change cutoff 2)
```{r}
# Subset for significant genes with p-value < 0.05 AND log2 fold change > 1
significant_genes_up <- (pvalues < 0.05) & (log2_fold_change > 1)

# Subset p-values and log2 fold change that meet the criteria for significantly up-regulated genes.
filtered_pvalues_up <- pvalues[significant_genes_up]
filtered_log2fc_up <- log2_fold_change[significant_genes_up]

# Print the results
filtered_pvalues_up
filtered_log2fc_up

# Subset for significant genes with p-value < 0.05 AND log2 fold change < -1
significant_genes_down <- (pvalues < 0.05) & (log2_fold_change < -1)

# Subset p-values and log2 fold change that meet the criteria for significantly down-regulated genes.
filtered_pvalues_down <- pvalues[significant_genes_down]
filtered_log2fc_down <- log2_fold_change[significant_genes_down]

# Print the results
filtered_pvalues_down
filtered_log2fc_down
```
# Exporting genes, fold change and adjacent p values to CSV file
```{r}

background_genes <- data.frame(gene = names(pvalues), log2FC = as.vector(log2_fold_change), pval = as.vector(pvalues))
DE_significantly_up_genes <- data.frame(gene = names(filtered_pvalues_up), log2FC = as.vector(filtered_log2fc_up), pval = as.vector(filtered_pvalues_up))
DE_significantly_down_genes <- data.frame(gene = names(filtered_pvalues_down), log2FC = as.vector(filtered_log2fc_down), pval = as.vector(filtered_pvalues_down))

# Exporting into a CSV file
write.csv(background_genes, "background_genes.csv", row.names = FALSE)
write.csv(DE_significantly_up_genes, "DE_significantly_up_genes.csv", row.names = FALSE)
write.csv(DE_significantly_down_genes, "DE_significantly_down_genes.csv", row.names = FALSE)
```
# Visualization of Biological Process Pathways

Using the default parameters in [ShinyGO 0.80](http://bioinformatics.sdstate.edu/go/), for 10 significantly differential expressed genes, we found the following top 5 enriched biological pathways, visualizated using R

```{r, echo=FALSE, fig.width=10, fig.height=10}
# Install and load ggplot2 package
install.packages("ggplot2")
library(ggplot2)

# Load the CSV data
pathways <- read.csv("https://raw.githubusercontent.com/shalaka98/hackbio-cancer-internship/0bb318818951e6d5d1b583e41a4caaecd33c5a44/Stage%202%20Task/data/enrichment.csv")

# Calculate -log10 of FDR for significance
pathways$logFDR <- -log10(pathways$Enrichment.FDR)

# Create a lollipop plot
ggplot(pathways, aes(x = nGenes, y = reorder(Pathway, nGenes))) +
  geom_segment(aes(xend = 0, yend = reorder(Pathway, nGenes)), color = "grey") +
    geom_point(aes(size = logFDR), color = "blue") +
    scale_size_continuous(range = c(2, 10)) +  # Adjust size range for logFDR
    labs(x = "Number of Genes", y = "Pathway", size = "-log10(FDR)",  
       title = "Top 5 Pathways Enriched by Genes") +
    theme_minimal() +
    theme(axis.text.y = element_text(size = 10))

```
