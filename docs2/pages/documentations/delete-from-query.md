# Delete from Query

## Delete From Query
Execute a DELETE operation using a LINQ Query.

### Example
```csharp
var bulk = new BulkOperation<Customer>(connection);

// DELETE all customers inactive for more than 2 years
bulk.DeleteFromQuery(
    c => c.Where(x => x.LastLogin < DateTime.Now.AddYears(-2)));
```

### Performance Benchmarks

| Operations      | 1,000 Entities | 2,000 Entities | 5,000 Entities |
| :-------------- | -------------: | -------------: | -------------: |
| DeleteFromQuery | 1 ms           | 1 ms           | 1 ms           |

### Support
- SQL Server 2008+
- SQL Azure
