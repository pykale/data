# The Sheffield Landmark Uncertainty Estimation Dataset


Reference:  [L. A. Schobs, A. J. Swift and H. Lu, "Uncertainty Estimation for Heatmap-Based Landmark Localization," in IEEE Transactions on Medical Imaging, vol. 42, no. 4, pp. 1021-1034, April 2023, doi: 10.1109/TMI.2022.3222730](https://arxiv.org/abs/2203.02351).


The Sheffield Landmark Uncertainty Estimation dataset contain three datasets with landmark localization error and uncertainty estimation values across 6 landmarks in Cardiac Magnetic Imaging (CMR) data and 19 landamrks from Cephalometric data, using 3 model-derived predictive uncertainty estimation measures. The CMR data is derived from a landmark localization task, using data from the [ASPIRE Registry](https://erj.ersjournals.com/content/39/4/945) [1]. We have 303 Short Axis View (CMR) scans with 3 landmarks each, and 422 Four Chamber View CMR scans with 3 landmarks each. We also provide landmark predictions with uncertainty measures from 400 Cephalometric Radiology images with 19 landmarks from a [2015 ISBI grand challenge](https://www.researchgate.net/publication/296621456_A_benchmark_for_comparison_of_dental_radiography_analysis_algorithms). 

For each uncertainty measure we provide tuples of (*Continuous Uncertainty Measure*, *Continuous Localization Error*) for each sample in the validation and test set in tabular form. We have split the data into 8 folds and used cross validation to gather validation and test set uncertainty tuples for every sample in the datasets.

We have data for the following uncertainty measures:

- Single Maximum Heatmap Activation (S-MHA).
- Ensemble Maximum Heatmap Activation (E-MHA).
- Ensemble Coordinate Prediction Variance (E-CPV).

These measures describe the predictive uncertainty of a model for a given sample, explained more in the [paper](https://arxiv.org/abs/2203.02351).

We compare these measures on landmark predictions from:

- A [U-Net model](https://link.springer.com/content/pdf/10.1007/978-3-319-24574-4_28.pdf) [2].
- A [PHD-Net model](https://ieeexplore.ieee.org/document/9433895/) [3].

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
        ├───PHD-NET-NO-GT
    │   ├───4CH
    │   │   ├───uncertainty_pairs_test_l0.csv
    │   │   ├───uncertainty_pairs_valid_l0.csv
    ...
    │   │   ├───uncertainty_pairs_test_l2.csv
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


## Datasets where the GT is not available
For practical use, the ground truth landmark coordinates may not be available at test time, but you still want to bin the predictions by uncertainty.

Therefore, we  provide a dataset called **PHD-NET-NO-GT**, which contains uncertainty and localization estimates from PHD-Net. The ground truth landmark coordinates are avaliable for the validation set, but not the test set. This means you can fit the Quantile Binning procedure on the validation set, get your binning thresholds and error bound estimates for the bins, and bin your test set.

## How to reference this dataset

We would appreciate it if you cite our work [4] below when using this dataset:

### References



[1] J. Hurdman, R. Condliffe, C.A. Elliot, C. Davies, C. Hill, J.M. Wild, D. Capener, P. Sephton, N. Hamilton, I.J. Armstrong, C. Billings, A. Lawrie, I. Sabroe, M. Akil, L. O’Toole, D.G. Kiely
European Respiratory Journal 2012 39: 945-955; DOI: 10.1183/09031936.00078411 

[3] Wang, Ching-Wei & Huang, Cheng-Ta & Lee, Jia-Hong & Li, Chung-Hsing & Chang, Sheng-Wei & Siao, Ming-Jhih & Lai, Tat-Ming & Ibragimov, Bulat & Vrtovec, Tomaž & Ronneberger, Olaf & Fischer, Philipp & Cootes, Tim & Lindner, Claudia. (2016). A benchmark for comparison of dental radiography analysis algorithms. Medical Image Analysis. 31. 10.1016/j.media.2016.02.004. 

[2] Ronneberger, O., Fischer, P., Brox, T. (2015). U-Net: Convolutional Networks for Biomedical Image Segmentation. In: Navab, N., Hornegger, J., Wells, W., Frangi, A. (eds) Medical Image Computing and Computer-Assisted Intervention – MICCAI 2015. MICCAI 2015. Lecture Notes in Computer Science(), vol 9351. Springer, Cham. https://doi.org/10.1007/978-3-319-24574-4_28

[3] L. Schobs, S. Zhou, M. Cogliano, A. J. Swift and H. Lu, "Confidence-Quantifying Landmark Localisation For Cardiac MRI," 2021 IEEE 18th International Symposium on Biomedical Imaging (ISBI), Nice, France, 2021, pp. 985-988, doi: 10.1109/ISBI48211.2021.9433895.



[4] L. A. Schobs, A. J. Swift and H. Lu, "Uncertainty Estimation for Heatmap-Based Landmark Localization," in IEEE Transactions on Medical Imaging, vol. 42, no. 4, pp. 1021-1034, April 2023, doi: 10.1109/TMI.2022.3222730.
