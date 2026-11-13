# Performance Evaluation of Regression Models & Gradient Descent

**Application:** Predicting individual medical insurance charges from personal and lifestyle details.

| | |
|---|---|
| **Name** | Ojas Wankhede |
| **Division** | E |
| **Batch** | E1 |
| **PRN** | 202401040326 |

## Aim

1. Develop a regression model for a real-world application and evaluate its performance using appropriate metrics.
2. Implement and analyze the performance of Gradient Descent optimization for Linear Regression.

## Dataset

**Medical Cost Personal Dataset** (`insurance.csv`): 1338 records (1337 after removing one duplicate).

| Feature | Description |
|---|---|
| `age` | Age of the person |
| `sex` | Gender |
| `bmi` | Body mass index |
| `children` | Number of dependents |
| `smoker` | Smoker or not |
| `region` | Residential region in the US |
| `charges` | **Target** – medical insurance cost (USD) |

Source: https://github.com/stedy/Machine-Learning-with-R-datasets  
The notebook loads the CSV directly from this URL, so **no download is needed, but an internet connection is required**.

## Project Files

| File | Description |
|---|---|
| `Ojas_Wankhede_ML_Regression_Assignment.ipynb` | Main notebook with code, outputs, plots and conclusion |
| `README.md` | Project description (this file) |

## Notebook Contents

1. Import libraries
2. Load and inspect the dataset
3. Exploratory data analysis
4. Prepare training and testing data (one-hot encoding, 80/20 split, standard scaling)
5. Evaluation function (MAE, MSE, RMSE, R²)
6. Linear Regression (scikit-learn)
7. Linear Regression using Batch Gradient Descent (NumPy, from scratch)
8. Gradient Descent convergence plot
9. Effect of learning rate
10. Effect of number of iterations
11. Comparison of Gradient Descent weights with the closed-form solution
12. Actual vs predicted values and residual analysis
13. Final model comparison
14. Result and conclusion

## Evaluation Metrics

- **MAE** – average absolute error (in USD)
- **MSE** – average squared error
- **RMSE** – square root of MSE (in USD)
- **R² score** – proportion of variance in charges explained by the model

## Results

| Model | MAE | RMSE | R² |
|---|---|---|---|
| Linear Regression | 4177.05 | 5956.34 | 0.807 |
| Linear Regression (Batch GD) | 4177.05 | 5956.34 | 0.807 |

**Key findings**

- The model explains about **81%** of the variation in insurance charges.
- Batch Gradient Descent converges to the same weights as the closed-form solution (difference ≈ 1e-11).
- Learning rate: `0.001` converges slowly, `0.05–0.1` converge quickly, and `1.1` diverges.
- Feature scaling is essential for stable Gradient Descent.
- Smoking status, age and BMI are the most influential features.
- Residuals are larger for high-cost patients, since the true relationship is not perfectly linear (smoking and BMI interact).

## Requirements

- Python 3.8+
- numpy
- pandas
- matplotlib
- seaborn
- scikit-learn
- jupyter

Install with:

```bash
pip install numpy pandas matplotlib seaborn scikit-learn jupyter
```

## How to Run

```bash
jupyter notebook 3-Assignment.ipynb
```

Then choose **Kernel → Restart & Run All**. The notebook also works on Google Colab without changes.

## Note

This dataset is used for educational purposes only. The model is not a real insurance pricing tool.