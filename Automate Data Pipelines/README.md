# Automate Data Pipelines

Pipeline Airflow chạy hằng giờ: stage JSON từ S3 vào Redshift, build star schema, rồi kiểm tra chất lượng dữ liệu.

## DAG (`dags/udac_example_dag.py`)
```
Begin_execution → create_tables
  → Stage_events ┐
  → Stage_songs  ┴→ Load_songplays_fact_table
      → Load_user / song / artist / time dim tables
          → Run_data_quality_checks → Stop_execution
```

## Cấu trúc
| Path | Mô tả |
|------|-------|
| `dags/udac_example_dag.py` | Định nghĩa DAG (`@hourly`, `catchup=False`, retries 3) |
| `create_tables.sql` | DDL cho staging và star schema trên Redshift |
| `plugins/operators/stage_redshift.py` | `StageToRedshiftOperator` — `COPY` từ S3 |
| `plugins/operators/load_fact.py` / `load_dimension.py` | Load fact / dimension (có tuỳ chọn truncate) |
| `plugins/operators/data_quality.py` | `DataQualityOperator` — chạy list query, so với kết quả mong đợi |
| `plugins/helpers/sql_queries.py` | Các câu `INSERT ... SELECT` |
| `iac_redshift.py` | Dựng Redshift cluster + IAM role bằng boto3 (đọc `plugins/airflow.cfg`) |

## Cách chạy
1. Chạy `iac_redshift.py` để tạo cluster (điền key/password trong `plugins/airflow.cfg`).
2. Trong Airflow UI tạo Connection `aws_credentials` (Amazon Web Services) và `redshift` (Postgres).
3. Bật DAG `udac_example_dag`.

