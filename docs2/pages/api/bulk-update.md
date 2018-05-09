---
layout: default
title: Bulk Update
permalink: bulk-update
---



## Bulk Update
Execute an UPDATE operation.

### Example - Bulk Update
```csharp
var dt = new DataTable();
// ...seed...

var bulk = new BulkOperation(connection);

// Easy to customize
bulk.BatchSize = 1000;

// Easy to use
bulk.BulkUpdate(dt);
```

### Example - Bulk Update Generic
```csharp
var list = new List<Customer>();
// ...seed...

var bulk = new BulkOperation<Customer>(connection);

// Easy to customize
bulk.BatchSize = 1000;

// Easy to use
bulk.BulkUpdate(customers);
```

### Performance Benchmarks

| Operations      | 1,000 Rows     | 10,000 Rows    | 100,000 Rows   | 1,000,000 Rows |
| :-------------- | -------------: | -------------: | -------------: | -------------: |
| BulkUpdate      | 50 ms          | 80 ms          | 575 ms         | 6,500 ms       |
