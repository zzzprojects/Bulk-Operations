# From Query Methods

## Introduction
FromQuery operations allow you to use LINQ Query to execute an operation directly in the database

| Name      | Description |
| :-------------- | :------------- |
| <a href="/delete-from-query">DeleteFromQuery</a> | Execute a DELETE operation using a LINQ Query. |
| <a href="/update-from-query">UpdateFromQuery</a> | Execute an UPDATE operation using a LINQ Query. |



### Example
```csharp
var bulk = new BulkOperation<Customer>(connection);

// DELETE all customers inactive for more than 2 years
bulk.DeleteFromQuery(
    c => c.Where(x => x.LastLogin < DateTime.Now.AddYears(-2)));

// UPDATE all customers inactive for more than 2 years
bulk.UpdateFromQuery(
    c => c.Where(x => x.IsActive && x.LastLogin < DateTime.Now.AddYears(-2)),
    c => new Customer {IsActive = false});
```


### Performance Benchmarks

| Operations      | 1,000 Entities | 2,000 Entities | 5,000 Entities |
| :-------------- | -------------: | -------------: | -------------: |
| <a href="/delete-from-query">DeleteFromQuery</a> | 1 ms           | 1 ms           | 1 ms           |
| <a href="/update-from-query">UpdateFromQuery</a> | 1 ms           | 1 ms           | 1 ms           |

### Support
- SQL Server 2008+
- SQL Azure
