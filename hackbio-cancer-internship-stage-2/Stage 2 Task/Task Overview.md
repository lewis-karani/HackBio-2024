## **Overview**
### In this task, you will visualize and interpret a gene expression dataset to generate a heatmap and perform downstream functional enrichment analysis. This will help you understand and learn how to interpret patterns of gene expression and the biological significance of differentially expressed genes. The task involves data preprocessing, visualization, and interpretation of functional enrichment results.

1. Download and use one of these datasets (they are all top 500+ differentially expressed genes under different conditions
   
`<https://raw.githubusercontent.com/HackBio-Internship/public_datasets/main/Cancer2024/glioblastoma.csv>`

`<https://raw.githubusercontent.com/HackBio-Internship/public_datasets/main/Cancer2024/pregnancyLactationCells.csv>`

3. Visit the [cancer page of the Human Proteome Atlas](https://www.proteinatlas.org/humanproteome/pathology)
4. Generate a heatmap for the entire dataset. Use a diverging and sequential color palette to generate two color variants of the same heatmap. Think about the importance of color selection in the ease of interpreting plots. Write about this in your report. We recommend using the heatmap.2() function under [gplots](https://cran.r-project.org/web/packages/gplots/index.html) in R.
5. With the same heatmap, generate a variant of your heatmap where you
6. Cluster your genes (rows) alone,
7. Cluster your samples (col) alone;
8. Cluster both genes and sample together;
9. Subset genes that are significantly upregulated. (Setup your own cut-offs for the fold change and P-values).
10. Subset genes that are significantly downregulated. (Setup your own cut-offs for the fold change and P-values).
11. Perform functional enrichment analysis with either [ShinyGO](http://bioinformatics.sdstate.edu/go/), [GOrilla](https://cbl-gorilla.cs.technion.ac.il/) or [PANTHER](https://geneontology.org/).
12. Using the top 5 pathways, create a straightforward visualization (such as a lollipop plot, dot plot, lineplot or bubble plot) that displays the number of genes associated with each pathway. The plot should also reflect the significance of each pathway by scaling the points according to the negative log10 of the p-value.
13. Describe the top 3 enriched pathways according to biological process in your report

 
