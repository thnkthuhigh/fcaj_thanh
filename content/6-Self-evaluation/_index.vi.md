---
title: "Tự đánh giá"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 6. </b> "
---

Trong suốt thời gian thực tập tại **Amazon Web Services Viet Nam Company Limited** từ **17/04/2026** đến **10/07/2026**, tôi tham gia dự án **CloudDoc** với định hướng chính là **backend**. Quá trình này giúp tôi đi từ mức làm quen với API và AWS sang mức hiểu rõ hơn cách một backend cần được tổ chức để phục vụ một sản phẩm có dữ liệu, có luồng nghiệp vụ và có yêu cầu vận hành thực tế.

### Tôi nhìn lại vai trò của mình như thế nào?

Nếu tóm gọn phần việc đã làm, tôi xem vai trò của mình là xây phần lõi đứng phía sau giao diện: tổ chức dữ liệu tài liệu, xây các endpoint cần thiết, kết nối PostgreSQL, làm việc với S3 theo luồng presigned URL và hỗ trợ để frontend có thể tích hợp ổn định. Điều tôi học được lớn nhất không chỉ là viết thêm được API, mà là hiểu backend phải giữ tính nhất quán cho hệ thống như thế nào.

So với thời điểm đầu, tôi tiến bộ rõ ở chỗ không còn nhìn từng chức năng một cách rời rạc. Thay vào đó, tôi bắt đầu suy nghĩ theo luồng hoàn chỉnh: request đi vào đâu, dữ liệu nào cần kiểm tra, dữ liệu nào lưu vào database, phần nào nên giao cho S3, và khi lỗi xảy ra thì nên quan sát ở đâu để tìm nguyên nhân.

### Tự đánh giá theo tiêu chí

| STT | Tiêu chí | Tốt | Khá | Trung bình |
| --- | --- | --- | --- | --- |
| 1 | Kiến thức và kỹ năng chuyên môn | x |  |  |
| 2 | Khả năng học hỏi | x |  |  |
| 3 | Chủ động | x |  |  |
| 4 | Tinh thần trách nhiệm | x |  |  |
| 5 | Kỷ luật |  | x |  |
| 6 | Tính cầu tiến | x |  |  |
| 7 | Giao tiếp |  | x |  |
| 8 | Hợp tác nhóm | x |  |  |
| 9 | Ứng xử chuyên nghiệp | x |  |  |
| 10 | Tư duy giải quyết vấn đề | x |  |  |
| 11 | Đóng góp vào dự án/tổ chức |  | x |  |
| 12 | Tổng thể | x |  |  |

### Ba điểm tôi làm tốt trong kỳ thực tập

Điểm đầu tiên là tôi bám khá sát vào lõi nghiệp vụ backend của CloudDoc thay vì làm lan man nhiều phần không cần thiết. Tôi ưu tiên những việc có tác động trực tiếp đến hệ thống như mô hình metadata, API tài liệu, luồng upload và kết nối dữ liệu, nhờ vậy phần việc của mình có giá trị rõ hơn đối với sản phẩm.

Điểm thứ hai là khả năng tự học và nối kiến thức. Khi gặp nội dung mới như presigned URL, lifecycle dữ liệu hay tổ chức API theo module, tôi có thể đọc tài liệu, đối chiếu với codebase và thử áp dụng vào phần việc thực tế thay vì chỉ dừng ở mức hiểu lý thuyết.

Điểm thứ ba là tinh thần phối hợp. Backend không thể chạy riêng lẻ nên tôi luôn phải làm việc cùng frontend để thống nhất input, output và trạng thái nghiệp vụ. Quá trình đó giúp tôi hiểu rõ hơn trách nhiệm của backend trong một sản phẩm chung, không chỉ trong một đoạn mã riêng lẻ.

### Những phần tôi còn cần cải thiện thêm

Tôi vẫn cần đầu tư thêm vào tư duy vận hành ở mức gần production hơn. Hiện tại tôi đã hiểu vì sao cần logging, monitoring, alerting và kiểm soát chi phí, nhưng để tự tin triển khai trọn vẹn các phần đó trong môi trường thật thì tôi còn cần thêm trải nghiệm.

Một điểm khác là kỹ năng diễn đạt giải pháp kỹ thuật theo cách gọn và sáng hơn. Có lúc tôi nắm được luồng xử lý nhưng mất thêm thời gian để trình bày cho người khác hiểu ngay. Với công việc backend làm theo nhóm, đây là kỹ năng rất quan trọng mà tôi muốn cải thiện.

Cuối cùng, tôi muốn mở rộng thêm kinh nghiệm kiểm thử ở nhiều tình huống hơn, đặc biệt là các case lỗi, dữ liệu biên và những tình huống liên quan đến đồng bộ giữa database, storage và API.

### Reflection cá nhân

**Khó khăn**

Khó khăn lớn nhất của tôi là chuyển từ tư duy làm từng endpoint riêng lẻ sang tư duy thiết kế luồng backend hoàn chỉnh. Khi làm CloudDoc, tôi không chỉ cần “trả dữ liệu cho frontend” mà còn phải hiểu vì sao metadata phải chặt, vì sao upload nên tách sang S3, và vì sao quyền truy cập AWS cần được kiểm soát đúng cách.

**Cách giải quyết**

Tôi xử lý bằng cách luôn quay về flow nghiệp vụ trước. Thay vì lao ngay vào code, tôi tách bài toán thành các câu hỏi nhỏ: người dùng gửi gì lên, backend cần kiểm tra gì, database giữ gì, S3 giữ gì, và phản hồi trả ra cho frontend ra sao. Cách làm này giúp tôi giảm rối và bám sát mục tiêu hơn.

**Hướng phát triển**

Sau kỳ thực tập, tôi muốn tiếp tục đi sâu theo hướng backend thực chiến: viết API chắc hơn, tổ chức dữ liệu tốt hơn, kiểm thử kỹ hơn và hiểu sâu hơn cách backend vận hành trên AWS với log, metric, cảnh báo và tối ưu chi phí.

### Kết luận tự đánh giá

Nếu tự đánh giá một cách thẳng thắn, tôi cho rằng mình đã hoàn thành khá tốt phần việc được giao và có bước tiến rõ ràng về tư duy hệ thống. Điều tôi hài lòng nhất là tôi không còn xem backend chỉ là nơi xử lý request, mà bắt đầu nhìn nó như phần giữ dữ liệu, giữ nghiệp vụ và giữ sự ổn định cho sản phẩm khi nhiều thành phần cùng làm việc với nhau.
