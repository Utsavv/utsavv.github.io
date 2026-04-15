---
layout: post
title: "New mssql-python Driver Claiming Faster BCP? A Fact Check"
date: 2026-04-14
excerpt: "A reproducible 1,000,000-row benchmark comparing native bcp vs mssql-python bulkcopy under the same settings."
---

My project relies heavily on bulk loads, often close to a million rows at a time. So when the new `mssql-python` driver introduced a native `bulkcopy()` API, I wanted to test the claim of near-native performance against classic `bcp`.

I ran a controlled benchmark with one goal: compare throughput and resource usage under identical conditions.

## Test Scenario

The benchmark loads 1,000,000 rows from CSV into this table:

```sql
CREATE TABLE dbo.BenchmarkData
(
    Id INT NOT NULL PRIMARY KEY,
    Name VARCHAR(100) NOT NULL,
    Amount DECIMAL(10,2) NOT NULL,
    CreatedAt DATETIME NOT NULL
);
```

Methods compared:

1. Native `bcp` utility
2. `mssql-python` using `cursor.bulkcopy()`

Controls applied to both:

- Same CSV input file
- `TABLOCK`
- Batch size of `50,000`
- Same machine and SQL Server instance
- Each test run three times; median reported

## TL;DR Results

| Rows | Driver | Time (s) | Rows/sec | CPU % | Peak Mem (MB) |
| --- | --- | ---: | ---: | ---: | ---: |
| 1,000,000 | `mssql-python` | 16.01 | 62,460 | 92.0 | 418.9 |
| 1,000,000 | `bcp` | 10.38 | 96,342 | 1.2 | 132.3 |

Winner: `bcp` (about 35% faster).

Quick arithmetic check:

- `1,000,000 / 16.01 ~= 62,460 rows/sec`
- `1,000,000 / 10.38 ~= 96,342 rows/sec`

## What The Numbers Mean

### 1) Throughput

`bcp` processed around `1.54x` more rows per second (`96,342 / 62,460`).

### 2) CPU Usage

`mssql-python` drove CPU much harder because the process still does Python-side work:

- Row materialization in memory
- Python object handling and marshaling
- Type conversion
- Interpreter participation in batching

`bcp` remains lean because it is native and optimized for direct bulk streaming.

### 3) Memory Usage

The difference is material for parallel loads:

- `mssql-python`: ~419 MB peak
- `bcp`: ~132 MB peak

For multiple concurrent import jobs, this gap can become a practical capacity constraint.

## Why bcp Still Wins

This is mostly architectural:

- `bcp`: compiled native path, minimal abstraction, mature bulk protocol optimizations
- `mssql-python bulkcopy`: significantly better than row-by-row inserts, but still includes Python runtime overhead

So yes, `mssql-python` is a strong improvement for Python-native bulk loading, but `bcp` is still the throughput and efficiency leader.

## Reproducible Benchmark Setup

To reproduce:

```bash
pip install mssql-python psutil
```

Also ensure `bcp` is installed and available in `PATH`.

Core benchmark flow:

1. Generate deterministic 1,000,000-row CSV
2. Create/reset benchmark database table
3. Load with `bcp` (`-b 50000`, `-h TABLOCK`) and capture elapsed time + process metrics
4. Load with `mssql-python` `bulkcopy(..., batch_size=50000, table_lock=True)` and capture same metrics
5. Repeat runs and compare median

## When To Use Which

Use `bcp` when:

- Raw throughput is the top requirement
- Low CPU and memory footprint matter
- You can use external CLI tooling in your pipeline

Use `mssql-python` when:

- You want an all-Python workflow
- Operational simplicity and integration matter more than max speed
- Bulk loads are moderate and performance headroom is acceptable

## Final Verdict

The new `mssql-python` `bulkcopy()` API is good and production-usable.  
But in this benchmark, `bcp` still won on speed and resource efficiency.

If absolute performance is your top priority, choose `bcp`.  
If Python-native maintainability is more important, `mssql-python` is a practical tradeoff.
