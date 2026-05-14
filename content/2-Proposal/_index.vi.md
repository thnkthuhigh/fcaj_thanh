---
title: "Bản đề xuất"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---
## CloudDoc Platform for HUTECH Students
## Định hướng backend cho hệ thống lưu trữ và tra cứu học liệu trên AWS

### 1. Tóm tắt điều hành
CloudDoc được hình thành từ một nhu cầu rất thực tế: sinh viên có quá nhiều tài liệu học tập nhưng lại thiếu một nơi tập trung đủ rõ ràng để lưu, tìm và kiểm soát chất lượng nội dung. Nếu tài liệu chỉ nằm rải rác trong Drive cá nhân, nhóm chat hoặc các thư mục chia sẻ tạm thời, người dùng sẽ mất nhiều thời gian tìm kiếm, còn phía hệ thống thì gần như không có nền dữ liệu đủ sạch để mở rộng về sau.

Với vai trò backend trong dự án, tôi không nhìn CloudDoc như một trang upload file đơn thuần. Bài toán quan trọng hơn là làm sao để backend xử lý được luồng tài liệu theo cách gọn, an toàn và có thể phát triển tiếp. File cần được lưu ở nơi phù hợp, metadata cần được kiểm soát chặt, còn API phải đủ rõ để frontend tích hợp ổn định mà không biến application server thành điểm nghẽn.

### 2. Tuyên bố vấn đề
Từ góc nhìn kỹ thuật, vấn đề lớn nhất không nằm ở chuyện "có upload được file hay không", mà nằm ở cách hệ thống quản lý vòng đời của tài liệu sau khi file được đưa lên. Khi một nền tảng học liệu bắt đầu có nhiều môn học, nhiều nhóm người dùng và nhiều tệp có nội dung gần giống nhau, nếu metadata không được chuẩn hóa ngay từ đầu thì việc tìm kiếm, lọc, kiểm duyệt và thống kê sẽ rất nhanh rơi vào tình trạng lộn xộn.

Ngoài ra, nếu backend nhận toàn bộ file rồi mới đẩy tiếp sang chỗ lưu trữ, server ứng dụng sẽ phải gánh thêm tải I/O không cần thiết. Mô hình đó có thể chạy được ở mức demo nhỏ, nhưng sẽ kém hiệu quả khi số lượng file tăng dần, đặc biệt với các tài liệu PDF, DOCX hoặc slide có dung lượng lớn hơn. Vì vậy, CloudDoc cần một kiến trúc mà backend tập trung vào nghiệp vụ và dữ liệu, còn file gốc được lưu đúng vai trò của object storage.

**Giải pháp đề xuất**

Ý tưởng cốt lõi là tách rõ bốn phần: giao diện người dùng, lớp API nghiệp vụ, kho metadata và vùng lưu trữ file. Cách tách này giúp mỗi thành phần làm đúng việc của nó:

- Frontend chịu trách nhiệm hiển thị luồng sử dụng, thu thập thông tin tài liệu và gọi API.
- Backend Node.js/Express xác thực input, sinh `s3_key`, cấp presigned URL, lưu metadata và trả kết quả cho giao diện.
- PostgreSQL giữ vai trò nguồn dữ liệu có cấu trúc cho các trường như tiêu đề, môn học, khoa, loại file, người tải lên, trạng thái duyệt và số lượt tải.
- Amazon S3 xử lý lưu trữ file gốc để backend không phải đóng vai trò trung gian truyền file.

Điểm quan trọng nhất của hướng làm này là backend không ôm toàn bộ quy trình upload theo kiểu truyền thống. Thay vào đó, backend điều phối và kiểm soát, còn thao tác upload thực tế được chuyển cho S3 thông qua presigned URL. Cách tiếp cận này phù hợp hơn với CloudDoc vì vừa giảm tải cho EC2, vừa giữ được tính nhất quán cho lớp dữ liệu.

### 3. Kiến trúc giải pháp
Sơ đồ dưới đây mô tả cấu trúc triển khai CloudDoc theo định hướng nhiều lớp, trong đó lớp phân phối nội dung, lớp xử lý ứng dụng, lớp dữ liệu và lớp giám sát được tách vai trò rõ ràng:

![CloudDoc AWS Architecture](/fcaj_thanh/images/2-Proposal/aws-drawio-cloudoc.png)

Trong kiến trúc này, CloudFront và S3 (static) phục vụ frontend; ALB tiếp nhận request từ bên ngoài; EC2 chạy backend Express; RDS PostgreSQL lưu metadata; S3 upload giữ file gốc; còn SQS, CloudWatch, SNS và Glacier đóng vai trò hỗ trợ cho xử lý nền, quan sát hệ thống, cảnh báo và tối ưu chi phí lưu trữ dài hạn.

Tôi chọn mô hình này vì nó phản ánh đúng cách một backend nên phục vụ sản phẩm tài liệu số: không dồn tất cả trách nhiệm vào một server, không trộn lẫn file với dữ liệu nghiệp vụ, và không bỏ qua các nhu cầu sẽ phát sinh sau này như moderation, monitoring hoặc background processing.

### 4. Triển khai kỹ thuật
Trong phạm vi thực tập, mục tiêu không phải triển khai đầy đủ một hệ thống production hoàn chỉnh, mà là hoàn thiện được phần lõi có thể chạy end-to-end và bám sát codebase CloudDoc hiện có. Vì vậy, các hạng mục ưu tiên gồm:

- Xây dựng và tổ chức các API backend cho health check, danh sách tài liệu, chi tiết tài liệu, tạo bản ghi tài liệu, cập nhật trạng thái và cấp presigned URL.
- Thiết kế bảng dữ liệu PostgreSQL phục vụ quản lý metadata theo hướng có thể truy vấn và mở rộng.
- Kết nối luồng upload trực tiếp lên S3 để application server không phải nhận file nhị phân.
- Chuẩn hóa đầu vào bằng validation, đồng thời giữ đường đi rõ ràng giữa frontend, backend và storage.

Một số dịch vụ như SQS, CloudWatch, SNS hay Glacier hiện được thể hiện trong báo cáo như phần định hướng kiến trúc hợp lý, chứ không overclaim rằng toàn bộ đều đã hoàn thiện ở mức production. Tôi chủ động trình bày như vậy để báo cáo bám sát phần nhóm thực sự làm được.

### 5. Lộ trình và mốc triển khai
**Giai đoạn 1: Hoàn thiện backend lõi**

- Ổn định các API tài liệu, health check và metadata flow.
- Hoàn thiện cấu trúc dữ liệu PostgreSQL và quy trình quản lý trạng thái tài liệu.
- Hỗ trợ frontend tích hợp các endpoint chính một cách nhất quán.

**Giai đoạn 2: Tích hợp cloud thực tế**

- Hoàn thiện upload trực tiếp lên S3 bằng presigned URL.
- Chuẩn hóa cấu hình môi trường và IAM Role cho backend.
- Kiểm thử end-to-end luồng upload, moderation và truy cập tài liệu.

**Giai đoạn 3: Mở rộng và vận hành**

- Bổ sung background processing cho các tác vụ nặng hoặc bất đồng bộ.
- Thêm logging, monitoring, alerting với CloudWatch và SNS.
- Tối ưu chi phí lưu trữ bằng lifecycle policy và phân tầng dữ liệu.

### 6. Ước tính ngân sách
Ảnh dưới đây là bản ước lượng chi phí tháng cho kiến trúc CloudDoc theo mô hình gần production, được tổng hợp từ AWS Pricing Calculator và xuất vào ngày **17/06/2026**:

![CloudDoc AWS Monthly Cost](/fcaj_thanh/images/2-Proposal/aws-monthly-cost-cloudoc.jpg)

| Hạng mục | Chi phí ước tính / tháng (USD) | Nhận xét |
| --- | ---: | --- |
| RDS PostgreSQL Multi-AZ | 85.50 | Thành phần tốn kém nhất vì ưu tiên sẵn sàng và an toàn dữ liệu |
| EC2 Server (t4g.micro x2) | 19.51 | Hai máy ứng dụng phục vụ backend trên hai AZ |
| Application Load Balancer | 18.98 | Bảo đảm điểm vào thống nhất và cân bằng tải |
| NAT Instance (t4g.nano) | 4.64 | Hỗ trợ outbound traffic cho private subnet |
| CloudWatch | 4.01 | Log, metric và alarm cơ bản cho vận hành |
| Khác (SNS, CloudFront) | 0.89 | Chi phí thấp nhưng cần thiết cho phân phối và cảnh báo |
| **Tổng cộng** | **133.53** | Mức tham chiếu cho kiến trúc định hướng |

Từ góc nhìn backend, đây không chỉ là câu chuyện "bao nhiêu tiền mỗi tháng", mà còn là cơ sở để đưa ra quyết định kỹ thuật đúng mức. Nếu đang ở giai đoạn dev hoặc demo, nhóm hoàn toàn có thể giảm cấu hình, tắt bớt tài nguyên, dùng single-AZ và áp dụng S3 Lifecycle để tránh phát sinh chi phí không cần thiết. Tư duy FinOps vì vậy cần xuất hiện ngay từ lúc thiết kế chứ không phải đợi đến khi hệ thống chạy lớn.

### 7. Đánh giá rủi ro
Có ba nhóm rủi ro tôi xem là đáng chú ý nhất. Thứ nhất là rủi ro lệch luồng tích hợp giữa frontend và backend, đặc biệt ở phần presigned upload. Chỉ cần contract dữ liệu không thống nhất, toàn bộ trải nghiệm upload sẽ dễ hỏng. Thứ hai là rủi ro metadata thiếu chuẩn, khiến tài liệu có thể lưu được nhưng không khai thác tốt được. Thứ ba là rủi ro về quyền truy cập AWS và chi phí vận hành nếu hệ thống được cấu hình quá rộng hoặc giám sát chưa đủ.

Để giảm các rủi ro đó, phần backend cần đi theo các nguyên tắc rõ ràng:

- Xác thực dữ liệu đầu vào trước khi tạo bản ghi tài liệu.
- Dùng IAM Role theo nguyên tắc đặc quyền tối thiểu, tránh hard-code access key trong mã nguồn hoặc `.env`.
- Giữ riêng file và metadata để thuận lợi cho tra cứu, moderation và thống kê.
- Bổ sung CloudWatch logging, metric và SNS alert ở các điểm quan trọng để khi có sự cố còn lần vết được.
- Ghi rõ đâu là phần đã triển khai, đâu là hướng mở rộng để tránh overclaim trong báo cáo kỹ thuật.

### 8. Kết quả kỳ vọng
Điều tôi muốn thể hiện qua bản đề xuất không chỉ là một sơ đồ AWS đẹp hay một danh sách dịch vụ đủ dài. Quan trọng hơn, CloudDoc cho thấy backend phải đóng vai trò "giữ trật tự" cho hệ thống: giữ cho dữ liệu có cấu trúc, cho luồng upload hợp lý, cho bảo mật không bị bỏ quên và cho việc mở rộng về sau không trở nên bế tắc.

Với dự án, hướng tiếp cận này giúp CloudDoc có nền tảng tốt hơn để phát triển tiếp các tính năng như kiểm duyệt sâu hơn, phân tích nội dung, xử lý nền hoặc tối ưu trải nghiệm tìm kiếm. Với cá nhân tôi, đây là bước chuyển rõ rệt từ tư duy viết API theo từng màn hình sang tư duy thiết kế backend như phần lõi của một sản phẩm có dữ liệu, có vận hành và có lộ trình dài hơn sau kỳ thực tập.
