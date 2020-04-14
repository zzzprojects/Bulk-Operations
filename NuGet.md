An improved version of SqlBulkCopy.

## Url

- [Website](https://bulk-operations.net/)
- [Getting Started](https://bulk-operations.net/overview)
- [Documentation](https://bulk-operations.net/bulk-insert)
- [Online Examples](https://bulk-operations.net/online-examples)

## Example

```csharp
// Easy to use
bulk.DestinationTableName = "Customers";
bulk.BulkMerge(customers);

// Easy to customize
bulk.DestinationTableName = "Customers";
bulk.BatchSize = 100;
bulk.AutoMapOutputIdentity = true;
bulk.BulkMerge(customers);
```

- Try it (DataTable): [https://dotnetfiddle.net/2B7QpT](https://dotnetfiddle.net/2B7QpT)
- Try it (Entity): [https://dotnetfiddle.net/istUUT](https://dotnetfiddle.net/istUUT)
