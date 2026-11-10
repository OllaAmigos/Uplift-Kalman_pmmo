# Uplift modeling with Kalman filtering

**Research case study** · Causal uplift · State-space modeling · Customer behavior

This project explores a difficult marketing question: **can we transfer what we learn from an intervention in one customer population to another population where an intervention is not feasible?**

The approach combines feature engineering from customer transactions, **latent-state estimation using a Kalman filter**, and **uplift modeling**. The result is an exploratory methodology rather than a validated business deployment.

## Business context

Imagine two cities with different customer profiles:

- **City Y**: a wealthier population where a promotion can be run and treatment outcomes can be observed.
- **City X**: a less wealthy population where launching the promotion is not currently possible.

The goal is to study whether patterns learned in City Y can help prioritize customers or estimate potential response in City X. This is a **domain-transfer assumption**, not evidence that treatment effects are transportable.

## Research workflow

```text
Transactions / customers / products
            │
            ▼
     Feature engineering
            │
            ▼
    Panel-data construction
            │
            ▼
  Linear state-space formulation
            │
            ▼
      Kalman filtering
  (latent customer features)
            │
            ▼
  Uplift modeling in City Y
            │
            ▼
  Exploratory scoring in City X
```

## Notebooks

| Order | Notebook | Purpose |
| --- | --- | --- |
| 0 | [`0_data_collect.ipynb`](uplift_and_kalman/0_data_collect.ipynb) | Inspect source files and split customer cohorts |
| 1 | [`1_feature_modeling.ipynb`](uplift_and_kalman/1_feature_modeling.ipynb) | Build transaction-level and customer features |
| 2 | [`2_EDA.ipynb`](uplift_and_kalman/2_EDA.ipynb) | Explore distributions, correlations and data quality |
| 3 | [`3_do_preproc.ipynb`](uplift_and_kalman/3_do_preproc.ipynb) | Construct a prepared panel dataset |
| 4 | [`4_LSS_and_Kalman.ipynb`](uplift_and_kalman/4_LSS_and_Kalman.ipynb) | Estimate a linear state-space representation and restore latent features |
| 5 | [`5_Uplift.ipynb`](uplift_and_kalman/5_Uplift.ipynb) | Train an exploratory uplift model and inspect its scores |

The repository also retains the original [`project.pptx`](uplift_and_kalman/project.pptx) and [`project notes`](uplift_and_kalman/ход%20работы.pdf) as supporting research materials.

## Methods and tools

- Time-dependent customer feature engineering from transactional data
- Linear state-space modeling and Kalman filtering
- Uplift modeling and gain-curve exploration
- Python, pandas, NumPy, SciPy, scikit-learn, `pylift`, `causalml`

## Data and reproducibility

The research uses the X5 uplift data ecosystem, with original context in the [scikit-uplift X5 dataset documentation](https://www.uplift-modeling.com/en/latest/api/datasets/fetch_x5.html).

**Important:** The notebooks currently refer to intermediate CSV exports (including `large_data/...`) which are **not shipped in this repository**. Running the entire notebook sequence from a clean clone is therefore **not yet reproducible** without reconstructing those preprocessing outputs. See [DATA_REQUIREMENTS.md](DATA_REQUIREMENTS.md) for the paths used by the original work.

The following command installs the main import-time dependencies, **but does not by itself make missing data available**:

```bash
python -m pip install -r requirements.txt
```

## Interpretation & limitations

- The two-city setup is a **research scenario**; differences between populations may introduce covariate and treatment-effect shift.
- Scores computed for City X **do not establish a causal uplift gain** there without a suitable counterfactual evaluation strategy.
- The final notebook contains exploratory treatment/outcome manipulations; its plots should **not** be presented as independently validated effects in City X.
- Additional work would be required for robust holdout validation, transportability checks, and a fully reproducible pipeline.

## Contributors

Original collaborative project by **Olga Androsova, Diana Khubezhova, and Nikita Tretyak**. With thanks to Nikita Chukhrov for the task formulation. The analysis and notebooks are retained as a historical research project.
