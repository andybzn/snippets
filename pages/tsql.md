# T-SQL

## get percentage of adhoc queries 

```sql
DECLARE @SQLServerVersion VARCHAR(2);
SET @SQLServerVersion = CONVERT(VARCHAR,(SELECT value_data FROM sys.dm_server_registry WHERE value_name = 'CurrentVersion'));
DECLARE @TotalCacheMB VARCHAR(14);
IF @SQLServerVersion <= 12
    SET @TotalCacheMB = 'Total_CacheMB';
ELSE 
    SET @TotalCacheMB = 'Total_Cache_MB';
DECLARE @AdHocPlanQuery NVARCHAR(MAX);
SET @AdHocPlanQuery = '
    SELECT
        AdHoc_Plan_MB, '+ @TotalCacheMB +',
        AdHoc_Plan_MB*100.0 / '+ @TotalCacheMB +' AS ''AdHoc %''
    FROM (
    SELECT SUM(CASE
    WHEN objtype = ''adhoc''
            THEN CONVERT(BIGINT,size_in_bytes)
    ELSE 0 END) / 1048576.0 AdHoc_Plan_MB,
            SUM(CONVERT(BIGINT,size_in_bytes)) / 1048576.0 '+ @TotalCacheMB +'
    FROM sys.dm_exec_cached_plans) T
';
EXEC sp_executesql @AdHocPlanQuery;
```
