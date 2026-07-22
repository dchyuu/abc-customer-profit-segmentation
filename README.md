# ABC Customer Profit Segmentation

> Mini project CRM thực hành ABC Analysis để ưu tiên khách hàng theo lợi nhuận.

[**Mở notebook**](./abc_customer_profit_segmentation.ipynb)

## Project overview

Bộ phận Marketing và Chăm sóc khách hàng có 500 suất quà tri ân nhưng số khách hàng giá trị cao lớn hơn ngân sách cho phép. Project sử dụng ABC segmentation để xác định tập khách hàng tạo ra phần lớn lợi nhuận, sau đó đề xuất tiêu chí lọc Top 500.

Project được xây dựng như một **mini project học tập**, tập trung chứng minh khả năng áp dụng kỹ thuật phân tích vào một business question cụ thể.

## Business questions

1. Nhóm khách hàng nào tạo ra khoảng 80% tổng lợi nhuận?
2. Nhóm A có vượt quá giới hạn 500 suất quà không?
3. Nhóm A có đặc điểm gì về thu nhập và nghề nghiệp?
4. Business nên chọn Top 500 khách hàng bằng tiêu chí nào?

## Dataset

| File | Vai trò / trường dữ liệu chính |
| --- | --- |
| EcomSales.csv | `RowID`, `OrderID`, `CustomerID`, `Profit` |
| Customer.csv | `CustomerID`, tên, `AnnualIncome`, `Occupation` |


Dữ liệu gốc không được đưa vào repository mặc định. Danh sách file và hướng dẫn chạy nằm tại [`data/README.md`](./data/README.md).

## Techniques practiced

- Tổng hợp lợi nhuận theo khách hàng
- Sắp xếp và tính cumulative profit share
- Phân nhóm ABC theo ngưỡng 80% và 95%
- Xử lý trường hợp lợi nhuận âm trong đường tích lũy
- Kiểm tra business constraint 500 suất quà
- Customer profiling theo thu nhập và nghề nghiệp

## Main KPIs

| KPI | Ý nghĩa |
| --- | --- |
| Total Profit | Tổng lợi nhuận ròng của từng khách hàng |
| Profit Share | Tỷ trọng lợi nhuận của khách hàng |
| Cumulative Profit Share | Tỷ trọng lợi nhuận tích lũy |
| Customer Count by ABC | Số khách hàng trong từng nhóm A/B/C |


## Analysis workflow

1. Kiểm tra chất lượng dữ liệu giao dịch và khách hàng.
2. Chuẩn hóa khóa `CustomerID` và merge hai bảng.
3. Tổng hợp `TotalProfit` theo khách hàng.
4. Tính tỷ trọng lợi nhuận tích lũy và gán nhóm A/B/C.
5. So sánh số khách hàng nhóm A với constraint 500.
6. Phân tích chân dung nhóm A và đề xuất cách chọn Top 500.

## Key findings

- Nhóm A là tập khách hàng tạo ra phần lớn lợi nhuận của doanh nghiệp.
- Số khách hàng nhóm A vượt đáng kể giới hạn **500 suất quà**, nên ABC chỉ là bước tạo candidate pool.
- Các giao dịch hoặc khách hàng có lợi nhuận âm không bị loại bỏ vì đây là tín hiệu kinh doanh cần điều tra.

## Recommendations

- Xếp hạng nhóm A theo `TotalProfit`, số đơn hàng và mức độ mua gần đây để chọn đúng Top 500.
- Dùng chân dung thu nhập và nghề nghiệp của nhóm A để xây dựng lookalike audience.
- Phân tích riêng khách hàng có lợi nhuận âm để tìm nguyên nhân từ discount, refund, shipping hoặc product mix.

## Limitations

- ABC segmentation phản ánh giá trị lịch sử, chưa phản ánh khả năng mua lại trong tương lai.
- Ngưỡng 80%/95% là quy ước và có thể cần điều chỉnh theo mục tiêu kinh doanh.
- Cần bổ sung Recency/Frequency hoặc customer lifetime value để chọn danh sách tri ân tối ưu hơn.

## Repository structure

```text
abc-customer-profit-segmentation/
├── README.md
├── abc_customer_profit_segmentation.ipynb
├── requirements.txt
├── .gitignore
└── data/
    └── README.md
```

## How to run

### Google Colab

1. Tải notebook từ repository hoặc mở notebook trên GitHub rồi chọn **Open in Colab** nếu nút này khả dụng.
2. Upload các file được liệt kê trong [`data/README.md`](./data/README.md) vào `/content/`.
3. Chọn **Runtime → Restart session and run all** để kiểm tra notebook chạy từ đầu đến cuối.

### Local Jupyter

```bash
pip install -r requirements.txt
jupyter notebook
```

Notebook hiện được thiết kế chủ yếu cho Google Colab và có thể dùng đường dẫn `/content/...`. Khi chạy local, cần đổi đường dẫn dữ liệu sang thư mục `data/`.

## Tools

- Python
- Jupyter Notebook / Google Colab
- pandas, numpy, matplotlib

## Suggested GitHub topics

`python` · `pandas` · `crm-analytics` · `abc-analysis` · `customer-segmentation`

## Author

**Your Name**  
Data Analyst Portfolio  
LinkedIn: `add-your-link`  
Email: `add-your-email`
