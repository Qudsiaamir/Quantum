# Quantum Home Credit Default Risk

A Python/Jupyter machine-learning project for exploring Home Credit loan default prediction with classical baselines and an optional experimental D-Wave quantum feature-selection section.

## What This Project Does

This repository contains a notebook-based workflow for the Kaggle Home Credit Default Risk dataset. It walks through exploratory data analysis, preprocessing, feature engineering, baseline model training, feature importance review, LightGBM modeling, and an optional quantum-inspired feature-selection experiment.

## Features

- Exploratory analysis of Home Credit application data
- Missing-value review and anomaly handling
- Label encoding and one-hot encoding for categorical features
- Logistic regression and random forest baselines
- Polynomial and domain-knowledge feature engineering
- LightGBM cross-validation workflow
- Optional D-Wave feature-selection experiment
- Clean output handling through the `outputs/` directory

## Tech Stack

- Python 3.10+
- JupyterLab
- NumPy
- pandas
- scikit-learn
- matplotlib
- seaborn
- LightGBM
- Optional: D-Wave Ocean SDK

## Folder Structure

```text
.
|-- README.md
|-- requirements.txt
|-- requirements-optional.txt
|-- .env.example
|-- .gitignore
|-- data/
|   |-- README.md
|   `-- raw/
|       `-- README.md
|-- docs/
|   `-- model-summaries/
|-- notebooks/
|   `-- home_credit_default_risk_quantum.ipynb
`-- outputs/
    `-- README.md
```

## Installation

Create and activate a virtual environment:

```bash
python -m venv .venv
source .venv/bin/activate
```

Install the core dependencies:

```bash
pip install -r requirements.txt
```

Optional, only for the D-Wave feature-selection section:

```bash
pip install -r requirements-optional.txt
```

## Data Setup

Download the Home Credit Default Risk dataset from Kaggle:

https://www.kaggle.com/competitions/home-credit-default-risk/data

Place the CSV files in:

```text
data/raw/
```

At minimum, the notebook requires:

```text
data/raw/application_train.csv
data/raw/application_test.csv
```

## Run Locally

Start JupyterLab from the repository root:

```bash
jupyter lab
```

Open and run:

```text
notebooks/home_credit_default_risk_quantum.ipynb
```

Generated submission CSVs and plots are written to:

```text
outputs/
```

## Environment Variables

No environment variables are required for the classical machine-learning notebook sections.

The optional D-Wave section may require D-Wave credentials. Use `.env.example` as a template, then export the values in your shell before starting Jupyter:

```bash
export DWAVE_API_TOKEN="your-token"
export DWAVE_API_SOLVER="your-solver-name"
```

The notebook does not auto-load `.env` files.

## Example Usage

After the setup above, run the notebook cells in order. The baseline models create files such as:

```text
outputs/log_reg_baseline.csv
outputs/random_forest_baseline.csv
outputs/baseline_lgb.csv
```

These files follow the Kaggle submission format with `SK_ID_CURR` and `TARGET` columns.

## Testing And Verification

There is no formal test suite yet. For a quick repository sanity check, run:

```bash
python -m compileall .
```

To fully verify the notebook, install dependencies, add the Kaggle data files to `data/raw/`, then run the notebook in JupyterLab.

## Troubleshooting

- `FileNotFoundError` for `application_train.csv` or `application_test.csv`: download the Kaggle data and place the CSV files in `data/raw/`.
- `ModuleNotFoundError`: confirm your virtual environment is activated and run `pip install -r requirements.txt`.
- LightGBM install issues: upgrade `pip` first with `python -m pip install --upgrade pip`.
- D-Wave import or authentication errors: install `requirements-optional.txt` and configure D-Wave credentials. The classical ML sections do not require D-Wave.
- Long runtime: random forest, LightGBM, and D-Wave sections can take noticeably longer than the exploratory cells.

## Roadmap

- Add a small script that validates expected data files before launching the notebook.
- Extract reusable preprocessing and modeling code into Python modules.
- Add tests for feature engineering helpers after code is extracted from the notebook.
- Add a lightweight sample dataset or synthetic-data mode for quick smoke tests.

## License

No license file is currently included. If you plan to share or accept contributions, choose and add a license such as MIT, Apache-2.0, or another license appropriate for your goals.
