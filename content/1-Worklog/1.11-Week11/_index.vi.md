---
title: "Tăng cường bảo mật, logging và khả năng vận hành backend"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.11. </b> "
---
### Mục tiêu tuần 11:

- Tăng độ ổn định và an toàn cho backend CloudDoc trước khi tích hợp hoàn chỉnh với frontend.
- Hoàn thiện cấu hình kết nối PostgreSQL, logging, validation và xử lý lỗi.
- Bổ sung tư duy vận hành hệ thống thông qua health check, giám sát và các nguyên tắc bảo mật backend.

### Các công việc triển khai trong tuần:
| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 1 | Hoàn thiện cấu hình `config`, `db`, `app` và kiểm tra lại luồng khởi động/tắt backend an toàn. | 29/06/2026 | 29/06/2026 |  |
| 2 | Rà soát middleware `cors`, `helmet`, `morgan`, validation schema và cơ chế xử lý lỗi của API. | 30/06/2026 | 30/06/2026 |  |
| 3 | Kiểm tra lại kết nối PostgreSQL, thời gian chờ, pool config và độ ổn định của các câu truy vấn. | 01/07/2026 | 01/07/2026 |  |
| 4 | Nghiên cứu thêm cách áp dụng IAM Role, CloudWatch, SNS và các điểm giám sát cần thiết cho môi trường AWS thật. | 02/07/2026 | 02/07/2026 |  |
| 5 | Demo nội bộ backend với nhóm, ghi nhận lỗi tích hợp và chỉnh sửa những vấn đề ảnh hưởng đến luồng nghiệp vụ. | 03/07/2026 | 03/07/2026 |  |

### Kết quả đạt được trong tuần 11:

- Backend trở nên ổn định và có tổ chức hơn nhờ hoàn thiện cấu hình, validation, logging và error handling.
- Làm rõ các điểm cần chú ý về bảo mật và khả năng vận hành khi đưa backend lên môi trường AWS thật.
- Giảm bớt lỗi tích hợp nhờ quá trình demo nội bộ và rà soát lại toàn bộ luồng nghiệp vụ chính.
