# Log

## Log Options
- [Log](#log)
- [UseLogDump](#uselogdump)
- [LogDump](#logdump)

## Log
Allow you to log some event happening in your database.

### Example
```csharp
StringBuilder logger = new StringBuilder();
var bulk = new BulkOperation(connection);

bulk.Log += s => logger.AppendLine(s);

bulk.BulkMerge(dt);
```

## UseLogDump
Allow you to log in a string (LogDump) event happening in your database.

### Example
```csharp
var bulk = new BulkOperation(connection);

bulk.UseLogDump = true;

bulk.BulkMerge(dt);

var logDump = bulk.LogDump;
```

## LogDump
Allow you to retrieve event happening in your database when UseLogDump is enabled.

### Example
```csharp
var bulk = new BulkOperation(connection);

bulk.UseLogDump = true;

bulk.BulkMerge(dt);

var logDump = bulk.LogDump;
```
