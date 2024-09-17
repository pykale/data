# Molecular Datasets

This dataset contains a collection of publicly available drug-target interaction datasets that have been slightly modified for use
with the [PyKale](https://github.com/pykale/pykale) library.

## Dataset Description and Splitting

We have three datasets in this collection:
- BindingDB
- BioSNAP
- Human
where BindingDB and BioSNAP are split into random and cluster splits, while Human is split into cold and random splits. The full dataset is also provided for each dataset.

There are three types of splitting:
- Random splitting: The dataset is randomly split into training, validation, and test sets (7:1:2 ratio); drugs or proteins seen during training can appear in test pairs.
- Cold splitting: The dataset is split into training, validation, and test sets (7:1:2 ratio); it ensures that neither the drug nor the protein in a test pair has been seen during training.
- Cluster splitting: Drugs and proteins are grouped into clusters based on their similarity. Once clustered, a portion of the clusters (e.g., 60%) is selected for the source domain (training data), and the remaining clusters are assigned to the target domain (test data).


The files are organized in the following structure:

```sh
└───drug-target-datasets.zip
    ├───bindingdb
    │   ├───cluster
    │   │   ├───source_train.csv
    │   │   ├───target_train.csv
    │   │   ├───target_test.csv
    │   ├───random
    │   │   ├───test.csv
    │   │   ├───train.csv
    │   │   ├───val.csv
    │   ├───full.csv
    ├───biosnap
    │   ├───cluster
    │   │   ├───source_train.csv
    │   │   ├───target_train.csv
    │   │   ├───target_test.csv
    │   ├───random
    │   │   ├───test.csv
    │   │   ├───train.csv
    │   │   ├───val.csv
    │   ├───full.csv
    ├───human
    │   ├───cold
    │   │   ├───test.csv
    │   │   ├───train.csv
    │   │   ├───val.csv
    │   ├───random
    │   │   ├───test.csv
    │   │   ├───train.csv
    │   │   ├───val.csv
    │   ├───full.csv
```

Each full.csv and cluster-splitting file follows the structure below: 

|        SMILES        |        Protein         |               Y                | Drug cluster | Target cluster |
|:--------------------:|:----------------------:|:------------------------------:|:------------:|:--------------:|
| Drug SMILES Notation |    Protein Sequence    | Drug-protein Interaction Label |    number    |     number     |
|  O=C(O)C...cc1Cl     |  MLARALLL...LLKERSTEL  |               1                |     1669     |      464       |


Each cold-splitting and random-splitting file follows the structure below:


|        SMILES        |        Protein         |               Y                | 
|:--------------------:|:----------------------:|:------------------------------:|
| Drug SMILES Notation |    Protein Sequence    | Drug-protein Interaction Label |  
|  O=C(O)C...cc1Cl     |  MLARALLL...LLKERSTEL  |               1                |  


## Acknowledgements
You can also find the data sources from [BindingDB](https://www.bindingdb.org/bind/index.jsp) [1], [BioSNAP](https://github.com/kexinhuang12345/MolTrans) [2] and [Human](https://github.com/lifanchen-simm/transformerCPI) [3].

## Reference
    [1] Bai, P., Miljković, F., John, B. and Lu, H., 2023. Interpretable bilinear attention network with domain adaptation improves drug–target prediction. Nature Machine Intelligence, 5(2), pp.126-136.
    [2] Liu, T., Lin, Y., Wen, X., Jorissen, R.N. and Gilson, M.K., 2007. BindingDB: a web-accessible database of experimentally determined protein–ligand binding affinities. Nucleic acids research, 35(suppl_1), pp.D198-D201.
    [3] Huang, K., Xiao, C., Glass, L.M. and Sun, J., 2021. MolTrans: molecular interaction transformer for drug–target interaction prediction. Bioinformatics, 37(6), pp.830-836.
    [4] Chen, L., Tan, X., Wang, D., Zhong, F., Liu, X., Yang, T., Luo, X., Chen, K., Jiang, H. and Zheng, M., 2020. TransformerCPI: improving compound–protein interaction prediction by sequence-based deep learning with self-attention mechanism and label reversal experiments. Bioinformatics, 36(16), pp.4406-4414.