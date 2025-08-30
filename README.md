# bigquery-cross-account-migration
BQ cross account migration project using DevOps setup



## Purpose:
- Run this in a Python notebook (or as a script) in the DESTINATION GCP account.
- Provide a service-account JSON key for the SOURCE BigQuery account.
- The script will scan source projects (either auto-discovered or provided) and copy all datasets/tables
into a single destination project, preserving dataset/table structure.
- If a dataset/table name conflict occurs at the destination, a random 2-digit suffix will be appended.
- All created datasets will be set to location 'EU'.