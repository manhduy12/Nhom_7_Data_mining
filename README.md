# Shopping Cart Analysis

Phân tích dữ liệu bán lẻ nhằm khám phá mối quan hệ giữa các sản phẩm thường được mua cùng nhau bằng kỹ thuật **Association Rule Mining (Apriori)**. Project triển khai **pipeline hoàn chỉnh** từ xử lý dữ liệu → phân tích → khai thác luật → trực quan hóa → sinh báo cáo, phù hợp với tư duy Data Mining và Data Engineering.

---

## Features

* Làm sạch dữ liệu bán lẻ (loại bỏ hóa đơn hủy, dữ liệu lỗi)
* Xây dựng **basket matrix** (transaction × product)
* Khai phá **Frequent Itemsets** bằng Apriori
* Sinh **Association Rules**
* Đánh giá luật bằng các chỉ số:

  * Support
  * Confidence
  * Lift
* Trực quan hóa dữ liệu:

  * Bar chart (Top rules)
  * Scatter plot (Support – Confidence – Lift)
  * Network graph (quan hệ sản phẩm)
  * Biểu đồ tương tác Plotly
* Tự động hóa pipeline notebook bằng **Papermill**

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

Đặt file dữ liệu gốc vào thư mục:

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

### Output sinh ra

```text
data/processed/cleaned_uk_data.csv
data/processed/basket_bool.parquet
data/processed/rules_apriori_filtered.csv
notebooks/runs/apriori_modelling_run.ipynb
```

Notebook trong thư mục `notebooks/runs/` chứa **toàn bộ kết quả, bảng luật và biểu đồ**.

---

## Changing Parameters

Các tham số Apriori có thể điều chỉnh trong `run_papermill.py`:

```python
MIN_SUPPORT = 0.01
MAX_LEN = 3
FILTER_MIN_CONF = 0.3
FILTER_MIN_LIFT = 1.2
```

Hoặc chỉnh trực tiếp trong cell **PARAMETERS** của từng notebook để thử nghiệm các cấu hình khác nhau.

---

## Visualization & Results

Notebook `apriori_modelling_run.ipynb` hiển thị các biểu đồ:

* Top luật theo **Lift**
* Top luật theo **Confidence**
* Scatter plot: Support – Confidence – Lift
* Network Graph thể hiện mối quan hệ giữa các sản phẩm
* Biểu đồ **Plotly tương tác**

Có thể export notebook sang HTML:

```bash
jupyter nbconvert notebooks/runs/apriori_modelling_run.ipynb --to html
```

---

## Ứng dụng thực tế

* Gợi ý sản phẩm (Product Recommendation)
* Chiến lược **Cross-selling**
* Tạo combo sản phẩm
* Phân tích hành vi mua hàng
* Sắp xếp, trưng bày sản phẩm trong siêu thị / website

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

## Author

Project được thực hiện bởi:
**Trang Lê**

---

## License

MIT License — sử dụng tự do cho mục đích học tập, nghiên cứu và ứng dụng nội bộ.
