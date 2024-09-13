# Molecular Datasets

This dataset contains a collection of publicly available drug-target interaction datasets that have been slightly modified for use
with the [PyKale](https://github.com/pykale/pykale) library.

We have three datasets in this collection:
- BindingDB
- BioSNAP
- Human

where BindingDB and BioSNAP are split into random and cluster splits, while Human is split into cold and random splits. The full dataset is also provided for each dataset.

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
    [1] Liu, Tiqing, Yuhmei Lin, Xin Wen, Robert N. Jorissen, and Michael K. Gilson (2007). BindingDB: a web-accessible database of experimentally determined protein–ligand binding affinities. Nucleic acids research, 35(suppl_1), D198-D201.
    [2] Huang, Kexin, Cao Xiao, Lucas M. Glass, and Jimeng Sun (2021). MolTrans: Molecular Interaction Transformer for drug–target interaction prediction. Bioinformatics, 37(6), 830-836.
    [3] Chen, Lifan, et al (2020). TransformerCPI: improving compound–protein interaction prediction by sequence-based deep learning with self-attention mechanism and label reversal experiments. Bioinformatics, 36(16), 4406-4414.
