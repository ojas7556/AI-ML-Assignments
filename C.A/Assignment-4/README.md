# Assignment 4: Breast Cancer Diagnosis Classification

**Name:** Ojas Wankhede
**Div:** E  **Batch:** E1
**PRN:** 202401040326

## Aim

Prepare the Breast Cancer Wisconsin (Diagnostic) dataset, train four classification algorithms and compare their performance.

## Dataset

- **Name:** Breast Cancer Wisconsin (Diagnostic) Data Set (WDBC)
- **Source:** UCI Machine Learning Repository, https://archive.ics.uci.edu/dataset/17/breast+cancer+wisconsin+diagnostic
- **DOI:** 10.24432/C5DW2B
- **License:** CC BY 4.0
- **Creators:** W. H. Wolberg, W. N. Street, O. L. Mangasarian
- **Size:** 569 patients, 32 columns (ID, diagnosis, 30 features)
- **Target:** `Diagnosis` (212 Malignant, 357 Benign)
- **Features:** 10 measurements of the cell nuclei (radius, texture, perimeter, area, smoothness, compactness, concavity, concave points, symmetry, fractal dimension), each given as mean, standard error and worst value.
- **Missing values:** None.

The raw file `wdbc.data` has no header row. Column names are assigned in the notebook using the description in `wdbc.names`.

## Project structure

```
.
├── 4-Assignment.ipynb
├── README.md
└── data/
    ├── wdbc.data
```

## Methodology

1. **Import libraries**: pandas, numpy, matplotlib, seaborn, scikit-learn.
2. **Load and inspect**: read `wdbc.data`, assign column names, check shape, data types, missing values and class distribution.
3. **Preprocessing**: drop `Patient_ID`, encode the target with `LabelEncoder` (Benign = 0, Malignant = 1), and build a `ColumnTransformer` pipeline (median imputation and standard scaling for numeric features, most-frequent imputation and one-hot encoding for categorical features).
4. **Split**: 80:20 stratified train-test split (455 training, 114 testing records, `random_state=42`).
5. **Models** (all share the same preprocessing pipeline):
   - SVM (RBF kernel)
   - Decision Tree (CART, Gini, `max_depth=5`)
   - K-Nearest Neighbors (`k=5`)
   - Gaussian Naive Bayes
6. **Evaluation**: accuracy, precision, recall, F1-score and log loss. Malignant is the positive class.
7. **Visualisation**: bar charts of the metrics and log loss, plus confusion matrices for each model.
8. **Classification reports**: per-class precision, recall and F1-score.

## Results

| Model | Accuracy | Precision | Recall | F1-Score | Log Loss |
|---|---|---|---|---|---|
| SVM | 0.9737 | 1.0000 | 0.9286 | 0.9630 | 0.0822 |
| K-Nearest Neighbors | 0.9561 | 0.9744 | 0.9048 | 0.9383 | 0.4091 |
| Naive Bayes | 0.9211 | 0.9231 | 0.8571 | 0.8889 | 0.4999 |
| Decision Tree (CART) | 0.9211 | 0.9459 | 0.8333 | 0.8861 | 1.0968 |

**Conclusion:** SVM performs best on every metric. Recall is the most important metric in this medical setting, since a missed malignant case costs more than a false alarm.

## How to run

1. Install the requirements:
   ```bash
   pip install numpy pandas matplotlib seaborn scikit-learn jupyter
   ```
2. Place `wdbc.data` in a `data/` folder next to the notebook (or directly beside it).
3. Open and run the notebook:
   ```bash
   jupyter notebook 4-Assignment.ipynb
   ```

## Note

Recent scikit-learn versions show a harmless `FutureWarning` about `SVC(probability=True)`. It does not affect the results.

## Reference

Wolberg, W. H., Street, W. N., & Mangasarian, O. L. (1995). *Breast Cancer Wisconsin (Diagnostic)* [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5DW2B