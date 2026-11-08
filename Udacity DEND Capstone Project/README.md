# Capstone Project: US Immigration (I94) Data Lake

Xây data lake về điểm đến của người nhập cư vào Mỹ: gộp dữ liệu I94 immigration với demographics, airports và temperature, làm sạch bằng PySpark và ghi ra Parquet theo star schema.

## Nguồn dữ liệu
- I94 immigration (sample: `immigration_data_sample.csv`; bản đầy đủ ~40M dòng)
- `us-cities-demographics.csv`
- `airport-codes_csv.csv`
- World temperature data
- Lookup từ `I94_SAS_Labels_Descriptions.SAS` → `countries`, `ports`, `states`, `visas` (`*.txt` / `*.csv`)

## Data model
- Fact: `fact_immigration`
- Dimension: `dim_visa`, `dim_country`, `dim_state`, `dim_time`, `dim_airport`, `dim_port`, `dim_temperature`

Mô tả từng cột xem [Data_Dictionary.txt](Data_Dictionary.txt).

## Files
| File | Mô tả |
|------|-------|
| `Capstone Project Template.ipynb` | Notebook chính: scope, model, chạy ETL, write-up (5 bước) |
| `Explore and Assess the Data.ipynb` | EDA và các bước cleaning |
| `etl.py` | Hàm `create_dim_*` và `create_fact_immigration` |
| `tools.py` | Helper: bỏ cột thiếu dữ liệu >95%, drop duplicate, ghi Parquet, `quality_check` |
| `Data_Dictionary.txt` | Data dictionary |

## Cách chạy
Python 3.7 + PySpark; chạy `Capstone Project Template.ipynb` từ trên xuống. Cập nhật dữ liệu hằng tháng (theo chu kỳ cập nhật của I94).
