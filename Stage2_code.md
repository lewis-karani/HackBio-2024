```
# Load necessary libraries
library(gplots)
library(RColorBrewer)

# Step 2: Load the dataset from the URL

glioblastoma <- read.csv("https://raw.githubusercontent.com/HackBio-Internship/public_datasets/main/Cancer2024/glioblastoma.csv")

# Extract Ensembl IDs and numeric data
gene_ids <- glioblastoma[, 1]  # Ensembl IDs
expression_data <- glioblastoma[, 2:11]  # Gene expression data for heatmap
rownames(expression_data) <- gene_ids  # Set row names to Ensembl IDs

# Define the gene with unfavoravble outcome to highlight
highlight_gene <- "ENSG00000135439"

# Define colors
highlight_color <- "red"
default_palette <- colorRampPalette(c("white", "blue"))(100)

# Generate the heatmap
heatmap.2(
  as.matrix(expression_data),
  col = default_palette,                 # Color palette
  trace = "none",               # No trace lines
  dendrogram = "both",          # Cluster both rows and columns
  Rowv = TRUE,                  # Cluster rows
  Colv = TRUE,                  # Cluster columns
  main = "Heatmap with Highlighted Gene",
  key.title = "Expression",
  key.xlab = "Expression level",
  key.ylab = "Frequency",
  labRow = rownames(expression_data),
  labCol = colnames(expression_data),
  colsep = 1:ncol(expression_data),  # Separate columns for clarity
  rowsep = which(rownames(expression_data) == highlight_gene),  # Add separator for highlighted row
  sepcolor = "black",             # Color of the separator line
  sepwidth = c(0.1, 0.1)         # Width of the separator line
)

# Cluster genes by expression (rows) alone
heatmap.2(
  as.matrix(expression_data),
  col = default_palette,               # Use the default color palette
  trace = "none",                     # No trace lines
  dendrogram = "row",                 # Cluster rows (genes) only
  Rowv = TRUE,                        # Cluster rows
  Colv = FALSE,                       # Do not cluster columns
  main = "Heatmap with Clustering of Genes Only",
  key.title = "Expression",
  key.xlab = "Expression level",
  key.ylab = "Frequency",
  labRow = rownames(expression_data),
  labCol = colnames(expression_data)
)
# Cluster by samples (columns) alone
heatmap.2(
  as.matrix(expression_data),
  col = default_palette,               # Use the default color palette
  trace = "none",                     # No trace lines
  dendrogram = "column",              # Cluster columns (samples) only
  Rowv = FALSE,                       # Do not cluster rows
  Colv = TRUE,                        # Cluster columns
  main = "Heatmap with Clustering of Samples Only",
  key.title = "Expression",
  key.xlab = "Expression level",
  key.ylab = "Frequency",
  labRow = rownames(expression_data),
  labCol = colnames(expression_data)
)
# Cluster both genes and samples
heatmap.2(
  as.matrix(expression_data),
  col = default_palette,               # Use the default color palette
  trace = "none",                     # No trace lines
  dendrogram = "both",                # Cluster both rows and columns
  Rowv = TRUE,                        # Cluster rows
  Colv = TRUE,                        # Cluster columns
  main = "Heatmap with Clustering of Both Genes and Samples",
  key.title = "Expression",
  key.xlab = "Expression level",
  key.ylab = "Frequency",
  labRow = rownames(expression_data),
  labCol = colnames(expression_data)
)
```


