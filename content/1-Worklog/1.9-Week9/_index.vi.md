---
title: "Xây dựng API tài liệu cốt lõi và truy vấn dữ liệu PostgreSQL"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---
### Mục tiêu tuần 9:

- Xây dựng các API cốt lõi để quản lý tài liệu trong CloudDoc.
- Kết nối backend với PostgreSQL và chuẩn hóa cách truy vấn dữ liệu tài liệu.
- Làm rõ các thao tác list, get detail, create document và filter dữ liệu phục vụ frontend.

### Các công việc triển khai trong tuần:
| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 1 | Xây dựng module repository để truy vấn dữ liệu tài liệu từ PostgreSQL theo đúng mô hình đã thiết kế. | 15/06/2026 | 15/06/2026 |  |
| 2 | Viết API lấy danh sách tài liệu có hỗ trợ filter theo trường, ngành, môn học, trạng thái và từ khóa. | 16/06/2026 | 16/06/2026 |  |
| 3 | Viết API lấy chi tiết tài liệu theo `id` và chuẩn hóa cấu trúc response trả về cho frontend. | 17/06/2026 | 17/06/2026 |  |
| 4 | Xây dựng API tạo mới document và kiểm tra dữ liệu đầu vào bằng schema validation. | 18/06/2026 | 18/06/2026 |  |
| 5 | Test lại các API bằng Postman, rà soát câu lệnh SQL và xử lý những lỗi ban đầu trong truy vấn dữ liệu. | 19/06/2026 | 19/06/2026 |  |

### Kết quả đạt được trong tuần 9:

- Hoàn thiện được nhóm API backend cốt lõi phục vụ danh sách, chi tiết và tạo tài liệu.
- Kết nối được backend với PostgreSQL theo hướng có cấu trúc và dễ mở rộng.
- Làm rõ được format dữ liệu trả về để frontend có thể tích hợp thuận lợi ở các tuần tiếp theo.
