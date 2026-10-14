# BÁO CÁO THỰC HÀNH KIỂM THỬ HIỆU NĂNG - REQRES API

- **Họ và tên:** Nguyễn Thị Nhung
- **Mã sinh viên:** 23010607

---

## 1. Mục tiêu bài tập
- Thực hành xây dựng kịch bản kiểm thử hiệu năng độc lập với API phân trang (Pagination API).
- Kiểm thử sức chịu tải của hệ thống ReqRes với 20 người dùng truy cập đồng thời.
- Phân tích các thông số phản hồi (Response Time, Throughput, Error Rate) và đóng gói báo cáo lên GitHub.

---

## 2. Kịch bản kiểm thử (Test Scenario)
- **Đối tượng kiểm thử:** API lấy danh sách người dùng theo trang (Page 2).
- **Target Server:** `reqres.in`
- **Protocol:** `https`
- **HTTP Method:** `GET`
- **Path:** `/api/users?page=2`
- **Cấu hình Thread Group:**
  - **Number of Threads (users):** 20 (20 người dùng truy cập cùng lúc)
  - **Ramp-up Period (seconds):** 5 (Khởi tạo 20 users trong 5 giây)
  - **Loop Count:** 1 (Mỗi user thực hiện 1 lần)

---

## 3. Các bước thực hiện & Hình ảnh minh họa

### 3.1. Cấu hình Thread Group
<img width="1920" height="1080" alt="thr2" src="https://github.com/user-attachments/assets/265122f7-f507-4b44-b213-38b9599616b3" />

*Hình 1: Cấu hình kịch bản kiểm thử tải với 20 users.*

---

### 3.2. Cấu hình HTTP Request
<img width="1920" height="1080" alt="http2" src="https://github.com/user-attachments/assets/329e4ff3-b267-4c49-9826-234ef77b45a5" />

*Hình 2: Cấu hình gọi API GET https://reqres.in/api/users?page=2.*

---

### 3.3. Kết quả chạy kịch bản (View Results Tree)
<img width="1920" height="1080" alt="tree2" src="https://github.com/user-attachments/assets/c91250b0-69b1-4530-9613-a64e17efb86b" />

*Hình 3: Kết quả thực thi thành công trả về mã HTTP 200 OK.*

---

### 3.4. Báo cáo tổng hợp (Summary Report)
<img width="1920" height="1080" alt="summary2" src="https://github.com/user-attachments/assets/dea11c1b-9aa4-4310-8d93-59f5dd8c7d7c" />

*Hình 4: Bảng tổng hợp các chỉ số hiệu năng cơ bản.*

---

### 3.5. Báo cáo nâng cao (Aggregate Report)
<img width="1920" height="1080" alt="aggregate2" src="https://github.com/user-attachments/assets/7b2803bd-e607-48a4-adf9-0a2bd14cf763" />

*Hình 5: Báo cáo phân tích chi tiết thời gian phản hồi theo các mốc phần trăm.*

---

## 4. Phân tích kết quả thực nghiệm

Dựa trên dữ liệu thu được sau khi chạy kịch bản:

| Chỉ số (Metric) | Giá trị ghi nhận | Đánh giá & Phân tích |
| :--- | :---: | :--- |
| **Total Samples** | **20** | Tất cả 20 request đã được gửi đi thành công |
| **Average Time** | **210 ms** | Thời gian phản hồi trung bình rất nhanh |
| **Min / Max Time** | **145 ms / 520 ms** | Biên độ thời gian phản hồi giữa request nhanh nhất và chậm nhất |
| **Error %** | **0.00%** | Hệ thống hoạt động 100% ổn định, không phát sinh lỗi |
| **Throughput** | **3.8 / sec** | Tốc độ xử lý trung bình đạt 3.8 request/giây |

---

## 5. Kết luận
- API `https://reqres.in/api/users?page=2` đáp ứng rất tốt với tải 20 người dùng đồng thời.
- Tỷ lệ lỗi đạt 0.00% và thời gian phản hồi trung bình duy trì ở mức thấp (210 ms).
