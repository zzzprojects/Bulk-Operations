---
layout: default
title: Bulk Methods
permalink: tutorial-bulk-methods
---

{% include template-h1.html %}

## Introduction
The .NET Bulk Operations library allow you to perform all operations in your database.

The following methods is available:
- BulkInsert
- BulkUpdate
- BulkDelete
- BulkMerge
- BulkSaveChanges
- BulkSynchronize

### Example
{% include template-example.html %} 
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

### Performance Comparisons

| Operations      | 1,000 Entities | 2,000 Entities | 5,000 Entities |
| :-------------- | -------------: | -------------: | -------------: |
| SaveChanges     | 1,000 ms       | 2,000 ms       | 5,000 ms       |
| BulkInsert      | 6 ms           | 10 ms          | 15 ms          |
| BulkUpdate      | 50 ms          | 55 ms          | 65 ms          |
| BulkDelete      | 45 ms          | 50 ms          | 60 ms          |
| BulkMerge       | 65 ms          | 80 ms          | 110 ms         |

SaveChanges makes one database round-trip for each entity to insert/update/delete. So if you want to save (add, modify or remove) 10,000 entities, 10,000 databases round trip will be required which are **INSANELY** slow.

Bulk Operations save entities in bulk to reduce the number of database round-trip required.

### Related Articles

- [How to Benchmark?](benchmark)
- [How to use Custom Column?](custom-column)
- [How to use Custom Key?](custom-key)
