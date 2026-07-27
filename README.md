#  ML Internship Starter

This repository is a **notebook-first machine learning starter** for the FlyRank internship workflow.  
It is designed to teach a complete, reproducible ML loop:

- Inspect raw data
- Build an interpretable baseline
- Compare with a simple model
- Work with the full release through DuckDB
- Produce shareable artifacts

The repo currently contains three notebooks under `notebooks/` and no production `src/` package yet.

## Repository Layout

```text
.
├── README.md
└── notebooks/
    ├── 01_first_look_and_discovery.ipynb
    ├── 02_your_first_readable_model.ipynb
    └── 03_working_with_the_full_release.ipynb
```

## Notebook Roles

### `01_first_look_and_discovery.ipynb`
- Local/Colab setup
- Pipeline execution
- First-pass discovery from the starter CSV

### `02_your_first_readable_model.ipynb`
- Transparent baseline rules
- Shallow decision trees
- Leakage examples
- Client-aware validation

### `03_working_with_the_full_release.ipynb`
- Hugging Face release access via DuckDB
- SQL feature engineering
- First model on release tables

## Technical Stack

The notebooks assume:

- Python 3.11+
- `pandas`
- `numpy`
- `scikit-learn`
- `matplotlib`
- `duckdb`
- `huggingface_hub`

When running in Colab, notebooks may clone the upstream starter repository and install dependencies from `requirements.txt` if present.  
Locally, notebooks walk up to the repository root and expect the shipped data layout to exist.

## Data Contracts

The notebooks rely on:

- Local starter dataset:  
  `data/raw/content_refresh_anonymized.csv`
- Hugging Face release tables:
  - `dim_clients`
  - `dim_content`
  - `fact_content_daily_performance`
  - `fact_content_query_90d`

If either data source changes, update notebook assumptions before changing model logic.

## What This Workflow Demonstrates

This starter is intentionally opinionated:

- Baseline ranking should be understandable before it is accurate
- Ranking metrics should be prioritized over generic classification accuracy
- Client-level leakage must be avoided in evaluation
- Feature engineering should be deterministic
- Release-scale data should be aggregated in SQL before passing to pandas/scikit-learn

## Running the Notebooks

### Colab

1. Open the notebook
2. Run the setup cell
3. Execute notebooks in order: `01` → `02` → `03`

> `03_working_with_the_full_release.ipynb` requires a Hugging Face read token.  
> Prefer setting `HF_TOKEN` as an environment variable or Colab secret (do not paste tokens into prompts).

### Local

1. Open the repository root in VS Code or Jupyter
2. Ensure the starter CSV exists at:  
   `data/raw/content_refresh_anonymized.csv`
3. Execute notebooks in order

Example setup:

```bash
python -m venv .venv
source .venv/bin/activate
pip install pandas numpy scikit-learn matplotlib duckdb huggingface_hub
```

## Expected Outputs

The notebooks should produce:

- Console summaries of data and model metrics
- Precision/recall analysis charts
- Readable tree exports and baseline comparisons
- DuckDB query outputs for full-release feature engineering

## Engineering Notes

Keep the repository notebook-driven until the workflow stabilizes.  
If extending to a production package, separate concerns clearly:

- Data loading and validation
- Feature generation
- Training and evaluation
- Artifact generation
- Deployment/reporting

Always keep evaluation client-aware, avoid leakage, and document any feature that would not exist before the target event.

## Contributing

- Keep changes small and traceable
- Update notebooks and README together when workflow changes
- Preserve notebook order unless there is a strong reason to reshuffle the teaching flow
- Add reproducible setup steps for any new dependency

## License

Add the project license here once finalized.
