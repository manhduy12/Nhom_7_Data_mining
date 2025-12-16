# Shopping Cart Analysis

Phân tích dữ liệu bán lẻ nhằm khám phá mối quan hệ giữa các sản phẩm thường được mua cùng nhau bằng kỹ thuật **Association Rule Mining (Apriori)**. Dự án triển khai **pipeline hoàn chỉnh** từ xử lý dữ liệu → phân tích → khai thác luật → trực quan hóa → sinh báo cáo, phù hợp với tư duy **Data Mining** và **Data Engineering**.

---

## Features

* Làm sạch dữ liệu bán lẻ (loại bỏ hóa đơn hủy, dữ liệu lỗi)
* Xây dựng **basket matrix** (transaction × product)
* Khai phá **Frequent Itemsets** bằng Apriori
* Sinh **Association Rules**
* Đánh giá luật bằng các chỉ số: **Support, Confidence, Lift**
* Trực quan hóa dữ liệu:

  * Bar chart (Top rules)
  * Scatter plot (Support – Confidence – Lift)
  * Network graph (quan hệ sản phẩm)
  * Biểu đồ tương tác Plotly
* Tự động hóa pipeline notebook bằng **Papermill** (one-command run)

---

## Project Structure

```text
shopping_cart_analysis/
├── data/
│   ├── raw/
│   │   └── online_retail.csv
│   └── processed/
│       ├── cleaned_uk_data.csv
│       ├── basket_bool.parquet
│       └── rules_apriori_filtered.csv
│
├── notebooks/
│   ├── preprocessing_and_eda.ipynb
│   ├── basket_preparation.ipynb
│   ├── apriori_modelling.ipynb
│   └── runs/
│       ├── preprocessing_and_eda_run.ipynb
│       ├── basket_preparation_run.ipynb
│       └── apriori_modelling_run.ipynb
│
├── src/
│   └── apriori_library.py
│
├── run_papermill.py
├── requirements.txt
└── README.md
```

---

## Installation

```bash
git clone <your_repo_url>
cd shopping_cart_analysis
pip install -r requirements.txt
```

### Data Preparation

Đặt file dữ liệu gốc vào:

```bash
data/raw/online_retail.csv
```

Các file dữ liệu trung gian và kết quả sẽ được sinh tự động tại:

```bash
data/processed/
```

---

## Run Pipeline (Recommended)

Chạy toàn bộ pipeline phân tích chỉ với **một lệnh**:

```bash
python run_papermill.py
```

### Outputs

```text
data/processed/cleaned_uk_data.csv
data/processed/basket_bool.parquet
data/processed/rules_apriori_filtered.csv
notebooks/runs/preprocessing_and_eda_run.ipynb
notebooks/runs/basket_preparation_run.ipynb
notebooks/runs/apriori_modelling_run.ipynb
```

Các notebook trong `notebooks/runs/` chứa **toàn bộ kết quả, bảng luật và biểu đồ** để tái lập thí nghiệm.

---

## Changing Parameters

Có thể điều chỉnh tham số Apriori trong `run_papermill.py`:

```python
MIN_SUPPORT = 0.01
MAX_LEN = 3
FILTER_MIN_CONF = 0.3
FILTER_MIN_LIFT = 1.2
```

Hoặc chỉnh trực tiếp trong cell **PARAMETERS** của từng notebook để thử nghiệm cấu hình khác nhau.

---

## Visualization & Results

Notebook `apriori_modelling_run.ipynb` hiển thị:

* Top luật theo **Lift**
* Top luật theo **Confidence**
* Scatter plot: Support – Confidence – Lift
* Network Graph (quan hệ sản phẩm)
* Biểu đồ **Plotly tương tác**

Xuất notebook sang HTML:

```bash
jupyter nbconvert notebooks/runs/apriori_modelling_run.ipynb --to html
```

---

## Reproducibility

Pipeline được thiết kế để **tái lập kết quả**: chỉ cần cùng dữ liệu đầu vào và tham số, kết quả thu được là nhất quán giữa các lần chạy.

---

## Git Workflow (Course Requirement)

* Mỗi tác vụ được thực hiện trên **branch riêng**.
* Sau khi hoàn tất, thay đổi được **merge vào `main`** (qua PR hoặc merge trực tiếp).
* Lịch sử commit giúp truy vết và đánh giá tiến độ theo yêu cầu học phần.

---

## Ứng dụng thực tế

* Gợi ý sản phẩm (Product Recommendation)
* Chiến lược **Cross-selling**
* Tạo combo sản phẩm
* Phân tích hành vi mua hàng
* Tối ưu trưng bày sản phẩm trong siêu thị/website

---

## Tech Stack

| Công nghệ        | Mục đích                      |
| ---------------- | ----------------------------- |
| Python           | Ngôn ngữ chính                |
| Pandas           | Xử lý dữ liệu giao dịch       |
| MLxtend          | Apriori / Association Rules   |
| Papermill        | Tự động hóa pipeline notebook |
| Matplotlib       | Biểu đồ tĩnh                  |
| Plotly           | Biểu đồ tương tác             |
| Jupyter Notebook | Môi trường phân tích          |

---

## Roadmap

* [ ] Thêm notebook **FP-Growth**
* [ ] Xây dựng **Streamlit Dashboard** để lọc và phân tích luật

---

## Authors

**Nhóm 7 – Data Mining**
(Repo nhóm: `manhduy12/Nhom_7_Data_mining`)

---

## License

MIT License — sử dụng cho mục đích học tập, nghiên cứu và ứng dụng nội bộ.
