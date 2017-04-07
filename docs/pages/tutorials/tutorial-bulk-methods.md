---
layout: default
title: Bulk Methods
permalink: tutorial-bulk-methods
---

{% include template-h1.html %}

## Introduction
The .NET Bulk Operations library allow you to perform all operations in your database.

| Name      | Description |
| :-------------- | :------------- |
| BulkInsert      | Execute an INSERT operation. |
| BulkUpdate      | Execute an UPDATE operation. |
| BulkDelete      | Execute a DELETE operation. |
| BulkMerge       | Execute a MERGE/UPSERT operation. UPDATE existing rows matching the key, and INSERT new rows. |
| BulkSaveChanges | Execute an INSERT/UPDATE/DELETE operation using the DataRowState of the DataTable. |
| BulkSynchronize | Execute a SYNCHRONIZE operation. UPDATE existing rows matching the key, INSERT new rows and DELETE records from the destination not existing in the source. |

### Example

{% highlight csharp %}
var dt = new DataTable();

// ...code...

// Easy to use
ctx.BulkInsert(dt);
ctx.BulkUpdate(dt);
ctx.BulkDelete(dt);
ctx.BulkMerge(dt);
ctx.BulkSaveChanges(dt);
ctx.BulkSynchronize(dt);

// Easy to customize
context.BulkMerge(customers, 
   bulk => bulk.ColumnPrimaryKeyExpression = customer => customer.Code; });
{% endhighlight %}

### Performance Benchmark

| Operations      | 1,000 Entities | 2,000 Entities | 5,000 Entities |
| :-------------- | -------------: | -------------: | -------------: |
| BulkInsert      | 6 ms           | 10 ms          | 15 ms          |
| BulkUpdate      | 50 ms          | 55 ms          | 65 ms          |
| BulkDelete      | 45 ms          | 50 ms          | 60 ms          |
| BulkMerge       | 65 ms          | 80 ms          | 110 ms         |
