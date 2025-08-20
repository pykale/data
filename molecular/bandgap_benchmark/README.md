This dataset contains a collection of publicly available materials structure data, adapted for use with the [PyKale](https://github.com/pykale/pykale) library.  

## Source  
The dataset is collected from the [Materials Project](https://materialsproject.org/) [1], which provides both 3D crystal structures and PBE band gap values.  

To ensure relevance for semiconductor behavior, we applied the following filters:
- Removed entries whose chemical formulas contain more than eight elements.
- Kept only entries with band gaps in the range 0.5–5.0 eV.

After filtering, 60,218 entries remained.  

Within these 60,218 entries, we matched experimental band-gap data from [BandgapDatabase1](https://github.com/QingyangDong-qd220/BandgapDatabase1) [2], yielding 1,183 high-fidelity experimental band-gap values. All band-gap values are stored in JSON files. The experimental dataset is split into training and test sets using a 9:1 ratio.

The experimental band gaps are also categorized by composition-based types. The classified files can be found under `data/data_by_type/`.

More details on how the dataset is constructed can be found in the paper:  
[Benchmarking Band Gap Prediction For Semiconductor Materials Using Multimodal And Multi-fidelity Data](https://openreview.net/pdf?id=u8FripvaG5).  

## Contents  
The provided zip file includes two types of files:  

1. **`atom_init.json`**  
   - Defines a one-hot encoding scheme over nine atomic features:  
     - Group number  
     - Period number  
     - Electronegativity  
     - Covalent radius  
     - Number of valence electrons  
     - First ionization energy  
     - Electron affinity  
     - Block  
     - Atomic volume  
   - This feature set follows the design in CGCNN [3].  

2. **`.cif` files**  
   - Contain the 3D crystal structure information for all 61,570 entries.  

The band gap value files are organized as:

```sh
data/
├─ data_by_type/
│  ├─ bandgap_data_Antimonides.json
│  ├─ bandgap_data_Arsenides.json
│  ├─ bandgap_data_Carbides.json
│  ├─ bandgap_data_Chalcogenides.json
│  ├─ bandgap_data_Halides.json
│  ├─ bandgap_data_Hydrides.json
│  ├─ bandgap_data_Nitrides.json
│  ├─ bandgap_data_Oxides.json
│  ├─ bandgap_data_Phosphides.json
│  └─ bandgap_data_Silicides.json
├─ experimental/
│  ├─ train_data.json
│  └─ test_data.json
└─ pbe.json
```

## Reference
    [1] A. Jain*, S.P. Ong*, G. Hautier, W. Chen, W.D. Richards, S. Dacek, S. Cholia, D. Gunter, D. Skinner, G. Ceder, K.A. Persson (*=equal contributions) The materials project: A materials genome approach to accelerating materials innovation. APL Materials, 1(1):011002, 2013.
    [2] Q. Dong and J. M. Cole. Auto-generated database of semiconductor band gaps using ChemDataExtractor. Scientific Data, 9(1):193, 2022.
    [3] T. Xie and J.C. Grossman. Crystal graph convolutional neural networks for an accurate and interpretable prediction of material properties. Physical Review Letters, 120:145301, 2018.
