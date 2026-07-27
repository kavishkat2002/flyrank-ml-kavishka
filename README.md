 #ML Internship Starter

 
This repository is a notebook-first machine learning starter for the FlyRank internship workflow. It is designed to teach a complete, reproducible ML loop:

inspect the raw data,
build an interpretable baseline,
compare it with a simple model,
work with the full release through DuckDB,
produce shareable artifacts.
The repo currently contains three notebooks under notebooks/ and no production src/ package yet.

Repository Layout
.
├── README.md
└── notebooks/
	├── 01_first_look_and_discovery.ipynb
	├── 02_your_first_readable_model.ipynb
	└── 03_working_with_the_full_release.ipynb
Notebook Roles
01_first_look_and_discovery.ipynb: local/Colab setup, pipeline execution, and first-pass discovery from the starter CSV.
02_your_first_readable_model.ipynb: transparent baseline rules, shallow decision trees, leakage examples, and client-aware validation.
03_working_with_the_full_release.ipynb: Hugging Face release access via DuckDB, SQL feature engineering, and a first model on the release tables.
Technical Stack
The notebooks assume the following runtime profile:

Python 3.11+
pandas
numpy
scikit-learn
matplotlib
duckdb
huggingface_hub
When running in Colab, the notebooks clone the upstream starter repository and install dependencies from requirements.txt if present in that environment. Locally, they walk up to the repository root and expect the shipped data layout to exist.

Data Contracts
The notebooks rely on a stable starter dataset and a release schema:

data/raw/content_refresh_anonymized.csv for the local starter workflow.
Hugging Face release tables for the full-release workflow, including dim_clients, dim_content, fact_content_daily_performance, and fact_content_query_90d.
If either data source changes, update the notebook assumptions before changing the model logic.

What The Workflow Demonstrates
This starter is intentionally opinionated:

baseline ranking should be understandable before it is accurate,
ranking metrics should be used instead of generic classification accuracy alone,
client-level leakage must be avoided in evaluation,
feature engineering should be deterministic,
release-scale data should be aggregated in SQL before being handed to pandas or scikit-learn.
Running The Notebooks
Colab
Open the notebook.
Run the setup cell.
Follow the execution order from notebook 01 to notebook 03.
Notebook 03 requires a Hugging Face read token. Prefer setting HF_TOKEN as an environment variable or a Colab secret rather than pasting it into the prompt.

Local
Open the repository root in VS Code or Jupyter.
Ensure the expected starter CSV is available at data/raw/content_refresh_anonymized.csv.
Execute the notebooks in order.
Example local setup:

python -m venv .venv
source .venv/bin/activate
pip install pandas numpy scikit-learn matplotlib duckdb huggingface_hub
Expected Outputs
The notebooks are meant to produce the following kinds of artifacts:

console summaries of the data and model metrics,
charts for precision/recall analysis,
readable tree exports and baseline comparisons,
DuckDB query results for full-release feature engineering.
Engineering Notes
The repository should stay notebook-driven until the workflow stabilizes. If you extend it into a production package, separate concerns explicitly:

data loading and validation,
feature generation,
training and evaluation,
artifact generation,
deployment or reporting.
Keep the evaluation client-aware, avoid leakage, and document any feature that could not exist before the target event.

Contributing
Keep changes small and traceable.
Update the notebooks and README together when the workflow changes.
Preserve the notebook order unless there is a strong reason to reshuffle the teaching flow.
Add reproducible setup steps for any new dependency.
License
Add the project license here once it is finalized.
