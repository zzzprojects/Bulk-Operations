---
layout: default
title: Bulk Operations - Overview
permalink: overview
---

{% include template-h1.html %}

## What’s .NET Bulk Operations?

Like SqlBulkCopy, it's allow to perform very fast insertion in an SQL Server.

However, it also support all kind of operations:

- Bulk Insert
- Bulk Update
- Bulk Delete
- Bulk Merge
- Bulk Synchronize
- Bulk SaveChanges

And support many provider:

- SQL Server 2008+
- SQL Azure
- SQL Compact
- Oracle
- MySQL
- PostgreSQL
- SQLite

It’s easy to use, and easy to customize.

{% include template-example.html %} 

{% highlight csharp %}
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
{% endhighlight %}

### Is it that simple?

Yes,

That’s why people feel in love so easily with our library.

### Who use it?

Already **thousands** of companies of all sizes and kinds use it:

- From start-up company with one developer
- To fortune 100 companies with hundreds of developers

Are you still not using it? Give it one try and you will understand why they choose our library.

Under the hood, the following library also use it:

- [Entity Framework Extensions](http://entityframework-extensions.net/)
- [Dapper Plus](http://dapper-plus.net/)

## Bulk Methods

Bulk methods give you flexibility by allowing to customize options such as primary key, columns and more.

All methods your application could require is supported:

- BulkInsert
- BulkUpdate
- BulkDelete
- BulkMerge (UPSERT operation)
- BulkSynchronize

### Example

{% include template-example.html %} 
{% highlight csharp %}
var ctx = new EntitiesContext();

// Easy to use
ctx.BulkInsert(list);
ctx.BulkUpdate(list);
ctx.BulkDelete(list);
ctx.BulkMerge(list);

// Easy to customize
context.BulkMerge(customers, 
   bulk => bulk.ColumnPrimaryKeyExpression = customer => customer.Code; });
{% endhighlight %}

### Performance Comparisons

| Operations      | 1,000 Entities | 2,000 Entities | 5,000 Entities |
| :-------------- | -------------: | -------------: | -------------: |
| BulkInsert      | 6 ms           | 10 ms          | 15 ms          |
| BulkUpdate      | 50 ms          | 55 ms          | 65 ms          |
| BulkDelete      | 45 ms          | 50 ms          | 60 ms          |
| BulkMerge       | 65 ms          | 80 ms          | 110 ms         |

## FromQuery Operations

FromQuery method allows you to execute UPDATE or DELETE statements without loading entities in the context.

Everything is executed on the database side, so nothing is faster than these methods.

### Example

{% include template-example.html %} 
{% highlight csharp %}
// DELETE all customers that are inactive for more than two years
context.Customers
    .Where(x => x.LastLogin < DateTime.Now.AddYears(-2))
    .DeleteFromQuery();
 
// UPDATE all customers that are inactive for more than two years
context.Customers
    .Where(x => x.Actif && x.LastLogin < DateTime.Now.AddYears(-2))
    .UpdateFromQuery(x => new Customer {Actif = false});
{% endhighlight %}

### Performance Comparisons

| Operations      | 1,000 Entities | 2,000 Entities | 5,000 Entities |
| :-------------- | -------------: | -------------: | -------------: |
| SaveChanges     | 1,000 ms       | 2,000 ms       | 5,000 ms       |
| DeleteFromQuery | 1 ms           | 1 ms           | 1 ms           |
| UpdateFromQuery | 1 ms           | 1 ms           | 1 ms           |
