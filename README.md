## What's Bulk Operations?
It overcomes SqlBulkCopy limitations by adding high-performance bulk operations to insert, update, delete and merge.

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
- PostgreSQL
- Oracle

Support Multiple Datasources:
- Entity
- DataTable
- DataRow
- DataReader
- DataSet
- Expando Object

## Download
<a href="https://www.nuget.org/packages/Z.BulkOperations/" target="_blank"><img src="https://zzzprojects.github.io/images/nuget/bulk-operations-v.svg" alt="download" /></a>
<a href="https://www.nuget.org/packages/Z.BulkOperations/" target="_blank"><img src="https://zzzprojects.github.io/images/nuget/bulk-operations-d.svg" alt="" /></a>

```
PM> Install-Package Z.BulkOperations
```

_* PRO Version unlocked for the current month_

Stay updated with the latest changes:

<a href="https://twitter.com/zzzprojects" target="_blank"><img src="http://www.zzzprojects.com/images/twitter_follow.png" alt="Twitter Follow" height="24" /></a>
<a href="https://www.facebook.com/zzzprojects/" target="_blank"><img src="http://www.zzzprojects.com/images/facebook_like.png" alt="Facebook Like" height="24" /></a>

## Insert - Output Identity Value

##### Problem
You need to output newly generated identity value, but SqlBulkCopy does not support it.

##### Solution
Map your identity column with output direction.

```
var bulk = new BulkOperation(connection);

bulk.ColumnMappings.Add("CustomerID", ColumnMappingDirectionType.Output);
// ... mappings ...

bulk.BulkInsert(dt);
```

##### Flexibility
You can also output concurrency column (Timestamp) or any other column values. All kinds of mapping directions are supported, including "Formula" to use with a SQL Formula.

## Entity DataSource / Lambda Mapping
##### Problem
You have a list of entities to insert, but SqlBulkCopy doesn't support entity and lambda expression mapping.

##### Solution
Create generic bulk operations with your entity type and use lambda expression for your column input, output, and primary key mapping.

```csharp
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
You have a DataTable which columns name match name in the database but SqlBulkCopy throws an error because name matches are case insensitive.

##### Solution
Turn off case sensitivity with **IsCaseSensitive** property.

```csharp
var bulk = new BulkOperation(connection);

bulk.IsCaseSensitive = false;

bulk.BulkMerge(dt);
```

##### Readability
Remove useless code that would have required you to create your own mapping and keep the essentials.

## Support
Contact our outstanding customer support for any request. We usually answer within the next business day, hour, or minutes!

- info@zzzprojects.com
- [Documentation](https://github.com/zzzprojects/Bulk-Operations/wiki)
- [Issues / Questions](https://github.com/zzzprojects/Bulk-Operations/issues)

## PRO
_PRO Version unlocked for the current month_

Features                    | [PRO Version](https://bulk-operations.net/#pro)
--------                    | :-------------: |
Bulk Insert                 | Yes
Bulk Update                 | Yes
Bulk Delete                 | Yes
Bulk Merge                  | Yes
Bulk SaveChanges            | Yes
Bulk Synchornize            | Yes
DeleteFromQuery             | Yes
UpdateFromQuery             | Yes
Commercial License          | Yes
Royalty-Free                | Yes
Support & Upgrades (1 year) | Yes

Learn more about the **[PRO Version](https://bulk-operations.net/#pro)**

## Contribute

You want to help us? 
Your donation directly helps us maintaining and growing ZZZ Free Projects. We can’t thank you enough for your support.

### Why should I contribute to this free & open source library?
We all love free and open source libraries!
But there is a catch! Nothing is free in this world.
Contributions allow us to spend more of our time on: Bug Fix, Content Writing, Development and Support.

We NEED your help. Last year alone, we spent over **3000 hours** maintaining all our open source libraries.

### How much should I contribute?
Any amount is much appreciated. All our libraries together have more than 100 million downloads, if everyone could contribute a tiny amount, it would help us to make the .NET community a better place to code!

Another great free way to contribute is  **spreading the word** about the library!
 
A **HUGE THANKS** for your help.

## More Projects

- [EntityFramework Extensions](https://entityframework-extensions.net/)
- [Dapper Plus](https://dapper-plus.net/)
- [C# Eval Expression](https://eval-expression.net/)
- and much more! 
To view all our free and paid librariries visit our [website](https://zzzprojects.com/).

**Need more info?** info@zzzprojects.com

Contact our outstanding customer support for any request. We usually answer within the next business day, hour, or minutes!
