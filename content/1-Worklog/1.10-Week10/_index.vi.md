---
title: "Tích hợp upload S3 bằng presigned URL và hoàn thiện nghiệp vụ tài liệu"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.10. </b> "
---
### Mục tiêu tuần 10:

- Tích hợp luồng upload tài liệu trực tiếp lên Amazon S3 thông qua presigned URL.
- Hoàn thiện các nghiệp vụ backend liên quan đến metadata, trạng thái duyệt và tải xuống tài liệu.
- Chuẩn hóa cách frontend và backend phối hợp trong luồng upload/download thực tế.

### Các công việc triển khai trong tuần:
| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 1 | Xây dựng API `presign-upload` để backend sinh URL tạm thời cho frontend tải file trực tiếp lên Amazon S3. | 22/06/2026 | 22/06/2026 |  |
| 2 | Viết logic tạo `s3_key`, chuẩn hóa tên file và cấu hình thời gian hết hạn cho presigned URL. | 23/06/2026 | 23/06/2026 |  |
| 3 | Hoàn thiện API lưu metadata tài liệu sau khi file đã được tải thành công lên S3. | 24/06/2026 | 24/06/2026 |  |
| 4 | Bổ sung nghiệp vụ cập nhật trạng thái tài liệu (`pending`, `approved`, `rejected`) và tăng bộ đếm download. | 25/06/2026 | 25/06/2026 |  |
| 5 | Xây dựng API tạo presigned download URL và trao đổi với frontend để đồng bộ luồng upload/download. | 26/06/2026 | 26/06/2026 |  |

### Kết quả đạt được trong tuần 10:

- Hoàn thiện được luồng upload tài liệu trực tiếp lên S3 theo hướng giảm tải cho backend.
- Xây dựng đầy đủ hơn các nghiệp vụ lưu metadata, cập nhật trạng thái và tải xuống tài liệu.
- Frontend và backend đồng bộ tốt hơn về API contract và dữ liệu trao đổi thực tế.
