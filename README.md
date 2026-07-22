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


### Download data

Do kích thước dữ liệu lớn, các file dữ liệu đầy đủ không được lưu trực tiếp trong repository.

[**Mở thư mục dữ liệu dùng chung trên Google Drive**](https://drive.google.com/drive/folders/1NrvyT_tMArcoZvI_sEgPLclD4Vw0iCBq?usp=sharing)

Chỉ cần tải các file được liệt kê trong bảng phía trên; các file còn lại trong thư mục Drive được sử dụng cho những mini project khác. Giữ nguyên tên file để notebook đọc dữ liệu chính xác.

> Quyền chia sẻ đề xuất: **Anyone with the link → Viewer**. Hãy kiểm tra link bằng cửa sổ ẩn danh trước khi public repository.

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
└── .gitignore
```

## How to run

### Google Colab

1. Mở notebook từ repository bằng Google Colab.
2. Truy cập [thư mục dữ liệu trên Google Drive](https://drive.google.com/drive/folders/1NrvyT_tMArcoZvI_sEgPLclD4Vw0iCBq?usp=sharing).
3. Tải đúng các file được liệt kê trong phần **Dataset** và upload chúng vào thư mục `/content/` của Colab.
4. Giữ nguyên tên file, sau đó chọn **Runtime → Restart session and run all**.

### Local Jupyter

1. Tải đúng các file được liệt kê trong phần **Dataset** từ [Google Drive](https://drive.google.com/drive/folders/1NrvyT_tMArcoZvI_sEgPLclD4Vw0iCBq?usp=sharing).
2. Đặt các file cạnh notebook hoặc cập nhật đường dẫn đọc dữ liệu trong notebook cho phù hợp.
3. Cài thư viện và mở Jupyter:

```bash
pip install -r requirements.txt
jupyter notebook
```

Notebook hiện được thiết kế chủ yếu cho Google Colab và có thể sử dụng đường dẫn `/content/...`; khi chạy local, cần thay đường dẫn này bằng vị trí dữ liệu trên máy.

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
