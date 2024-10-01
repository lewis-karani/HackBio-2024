<h1 align="center"> REPORT </h1>

<a align="center"> Table of Contents: </a>
  <a href="#Introduction"> Introduction </a> |
  <a href="#Heatmap-Visualization-and-Color-Palettes-in-Gene-Expression-Analysis"> Heatmap </a> | 
  <a href="#Importance-of-Clustering"> Clustering </a> |
  <a href="#enriched-pathways-according-to-biological-process"> Pathways </a> | 
  <a href="#References"> References </a> |
  <a href="#Contributors"> Contributors </a> 
</a>

>  ## Introduction
The whole analysis will use a [count dataset of glioblastoma transcriptomic samples](https://raw.githubusercontent.com/HackBio-Internship/public_datasets/main/Cancer2024/glioblastoma.csv). This dataset contains a total of 10 samples.

>  ## Heatmap Visualization and Color Palettes in Gene Expression Analysis
### Importance of Color Selection in Interpreting Plots:
Color selection is crucial for heatmap interpretability. Diverging palettes (e.g., Red-Blue) are effective for highlighting deviations from a central point, such as gene over- or under-expression, and make extreme values and patterns more noticeable. Sequential palettes (e.g., Blues) are ideal for datasets with a natural progression from low to high, helping viewers easily perceive the magnitude of values and intensity changes.

![Heatmap with Diverging Color Palette](Images/heatmap_diverging_pages-to-jpg-0001.jpg)
<p align="center">Fig 1: Diverging palettes </p>

![Heatmap with Diverging Color Palette](Images/heatmap_sequential_pages-to-jpg-0001.jpg)
<p align="center">Fig 2: Sequential palettes </p>


### Importance of Clustering:
- Clustering Genes Alone: Focuses on gene behavior across all samples. Useful for identifying gene co-expression patterns and functional relationships.
![Heatmap with Clustering - Rows](Images/heatmap_row_clustering.jpg)
<p align="center"> Fig 3: Clustering Genes Alone </p>

- Clustering Samples Alone: Focuses on sample behavior across all genes. Useful for discovering sample similarities and potential subgroups.
![Heatmap with Clustering - Columns](Images/heatmap_col_clustering.jpg)
<p align="center"> Fig 4: Clustering Samples Alone </p>

- Clustering Both: Provides a holistic view of the data, showing relationships between genes and samples simultaneously. Useful for integrated insights into gene expression patterns and sample similarities.
![Heatmap with Clustering - both](Images/heatmap_col_row_clustering.jpg)
<p align="center"> Fig 5: Clustering Both </p>


>  ## Enriched Pathways According to Biological Process
![Heatmap with Diverging Color Palette](Images/visualization%20of%20Top%205%20Enrichment%20Pathway.png)
Fig:  Enriched Pathways According to Biological Process

**Top 3 Enriched Pathways includes:** Glutathione Derivative Metabolic process, Glutathione Derivative Metabolic Biosynthesis Process, the Linoleic Acid Metabolic Process

### Glutathione Derivative Metabolic and Biosynthesis Process
These are the chemical reactions involving the formation of glutathione derivative, which acts as a coenzyme and as an antioxidant in the protection of sulfhydryl groups in enzymes and other proteins (Lapenna, 2023). Additionally, glutathione(GSH) biosynthesis involves a series of enzymatic reactions using L-glutamic acid, L-cysteine, and glycine (Ikeda & Fujii, 2023). It is synthesized through two ATP-dependent reactions catalyzed by γ-glutamylcysteine synthetase (γ-GCS) and glutathione synthetase (Jiang et al., 2016).
Glutathione and antioxidants exhibit a dual role in cancer by safeguarding cell homeostasis from oxidative damage or by promoting cancer progression to avoid the activation of cell death pathways (Desideri et al., 2019). High GSH levels observed in cancer cells protect them from the activity of chemotherapeutic agents (Desideri et al., 2019).
The gene found in the metabolic and biosynthetic processes is the Glutathione S-transferase A1 (GSTA1) and its increased expression is associated with a worse prognosis in glioblastoma patients (Liu et al., 2014). GSTA1 activity also enhances the ability of glioblastoma cells to withstand oxidative stress and survive (Liu et al., 2014).
Glutathione metabolism is upregulated in glioblastoma to support rapid tumor growth (Obukhova et al., 2022)


### Linoleic acid metabolic process:
Linoleic acid is an essential fatty acid that is metabolized in the human body through a number of processes. The oxidative metabolism of linoleic acid influence processes like growth factor signaling and cellular differentiation, and Role of Glutathione transferase (GST) (encoded by GST gene), is to remove these oxidation products (Seeley et al., 2006). 
A study showed therapeutic effect of Gamma-linolenic acid on Glioblastoma cells by altering cyclooxygenase metabolism, increasing reactive oxygen species, activating caspases, and inducing apoptosis, inhibit proliferation and migration. (Miyake et al., 2020)

>  ## References
- Desideri, E., Ciccarone, F., & Ciriolo, M. R. (2019). Targeting glutathione metabolism: partner in crime in anticancer therapy. *Nutrients*, 11(8), 1926. [Link](https://doi.org/10.3390/nu11081926)
- Lapenna, D. (2023). Glutathione and Glutathione-dependent Enzymes: From Biochemistry to Gerontology and Successful Aging. *Ageing Research Reviews*, 102066-102066. [Link](https://doi.org/10.1016/j.arr.2023.102066)
- Ikeda, Y., & Fujii, J. (2023). The emerging roles of Γ-Glutamyl peptides produced by Γ-Glutamyltransferase and the glutathione synthesis system. *Cells*, 12(24), 2831. [Link](https://doi.org/10.3390/cells12242831)
- Jiang, Y., Tao, R., Shen, Z., Sun, L., Zhu, F., & Yang, S. (2016). Enzymatic Production of Glutathione by Bifunctional γ-Glutamylcysteine Synthetase/Glutathione Synthetase Coupled with In Vitro Acetate Kinase-Based ATP Generation. *Applied Biochemistry and Biotechnology*, 180(7), 1446–1455. [Link](https://doi.org/10.1007/s12010-016-2178-5)
- Liu, Y., Hyde, A. S., Simpson, M. A., & Barycki, J. J. (2014). Emerging regulatory paradigms in glutathione metabolism. *Advances in Cancer Research*, 69–101. [Link](https://doi.org/10.1016/b978-0-12-420117-0.00002-5)
- Obukhova, L., Kopytova, T., Murach, E., Shchelchkova, N., Kontorshchikova, C., Medyanik, I., Orlinskaya, N., Grishin, A., Kontorshchikov, M., & Badanina, D. (2022). Relationship between Glutathione-Dependent Enzymes and the Immunohistochemical Profile of Glial Neoplasms. *Biomedicines*, 10(10), 2393. [Link](https://doi.org/10.3390/biomedicines10102393)
- Miyake, J. A., Gomes, R. N., & Colquhoun, A. (2020). Gamma-Linolenic acid alters migration, proliferation, and apoptosis in human and rat glioblastoma cells. *Prostaglandins & Other Lipid Mediators*, 150, 106452. [Link](https://doi.org/10.1016/j.prostaglandins.2020.106452)
- Seeley, S. K., Poposki, J. A., Maksimchuk, J., Tebbe, J., Gaudreau, J., Mannervik, B., & Bull, A. W. (2006). Metabolism of oxidized linoleic acid by glutathione transferases: Peroxidase activity toward 13-hydroperoxyoctadecadienoic acid. *Biochimica Et Biophysica Acta (BBA) - General Subjects*, 1760(7), 1064–1070. [Link](https://doi.org/10.1016/j.bbagen.2006.02.020)

>  ## Contributors
|Name|Slack ID|Linkedin|
| ----------- |----------- |----------- |
|Ayooluwa Joseph|@Jay1079| <a href="https://www.linkedin.com/in/ayooluwa-joseph/" target="_blank">	LinkedIn Profile</a> |
|Edikan Umoh|@usiwomaumoh| <a href="https://www.linkedin.com/in/edikan-umoh/" target="_blank">	LinkedIn Profile</a>|
|Lewis Karani|@Karani|<a href="https://www.linkedin.com/in/lewis-karani/" target="_blank">	LinkedIn Profile</a>|
|Nishat Tamanna|@Nishat| <a href="https://www.linkedin.com/in/nishat-tamanna-45863117a/" target="_blank">	LinkedIn Profile</a>|
|Shalaka More|@shalaka| <a href="https://www.linkedin.com/in/shalaka-more-03277913b/" target="_blank">	LinkedIn Profile</a>  |
|Sreeja Mondal|@sreeja| <a href="https://linkedin.com/in/sreejamondal263/" target="_blank">	LinkedIn Profile</a> |
