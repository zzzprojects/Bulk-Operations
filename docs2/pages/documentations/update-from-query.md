# Update from Query

## Update From Query
Execute an INSERT operation.

### Example
```csharp
var bulk = new BulkOperation<Customer>(connection);

// UPDATE all customers inactive for more than 2 years
bulk.UpdateFromQuery(
    c => c.Where(x => x.IsActive && x.LastLogin < DateTime.Now.AddYears(-2)),
    c => new Customer {IsActive = false});
```

### Performance Benchmarks

| Operations      | 1,000 Entities | 2,000 Entities | 5,000 Entities |
| :-------------- | -------------: | -------------: | -------------: |
| UpdateFromQuery | 1 ms           | 1 ms           | 1 ms           |

### Support
- SQL Server 2008+
- SQL Azure
