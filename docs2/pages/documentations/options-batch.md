# Batch

## Batch Options
- [BatchSize](#batchsize)
- [BatchTimeout](#batchtimeout)
- [BatchDelayInteval](#batchdelayinterval)

## BatchSize
Allow you to set the number of records to use in a batch.

By example, if you insert 1000 entities, and you set a batch size of 100, then ten inserts will be performed.

### Example
```csharp
var bulk = new BulkOperation(connection);

bulk.BatchSize = 100;

bulk.BulkMerge(dt);
```

## BatchTimeout
Allow you to set the maximum of time elapsing for a batch before the command throws a timeout exception.

### Example
```csharp
var bulk = new BulkOperation(connection);

bulk.BatchTimeout = 180;

bulk.BulkMerge(dt);
```

## BatchDelayInterval
Allow you to set a delay between every batch.

### Example
```csharp
var bulk = new BulkOperation(connection);

bulk.BatchDelayInterval = 100;

bulk.BulkMerge(dt);
```


> WARNING: Be careful, this options can often cause lock/deadlock within a transaction.
