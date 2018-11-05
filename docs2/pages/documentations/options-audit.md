# Audit

## UseAudit
Allow you to audit inserted/deleted rows from the database.

- Default Value: False

### Example
```csharp
var bulk = new BulkOperation(connection);

bulk.UseAudit = true;

bulk.BulkMerge(dt);

var auditEntries = bulk.AuditEntries;
```
