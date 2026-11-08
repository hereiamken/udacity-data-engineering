# AWS Data Warehouse

Sparkify chuyển data warehouse lên cloud. Project này load dữ liệu JSON từ S3 vào **staging tables** trên Amazon Redshift, rồi transform thành **star schema** phục vụ phân tích song play.

## Schema
- Staging: `staging_events` (log_data), `staging_songs` (song_data)
- Fact: `songplay`
- Dimension: `users`, `song`, `artist`, `time`

## Files
| File | Mô tả |
|------|-------|
| `sql_queries.py` | Toàn bộ câu SQL: drop/create table, `COPY` từ S3, insert vào star schema. Đọc config từ `dwh.cfg` |
| `create_tables.py` | Drop và tạo lại các bảng |
| `etl.py` | `COPY` vào staging, sau đó insert vào fact/dimension |
| `runner.ipynb` | Notebook chạy lần lượt 2 script trên |
| `dwh.cfg` | Config: cluster, IAM role ARN, đường dẫn S3 (điền giá trị của bạn, đừng commit) |

## Cách chạy
1. Tạo Redshift cluster + IAM role có quyền đọc S3, điền vào `dwh.cfg`.
2. `python create_tables.py`
3. `python etl.py`
