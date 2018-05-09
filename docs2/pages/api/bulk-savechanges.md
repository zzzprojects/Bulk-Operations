# Bulk SaveChanges

## Introduction

Execute an INSERT/UPDATE/DELETE operation using the DataRowState of the DataTable.

### Example - Bulk SaveChanges
```csharp
var dt = new DataTable();
// ...seed...

var bulk = new BulkOperation(connection);

// Easy to customize
bulk.BatchSize = 1000;

// Easy to use
bulk.BulkSaveChanges(dt);
```
