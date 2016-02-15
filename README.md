## What's .NET Bulk Operations?
The library offers high performance operations such as Bulk Insert, Update, Delete and Merge in a database.

**Who Need It?**

Anyone who need to perform an operation in the database on multiple rows fast and efficiently.

```csharp
// Support all type of operations && AutoMapping
var bulk = new BulkOperation(connection);

bulk.BulkInsert(dt);
bulk.BulkUpdate(dt);
bulk.BulkDelete(dt);
bulk.BulkMerge(dt);
```

```csharp
// Support Generic Type && Lambda Expressions
var bulk = new BulkOperation<Customer>(connection);
bulk.ColumnInputExpression = c => new { c.Name,  c.FirstName };
bulk.ColumnOutputExpression = c => c.CustomerID;
bulk.ColumnPrimaryKeyExpression = c => c.Code;
bulk.BulkMerge(customers);
```

## Supported Data Source
- Entity
- DataTable
- DataRow
- DataReader
- Expando Object

```csharp
var bulk = new BulkOperation<Customer>(connection);
bulk.BulkInsert(customers); // Entity
bulk.BulkInsert(dt); // DataTable
bulk.BulkInsert(dr); // DataRow
bulk.BulkInsert(reader); // DataReader
bulk.BulkInsert(expando); // ExpandoObject
```

## Supported Provider
- SQL Server 2008+
- SQL Azure
- SQL Compact
- MySQL
- SQLite

```csharp
// One class for all providers!
var bulk = new BulkOperation(connection);
```

## More Projects

**Entity Framework**
- [Entity Framework Extensions](http://www.zzzprojects.com/products/dotnet-development/entity-framework-extensions/)
- [Entity Framework Plus](https://github.com/zzzprojects/EntityFramework-Plus)

**Bulk Operations**
- [NET Entity Framework Extensions](http://www.zzzprojects.com/products/dotnet-development/entity-framework-extensions/)
- [NET Bulk Operations](http://www.zzzprojects.com/products/dotnet-development/bulk-operations/)

**Expression Evaluator**
- [Eval SQL.NET](https://github.com/zzzprojects/Eval-SQL.NET)
- [Eval Expression.NET](https://github.com/zzzprojects/Eval-Expression.NET)

**Others**
- [Extension Methods Library](https://github.com/zzzprojects/Z.ExtensionMethods/)
- [LINQ Async](https://github.com/zzzprojects/Linq-AsyncExtensions)

**Need more info?** info@zzzprojects.com

Contact our outstanding customer support for any request. We usually answer within the next business day, hour, or minutes!
