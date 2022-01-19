# The Sheffield Cardiac Landmark Uncertainty Estimation Dataset

The Sheffield Cardiac Landmark Uncertainty Estimation dataset contain two datasets with landmark localization error and uncertainty estimation values across 6 landmarks using 3 uncertainty estimation measures. The data is derived from a Cardiac Magnetic Resonance Imaging (CMR) landmark localization task, using data from the [ASPIRE Registry](https://erj.ersjournals.com/content/39/4/945). We have 303 Short Axis View (CMR) scans with 3 landmarks each, and 422 Four Chamber View CMR scans with 3 landmarks each. For each uncertainty measure we provide tuples of (*Continuous Uncertainty Measure*, *Continuous Localization Error*) for each sample in the validation and test set in tabular form. We have split the data into 8 folds and used cross validation to gather validation and test set uncertainty tuples for every sample in the datasets.

We have data for the following uncertainty measures:

- Single Maximum Heatmap Activation (S-MHA).
- Ensemble Maximum Heatmap Activation (E-MHA).
- Ensemble Coordinate Prediction Variance (E-CPV).

We compare these measures on landmark predictions from:

- A [U-Net model](https://link.springer.com/content/pdf/10.1007/978-3-319-24574-4_28.pdf).
- A [PHD-Net model](https://ieeexplore.ieee.org/document/9433895/).

The files are organized in the following structure:

```sh
└───Uncertainty_tuples
    ├───PHD-NET
    │   ├───4CH
    │   │   ├───uncertainty_pairs_test_l0.csv
    │   │   ├───uncertainty_pairs_valid_l0.csv
    ...
    │   │   ├───uncertainty_pairs_test_l2.csv
    │   │   ├───uncertainty_pairs_valid_l2.csv
    │   ├───SA
    |   │   ├───uncertainty_pairs_test_l0.csv
    │   │   ├───uncertainty_pairs_valid_l0.csv
    ...
    |   |   |───uncertainty_pairs_test_l2.csv
    │   │   ├───uncertainty_pairs_valid_l2.csv
    ├───U-Net
    │   ├───4CH
    │   │   ├───uncertainty_pairs_test_l0.csv
    │   │   ├───uncertainty_pairs_valid_l0.csv
    ...
    │   │   ├───uncertainty_pairs_test_l2.csv
    │   │   ├───uncertainty_pairs_valid_l2.csv
    │   ├───SA
    |   │   ├───uncertainty_pairs_test_l0.csv
    │   │   ├───uncertainty_pairs_valid_l0.csv
    ...
    |   |   |───uncertainty_pairs_test_l2.csv
    │   │   ├───uncertainty_pairs_valid_l2.csv
```

Each *.csv* file contains information of subject IDs (column 1 'uid'), and three column pairs of 'Error' and 'Uncertainty' for each uncertainty measure: 'E-CPV', 'E-MHA' and 'S-MHA' (columns 2 - 7). Column 8 'Validation Fold' shows which fold this subject was used for validation, and Column 9 'Test Fold' shows the fold this subject was used for test.

The *'.csv* files with *'valid'* in the suffix contain the predictions from the model trained at the fold 'Validation Fold', and the results will be used for fitting *Quantile Binning* (think of this as the training data). The *'.csv* files with *'test'* in the suffix contain the predictions from the model trained at the fold 'Test Fold', and the results will be used at test time for evaluation for that fold. Note, for each fold the remaining subjects not in 'Validation Fold' or 'Test Fold' were used to train the landmark localization model.

We have three pairs of *'valid'* and *'test'* files - a pair for each of the three landmarks. The landmark is indicated by *l0*, *l1* or *l2* in the suffix of the filename.

Each file follows the structure below:

| uid     | E-CPV Error | E-CPV Uncertainty | E-MHA Error | E-MHA Uncertainty | S-MHA Error | S-MHA Uncertainty | Validation Fold | Testing Fold |
|---------|-------------|-------------------|-------------|-------------------|-------------|-------------------|-----------------|--------------|
| PHD_103 | 14.035668   | 4.538336          | 12          | 0.234762975       | 8           | 0.381222          | 0               | 7            |
| PHD_107 | 14.21267    | 2.04222           | 14.86607    | 0.998703537       | 10.5        | 1.324168          | 0               | 7            |
| PHD_108 | 7.615773    | 5.596662          | 4.472136    | 0.581483632       | 3           | 0.973983          | 0               | 7            |

## How to reference this dataset

We would appreciate it if you cite our work [[1](placeholder)] below when using this dataset:

### Reference

[1]Placeholder
