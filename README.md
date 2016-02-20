## Bulk Operations
High performance SQL Bulk Operations with hundreds of flexible features missing from SqlBulkCopy.
 - Auditing
 - Case Sensitivity
 - Entity DataSource / Lambda Mapping
 - Output Value
 - And more...

##### Scalable
SQL Server - Benchmarks

| Operations | 1,000 Rows | 10,000 Rows | 100,000 Rows | 1,000,000 Rows |
| ---------- | ---------: | ----------: | -----------: | -------------: |
|**Insert**  | 6 ms       | 25 ms       | 200 ms       | 2,000 ms       |
|**Update**  | 50 ms      | 80 ms       | 575 ms       | 6,500 ms       |
|**Delete**  | 45 ms      | 70 ms       | 625 ms       | 6,800 ms       |
|**Merge**   | 65 ms      | 160 ms      | 1,200 ms     | 12,000 ms      |

> _As fast as SqlBulkCopy for insert but with way more capabilities_

##### Extensible
Support Multiple SQL Providers:
- SQL Server 2008+
- SQL Azure
- SQL Compact
- MySQL
- SQLite

Support Multiple Datasources:
- Entity
- DataTable
- DataRow
- DataReader
- DataSet
- Expando Object

## Download
**[NuGet](https://www.nuget.org/packages/Z.BulkOperations/)**

```
PM> Install-Package Z.BulkOperations
```

_* PRO Version unlocked for the current month_

Stay updated with latest changes

<a href="https://twitter.com/zzzprojects" target="_blank"><img src="http://www.zzzprojects.com/images/twitter_follow.png" alt="Twitter Follow" height="24" /></a>
<a href="https://www.facebook.com/zzzprojects/" target="_blank"><img src="http://www.zzzprojects.com/images/facebook_like.png" alt="Facebook Like" height="24" /></a>

## Insert - Output Identity Value

##### Problem
You need to output newly generated identity value but SqlBulkCopy do not support it.

##### Solution
Map your identity column with output direction.

```
var bulk = new BulkOperation(connection);
bulk.ColumnMappings.Add("CustomerID", ColumnMappingDirectionType.Output);
// ... mappings ...

bulk.BulkInsert(dt);
```

##### Flexibility
You can also output concurrency column (Timestamp) or any other column values. All kind of mapping direction are supported including "Formula" to use with a SQL Formula.

## Entity DataSource / Lambda Mapping
##### Problem
You have a list of entity to insert but SqlBulkCopy doesn't support entity and lambda expression mapping.

##### Solution
Create a generic bulk operations with your entity type and use lambda expression for your column input, output and primary key mapping.

```csharp
// Support Generic Type && Lambda Expressions
var bulk = new BulkOperation<Customer>(connection);
bulk.ColumnInputExpression = c => new { c.Name,  c.FirstName };
bulk.ColumnOutputExpression = c => c.CustomerID;
bulk.ColumnPrimaryKeyExpression = c => c.Code;
bulk.BulkMerge(customers);
```

##### Maintainability
Get rid of hardcoded string and use strongly-typed lambda expressions.

## AutoMapping & Case Sensitivity
##### Problem
You have a DataTable which columns name match name in the database but SqlBulkCopy throw an error because name match are case insensitive.

##### Solution
Turn off case sensitivity with **IsCaseSensitive** property.

```csharp
// Support Generic Type && Lambda Expressions
var bulk = new BulkOperation(connection);
bulk.IsCaseSensitive = false;
bulk.BulkMerge(dt);
```

##### Readability
Remove useless code which would have required to create your own mapping otherwise and keep the essentials.

## Support
Contact our outstanding customer support for any request. We usually answer within the next business day, hour, or minutes!

- info@zzzprojects.com
- [Documentation](https://github.com/zzzprojects/Bulk-Operations/wiki)
- [Issues / Questions](https://github.com/zzzprojects/Bulk-Operations/issues)

## FREE vs PRO
_PRO Version unlocked for the current month_

Features                    | Free Version | [PRO Version](http://bulk-operations.net/#pro)
--------                    | :----------: | :-------------: |
DeleteFromQuery             | Yes          | Yes
UpdateFromQuery             | Yes          | Yes
Bulk Insert                 | No           | Yes
Bulk Update                 | No           | Yes
Bulk Delete                 | No           | Yes
Bulk Merge                  | No           | Yes
Bulk SaveChanges            | No           | Yes
Bulk Synchornize            | No           | Yes
Commercial License          | Yes          | Yes
Royalty-Free                | Yes          | Yes
Support & Upgrades (1 year) | No           | Yes

Learn more about the **[PRO Version](http://bulk-operations.net/#pro)**

## Contribution

Help us to make this library a **MUST-HAVE** by contributing

 - Blog it
 - Comment it
 - Fork it
 - Star it
 - Share it

## More Projects

**Entity Framework**
- [EntityFramework Extensions](http://www.zzzprojects.com/products/dotnet-development/entity-framework-extensions/)
- [EntityFramework-Plus.NET](https://github.com/zzzprojects/EntityFramework-Plus)

**Bulk Operations**
- [EntityFramework Extensions](http://www.zzzprojects.com/products/dotnet-development/entity-framework-extensions/)
- [Bulk Operations](https://github.com/zzzprojects/Bulk-Operations)

**Expression Evaluator**
- [Eval-SQL.NET](https://github.com/zzzprojects/Eval-SQL.NET)
- [Eval-Expression.NET](https://github.com/zzzprojects/Eval-Expression.NET)

**Others**
- [Extension Methods Library](https://github.com/zzzprojects/Z.ExtensionMethods/)
- [LINQ Async](https://github.com/zzzprojects/Linq-AsyncExtensions)

**Need more info?** info@zzzprojects.com

Contact our outstanding customer support for any request. We usually answer within the next business day, hour, or minutes!
