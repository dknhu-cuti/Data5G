# Data5G
# Source Directory

Thư mục này chứa toàn bộ mã nguồn chính (Source Code) của phần phân tích dữ liệu và mô hình dự báo cho dự án Datathon Vinuni 2026 (Round 1).

## Cấu trúc thư mục và Mô tả các tệp

* **`EDA.ipynb`**
  Notebook thực hiện **Exploratory Data Analysis (Phân tích Dữ liệu Khám phá)**. Quá trình EDA được cấu trúc chuyên sâu theo góc nhìn Khách hàng - Doanh nghiệp, tập trung trả lời các câu hỏi trọng tâm:
  - Phân tích xu hướng tăng trưởng về số lượng đơn hàng và doanh thu thực nhận (Net Revenue) qua thời gian.
  - Phân tích tệp khách hàng dựa trên nhân khẩu học (độ tuổi, giới tính) và mức độ đóng góp.
  - Khám phá tính thời vụ (từng tháng/quý) và đánh giá sự đồng pha giữa doanh thu và lợi nhuận.
  - Đánh giá rủi ro hoạt động dựa vào hình thức thanh toán (tỷ lệ hoàn hàng, tỷ lệ hủy đơn).
  - Phân tích hiệu quả các kênh marketing đối với các nhóm khách hàng có giá trị đơn hàng cao (AOV).
  - Phân khúc khách hàng bằng mô hình RFM (Recency, Frequency, Monetary) để xác định nhóm tiềm năng và nhóm có nguy cơ rời bỏ.

* **`Model.ipynb`**
  Notebook xây dựng **Machine Learning Pipeline (Mô hình Học Máy dự báo)**. Quá trình bao gồm:
  - Tích hợp và gom cụm toàn diện các tệp dữ liệu gốc (Sales, Orders, Order Items, Payments, Web Traffic, Promotions, Reviews, Returns, v.v.).
  - **Feature Engineering**: Tạo lập các Date Features, Lag Features (lag ngắn hạn và dài hạn như lag_1, lag_7, lag_365,...), cùng các Rolling Features (thống kê trung bình, độ lệch chuẩn, v.v.).
  - Sử dụng **LightGBM Regressor** làm mô hình cốt lõi kết hợp thuật toán gán trọng số (ưu tiên dữ liệu các năm gần nhất) nhằm dự báo nhiều bước (multi-step forecast) cho chuỗi thời gian 548 ngày (01/01/2023 - 01/07/2024).

* **`submission.csv`**
  Tệp tin chứa kết quả dự báo cuối cùng được kết xuất từ `Model.ipynb`. Tệp xuất ra gồm các trường thông tin: `Date` (Ngày), `Revenue` (Doanh thu dự báo), và ước tính `COGS` (Giá vốn hàng bán).

## Hướng dẫn thực thi (Execution)

1. Đảm bảo toàn bộ các file dữ liệu dạng `.csv` được đặt ở cấp thư mục gốc của repository (`g:\Cuộc thi\Datathon_Vinuni - 2026\datathon-2026-round-1`).
2. Mở file `EDA.ipynb` trên Jupyter Notebook hoặc VS Code để xem chi tiết các phân tích và các biểu đồ đồ thị đã được định dạng.
3. Chạy toàn bộ các cell trong `Model.ipynb` để tự động quá trình tiền xử lý, khởi tạo đặc trưng, huấn luyện mô hình LightGBM và xuất kết quả ra tệp `submission.csv`. Lưu ý: Notebook này cần đọc dữ liệu, do đó khi thực thi cần cấu hình môi trường nằm tại thư mục cha chứa các file dữ liệu.
