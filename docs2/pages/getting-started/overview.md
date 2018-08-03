# Overview

## What's Bulk Operations library?

Like SqlBulkCopy, it allows you to perform very fast insertion in an SQL Server.

Unlike SqlBulkCopy, it supports all kind of operations:

- Bulk Insert
- Bulk Update
- Bulk Delete
- Bulk Merge
- Bulk SaveChanges
- Bulk Synchronize

And many providers:

- SQL Server 2008+
- SQL Azure
- SQL Compact
- Oracle
- MySQL
- PostgreSQL
- SQLite

It’s easy to use, and easy to customize.



```csharp
// Easy to use
var bulk = new BulkOperation(connection);
bulk.BulkInsert(dt);
bulk.BulkUpdate(dt);
bulk.BulkDelete(dt);
bulk.BulkMerge(dt);

// Easy to customize
var bulk = new BulkOperation<Customer>(connection);
bulk.BatchSize = 1000;
bulk.ColumnInputExpression = c => new { c.Name,  c.FirstName };
bulk.ColumnOutputExpression = c => c.CustomerID;
bulk.ColumnPrimaryKeyExpression = c => c.Code;
bulk.BulkMerge(customers);
```

## Installing & Upgrading
Download the <a href="/download">NuGet Package</a>

## Requirements

### .NET Framework Version

- .NET Framework 4.0 or greater

### Database Provider

- SQL Server 2008+
- SQL Azure
- SQL Compact
- Oracle
- MySQL
- PostgreSQL
- SQLite

### Note

- .NET Core is under development

### Is it that simple?

Yes,

That’s why people feel in love so quickly with our library.

## Installing
Download the <a href="/download">NuGet Package</a>

## Requirements

### .NET Framework Version

- .NET Framework 4.0 or greater

### Database Provider

- SQL Server 2008+
- SQL Azure
- SQL Compact
- Oracle
- MySQL
- PostgreSQL
- SQLite

### Note

- .NET Core is under development


### Who use it?

Already **thousands** of companies of all sizes and kinds use it:

- From start-up company with one developer
- To fortune 100 companies with hundreds of developers

Are you still not using it? Give it one try, and you will understand why they choose our library.

Under the hood, some of our libraries also use it:

- [Entity Framework Extensions](http://entityframework-extensions.net/)
- [Dapper Plus](http://dapper-plus.net/)
