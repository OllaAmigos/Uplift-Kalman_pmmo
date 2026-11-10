# Data requirements and reproducibility status

This repository does **not** include the original prepared transaction exports. The notebooks were created in an exploratory environment, and some paths were resolved against a working directory or external dataset state that was not committed.

Files referenced by the notebook pipeline include:

- `large_data/init_data/clients.csv`, `large_data/init_data/products.csv`, `large_data/init_data/purchases.csv`
- `large_data/raw_data/clients.csv`, `large_data/raw_data/rich_raw.csv`, `large_data/raw_data/poor_raw.csv`
- `large_data/intermediate_data/panel_data.csv`
- `large_data/output_data/restored_poor_people.csv`, `large_data/output_data/final_dfdiouuy.csv`
- Other working files such as `clients.csv`, `products.csv`, `purchases.csv`, `uplift_train.csv` and `uplift_test.csv`

**Before running:** check and adapt paths in each notebook. The exploratory notebook chain has **not** been re-executed from scratch for this portfolio refactor.

Dataset reference: https://www.uplift-modeling.com/en/latest/api/datasets/fetch_x5.html

Do not commit source records containing personal customer data. Keep large/generated files local via `.gitignore`.
