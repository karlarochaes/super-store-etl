# Queries
## 1. Process and prepare database
### 1.1 Upload tables
- Project name: super-store-etl
- Dataset name: superstore
- Tables:
  - sales
 
### 1.2 Identify and handle null values

Search in all table columns
```sql
SELECT
  col_name,
  COUNT(1) nulls_count
FROM
  `superstore.sales` t,
  UNNEST(REGEXP_EXTRACT_ALL(TO_JSON_STRING(t), r'"(\w+)":null')) col_name
GROUP BY
  col_name
```
