# Bulk Generic Methods

## Introduction
Bulk Generic Methods allow you to work with strongly type expression.

| Name      | Description |
| :-------------- | :------------- |
| <a href="/bulk-insert" target="_blank">BulkInsert</a>      | Execute an INSERT operation. |
| <a href="/bulk-update" target="_blank">BulkUpdate</a>      | Execute an UPDATE operation. |
| <a href="/bulk-delete" target="_blank">BulkDelete</a>      | Execute a DELETE operation. |
| <a href="/bulk-merge" target="_blank">BulkMerge</a>       | Execute a MERGE/UPSERT operation. UPDATE existing rows matching the key, and INSERT new rows. |
| <a href="/bulk-synchronize" target="_blank">BulkSynchronize</a> | Execute a SYNCHRONIZE operation. UPDATE existing rows matching the key, INSERT new rows and DELETE records from the destination not existing in the source.</a> |

### Example

```csharp
var list = new List<Customer>();
// ...seed...

var bulk = new BulkOperation<Customer>(connection);

// Easy to customize
bulk.BatchSize = 1000;
bulk.ColumnInputExpression = c => new { c.Name,  c.FirstName };
bulk.ColumnOutputExpression = c => c.CustomerID;
bulk.ColumnPrimaryKeyExpression = c => c.Code;

// Easy to use
bulk.BulkInsert(customers);
bulk.BulkUpdate(customers);
bulk.BulkDelete(customers);
bulk.BulkMerge(customers);

```

### Performance Benchmark

| Operations      | 1,000 Rows     | 10,000 Rows    | 100,000 Rows   | 1,000,000 Rows |
| :-------------- | -------------: | -------------: | -------------: | -------------: |
| <a href="/bulk-insert" target="_blank">BulkInsert</a>      | 6 ms           | 25 ms          | 200 ms         | 2,000 ms       |
| <a href="/bulk-update" target="_blank">BulkUpdate</a>      | 50 ms          | 80 ms          | 575 ms         | 6,500 ms       |
| <a href="/bulk-delete" target="_blank">BulkDelete</a>      | 45 ms          | 70 ms          | 625 ms         | 6,800 ms       |
| <a href="/bulk-merge" target="_blank">BulkMerge</a>       | 65 ms          | 160 ms         | 1200 ms        | 12,000 ms      |

