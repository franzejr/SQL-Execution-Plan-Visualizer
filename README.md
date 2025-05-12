# 🔍 SQL Execution Plan Visualizer

This tool helps developers and DBAs understand and analyze SQL execution plans visually. It supports PostgreSQL and MySQL-style EXPLAIN and EXPLAIN ANALYZE outputs, making it easier to spot performance bottlenecks in complex queries.

🚀 Try it on: [https://franzejr.github.io/SQL-Execution-Plan-Visualizer/](https://franzejr.github.io/SQL-Execution-Plan-Visualizer/)


<img width="977" alt="image" src="https://github.com/user-attachments/assets/a4c9dfc2-87f3-485c-b270-419e0bfe83b1" />


## Usage

📌 Example
Paste an execution plan like this:

```sql
-> Aggregate: count(0)  (cost=378641..378641 rows=1) (actual time=12059..12059 rows=1 loops=1)
    -> Table scan on hits  (cost=326954..332699 rows=459419) (actual time=12059..12059 rows=15 loops=1)
        -> Union materialize with deduplication  (cost=326954..326954 rows=459419) (actual time=12059..12059 rows=15 loops=1)
            -> Nested loop inner join  (cost=211571 rows=331229) (actual time=2305..11484 rows=14 loops=1)
                -> Filter: ((sp.acts_as = 0) ...)  (cost=95641 rows=331229) (actual time=2305..11482 rows=14 loops=1)
                -> Index lookup on oa ...  (cost=0.25 rows=1) (actual time=0.09..0.09 rows=1 loops=14)
```

And get this:


✅ Tree View

```sh
pgsql
Copy
Edit
Aggregate
└── Table scan on hits
    └── Union materialize with deduplication
        └── Nested loop inner join
            ├── Filter
            └── Index lookup on oa
```

✅ Table View

```sh
#	Operation	Cost	Actual Time
1	Aggregate: count(0)	378641..378641	12059..12059
2	Table scan on hits	326954..332699	12059..12059
3	Union materialize	326954..326954	12059..12059
4	Nested loop inner join	211571	2305..11484
5	Filter: ...	95641	2305..11482
6	Index lookup on oa	0.25	0.09..0.09
```

## 📚 Learn More

📘 [MySQL EXPLAIN ANALYZE Blog Post](https://dev.mysql.com/blog-archive/mysql-explain-analyze/)

📘 [PostgreSQL EXPLAIN Docs](https://www.postgresql.org/docs/current/using-explain.html)
