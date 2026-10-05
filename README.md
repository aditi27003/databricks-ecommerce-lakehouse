# Databricks E-commerce Lakehouse

A Databricks project that sets up a Unity Catalog lakehouse for e-commerce data using the **Medallion Architecture** (Bronze → Silver → Gold).

## Structure

```
catalog_setup.ipynb   # Creates the `ecommerce` catalog and bronze/silver/gold schemas
```

## What `catalog_setup` does

| Step | Command |
|------|---------|
| Create catalog | `CREATE CATALOG IF NOT EXISTS ecommerce` |
| Set active catalog | `USE CATALOG ecommerce` |
| Create schemas | `ecommerce.bronze`, `ecommerce.silver`, `ecommerce.gold` |
| Verify | `SHOW DATABASES FROM ecommerce` |
| Teardown (optional) | `DROP CATALOG IF EXISTS ecommerce CASCADE` |

### Medallion layers

- **Bronze** – raw ingested data, as-is from source
- **Silver** – cleaned, validated and conformed data
- **Gold** – business-level aggregates ready for analytics and reporting

## How to run

1. Import `catalog_setup.ipynb` into your Databricks workspace (or clone this repo via **Databricks Repos / Git folders**).
2. Attach it to a cluster or SQL warehouse with Unity Catalog enabled.
3. Run the cells in order.

> ⚠️ The last cell drops the entire `ecommerce` catalog and everything in it. Skip it unless you want to reset the setup.

## Requirements

- Databricks workspace with Unity Catalog
- Permission to create catalogs (`CREATE CATALOG` on the metastore)
