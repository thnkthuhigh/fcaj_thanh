---
title: "AWS Vietnam Community Day tháng 5/2026: góc nhìn về AI, dữ liệu và kiến trúc hệ thống"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---
### Mục tiêu sự kiện

Tôi tham gia sự kiện này để củng cố hiểu biết về kiến trúc backend, cấu trúc dữ liệu và mặt vận hành của hệ thống cloud. Vì nhiệm vụ chính của tôi trong CloudDoc là backend và tích hợp AWS, tôi muốn học cách các hệ thống thực tế cân bằng giữa ý tưởng AI, chất lượng metadata, khả năng mở rộng và kiểm soát chi phí.

### Diễn giả

Các diễn giả là những người làm trong cộng đồng AWS và có kinh nghiệm triển khai thực tế. Điều tôi thích là họ không trình bày dịch vụ như những công cụ rời rạc, mà luôn giải thích kiến trúc như một chuỗi quyết định vận hành.

### Chi tiết nội dung

Một trong những nội dung hữu ích nhất với tôi là phần nói về chất lượng dữ liệu và context. Diễn giả nhấn mạnh rằng hệ thống thông minh sẽ nhanh chóng yếu đi nếu metadata nền không nhất quán hoặc được tổ chức lỏng lẻo. Điều này liên hệ rất trực tiếp tới CloudDoc, vì các trường backend như school, subject, uploader, status hay S3 key không chỉ là chi tiết lưu trữ; chúng quyết định việc tìm kiếm và workflow sau này có còn đáng tin cậy hay không.

Một chủ đề quan trọng khác là tách lớp hệ thống. Sự kiện cho thấy hệ thống ổn định luôn phụ thuộc vào ranh giới rõ ràng giữa lớp delivery, business logic, storage và observability. Tư duy này rất khớp với hướng thiết kế backend của CloudDoc, đặc biệt là quyết định không để API server trực tiếp gánh phần truyền file lớn mà chuyển sang presigned URL.

### Trải nghiệm và suy ngẫm về sự kiện

Sự kiện này giúp tôi bớt nhìn backend như nơi chỉ để viết endpoint. Tôi bắt đầu chú ý nghiêm túc hơn tới thiết kế metadata, nhu cầu logging, khả năng quan sát vận hành và cách các tính năng tương lai phụ thuộc vào kỷ luật dữ liệu ngay từ đầu. Nhờ đó, tôi có cái nhìn mang tính hệ thống hơn đối với CloudDoc.

### Phần kết luận

Với vai trò backend, đây là một sự kiện rất giá trị vì nó nối được kiến trúc, chất lượng dữ liệu và vận hành cloud vào cùng một tư duy. Nó làm cho cách tôi tiếp cận API và cấu trúc metadata của CloudDoc rõ ràng hơn.
