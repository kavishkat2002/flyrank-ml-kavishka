# FlyRank ML Internship Starter

A notebook-first machine learning starter for the FlyRank internship workflow.

This project walks through a complete and reproducible ranking pipeline:

- Explore raw data
- Build an interpretable baseline
- Compare against a simple model
- Work with full-release tables using DuckDB
- Generate shareable outputs

---

## Repository Structure

```text
.
├── README.md
└── notebooks/
    ├── 01_first_look_and_discovery.ipynb
    ├── 02_your_first_readable_model.ipynb
    └── 03_working_with_the_full_release.ipynb
```

The repository is currently notebook-driven and does not yet include a production `src/` package.

---

## Learning Path

### 1) `01_first_look_and_discovery.ipynb`
- Environment setup (local and Colab)
- Starter pipeline execution
- Initial exploration of the starter CSV

### 2) `02_your_first_readable_model.ipynb`
- Transparent rule-based baseline
- Shallow decision tree modeling
- Leakage examples and prevention
- Client-aware validation

### 3) `03_working_with_the_full_release.ipynb`
- Accessing Hugging Face release data through DuckDB
- SQL-based feature engineering
- First model on release-scale tables

Run notebooks in this order: `01` → `02` → `03`.

---

## Prerequisites

- Python 3.11+
- `pandas`
- `numpy`
- `scikit-learn`
- `matplotlib`
- `duckdb`
- `huggingface_hub`

> In Colab, setup cells may clone the upstream starter repository and install from `requirements.txt` (if available).  
> Locally, notebooks expect the repository data layout to be present.

---

## Data Requirements

The notebooks depend on:

- Local starter dataset: `data/raw/content_refresh_anonymized.csv`
- Hugging Face release tables:
  - `dim_clients`
  - `dim_content`
  - `fact_content_daily_performance`
  - `fact_content_query_90d`

If these sources change, update notebook assumptions before changing model logic.

---

## Quick Start

### Local Setup

```bash
python -m venv .venv
source .venv/bin/activate
pip install pandas numpy scikit-learn matplotlib duckdb huggingface_hub
```

Then:
1. Open the repository root in VS Code or Jupyter.
2. Confirm `data/raw/content_refresh_anonymized.csv` exists.
3. Run notebooks in sequence (`01` → `02` → `03`).

### Colab Setup

1. Open a notebook in Colab.
2. Run the setup cell.
3. Execute notebooks in sequence (`01` → `02` → `03`).

> `03_working_with_the_full_release.ipynb` requires a Hugging Face read token.  
> Set `HF_TOKEN` as an environment variable or a Colab secret. Do not paste tokens into prompts.

---

## Expected Outputs

After completing the notebooks, you should have:

- Dataset and metric summaries in notebook output
- Precision/recall analysis visualizations
- Readable tree artifacts and baseline comparisons
- DuckDB query outputs for release-scale features

---

## Engineering Principles

This starter intentionally emphasizes:

- Interpretability before complexity
- Ranking-focused evaluation over generic classification metrics
- Strict prevention of client-level leakage
- Deterministic feature engineering
- SQL-first aggregation for release-scale data before pandas/scikit-learn

If this workflow is later promoted to production code, separate responsibilities into:

- Data loading and validation
- Feature engineering
- Training and evaluation
- Artifact generation
- Deployment and reporting

---

## Contributing

- Keep changes small, traceable, and well-scoped.
- Update notebooks and README together when workflow behavior changes.
- Preserve notebook order unless there is a strong reason to change the learning flow.
- Add reproducible setup steps for any new dependency.

---

## License

Add the project license information once finalized.
