---
title: "Hỗ trợ tích hợp frontend, kiểm thử end-to-end và hoàn thiện báo cáo"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.12. </b> "
---
### Mục tiêu tuần 12:

- Hỗ trợ frontend tích hợp với backend thật của CloudDoc dùng Express, PostgreSQL và S3 presigned URL.
- Kiểm thử xuyên suốt các luồng upload, lưu metadata, phê duyệt và download để giảm lỗi trước khi demo.
- Tổng hợp kết quả thực tập, hoàn thiện báo cáo FCAJ và rà soát lại phần đóng góp cá nhân theo vai trò backend.

### Các công việc triển khai trong tuần:
| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 1 | Làm việc với frontend để rà soát lại API `presign-upload`, `create document`, `status update` và `presign-download`. | 06/07/2026 | 06/07/2026 |  |
| 2 | Tích hợp thử frontend với backend, xử lý lỗi CORS, định dạng payload và trạng thái phản hồi của API. | 07/07/2026 | 07/07/2026 |  |
| 3 | Kiểm thử luồng upload trực tiếp lên S3, sau đó lưu metadata về PostgreSQL để xác nhận logic end-to-end. | 08/07/2026 | 08/07/2026 |  |
| 4 | Test các tình huống tải xuống, cập nhật trạng thái tài liệu, kiểm soát lỗi và các trường hợp dữ liệu không hợp lệ. | 09/07/2026 | 09/07/2026 |  |
| 5 | Tổng kết kết quả thực tập, cập nhật worklog và hoàn thiện báo cáo để phản ánh đúng vai trò backend trong CloudDoc. | 10/07/2026 | 10/07/2026 |  |

### Kết quả đạt được trong tuần 12:

- Frontend đã tích hợp tốt hơn với backend Express sử dụng PostgreSQL và S3 presigned URL.
- Tôi hiểu rõ hơn mối liên kết giữa API, dữ liệu tài liệu, storage trên S3 và các điểm cấu hình hạ tầng AWS.
- Báo cáo thực tập được hoàn thiện theo đúng định hướng dự án CloudDoc và phản ánh rõ vai trò backend của tôi trong nhóm.
