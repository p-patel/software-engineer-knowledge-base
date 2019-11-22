# Query Performance

## Resources
- https://stackoverflow.com/questions/1251636/what-do-clustered-and-non-clustered-index-actually-mean
- https://medium.com/geopits/differences-between-sql-server-clustered-index-scan-and-index-seek-311756e4d82c
- https://www.red-gate.com/simple-talk/sql/performance/simple-query-tuning-with-statistics-io-and-execution-plans/
-- unread --
- https://www.sqlshack.com/how-to-collect-performance-and-system-information-in-sql-server/
- https://solutioncenter.apexsql.com/how-to-optimize-sql-server-query-performance-statistics-joins-and-index-tuning/
- https://www.mssqltips.com/sqlservertip/1255/getting-io-and-time-statistics-for-sql-server-queries/
- https://stackify.com/performance-tuning-in-sql-server-find-slow-queries/
- https://www.red-gate.com/simple-talk/sql/performance/sql-server-statistics-basics/

## Write Up

### Clustered and Non-Clustered Indexes
- Clustered vs. Non-Clustered Index
- Table with no clustered index stored as a heap
- Max. 1 clustered index per table (example syntax), no limit on number of non-clustered indexes per table (example syntax)
- Clustered index stores address of pages containing data, non-clustered index stores address of clustered index (or row address?)

### Index Scan vs Index Seek
