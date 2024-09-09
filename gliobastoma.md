# step 1: install package gplots


install.packages("gplots")

# Step 2: Load the dataset from the URL


glioblastoma <- read.csv("https://raw.githubusercontent.com/HackBio-Internship/public_datasets/main/Cancer2024/glioblastoma.csv")

# step 3: load library

library(gplots)

# Step 4: Ensure the data contains only numeric values

numeric_data <- glioblastoma[, sapply(glioblastoma, is.numeric)]


# Step 5: Convert the data frame to a matrix for heatmap.2

data_matrix <- as.matrix(numeric_data)

# Step 6: Generate the heatmap

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

