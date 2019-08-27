# Bulk Merge

## Description

The `BulkMerge` method let you merge (insert or update/Upsert) a large number of entities in your database.

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
[Try it (Entity)](https://dotnetfiddle.net/qpe8bV)

[Try it (DataTable)](https://dotnetfiddle.net/rgugIj) 

### Performance Comparison

| Operations      | 1,000 Entities | 2,000 Entities | 5,000 Entities |
| :-------------- | -------------: | -------------: | -------------: |
| BulkMerge       | 80 ms          | 110 ms         | 170 ms         |

[Try this benchmark online (Entity)](https://dotnetfiddle.net/roGRsu)

[Try this benchmark online (DataTable)](https://dotnetfiddle.net/CY5s3G)

> HINT: A lot of factors might affect the benchmark time such as index, column type, latency, throttling, etc.

### Scenarios
The `BulkMerge` method is **fast** but also **flexible** to let you handle various scenarios such as:

- [Merge and keep identity value](#merge-and-keep-identity-value)
- [Merge with custom key](#merge-with-custom-key)
- [Merge and include/exclude properties](#merge-and-includeexclude-properties)
- [Merge with related child entities](#merge-with-related-child-entities) 
- [More scenarios](#more-scenarios)

### Advantages
- Easy to use
- Flexible
- Increase performance
- Increase application responsiveness

## Getting Started

### Bulk Merge
The `BulkMerge` and `BulkMergeAync` methods let you merge a large number of entities in your database.

```csharp
bulk.BulkMerge(customers);

bulk.BulkMergeAsync(customers, cancellationToken);
```
[Try it (Entity)](https://dotnetfiddle.net/pigFx8)

[Try it (DataTable)](https://dotnetfiddle.net/LULDpj) 

### Bulk Merge with options
The `options` parameter let you use a lambda expression to customize the way entities are inserted/updated.

```csharp
bulk.AutoMapKeyExpression = c => c.Code;
bulk.BulkMerge(customers);
```
[Try it (Entity)](https://dotnetfiddle.net/5wMQ6X)

```csharp
bulk.AutoMapKeyName = "Code";
bulk.BulkMerge(customers);
```
[Try it (DataTable)](https://dotnetfiddle.net/JJIPCB)

## Real Life Scenarios

### Merge and keep identity value
Your entity has an identity property, but you want to force to insert a specific value instead. The `MergeKeepIdentity` option allows you to keep the identity value of your entity.

```csharp
bulk.MergeKeepIdentity = true;
bulk.BulkMerge(customers);
```
[Try it (Entity)](https://dotnetfiddle.net/52uijH)

[Try it (DataTable)](https://dotnetfiddle.net/gNXl1z) 

### Merge and include/exclude properties
You want to merge your entities but only for specific properties.

- `ColumnInputExpression`: This option let you choose which properties to map.
- `ColumnIgnoreExpression`: This option let you ignore properties that are auto-mapped.
- `IgnoreOnMergeInsertExpression`: This option let you ignore properties only for the `INSERT` part.
- `IgnoreOnMergeUpdateExpression`: This option let you ignore properties only for the `UPDATE` part.

```csharp
bulk.ColumnInputExpression = c => new { c.CustomerID, c.Name};
bulk.BulkMerge(customers);
            
bulk.IgnoreOnMergeUpdateExpression = c => new { c.CreatedDate };
bulk.BulkMerge(customers);
```
[Try it (Entity)](https://dotnetfiddle.net/W4TJkK)

```csharp
var columnMapping = new ColumnMapping("CreatedDate");
				
columnMapping.IgnoreOnMergeUpdate = true;
					
bulk.ColumnMappings.Add("CustomerID", true);
bulk.ColumnMappings.Add("UpdatedDate");
bulk.ColumnMappings.Add("Name");
bulk.ColumnMappings.Add(columnMapping);
bulk.BulkMerge(dtCustomers);
```
[Try it (DataTable)](https://dotnetfiddle.net/TIfeSG)

### Merge with custom key
You want to merge entities, but you don't have the primary key. The `ColumnPrimaryKeyExpression` let you use as a key any property or combination of properties.

```csharp
bulk.AutoMapKeyExpression = c => c.Code;
bulk.BulkMerge(customers);
```
[Try it (Entity)](https://dotnetfiddle.net/Xlcdxq)

```csharp
bulk.AutoMapKeyName = "Code";
bulk.BulkMerge(customers);
```
[Try it (DataTable)](https://dotnetfiddle.net/9KOxdW) 


### Merge with related child entities
You want to merge entities but also merge related child entities.

```csharp
bulk.DestinationTableName = "Invoices";
bulk.AutoMapOutputIdentity = true;
bulk.BulkMerge(invoices);

// SET foreign key value			
invoices.ForEach(x => x.Items.ForEach(y => y.InvoiceID = x.InvoiceID));

bulk.DestinationTableName = "InvoiceItems";
bulk.BulkMerge(invoices.SelectMany(x => x.Items).ToList());
```
[Try it (Entity)](https://dotnetfiddle.net/LLDcvy)

[Try it (DataTable)](https://dotnetfiddle.net/rhq5ZM) 

### More scenarios
Hundred of scenarios has been solved and are now supported.

The best way to ask for a special request or to find out if a solution for your scenario already exists is by contacting us:
info@zzzprojects.com

## Documentation

### BulkMerge

###### Methods

| Name | Description | Example (DataTable) | Example (Entity) |
| :--- | :----------  | :------ | :------ |
| `BulkMerge<T>(items)` | Bulk insert entities in your database. | [Try it](https://dotnetfiddle.net/hjTQmE) | [Try it](https://dotnetfiddle.net/z2lxbA) |
| `BulkMergeAsync<T>(items)` | Bulk insert entities asynchronously in your database. | | |
| `BulkMergeAsync<T>(items, cancellationToken)` | Bulk insert entities asynchronously in your database. | | |

###### Options
More options can be found here:

- [Audit](https://bulk-operations.net/audit)
- [Batch](https://bulk-operations.net/batch)
- [Execute Event](https://bulk-operations.net/execute-event)
- [Log](https://bulk-operations.net/log)
- [Temporary Table](https://bulk-operations.net/temporary-table)
- [Transient Error](https://bulk-operations.net/transient-error)
- [SQL Server](https://bulk-operations.net/sql-server)
