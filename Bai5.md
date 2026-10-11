# Bài làm: Thiết kế mô hình vận hành Agile cho toàn mảng RikkeiGo

## Phần 1: Kiến trúc mô hình

### 1. Phạm vi áp dụng cho các đội
Đội Đặt xe và Đội Thanh toán áp dụng mô hình Scrum với nhịp Sprint cố định 2 tuần do yêu cầu sản phẩm thay đổi liên tục theo thị trường. 

Đội Đối soát không áp dụng mô hình Scrum này mà vận hành theo mô hình phát triển tuần tự (Waterfall), vì nghiệp vụ xuất hóa đơn thuế đòi hỏi tính ổn định, độ chính xác tuyệt đối và tuân thủ chặt chẽ hành lang pháp lý thay vì thử nghiệm lặp ngắn hạn.

### 2. Các module quy trình trong mô hình

- **Module 1: Quản trị định hướng và Backlog (Product Backlog Management)**
  - *Chủ trì:* Product Owner.
  - *Nội dung:* Tiếp nhận nhu cầu người dùng, phân tích giá trị kinh doanh và sắp xếp thứ tự ưu tiên trên Product Backlog.

- **Module 2: Lập kế hoạch Sprint (Sprint Planning)**
  - *Tham gia:* Product Owner, Scrum Master, Developers.
  - *Nội dung:* Xác định mục tiêu Sprint (Sprint Goal), chọn các hạng mục ưu tiên từ Product Backlog và chuyển thành Sprint Backlog. Developers tự ước lượng và phân rã công việc kỹ thuật.

- **Module 3: Thực thi và Tự tổ chức (Sprint Execution & Daily Scrum)**
  - *Chủ trì:* Developers (Scrum Master hỗ trợ tháo gỡ rào cản).
  - *Nội dung:* Nhóm phát triển tự chủ lập trình, kiểm thử và đồng bộ tiến độ qua buổi Daily Scrum 15 phút mỗi sáng nhằm phát hiện sớm vướng mắc kỹ thuật.

- **Module 4: Thanh tra và Bàn giao giá trị (Sprint Review & Increment)**
  - *Tham gia:* Toàn bộ Scrum Team và các bên liên quan.
  - *Nội dung:* Trình diễn bản tăng trưởng sản phẩm hoàn thành (Done Increment) đáp ứng Định nghĩa hoàn thành (Definition of Done) để thu thập phản hồi thực tế từ người dùng thử nghiệm.

- **Module 5: Thích nghi và Cải tiến quy trình (Sprint Retrospective)**
  - *Tham gia:* Nội bộ Scrum Team (Scrum Master điều phối).
  - *Nội dung:* Đánh giá quy trình làm việc, sự phối hợp giữa các thành viên và công cụ trong Sprint vừa qua, thống nhất ít nhất một hành động cải tiến cụ thể cho Sprint kế tiếp.

### 3. Phác thảo luồng giá trị khép kín

```text
Nhu cầu người dùng & Phản hồi thị trường
    ↓
[Module 1] Quản trị Product Backlog (Product Owner định hướng giá trị)
    ↓
[Module 2] Sprint Planning (Chốt Sprint Goal & Sprint Backlog)
    ↓
[Module 3] Thực thi Sprint & Daily Scrum (Developers tự tổ chức triển khai)
    ↓ (đáp ứng trọn vẹn Definition of Done)
[Module 4] Sprint Review (Trình diễn bản tăng trưởng Increment cho người dùng thử)
    ↓
[Module 5] Sprint Retrospective (Rà soát cách làm việc và chốt hành động cải tiến)
    ↓
Cập nhật ngược lại Product Backlog & Áp dụng cải tiến vào Sprint tiếp theo
```

---

## Phần 2: Xử lý tình huống

### Tình huống 1: Đến buổi Sprint Review nhưng không có hạng mục nào đạt tiêu chuẩn "xong" (Definition of Done)
- **Nơi phát hiện:** Được phát hiện trong buổi Daily Scrum cuối Sprint hoặc ngay trước thời điểm diễn ra Sprint Review khi đối soát với tiêu chuẩn Definition of Done.
- **Người xử lý:** Product Owner và Scrum Master cùng nhóm Developers.
- **Cách xử lý:** 
  1. Đội không trình diễn các phần code dở dang hoặc chưa đạt tiêu chuẩn hoàn thành cho người dùng xem tại Sprint Review nhằm bảo vệ tính minh bạch. Đội công bố rõ ràng việc chưa hoàn thành Sprint Goal trong kỳ này.
  2. Toàn bộ các hạng mục chưa đạt được chuyển ngược về Product Backlog để Product Owner đánh giá lại mức độ ưu tiên cho các Sprint sau.
  3. Tại buổi Sprint Retrospective, Scrum Master dẫn dắt đội phân tích nguyên nhân gốc rễ (như việc nhận quá nhiều việc, tiêu chuẩn kiểm thử chưa rõ ràng hoặc phát sinh lỗi kỹ thuật) để đưa ra biện pháp khắc phục cụ thể cho Sprint kế tiếp.

### Tình huống 2: Đội Thanh toán muốn kéo dài riêng Sprint đang chạy thêm 1 tuần để "làm cho xong"
- **Nơi phát hiện:** Được phát hiện trong buổi Daily Scrum gần cuối Sprint khi đội nhận thấy nguy cơ chậm tiến độ và đưa ra đề xuất kéo dài thời gian.
- **Người xử lý:** Scrum Master của đội Thanh toán.
- **Cách xử lý:**
  1. Scrum Master kiên quyết từ chối đề xuất kéo dài thời gian để giữ vững nguyên tắc khung thời gian cố định (Timebox 2 tuần) và duy trì tính đồng bộ với nhịp làm việc chung của tổ chức.
  2. Đội kết thúc Sprint đúng hạn quy định; các phần việc chưa xong sẽ không được đóng và chuyển về lại Product Backlog.
  3. Trong buổi Sprint Retrospective, Scrum Master hỗ trợ đội nhìn nhận lại năng lực thực tế (Capacity) và kỹ năng ước lượng, từ đó cam kết khối lượng công việc vừa sức hơn tại buổi Sprint Planning của Sprint tiếp theo.
