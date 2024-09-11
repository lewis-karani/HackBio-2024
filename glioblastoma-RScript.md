```
# Install gplots if not already installed
if (!require("gplots")) install.packages("gplots")

# Load dataset
glioblastoma <- read.csv("https://raw.githubusercontent.com/HackBio-Internship/public_datasets/main/Cancer2024/glioblastoma.csv")

# Load package library
library(gplots)

# Extract Ensembl IDs and numeric data
gene_ids <- glioblastoma[, 1]  # Ensembl IDs
expression_data <- glioblastoma[, 2:11]  # Gene expression data for heatmap
rownames(expression_data) <- gene_ids  # Set row names to Ensembl IDs

# Convert data frame to a numeric matrix for heatmap2
data_matrix <- as.matrix(expression_data)

# log transformation of matrix 
log_data_matrix <- log2(data_matrix+1) 

# Set output parameters
par(mar = c(10, 10, 10, 10))

# Heatmap using diverging color pallete
col_palette <- colorRampPalette(c('blue','yellow','red'))(n=300)
heatmap.2(x=log_data_matrix, col = col_palette, density.info = 'none', key = TRUE, keysize = 1.0, lhei = c(0.5, 4), lwid = c(1.5, 4), main = "Diverging heat map", cexRow = 0.8, cexCol = 0.8, key.title = "Fold change", key.xlab = "Expression")

#Heatmap using sequential color pallete
col_palette <- colorRampPalette(c('blue','yellow'))(n=300)
heatmap.2(x=log_data_matrix, col = col_palette, density.info = 'none', keysize = 1.0, lhei = c(0.5, 4), lwid = c(1.5, 4), main = "Sequential heat map", cexRow = 0.8, cexCol = 0.8, key.title = "Fold change", key.xlab = "Expression")

# Cluster rows(genes) only
col_palette <- colorRampPalette(c('blue','yellow','red'))(n=300)
heatmap.2(x=log_data_matrix, col = col_palette, density.info = 'none', dendrogram = 'row', Rowv = TRUE, Colv = FALSE, keysize = 1.0, lhei = c(0.5, 4), lwid = c(1.5, 4), main = "Clustered rows heat map", cexRow = 0.8, cexCol = 0.8, key.title = "Fold change", key.xlab = "Expression")

# Cluster columns(samples) only
col_palette <- colorRampPalette(c('blue','yellow','red'))(n=300)
heatmap.2(x=log_data_matrix, col = col_palette, density.info = 'none', dendrogram = 'column', Rowv = FALSE, Colv = TRUE, keysize = 1.0, lhei = c(0.5, 4), lwid = c(1.5, 4), main = "Clustered columns heat map", cexRow = 0.8, cexCol = 0.8, key.title = "Fold change", key.xlab = "Expression")
         
# Cluster both rows(genes) and column (samples)
col_palette <- colorRampPalette(c('blue','yellow','red'))(n=300)
heatmap.2(x=log_data_matrix, col = col_palette, density.info = 'none', Rowv = TRUE, Colv = TRUE, keysize = 1.0, lhei = c(0.5, 4), lwid = c(1.5, 4), main = "Clustered rows & columns heat map", cexRow = 0.8, cexCol = 0.8, key.title = "Fold change", key.xlab = "Expression")

# Install DESeq2 if not already installed
if (!requireNamespace("DESeq2", quietly = TRUE)) {
  install.packages("BiocManager")
  BiocManager::install("DESeq2")
}
# Load DESeq2 library
library(DESeq2)

# Check if the expression data is in integer format (DESeq2 requires count-like data)
expression_data <- round(expression_data)  # If the data is non-integer, round it to integers
# Define conditions based on sample names: "Primary" for 01A/01B, "Recurrent" for 02A
conditions <- ifelse(grepl("01[AB]", colnames(expression_data)), "Primary", "Recurrent")

# Create a DataFrame to hold the condition metadata
colData <- data.frame(condition = conditions)
rownames(colData) <- colnames(expression_data)
# Create a DESeqDataSet object
dds <- DESeqDataSetFromMatrix(countData = expression_data,
                              colData = colData,
                              design = ~ condition)
# Run the DESeq analysis
dds <- DESeq(dds)

# Get the results
results <- results(dds, contrast = c("condition", "Recurrent", "Primary"))
# Order results by adjusted p-value
results <- results[order(results$padj), ]
# Keep only significant genes
sig_genes <- subset(results, padj < 0.05)
# Subset for upregulated genes (log2FoldChange > 1 )
up <- subset(sig_genes, log2FoldChange > 1)

# Subset for downregulated genes (log2FoldChange < -1 )
down <- subset(sig_genes, log2FoldChange < -1)

# Save results to CSV files
write.csv(as.data.frame(results), "results.csv", row.names = TRUE)
write.csv(as.data.frame(sig_genes), "sig_genes.csv", row.names = TRUE)
write.csv(as.data.frame(up), "upregulated_genes.csv", row.names = TRUE)
write.csv(as.data.frame(down), "downregulated_genes.csv", row.names = TRUE)

```
