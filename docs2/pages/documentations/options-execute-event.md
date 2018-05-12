# Execute Event

## Excecute Event Options
- [BulkOperationExecuting](#bulkoperationexecuting)
- [BulkOperationExecuted](#bulkoperationexecuted)

## BulkOperationExecuting
Allow you to change configuration before the bulk operation is executed.

### Example
```csharp
var bulk = new BulkOperation(connection);

bulk.BulkOperationExecuting = bulkOperation => { /* configuration */ };

bulk.BulkMerge(dt);
```

## BulkOperationExecuted
Allow you to change configuration after the bulk operation is executed.

### Example
```csharp
var bulk = new BulkOperation(connection);

bulk.BulkOperationExecuted = bulkOperation => { /* configuration */ };

bulk.BulkMerge(dt);
```
