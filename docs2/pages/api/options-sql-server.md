# SQL Server

## SQL Server Options
- [SqlBulkCopyOptions](#sqlbulkcopyoptions)

## SqlBulkCopyOptions
Allow you to set the SqlBulkCopyOptions to use when a strategy with the SqlBulkCopy is selected.

### Example
```csharp
var bulk = new BulkOperation(connection);

bulk.SqlBulkCopyOptions = SqlBulkCopyOptions.Default | SqlBulkCopyOptions.TableLock;

bulk.BulkMerge(dt);
```
