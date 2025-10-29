#queries #ai #aisql #sql #jobbossapi #jobboss
get table info for AI Queries
```sql
SELECT 
    COLUMN_NAME, 
    DATA_TYPE,
    CHARACTER_MAXIMUM_LENGTH,
    IS_NULLABLE
FROM INFORMATION_SCHEMA.COLUMNS 
WHERE TABLE_NAME = 'job'
ORDER BY ORDINAL_POSITION
```

Distinct jobs shipped in the last 2 years
```sql
SELECT DISTINCT packlist_detail.Job
FROM packlist_header
INNER JOIN packlist_detail ON packlist_header.Packlist = packlist_detail.Packlist
WHERE packlist_header.Packlist_Date >= DATEADD(YEAR, -2, GETDATE())
ORDER BY packlist_detail.Job
```

Show shipments for given part number and given date to the current date
```sql
SELECT 
    job.job, 
    CAST(packlist_header.packlist_date AS date) AS packlist_date,
    packlist_detail.quantity,
    address.Address,
    address.name AS ship_to_name
FROM packlist_header
INNER JOIN packlist_detail ON packlist_header.packlist = packlist_detail.packlist
INNER JOIN job ON packlist_detail.job = job.job
INNER JOIN address ON packlist_header.ship_to = address.address
WHERE job.part_number = '40223785'
  AND packlist_header.packlist_date >= '1-1-2025'
  AND packlist_header.packlist_date < DATEADD(day, 1, CAST(GETDATE() AS date))
ORDER BY packlist_header.packlist_date DESC, job.job
```

Show part numbers shipped in the last 12 months and the last date that part was shipped
order by the most recent first
```sql
SELECT 
    job.part_number,
    MAX(CAST(packlist_header.packlist_date AS date)) AS last_shipped_date
FROM packlist_header
INNER JOIN packlist_detail ON packlist_header.packlist = packlist_detail.packlist
INNER JOIN job ON packlist_detail.job = job.job
WHERE packlist_header.packlist_date >= DATEADD(MONTH, -12, CAST(GETDATE() AS date))
GROUP BY job.part_number
ORDER BY last_shipped_date DESC
```

Show jobs by part number and the last time it was shipped #jobbsbypartnumberquery
```sql
SELECT
    job.job,
    job.customer,
    job.ship_to,
    job.part_number,
    job.rev,
    job.description,
    job.last_updated,
    (
        SELECT MAX(CAST(packlist_header.packlist_date AS date))
        FROM packlist_header
        INNER JOIN packlist_detail ON packlist_header.packlist = packlist_detail.packlist
        WHERE packlist_detail.job = job.job
    ) AS last_shipped,
    address.name AS ship_to_name
FROM job
LEFT JOIN address ON job.ship_to = address.address
WHERE job.part_number = '3133D7336'
ORDER BY last_shipped DESC
```