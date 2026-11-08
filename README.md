# udacity-data-engineering

Bài tập các khoá trong Udacity Data Engineering Nanodegree (DEND), đi từ data modeling đến data lake, data warehouse, pipeline tự động và capstone.

| # | Thư mục | Chủ đề | Công nghệ |
|---|---------|--------|-----------|
| 1 | [Data Modeling with Postgres](Data%20Modeling%20with%20Postgres/) | Star schema + ETL cho Sparkify | Python, PostgreSQL |
| 2 | [Data Modeling with Apache Cassandra](Data%20Modeling%20with%20Apache%20Cassandra/) | NoSQL, model bảng theo query | Python, Cassandra |
| 3 | [AWS Data Warehouse](AWS%20Data%20Warehouse/) | Staging + star schema trên Redshift | Python, S3, Redshift |
| 4 | [AWS Data Lake](AWS%20Data%20Lake/) | ETL bằng Spark, ghi Parquet lên S3 | PySpark, S3 |
| 5 | [Automate Data Pipelines](Automate%20Data%20Pipelines/) | Pipeline S3 → Redshift có data quality check | Airflow, Redshift |
| 6 | [Udacity DEND Capstone Project](Udacity%20DEND%20Capstone%20Project/) | Data lake về nhập cảnh Mỹ (I94) | PySpark, Parquet |

Bốn project đầu dùng chung dataset **Sparkify** (`song_data` + `log_data`, JSON). Capstone dùng dataset I94 immigration.

## Lưu ý
- Các file cấu hình (`dl.cfg`, `dwh.cfg`, `airflow.cfg`) cần điền credentials AWS/DB của bạn trước khi chạy. **Không commit credentials thật** — `AWS Data Lake/dl.cfg` hiện đang chứa AWS key trong git history; nên revoke key đó và rotate.
- `Udacity DEND Capstone Project.zip` là bản nén của thư mục capstone (trùng nội dung).
