# Multiomics Datasets

This multiomics dataset contains a collection of publicly available multiomics datasets that have been slightly modified for use
with the [PyKale](https://github.com/pykale/pykale) library.

## 1. TCGA-BRCA

The Cancer Genome Atlas Breast Invasive Carcinoma (TCGA-BRCA) dataset is a multiomics dataset for subtype classification of 
breast cancer (i.e., normal-like, basal-like, HER2-enriched, Luminal A, and Luminal B subtypes). The original version of
this dataset can be obtained from the TCGA program through [Broad GDAC Firehose](https://gdac.broadinstitute.org/).

Here, we provide a preprocessed version of the TCGA-BRCA dataset in accordance with the **Preprocessing** section of the 
[MOGONET](https://doi.org/10.1038/s41467-021-23774-w) [1] paper. This preprocessed dataset has been derived from the 
[MOGONET repository](https://github.com/txWang/MOGONET/tree/main/BRCA) on GitHub. Three omics modalities are included in
the collected dataset: gene expression RNA-seq (mRNA), DNA methylation (Meth), and miRNA expression (miRNA). A brief 
description of these datasets is shown in Table 1.

**Table 1**: Characteristics of the preprocessed BRCA multiomics dataset.

|      Omics       | #Training samples | #Test samples | #Features |
|:----------------:|:-----------------:|:-------------:|:---------:|
| mRNA expression  |        612        |      263      |   1000    |
| DNA methylation  |        612        |      263      |   1000    |
| miRNA expression |        612        |      263      |    503    |


## 2. ROSMAP

Religious Orders Study/Memory and Aging Project (ROSMAP) dataset is a multiomics dataset from Rush University for studying 
Alzheimer’s disease (i.e., classification of Alzheimer’s disease patients vs. normal control). The original 
version of this dataset can be obtained from [AMP-AD Knowledge Portal](https://adknowledgeportal.synapse.org/).

Here, we also present a preprocessed version of the ROSMAP dataset with the same omics modalities and preprocessing instructions as described in the TCGA-BRCA section. A summary of this dataset is provided in Table 2.

**Table 2**: Characteristics of the preprocessed ROSMAP multiomics dataset.

|      Omics       | #Training samples | #Test samples | #Features  |
|:----------------:|:-----------------:|:-------------:|:----------:|
| mRNA expression  |        245        |      106      |    200     |
| DNA methylation  |        245        |      106      |    200     |
| miRNA expression |        245        |      106      |    200     |


### Reference

[1] Wang, T., Shao, W., Huang, Z., Tang, H., Zhang, J., Ding, Z., Huang, K. (2021). [MOGONET integrates multi-omics data
using graph convolutional networks allowing patient classification and biomarker identification](https://doi.org/10.1038/s41467-021-23774-w). Nature Communications.
