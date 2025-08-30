# bigquery-cross-account-migration
BQ cross account migration project using DevOps setup



## Purpose:
- Run this in a Python notebook (or as a script) in the DESTINATION GCP account.
- Provide a service-account JSON key for the SOURCE BigQuery account.
- The script will scan source projects (either auto-discovered or provided) and copy all datasets/tables
into a single destination project, preserving dataset/table structure.
- If a dataset/table name conflict occurs at the destination, a random 2-digit suffix will be appended.
- All created datasets will be set to location 'EU'.




Purpose: migrate BigQuery datasets from a source account/project into a destination project.

Features:

Works from Jupyter notebook or CLI.

Supports scanning multiple source projects.

Handles dataset/table name conflicts.

EU-only (or configurable).

Optional GCS fallback.

Quickstart:

Install dependencies with pip install -r requirements.txt.

Run python scripts/bq_migrate_cli.py --source-key ... --dest-project ....

Or open notebook/migrate_demo.ipynb and run interactively.

Auth:

Source: pass JSON key.

Destination: use ADC (gcloud auth application-default login) or pass another key.

Permissions needed:

Source SA: roles/bigquery.dataViewer on source projects.

Destination SA: roles/bigquery.dataEditor on destination project.

(Optional) GCS roles if staging.



🚀 Suggested Workflow

One-time setup

Create a dedicated repo (bq-migration-tool).

Commit code + notebook + requirements.

Grant IAM roles for source and destination SAs.

Dry run first

Run notebook with dry_run=True to preview what will be created.

Run full migration

Use notebook (interactive) or CLI for automation.

Optionally enable GCS fallback if direct copy fails.

Post-migration checks

Verify row counts (SELECT COUNT(*)) in source vs destination.

Run sanity queries in new project.


🛠️ Enhancements you can add later

Logging results into CSV (success/failure per table).

Parallel execution with concurrent.futures to speed up many tables.

Dockerfile for portable runs.