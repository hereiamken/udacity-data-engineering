# Data Modeling with Apache Cassandra

Sparkify muốn trả lời 3 câu hỏi trên dữ liệu event của app. Với Cassandra, mỗi bảng được thiết kế theo từng query.

## Pipeline
1. **Part I** — gộp các file CSV trong `event_data/` thành một file duy nhất `event_datafile_new.csv` (chỉ giữ các cột cần thiết, bỏ dòng không có artist).
2. **Part II** — tạo keyspace, tạo bảng, insert dữ liệu từ `event_datafile_new.csv`, chạy query kiểm tra.

## 3 query
1. Artist, tên bài, độ dài bài nghe trong `sessionId = 338`, `itemInSession = 4`
2. Artist, bài (sắp theo `itemInSession`), tên user cho `userId = 10`, `sessionId = 182`
3. Tên user (first + last) đã nghe bài *'All Hands Against His Own'*

## Files
| File | Mô tả |
|------|-------|
| `Project_1B_ Project_Template.ipynb` | Notebook toàn bộ project |
| `event_data/` | Dữ liệu event gốc (CSV theo ngày) |
| `event_datafile_new.csv` | File đã denormalize, sinh ra từ Part I |
| `images/` | Ảnh minh hoạ `event_datafile_new.csv` |
| `graph.py` | Vẽ ER diagram (`sqlalchemy_schemadisplay`) — kết nối tới Postgres `sparkifydb`, thuộc project Postgres chứ không dùng cho Cassandra |

## Cách chạy
Cần Cassandra chạy ở `127.0.0.1`, rồi chạy lần lượt các cell trong notebook.
