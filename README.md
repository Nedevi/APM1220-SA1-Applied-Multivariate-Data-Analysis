# Physicochemical Differences and Latent Structure in Portuguese Vinho Verde Wines: A Multivariate Analysis Using MANOVA, PCA, and EFA

**Course:** APM1220 – Applied Multivariate Data Analysis
**Assessment:** Summative Assessment 1
**Author:** Ivan C. Cobarrubias

---

## Research Questions

1. **MANOVA:** Do red and white wines differ significantly in their combined physicochemical characteristics?
2. **PCA:** Can the 11 physicochemical measurements be summarized by a smaller number of principal components that retain a substantial proportion of the total variability?
3. **EFA:** What underlying latent dimensions or factors explain the relationships among the physicochemical characteristics of wine?

## Dataset Description

This project uses the **Wine Quality Dataset** of Portuguese *Vinho Verde* wines, combining the red and white wine files into one analytical dataset.

- **Observations:** 6,497 total (1,599 red, 4,898 white)
- **Physicochemical variables (11):** fixed acidity, volatile acidity, citric acid, residual sugar, chlorides, free sulfur dioxide, total sulfur dioxide, density, pH, sulphates, alcohol
- **Other variables:** `quality` (sensory score, 0–10) and `color` (red/white, added during data preparation)
- **Note:** `quality` is **not** used in the MANOVA, PCA, or EFA. The analyses focus on the 11 physicochemical variables.
- **Files:** `data/winequality-red.csv` and `data/winequality-white.csv` (semicolon-delimited, period as decimal mark)

## Dataset Source and Attribution

The data come from the UCI Machine Learning Repository: https://archive.ics.uci.edu/dataset/186/wine+quality

The dataset is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Credit goes to the dataset creators:

> Cortez, P., Cerdeira, A., Almeida, F., Matos, T., & Reis, J. (2009). *Wine quality* [Data set]. UCI Machine Learning Repository. [verify DOI on the UCI page]

The original study:

> Cortez, P., Cerdeira, A., Almeida, F., Matos, T., & Reis, J. (2009). Modeling wine preferences by data mining from physicochemical properties. *Decision Support Systems, 47*(4), 547–553.

## Statistical Methods

- **Exploratory data analysis:** missing values, duplicates, univariate and multivariate outliers (Mahalanobis distance), descriptive statistics, distributions, correlation matrix, and red vs. white comparisons
- **MANOVA:** color (red vs. white) as the grouping variable and [list dependent variables] as outcomes. Assumptions checked (multivariate normality, multivariate outliers, homogeneity of covariance matrices via Box's M, relationships among DVs). Test statistic: [Pillai's trace]. Follow-up univariate ANOVAs with [Bonferroni] adjustment and effect sizes
- **PCA:** standardized variables (correlation matrix). Number of components decided using eigenvalues, scree plot, variance explained, and parallel analysis
- **EFA:** factorability via KMO and Bartlett's test. Number of factors from scree plot and parallel analysis. [Extraction method] with [rotation method]. Loadings, communalities, and uniquenesses examined

## Summary of Major Findings

> [Fill in once the analysis is complete. Suggested: one or two sentences per method.]

- **MANOVA:** [Do red and white wines differ? Which variables contribute most? Effect size?]
- **PCA:** [How many components retained, how much variance, what they represent]
- **EFA:** [How many factors, what they represent]
- **Integration:** [How the three analyses fit together]

## Software Used

- [R version X.X.X / RStudio, or Python version]
- Packages: [e.g., tidyverse, psych, car, ...]
- Report written in LaTeX [Overleaf]

## Repository Structure

```
SA1-Applied-Multivariate-Data-Analysis/
│
├── data/
│   ├── winequality-red.csv
│   └── winequality-white.csv
│
├── code/
│   └── [SA1_Wine_Analysis.R / .Rmd / .ipynb]
│
├── output/
│   ├── figures/
│   └── tables/
│
├── report/
│   └── SA1_Wine_Quality_Report.pdf
│
└── README.md
```

## Instructions for Reproducing the Analysis

1. **Clone or download** this repository.
2. **Install the required software:** [R and RStudio / Python] and the packages listed above. [Add an install command, e.g., `install.packages(c("tidyverse", "psych", "car"))`.]
3. **Check the data files** are in the `data/` folder. They are semicolon-delimited with `.` as the decimal mark, so import them with `sep = ";"` and a period decimal mark.
4. **Set the working directory** to the repository root so the relative paths (`data/...`, `output/...`) resolve.
5. **Run** `code/[your script or notebook]` from top to bottom. It imports and combines the data, runs the exploratory analysis, MANOVA, PCA, and EFA, and saves figures and tables to `output/figures/` and `output/tables/`.
6. **Report:** the final write-up is in `report/SA1_Wine_Quality_Report.pdf`.

## License and Use

The analysis code and report are submitted for academic coursework. The underlying dataset is © its original creators and used under CC BY 4.0 (see above).
