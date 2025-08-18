This dataset contains a collection of publicly available materials structure data, adapted for use with the [PyKale](https://github.com/pykale/pykale) library.  

## Source  
The dataset is collected from the [Materials Project](https://materialsproject.org/)[1], which provides both 3D crystal structures and PBE band gap values.  

To ensure relevance for semiconductor behaviour, we applied the following filters:  
- Removed entries with chemical formulas containing more than 8 elements.  
- Kept only entries with band gap values in the range of 0.5–5 eV.  

After filtering, 61,570 entries remained.  

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
   - This feature set follows the design in CGCNN[2].  

2. **`.cif` files**  
   - Contain the 3D crystal structure information for all 61,570 entries.  

## Reference
    [1] A. Jain*, S.P. Ong*, G. Hautier, W. Chen, W.D. Richards, S. Dacek, S. Cholia, D. Gunter, D. Skinner, G. Ceder, K.A. Persson (*=equal contributions) The materials project: A materials genome approach to accelerating materials innovation. APL Materials, 1(1):011002, 2013.
    [2] T. Xie and J.C. Grossman. Crystal graph convolutional neural networks for an accurate and
interpretable prediction of material properties. Physical Review Letters, 120:145301, 2018.
