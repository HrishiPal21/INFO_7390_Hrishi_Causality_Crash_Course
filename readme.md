# Causal Inference Crash Course: Income and Employment Outcomes

**Author:** Hrishi  
**Course:** INFO 7390 — Crash Course in Causality  
**Date:** February 2026

## Overview

This project applies causal inference methods to two distinct datasets to demonstrate when and why causal adjustment matters for data analysis and machine learning.

**Example 1: Does a graduate degree cause higher income?**  
Using the UCI Adult Census dataset (32,561 observations), I apply propensity score matching, inverse propensity weighting, and linear regression via DoWhy to estimate the causal effect of holding a graduate degree on earning over $50K annually. The naive comparison overstates the effect by approximately 15 percentage points due to confounders like age, sex, and hours worked.

**Example 2: Does job training cause higher earnings?**  
Using the LaLonde dataset (445 observations) from the National Supported Work Demonstration, I apply both DoWhy's propensity score matching and the causalinference package's direct covariate matching with bias correction. Because treatment was randomized, causal adjustment has minimal impact — serving as a validation that the methods work correctly.

## Repository Structure

```
INFO_7390_Hrishi_Causality_Crash_Course/
├── Causality_Notebook.ipynb      # Main notebook with theory, both examples, and results
├── Example1_Dataset/             # UCI Adult Census data
│   └── adult_census.csv
├── Example2_Dataset/             # LaLonde NSW data
│   └── lalonde.csv
├── QuizQuestions.md              # 15 multiple-choice questions with answers and explanations
├── Video_Link.txt                # Link to video presentation
└── README.md                     # This file
```

## Key Findings

- **Example 1 (Observational):** The naive income gap between graduate degree holders and non-holders was 41.6%. After propensity score matching, the estimated causal effect dropped to 27.2%. Approximately one-third of the observed gap was due to confounding by age, sex, marital status, and hours worked — not the degree itself.

- **Example 2 (Experimental):** The naive earnings difference between treated and control groups was $1,794. Causal estimates across four different methods ranged from $1,676 to $1,916, confirming the finding is robust. The minimal change from naive to adjusted estimates validates that randomization already controlled for confounding.

- **Key Insight:** Causal adjustment matters most in observational settings where treatment is not randomly assigned. In experimental data, it serves as confirmation rather than correction.

## Methods Used

- Propensity Score Matching (DoWhy)
- Inverse Propensity Weighting (DoWhy)
- Linear Regression (DoWhy)
- Direct Covariate Matching with Bias Correction (causalinference package)
- Refutation Tests: Random Common Cause, Placebo Treatment, Data Subset

## How to Run

1. Clone this repository
2. Install dependencies:
```
pip install pandas numpy matplotlib seaborn dowhy==0.11.1 causalinference scikit-learn
```
3. Open `Causality_Notebook.ipynb` in Jupyter Notebook
4. Run all cells from top to bottom

Note: Both datasets load directly from URLs. Saved copies are included in the dataset folders as backup.

## Data Sources

- **UCI Adult Census Dataset:** Becker, B. & Kohavi, R. (1996). UCI Machine Learning Repository. https://archive.ics.uci.edu/dataset/2/adult. Licensed under CC BY 4.0.
- **LaLonde Dataset:** Dehejia, R. & Wahba, S. (1999). NBER Data Archive. https://users.nber.org/~rdehejia/nswdata2.html

## AI Usage Disclosure
AI tools (Claude by Anthropic) were used in a supporting capacity during this project. Specifically, AI assistance was used for researching dataset options, debugging code errors (such as package version conflicts)

## Video Presentation

A 3-5 minute video walkthrough of the notebook is available at the link provided in `Video_Link.txt`.

## License

MIT License. Copyright (c) 2026 Hrishi.
