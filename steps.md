1. create new account
2. create JSON file to access both accounts - test permissins to copy and create datasets / table with BQ cli
3. create script to perform these manual steps - logs in, adds permissions, create service.json file


## For Tomorrow's discussion :-

I still need to finalize on how to write underlying copying mechanism. So far, I checked:

1. Copying using `copy_table` function from google cloud SDK. It seems to be the fastest option available with some drawbacks - mainly, it cannot read external tables
2. Using google client - and to_dataframe function. It can be used as failback for copy_table
3. reading it using row iterator, and copying the table
4. Using `pandas.read_gbq`, but it is still limited to internal tables only.

So far, I have not found ways for external tables, and haven't tested above script with views, stored_procedures and function and other resource types

---

For Tomorrow’s Discussion

I’m still finalizing the approach for the underlying copying mechanism. Here’s a summary of the options I’ve explored so far:

copy_table function (Google Cloud SDK)

Pros: Fastest option available

Limitations: Cannot copy external tables

Google Client + to_dataframe

Pros: Works as a fallback for cases where copy_table is not applicable

Limitations: Potential performance trade-offs at scale

Row Iterator + Manual Copy

Pros: Flexible, works across different table types

Limitations: Likely to be slow for large datasets

pandas.read_gbq

Pros: Simple implementation for internal tables

Limitations: Does not support external tables

Open questions / gaps:

I haven’t identified a reliable option for external tables yet.

The above methods have not been validated against views, stored procedures, functions, or other resource types.

Next steps for discussion:

Decide on the primary approach (likely copy_table) and align on acceptable fallbacks.

Clarify whether we need to support external tables and non-table resources in scope.