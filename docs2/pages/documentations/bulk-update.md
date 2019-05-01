# Bulk Update

## Description

The `BulkUpdate` method let you update a large number of entities in your database.

```csharp
// easy to use
bulk.DestinationTableName = "Customers";
bulk.BulkUpdate(customers);

// Easy to customize
bulk.DestinationTableName = "Customers";
bulk.BatchSize = 100;
bulk.AutoMapOutputDirection = true;
bulk.BulkUpdate(customers);
```
[Try it (Entity)](https://dotnetfiddle.net/xKlMEt)

[Try it (DataTable)](https://dotnetfiddle.net/p2YC2w)

### Performance Comparison

| Operations      | 1,000 Entities | 2,000 Entities | 5,000 Entities |
| :-------------- | -------------: | -------------: | -------------: |
| BulkUpdate      | 80 ms          | 110 ms         | 170 ms         |

[Try it (Entity)](https://dotnetfiddle.net/tf8sSi)

[Try it (DataTable)](https://dotnetfiddle.net/j6bFmr) 

> HINT: A lot of factors might affect the benchmark time such as index, column type, latency, throttling, etc.

### Scenarios
The `BulkUpdate` method is **fast** but also **flexible** to let you handle various scenarios such as:

- [Update and include/exclude properties](#update-and-includeexclude-properties)
- [Update with custom key](#update-with-custom-key)
- [Update with related child entities (Include Graph)](#update-with-related-child-entities-include-graph)
- [More scenarios](#more-scenarios)

### Advantages
- Easy to use
- Flexible
- Increase performance
- Increase application responsiveness

## Getting Started

### Bulk Update
The `BulkUpdate` and `BulkUpdateAync` methods your let update a large number of entities in your database.

```csharp
bulk.BulkUpdate(customers);

bulk.BulkUpdateAsync(customers, cancellationToken);
```
[Try it (Entity)](https://dotnetfiddle.net/kK4qnb)

[Try it (DataTable)](https://dotnetfiddle.net/COCXD4) 

### Bulk Update with options
The `options` parameter let you use a lambda expression to customize the way entities are updated.

```csharp
bulk.AutoMapKeyExpression = c => c.Code;
bulk.BulkUpdate(customers);
```
[Try it (Entity)](https://dotnetfiddle.net/16kWmc)

```csharp
bulk.AutoMapKeyName = "Code";
bulk.BulkUpdate(dtCustomers);
```
[Try it (DataTable)](https://dotnetfiddle.net/uWRH6Y)  

## Real Life Scenarios

### Update and include/exclude properties
You want to update your entities but only for specific properties.

- `ColumnInputExpression`: This option let you choose which properties to map.
- `IgnoreOnUpdateExpression`: This option let you ignore properties that are auto-mapped.

```csharp
bulk.IgnoreOnUpdateExpression = c =>  new { c.ColumnToIgnore };
bulk.BulkUpdate(customers.Skip(2));
```
[Try it (Entity)](https://dotnetfiddle.net/3z531u)

```csharp
var columnMapping = new ColumnMapping("CreatedDate");
				
columnMapping.IgnoreOnUpdate = true;
					
bulk.ColumnMappings.Add("CustomerID", true);
bulk.ColumnMappings.Add("UpdatedDate");
bulk.ColumnMappings.Add("Name");
bulk.ColumnMappings.Add(columnMapping);
bulk.BulkUpdate(dtCustomers);
```
[Try it (DataTable)](https://dotnetfiddle.net/EyAtSE) 

### Update with custom key
You want to update entities, but you don't have the primary key. The `ColumnPrimaryKeyExpression` let you use as a key any property or combination of properties.

```csharp
bulk.AutoMapKeyExpression = c => c.Code;
bulk.BulkUpdate(customers);
```
[Try it (Entity)](https://dotnetfiddle.net/BEL4Ny)

```csharp
bulk.AutoMapKeyName = "Code";
bulk.BulkUpdate(customers);
```
[Try it (DataTable)](https://dotnetfiddle.net/wJJM5T) 

### Update with related child entities
You want to update entities but also automatically insert related child entities.

```csharp
bulk.DestinationTableName = "Invoices";
bulk.AutoMapOutputIdentity = true;

bulk.BulkUpdate(invoices);

// SET foreign key value			
invoices.ForEach(x => x.Items.ForEach(y => y.InvoiceID = x.InvoiceID));

bulk.DestinationTableName = "InvoiceItems"; 
bulk.BulkUpdate(invoices.SelectMany(x => x.Items).ToList());
```
[Try it (Entity)](https://dotnetfiddle.net/eEmCu1)

[Try it (DataTable)](https://dotnetfiddle.net/8C7est) 

### More scenarios
Hundred of scenarios has been solved and are now supported.

The best way to ask for a special request or to find out if a solution for your scenario already exists is by contacting us:
info@zzzprojects.com

## Documentation

### BulkUpdate

###### Methods

| Name | Description | Example (DataTable) | Example (Entity) |
| :--- | :---------- | :------ | :------ |
| `BulkUpdate<T>(items)` | Bulk update entities in your database. | [Try it](https://dotnetfiddle.net/jFMKu1) | [Try it](https://dotnetfiddle.net/fuv4IV) |
| `BulkUpdateAsync<T>(items)` | Bulk update entities asynchronously in your database. | |
| `BulkUpdateAsync<T>(items, cancellationToken)` | Bulk update entities asynchronously in your database. | |

###### Options
More options can be found here:

- [Audit](https://bulk-operations.net/audit)
- [Batch](https://bulk-operations.net/batch)
- [Execute Event](https://bulk-operations.net/execute-event)
- [Log](https://bulk-operations.net/log)
- [Temporary Table](https://bulk-operations.net/temporary-table)
- [Transient Error](https://bulk-operations.net/transient-error)
- [SQL Server](https://bulk-operations.net/sql-server)
