# ShefPAH179 Dataset

This ShefPAH179 dataset is a cardiac magnetic resonance imaging (CMR) dataset for Pulmonary Arterial Hypertension (PAH) diagnosis provided by the University of Sheffield. ShefPAH179 consists of the short-axis (SA) CMR images acquired from 179 subjects, which is a selected subset of the 220 subjects in [[1](#reference)]. The images have been resized to 64x64 and shared in DICOM format for demonstration and small-scale experiments. The files are organized in the following structure:

```sh
└───SA_64x64
    ├───DICOM
    │   ├───Subject_1
    │   │   ├───Phase_1.dcm
    │   │   ├───Phase_2.dcm
    ...
    │   │   ├───Phase_20.dcm
    │   ├───Subject_2
    ...
    │   ├───Subject_179
    ├───Mask
    │   ├───Mask_64x64
    │   │   ├───Phase_1.dcm
    ├───landmarks_64x64.csv
```

The *landmarks_64x64.csv* file contains information of subject IDs (column 1 'Subject'), locations of the three landmarks (columns 2 - 7), and medical diagnosis results (column 8 'Group'). We use the values in column 'Group' as labels for training and prediction, where "`0`" denotes health control (no PH), "`1`" denotes idiopathic PAH (IPAH), and "`2`" denotes PAH.

|   Subject |   inf insertion point X |   inf insertion point Y |   sup insertion point X |   sup insertion point Y |   RV inf X |   RV inf Y |   Group |
|----------:|------------------------:|------------------------:|------------------------:|------------------------:|-----------:|-----------:|--------:|
|         1 |                   32    |                   39.75 |                   29.25 |                   23.75 |      19    |      41    |       0 |
|         2 |                   24.5  |                   40    |                   28.5  |                   23.75 |      11    |      37.25 |       0 |
|         3 |                   26.25 |                   40.5  |                   27.75 |                   24.25 |      12.25 |      40.75 |       0 |
|         4 |                   34.25 |                   38    |                   34.25 |                   21.25 |      23    |      41    |       0 |
|         5 |                   33    |                   40.25 |                   31.5  |                   24.25 |      19.5  |      40.5  |       2 |

## How to Reference this Dataset

We would appreciate it if you cite our work [[1](#reference)] below when using the dataset:

### Reference

[1] Swift, A.J., Lu, H., Uthoff, J., Garg, P., Cogliano, M., Taylor, J., Metherall, P., Zhou, S., Johns, C.S., Alabed, S. and Condliffe, R.A., 2021. A machine learning cardiac magnetic resonance approach to extract disease features and automate pulmonary arterial hypertension diagnosis. *European Heart Journal-Cardiovascular Imaging*, 22(2), pp.236-245.
