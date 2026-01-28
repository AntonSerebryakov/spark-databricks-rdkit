While creating schema `mol_data` via Databricks UI with managed storage, the operation failed.

Error message:
"Metastore storage root URL does not exist. Default Storage is enabled in your account. You can use the UI to create a new catalog using Default Storage, or please provide a storage location for the catalog."

Context:
- Default Storage is enabled (Databricks Free Edition)
- UI indicates that managed storage creation should be supported
- Catalog creation via UI with Default Storage works
- Schema-level storage creation via UI failed with the error above

Resolution:
- Used existing schema in catalog `mols_storage`
- Uploaded input CSV files directly into the Volume

Additional environment setup:
- RDKit library was not available in the default Databricks runtime
- Installed RDKit via Python package installation
- Restarted Python kernel to apply the changes

Result:
- Data successfully stored in Volume
- Spark can read input files via paths under `/Volumes/...`
- RDKit descriptors calculation works correctly
- Processing continued without blocking issues
