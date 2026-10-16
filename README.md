Physicochemical Differences and Latent Structure in Portuguese Vinho Verde Wines: A Multivariate Analysis Using MANOVA, PCA, and EFA

Course: APM1220 – Applied Multivariate Data Analysis Assessment: Summative Assessment 1 Author: Ivan C. Cobarrubias

Research Questions
MANOVA: Do red and white wines differ significantly in their combined physicochemical characteristics (fixed acidity, volatile acidity, pH, residual sugar, chlorides, sulphates, and total sulfur dioxide)?
PCA: Can the 11 physicochemical measurements be summarized by a smaller number of principal components that retain a substantial proportion of the total variability?
EFA: What underlying latent dimensions or factors explain the relationships among the physicochemical characteristics of wine?
Dataset Description

This project uses the Wine Quality Dataset of Portuguese Vinho Verde wines, combining the red and white wine files into one analytical dataset.

Observations: 6,497 total (1,599 red, 4,898 white). There are no missing values. 1,177 rows (18.1%) are exact duplicates; they were retained because the files contain no wine identifier.
Physicochemical variables (11): fixed acidity, volatile acidity, citric acid, residual sugar, chlorides, free sulfur dioxide, total sulfur dioxide, density, pH, sulphates, alcohol
Other variables: quality (sensory score, 0–10) and color (red/white, added during data preparation to identify the source file)
Note: quality is not used in the MANOVA, PCA, or EFA. The analyses focus on the 11 physicochemical variables.
Files: data/winequality-red.csv and data/winequality-white.csv (semicolon-delimited, period as decimal mark)
Dataset Source and Attribution

The data come from the UCI Machine Learning Repository: https://archive.ics.uci.edu/dataset/186/wine+quality

The dataset is licensed under CC BY 4.0. Credit goes to the dataset creators:

Cortez, P., Cerdeira, A., Almeida, F., Matos, T., & Reis, J. (2009). Wine quality [Data set]. UCI Machine Learning Repository. https://doi.org/10.24432/C56S3T

The original study:

Cortez, P., Cerdeira, A., Almeida, F., Matos, T., & Reis, J. (2009). Modeling wine preferences by data mining from physicochemical properties. Decision Support Systems, 47(4), 547–553.

Statistical Methods
Exploratory data analysis: structure, missing values, duplicates, descriptive statistics (overall and by color, including skewness, kurtosis, and coefficient of variation), density plots and boxplots by color, Pearson correlation matrix and heatmap, scatterplot matrix, univariate outliers (1.5 × IQR rule), and multivariate outliers (Mahalanobis distance, χ² cutoff at p < .001). Flagged outliers and duplicates were retained.
MANOVA: color (red vs. white) as the grouping variable, with seven dependent variables selected using Cohen's d, pairwise correlations, and VIFs: fixed acidity, volatile acidity, pH, residual sugar, chlorides, sulphates, and total sulfur dioxide. Assumptions checked: independence (from the study design), multivariate normality (Mardia's tests, χ² Q–Q plots), multivariate outliers, homogeneity of covariance matrices (Box's M), and relationships among the DVs (correlations, VIFs, determinant, Bartlett's test). Primary test: Pillai's trace (Wilks' Λ, Hotelling's trace, and Roy's largest root also reported). Follow-up: univariate ANOVAs with a Bonferroni-adjusted α = .05/7, η² and Cohen's d, Welch t-tests as a robustness check, and discriminant analysis (standardized coefficients and structure correlations).
PCA: all 11 variables standardized (PCA on the correlation matrix, prcomp()). Factorability checked with KMO and Bartlett's test. Number of components decided using eigenvalues, scree plot, variance explained, cumulative variance (60–70% guide), and parallel analysis (100 iterations, seed = 123). Loadings, contributions, and communalities reported, with scree plot, loading plot, and biplot. Sensitivity check without multivariate outliers (Tucker's congruence).
EFA: factorability via the correlation matrix, KMO (overall, per variable, within each color, and without density), Bartlett's test, and the determinant. Number of factors from the scree plot, parallel analysis for common factors, eigenvalues, Velicer's MAP, RMSEA/BIC, and interpretability. Minimum residual (minres) extraction with oblimin rotation. Loadings (|.40| salient), cross-loadings, communalities, uniquenesses, and factor scores by color. Robustness checked with promax rotation, maximum likelihood extraction, removal of outliers, separate red/white solutions, and a refit without density (Tucker's congruence).
Summary of Major Findings
MANOVA: Red and white wines differ significantly and strongly in their combined physicochemical profile, Pillai's trace = 0.79, F(7, 6489) = 3518.70, p < .001, partial η² = .79. All seven follow-up ANOVAs were significant after Bonferroni correction. Total sulfur dioxide (higher in white wines, d = −2.28) and volatile acidity (higher in red wines, d = 2.00) contribute most. Red wines are also higher in chlorides, sulphates, fixed acidity, and pH; white wines are also higher in residual sugar. The assumptions of multivariate normality and equal covariance matrices were not met, and independence could not be verified, so exact F and p values should be read with caution. The size of the effect and the agreement between the Welch and conventional tests make it unlikely that the conclusion changes.
PCA: Three components were retained (parallel analysis, scree plot, and Kaiser rule agree), explaining 64.4% of the total variance. PC1 (27.5%) is a preservative–sugar versus volatile-acidity–salts contrast that coincides with wine type (d = −3.39). PC2 (22.7%) is a density–extract versus alcohol dimension. PC3 (14.1%) is a fixed-acid versus pH dimension. The overall KMO was low (.405), so the components are treated as data summaries, not latent constructs.
EFA: Three nearly uncorrelated factors (|φ| ≤ .17) were retained, explaining 53.1% of the variance: (1) preservation (sulfur dioxide and sugar) versus volatile acidity and salts, which separates red from white wines (d = −3.17); (2) body (density–extract) versus alcohol; and (3) fixed-acid strength (citric acid, fixed acidity, pH). Fit is poor (RMSEA = .252, TLI = .389), density produced a Heywood case (communality = 1.04), and the overall KMO was .405 (.66 without density). Chlorides, sulphates, and pH are weakly represented, and the first factor is partly an artifact of pooling red and white wines.
Integration: The three analyses agree. The variables that separate red from white wines in the MANOVA (total sulfur dioxide, volatile acidity) are the ones that define PC1 and the first factor, and the unsupervised methods recover the grouping without using color. PCA and EFA give nearly the same three-dimensional structure; PCA retains more variance because it models total variance, while EFA exposes the redundancy of density and the weakness of chlorides and sulphates. Limitations include the observational data, unmet MANOVA assumptions, weak factorability, and the pooling of two chemically different wine types.
Software Used
R version 4.4.0, run in a Kaggle notebook (R kernel)
Packages: tidyverse (2.0.0; includes readr, dplyr, tidyr, ggplot2), psych (descriptive statistics, KMO, Bartlett's test, parallel analysis, Mardia's tests, EFA), car (VIFs), heplots (Box's M), GPArotation (oblique rotation), and MASS (discriminant analysis). MANOVA and PCA use base R (manova() and prcomp()).
Report written in LaTeX (Overleaf)
Repository Structure
SA1-Applied-Multivariate-Data-Analysis/
│
├── data/
│   ├── winequality-red.csv
│   └── winequality-white.csv
│
├── code/
│   └── SA1_Wine_Analysis.ipynb      (R kernel)
│
├── output/
│   ├── figures/
│   └── tables/
│
├── report/
│   └── SA1_Wine_Quality_Report.pdf
│
└── README.md
Instructions for Reproducing the Analysis
Clone or download this repository.
Install R (4.4.0 or later) and the required packages:
r
   install.packages(c("tidyverse", "psych", "car", "heplots", "GPArotation", "MASS"))

To run the notebook, also install Jupyter with the R kernel (IRkernel), or upload the notebook to Kaggle. 3. Check the data files are in the data/ folder. They are semicolon-delimited with . as the decimal mark, so they are read with read_delim(..., delim = ";", locale = locale(decimal_mark = ".")). 4. Update the file paths. The notebook was run on Kaggle and reads the data from /kaggle/input/.... Replace these two paths in the import cell with data/winequality-red.csv and data/winequality-white.csv. 5. Set the working directory to the repository root so the relative paths (data/..., output/...) resolve. Create output/figures/ and output/tables/ if they do not exist (the export cells create them). 6. Run code/SA1_Wine_Analysis.ipynb from top to bottom. It imports and combines the data, runs the exploratory analysis, MANOVA, PCA, and EFA, and saves figures and tables to output/figures/ and output/tables/. Random seeds are fixed (set.seed(123)), so the sampled scatterplot matrix and the parallel analyses are reproducible. 7. Report: the final write-up is in report/SA1_Wine_Quality_Report.pdf.

License and Use

The analysis code and report are submitted for academic coursework. The underlying dataset is © its original creators and used under CC BY 4.0 (see above).
