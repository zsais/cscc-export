Convert CSCC Export for BQ Import
---

We need to convert the CSCC json export file into newline delimited JSON ([NDJON](https://medium.com/datadriveninvestor/json-parsing-error-how-to-load-json-into-bigquery-successfully-using-ndjson-2b7d94616bcb)) in order to import it into BigQuery.


`cat cscc-assets-resource-type.json | jq  -c '.[]' | sed "s/.resource_/_resource_/g" > ndjson-assets.json`


From here, we can create a new table in BigQuery and upload the `ndjson-assets.json` file.
