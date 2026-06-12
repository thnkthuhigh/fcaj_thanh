---
title: "Khởi tạo backend CloudDoc và thiết kế mô hình dữ liệu"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---
### Mục tiêu tuần 8:

- Khởi tạo dự án backend cho CloudDoc bằng Node.js và Express.
- Thiết kế mô hình dữ liệu tài liệu và chuẩn bị kết nối PostgreSQL cho hệ thống.
- Kết hợp quá trình tự phát triển với việc học tập tại văn phòng để trao đổi định hướng kỹ thuật cùng mentor.

### Các công việc triển khai trong tuần:
| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 1 | Rà soát lại sơ đồ kiến trúc AWS của CloudDoc với trọng tâm là backend API, PostgreSQL, S3 và các điểm giám sát vận hành. | 08/06/2026 | 08/06/2026 |  |
| 2 | Trao đổi với mentor về cách tổ chức source code backend, chia module và chuẩn hóa cấu hình môi trường. | 09/06/2026 | 09/06/2026 |  |
| 3 | Khởi tạo project Node.js/Express, thiết lập cấu trúc thư mục `app`, `routes`, `repository`, `config`, `db`. | 10/06/2026 | 10/06/2026 |  |
| 4 | Thiết kế mô hình dữ liệu tài liệu: tiêu đề, trường, ngành, môn học, trạng thái duyệt, `s3_key`, số lượt tải và metadata liên quan. | 11/06/2026 | 11/06/2026 |  |
| 5 | Chuẩn bị cấu hình kết nối PostgreSQL và kiểm tra endpoint health để xác nhận backend sẵn sàng phát triển nghiệp vụ. | 12/06/2026 | 12/06/2026 |  |

### Kết quả đạt được trong tuần 8:

- Hoàn thiện được bộ khung backend CloudDoc với Node.js/Express để tiếp tục phát triển các nghiệp vụ chính.
- Xác định rõ mô hình dữ liệu tài liệu và những trường thông tin cần lưu ở PostgreSQL.
- Chuẩn bị xong nền tảng kỹ thuật để bước sang giai đoạn xây dựng API và xử lý dữ liệu.
