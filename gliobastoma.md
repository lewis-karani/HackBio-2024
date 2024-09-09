# Generating heatmap from entire glioblastoma dataset

## steps followed listed below

### step 1: install package ` gplots `


```
install.packages("gplots") 
```
### Step 2: Load the dataset from the URL

```
glioblastoma <- read.csv("https://raw.githubusercontent.com/HackBio-Internship/public_datasets/main/Cancer2024/glioblastoma.csv")
```
### step 3: load library

```
library(gplots)
```
### Step 4: Ensure the data contains only numeric values

```
numeric_data <- glioblastoma[, sapply(glioblastoma, is.numeric)]
```

### Step 5: Convert the data frame to a matrix for heatmap.2

```
data_matrix <- as.matrix(numeric_data)
```
### Step 6: Generate the heatmap
```
heatmap.2(data_matrix,
          scale = "row",  # Normalize values across rows (genes)
          dendrogram = "both",  # Cluster both rows and columns
          trace = "none",  # Disable cell trace lines for clarity
          col = bluered(100),  # Use a red-blue color palette
          density.info = "none",  # No density plot on the margins
          key = TRUE,  # Show color key
          margins = c(10, 10),  # Margins for row and column labels
          lhei = c(1.5, 4),  # Layout height for key and plot
          lwid = c(1.5, 4),  # Layout width for row dendrogram and plot
          cexRow = 0.8,  # Adjust row text size
          cexCol = 0.8  # Adjust column text size
)
```
### Output heatmap
![Rplot](https://github.com/user-attachments/assets/177e829c-9074-4d15-8f56-07791c5fa395)


### Cluster rows (genes) only
```
heatmap.2(data_matrix,
          scale = "row",  # Scale across genes (rows)
          dendrogram = "row",  # Cluster only rows (genes)
          Rowv = TRUE,  # Enable row clustering
          Colv = FALSE,  # Disable column clustering
          trace = "none",
          col = bluered(100),
          density.info = "none",
          key = TRUE,
          margins = c(10, 10),
          cexRow = 0.8,
          cexCol = 0.8
)
```
### Output
![Rplot01](https://github.com/user-attachments/assets/0a5d0e07-6326-4d4c-bcc6-4cbf6931c740)

### Cluster columns (samples) only
```
heatmap.2(data_matrix,
          scale = "row",  # Scale across genes (rows)
          dendrogram = "column",  # Cluster only columns (samples)
          Rowv = FALSE,  # Disable row clustering
          Colv = TRUE,  # Enable column clustering
          trace = "none",
          col = bluered(100),
          density.info = "none",
          key = TRUE,
          margins = c(10, 10),
          cexRow = 0.8,
          cexCol = 0.8
)
```
### Output
![Rplot02](https://github.com/user-attachments/assets/dc23ce0a-9321-49f6-820c-e2dddca2e1fc)

### Cluster both rows (genes) and columns (samples)
```
heatmap.2(data_matrix,
          scale = "row",  # Scale across genes (rows)
          dendrogram = "both",  # Cluster both rows and columns
          Rowv = TRUE,  # Enable row clustering
          Colv = TRUE,  # Enable column clustering
          trace = "none",
          col = bluered(100),
          density.info = "none",
          key = TRUE,
          margins = c(10, 10),
          cexRow = 0.8,
          cexCol = 0.8
)
```
### Output:
![Rplot03](https://github.com/user-attachments/assets/b6c86ad0-1659-47de-8a51-e81d006f038e)

