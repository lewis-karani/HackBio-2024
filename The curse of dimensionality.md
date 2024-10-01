<!-- This content will not appear in the rendered Markdown -->

# Topic: Curse of Dimensionality

## Link between Machine learning and Cancer Diagnosis
Machine learning is a branch of AI, allows system to learn and make predictions. It’s useful in automating the use of microarray data and contributed to the creation of gene expression datasets (Nogueira et al., 2023), It is effective in predicting various types of cancers (Zhang et al., 2023). However, these datasets are highly dimensional with many features, making interpretation challenging and complicating the application of classification techniques due to the "curse of dimensionality" (Nogueira et al., 2023).

## What is the Curse of Dimensionality?
It is a phenomenon where algorithms become less effective as dimensions of data increase, leading to dispersed data and difficulty in identifying patterns. Causing higher computational complexity, longer training times, and inaccurate results.

## How to Overcome the Curse of Dimensionality?
In cancer research, reducing the dimensions of the microarray datasets to a reasonable number overcomes the limitation (Osama et al., 2023), Several machine learning techniques are helpful in reducing irrelevant and redundant features (Saeys et al., 2007) (Aziz et al., 2017).

## Dimensionality reduction algorithm includes:
1\. Feature selection
It involves choosing a subset of relevant and non-redundant features from a dataset to enhance the performance of classification algorithms, both in terms of accuracy and the time required to build the model. This process is divided into three categories: filters, wrappers, and embedded techniques

2\. Feature extraction
It is an effective alternative to feature selection for reducing the size of high-dimensional data. This approach involves transforming the original features into a lower-dimensional space, making the problem representation more informative and thus enhancing the efficiency of subsequent analysis (Aziz et al., 2017). It has two main categories: linear and nonlinear.

3\. Hybrid search technique
This technique combines the advantages of both filter/extraction methods and wrapper methods.
It involves two stages: first, a filter/extraction method is used to identify the most relevant features from the dataset and next stage a wrapper method evaluates these identified feature subsets to ensure the yield higher classification accuracy (Aziz et al., 2017). This approach employs various evaluation criteria at different search stages to enhance efficiency, improve classification accuracy, and achieve better computational performance (Chuang et al., 2011).

# Conclusion:
Though the 'curse of dimensionality' creates limitations for classification and interpretation in cancer prediction using machine learning; techniques like feature selection, feature extraction, and hybrid methods help reduce irrelevant features, enhancing accuracy and efficiency in cancer research.

# Reference:
1\. <!--[if !supportLists]--> <!--[endif]-->Nogueira A, Ferreira A, Figueiredo M. A Machine Learning Pipeline for Cancer Detection on Microarray Data: The Role of Feature Discretization and Feature Selection. BioMedInformatics. 2023; 3(3):585-604. https\://doi.org/10.3390/biomedinformatics3030040

2\. <!--[if !supportLists]-->  <!--[endif]-->Zhang, B., Shi, H., & Wang, H. (2023). Machine Learning and AI in Cancer Prognosis, Prediction, and Treatment Selection: A Critical Approach. Journal of Multidisciplinary Healthcare, Volume 16, 1779–1791. <https://doi.org/10.2147/jmdh.s410301>

3\. <!--[if !supportLists]-->  <!--[endif]-->Rabia Aziz,  C.K. Verma,  Namita Srivastava. Dimension reduction methods for microarray data: a review\[J]. AIMS Bioengineering, 2017, 4(1): 179-197. doi: 10.3934/bioeng.2017.1.179

4\. <!--[if !supportLists]-->  <!--[endif]-->Osama, S., Shaban, H., & Ali, A. A. (2023). Gene reduction and machine learning algorithms for cancer classification based on microarray gene expression data: A comprehensive review. Expert Systems With Applications, 213, 118946. https\://doi.org/10.1016/j.eswa.2022.118946

5\. <!--[if !supportLists]--> <!--[endif]--> Saeys Y, et al. Feature selection for splice site prediction: a new method using EDA-based feature ranking, BMC Bioinformatics, 2004, vol. 5 pg. 64 

6\.<!--[if !supportLists]--> <!--[endif]-->Chuang LY, Yang CH, Wu KC, et al. (2011) A hybrid feature selection method for DNA microarray data. Comput Biol Med 41: 228–237. doi: 10.1016/j.compbiomed.2011.02.004
