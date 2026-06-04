---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

## Xây dựng hệ thống CloudDoc trên AWS

#### Tổng quan
CloudDoc là nền tảng lưu trữ và chia sẻ tài liệu học tập dành cho sinh viên, được thiết kế theo hướng tách biệt lưu trữ và xử lý. Hệ thống tiếp nhận yêu cầu nghiệp vụ qua application server, lưu trữ file vật lý trên Amazon S3, quản lý metadata qua cơ sở dữ liệu quan hệ, và áp dụng quy trình kiểm duyệt nội dung. Mục 5 của báo cáo này được biên soạn dưới dạng bài thực hành (workshop) end-to-end, nhằm mô phỏng trọn vẹn vòng đời tài liệu trên nền tảng AWS thay vì liệt kê các dịch vụ một cách rời rạc.

Điểm trọng tâm của workshop là việc phác thảo một luồng nghiệp vụ kỹ thuật hoàn chỉnh: từ khâu chuẩn bị môi trường, khởi tạo yêu cầu tải lên, xác minh lưu trữ, kiểm thử quy trình kiểm duyệt, cho đến việc đồng bộ hiển thị và thu hồi tài nguyên. Phương pháp trình bày này nhằm minh hoạ sự gắn kết giữa thiết kế kiến trúc lý thuyết và quá trình triển khai, kiểm thử, vận hành thực tiễn.

#### Mục tiêu
Sau khi hoàn thành nội dung phần này, người đọc có thể:
- Nắm rõ vai trò của các dịch vụ AWS trong việc cấu thành nên kiến trúc CloudDoc.
- Theo dõi và đánh giá luồng xử lý tài liệu (upload & moderation) từ đầu đến cuối.
- Đối chiếu giao diện thiết lập trên AWS Console với từng giai đoạn triển khai cụ thể.
- Phân tích các đoạn mã (code snippet) tích hợp giữa giao diện người dùng và máy chủ ứng dụng.
- Nhận thức được tầm quan trọng của việc giám sát hệ thống (monitoring) và tối ưu chi phí (resource clean-up).

#### Kết quả mong đợi
Mô hình hệ thống triển khai thành công sẽ cho phép người dùng khởi tạo yêu cầu tải lên, quản trị viên phê duyệt qua giao diện nội bộ và tài liệu tự động xuất hiện trên danh mục tìm kiếm công khai. Đồng thời, hệ thống vận hành trơn tru dưới sự giám sát liên tục của Amazon CloudWatch thông qua các chỉ số (metrics) và cảnh báo (alarms) thời gian thực.

#### Cấu trúc workshop

1. [Giới thiệu](5.1-workshop-overview/)
2. [Điều kiện tiên quyết](5.2-prerequiste/)
3. [Triển khai luồng upload và lưu trữ tài liệu](5.3-s3-vpc/)
4. [Kiểm thử hệ thống end-to-end](5.4-s3-onprem/)
5. [Tích hợp ứng dụng khách và quan sát hệ thống](5.5-policy/)
6. [Cập nhật dữ liệu](5.6-cleanup/)
7. [Dọn dẹp tài nguyên](5.7-clean-resources/)

