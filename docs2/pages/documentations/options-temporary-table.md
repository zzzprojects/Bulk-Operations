# Temporary Table

Customize how and when to use a temporary table instead of inline SQL.

## TemporaryTableBatchByTable
Allow you to set the maximum number of batches a temporary table can contain.

- Default Value: 0 (unlimited)
### Example
```csharp
var bulk = new BulkOperation(connection);

bulk.TemporaryTableBatchByTable = 5;

bulk.BulkMerge(dt);
```

## TemporaryTableInsertBatchSize
Allow you to set the number of record by batch to insert in a temporary table.

- Default Value: 10,000
### Example
```csharp
var bulk = new BulkOperation(connection);

bulk.TemporaryTableInsertBatchSize = 1000;

bulk.BulkMerge(dt);
```

## TemporaryTableMinRecord
Allow you to set the minimum number of records before a temporary table strategy is used.

- Default Value: 10
### Example
```csharp
var bulk = new BulkOperation(connection);

bulk.TemporaryTableMinRecord = 15;

bulk.BulkMerge(dt);
```

## TemporaryTableUseTableLock
Allow you to lock the temporary table while being populated.

- Default Value: true

### Example
```csharp
var bulk = new BulkOperation(connection);

bulk.TemporaryTableUseTableLock = true;

bulk.BulkMerge(dt);
```
