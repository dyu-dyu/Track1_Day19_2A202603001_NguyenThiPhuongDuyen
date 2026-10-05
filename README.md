# Case B – AI Notes | Day 18–19

## 1. Thông tin cá nhân & Đội ngũ

### Thông tin cá nhân

- **Họ và tên:** Nguyễn Thị Phương Duyên
- **Mã sinh viên:** 2A202603001
- **Tên nhóm:** Case B – AI Notes *(tên đang được sử dụng trong tài liệu dự án; nhóm chưa cung cấp một tên riêng khác)*

### Thành viên nhóm

| STT | Họ và tên | Mã sinh viên |
|---:|---|---|
| 1 | Nguyễn Thị Phương Duyên | 2A202603001 |
| 2 | Nguyễn Hà Khuê | 2A202602938 |
| 3 | Hà Thị Mỹ Linh | 2A202602619 |

### Case bài toán nghiên cứu

Nhóm nghiên cứu **Case B – AI Notes**: hỗ trợ học viên biến các dấu vết học tập rời rạc như ảnh chụp màn hình, highlight, ghi chú ngắn và câu hỏi chưa hiểu thành một bản ghi chú có cấu trúc, giữ được nguồn/ngữ cảnh và có thể dùng lại khi ôn tập.

---

## 2. Hypothesis Problem

### Năm thành tố của giả thuyết

| Thành tố | Nội dung |
|---|---|
| **Situation – Tình huống** | Sau khi học xong một bài và cần xem lại hoặc ôn lại nội dung đã học. |
| **User – Người dùng** | Học viên có thói quen lưu highlight, ảnh chụp, câu hỏi hoặc ghi chú ngắn trong quá trình học. |
| **Job – Nhiệm vụ** | Biến các nội dung đã lưu thành một bản ghi chú có cấu trúc, dễ hiểu và có thể sử dụng lại. |
| **Barrier – Rào cản** | Các ghi chú được tạo rời rạc theo từng thời điểm hoặc slide, thiếu kết nối và ngữ cảnh nên người học phải tự tổ chức lại thủ công. |
| **Consequence – Hậu quả** | Người học tốn thời gian tìm và gom nội dung; đôi khi không nhớ lý do đã lưu hoặc không sử dụng lại ghi chú. |

### Câu phát biểu giả thuyết vấn đề

> **Khi học xong một bài và cần xem lại nội dung đã học, những học viên có thói quen lưu các ghi chú ngắn, hình ảnh hoặc điểm chưa hiểu gặp khó khăn trong việc biến những mảnh ghi chú đó thành một bản note có thể sử dụng để ôn tập, bởi vì chúng được tạo rời rạc theo từng thời điểm và thiếu sự kết nối/ngữ cảnh, dẫn đến người học phải tốn thêm thời gian để tìm và tổ chức lại thủ công, thậm chí không nhớ lý do đã lưu hoặc bỏ không sử dụng lại.**

Giả thuyết được neo vào evidence Day 17: người học chụp và để ảnh rời rạc, lưu lại phần chưa hiểu để hỏi ChatGPT, hoặc phải chuyển note của từng slide sang file tổng hợp bằng thao tác thủ công.

---

## 3. Three Solution Options

Ba phương án giải cùng một nhiệm vụ nhưng phân chia khác nhau quyền chủ động giữa người dùng và AI.

| Phương án | Cơ chế hoạt động | Quyền kiểm soát của người dùng | Prototype |
|---|---|---|---|
| **Option A – User-led Tagging** | Hệ thống chỉ tập hợp và giữ liên kết nguồn; người dùng tự mở nguồn, giữ/bỏ từng mảnh, gắn tag có sẵn hoặc tạo tag riêng để tổ chức ghi chú. | Người dùng tạo cấu trúc và quyết định toàn bộ nội dung; hệ thống không tự diễn giải. | [Trải nghiệm Option A](./prototype-option-a.html) |
| **Option B – User + AI Co-create** | AI đặt 2–3 câu hỏi làm rõ có gắn nguồn; câu trả lời của người dùng được định dạng thành ghi chú để tiếp tục sửa, tag hoặc bỏ. | AI hỗ trợ đặt câu hỏi, nhưng người dùng tự tạo nội dung và quyết định bản cuối. | [Trải nghiệm Option B](./option-b.html) |
| **Option C – AI-led Draft** | AI tạo sẵn bản nháp có nguồn và mức chắc; người dùng mở nguồn, sửa, bỏ hoặc duyệt từng mục. Mục có mức chắc thấp cần được kiểm tra nguồn trước khi duyệt. | AI khởi tạo nội dung; người dùng giữ quyền kiểm chứng và xác nhận cuối. | [Trải nghiệm Option C](./Option-C.html) |

> **Tình trạng liên kết:** ba đường dẫn trên mở file HTML trong repository. Dự án chưa có URL public đã được xác nhận, vì vậy README không tự điền liên kết triển khai giả.

---

## 4. Đóng góp cụ thể của tôi trong sản phẩm nhóm

### Phần việc chịu trách nhiệm chính

Tôi chịu trách nhiệm chính xây dựng **Option A – User-led Tagging** theo hướng **User creates/initiates**. Tôi triển khai luồng ba màn hình từ bối cảnh chung, tương tác gắn tag đến kết quả; giữ liên kết về slide nguồn; cho phép người dùng chọn nhiều tag, tạo tag riêng, bỏ mảnh, đổi quyết định, quay lại và reset. Mục tiêu là kiểm tra liệu người học có sẵn sàng tự tổ chức ghi chú khi hệ thống cung cấp đủ ngữ cảnh hay không.

### Đóng góp vào bối cảnh chung

- Tham gia chuẩn hóa cùng một target user, tình huống “đã học xong và sắp thi”, nhiệm vụ tạo note từ sáu dấu vết đã lưu và flow ba màn hình cho A/B/C.
- Góp phần giữ ba option khác nhau về **cơ chế và mức tự trị**, không chỉ khác màu sắc hoặc bố cục.
- Rà soát source, edit/reject, recovery và reset để người dùng có thể lấy lại quyền kiểm soát khi quyết định sai.
- Đối chiếu log với nhận định, phân biệt dữ kiện quan sát được với diễn giải và không tự bổ sung feedback còn thiếu.

### Tham gia xây dựng Human–AI Decision Table

Tôi đóng góp các nguyên tắc sau vào bảng phân quyền:

| Quyết định | Vai trò của AI/hệ thống | Quyền phải thuộc về người dùng |
|---|---|---|
| Gom dấu vết | Tập hợp nội dung và giữ link nguồn | Chọn dấu vết nào có liên quan |
| Tạo cấu trúc/nháp | Gợi ý nhóm hoặc câu diễn đạt tùy option | Sửa, giữ hoặc bỏ từng mục |
| Nội dung không chắc | Hiện mức chắc và cảnh báo | Mở nguồn trước khi duyệt |
| Phân loại cá nhân | Có thể gợi ý tag | Tạo tag riêng, đổi hoặc xóa tag |
| Lưu kết quả | Chuẩn bị bản xem trước | Xác nhận lưu và có đường quay lại |

### Hỗ trợ đồng đội

Tôi chia sẻ cấu trúc flow, bộ nguyên tắc về source và recovery, đồng thời hỗ trợ rà sự khác biệt giữa A/B/C để Option B vẫn là co-create và Option C vẫn là AI-led draft. Tôi cũng tham gia tổng hợp feedback, chỉ ra các mismatch giữa shared spec và prototype, và giữ những phần chưa có dữ liệu ở trạng thái chưa kiểm chứng thay vì suy diễn thành kết luận chung của nhóm.

---

## 5. Dữ liệu kiểm thử & Bài học

### Phiên kiểm thử do tôi dẫn dắt

Tôi dẫn dắt phiên của **Đào Trọng Khang**, trong đó tester trải nghiệm cả A, B và C:

- **Option A:** tester xem nhiều slide và mở lại nguồn; có gắn rồi bỏ tag và quay lại các màn để chỉnh. Tester nhận xét thao tác dễ hiểu nhưng hơi thủ công, tag quá nổi bật nên cạnh tranh sự chú ý với nội dung note.
- **Option B:** tester mở các mảnh nguồn trước và trong phiên review, nhưng bỏ qua câu 2 và để câu 3 trống. Bản lưu có ba mục nhưng hai mục trống. Tester không thích chat/gõ và thấy cơ chế AI hỏi lại gây phiền.
- **Option C:** tester mở danh sách sáu mảnh gốc hai lần, sửa hai mục nháp và mở nguồn của một mục để đối chiếu. Tester chọn **C** vì dễ tương tác, thân thiện và nút rõ, nhưng phần note chưa nổi bật và panel AI chiếm nhiều diện tích.

Phiên này tạo tín hiệu nghiêng về C, nhưng chưa chứng minh ghi chú AI tạo ra chính xác, hữu ích khi ôn thật hoặc tốt hơn cho mọi người dùng.

### Bảng tổng hợp ba phiên có dữ liệu của nhóm

| Phiên | Phạm vi dữ liệu | Dữ kiện quan sát chính | Giới hạn của dữ liệu |
|---|---|---|---|
| **Đào Trọng Khang – A/B/C** | Feedback so sánh ba option do Duyên dẫn dắt | Kiểm tra nguồn ở cả ba option; dùng đường sửa/khôi phục; B tạo friction do hỏi–đáp; chọn C. | C chưa có log lưu hoàn tất; một lựa chọn không đại diện cho toàn bộ người dùng. |
| **Linh – Option A** | Log 31 hành động | Mở nguồn cả sáu mảnh; giữ 5/bỏ 1; đổi tag; lưu sau **2 phút 19 giây** từ lúc vào màn 2. | Không có lời giải thích hoặc đánh giá chủ quan; chưa thử đủ B/C trong feedback note này. |
| **K – Option A** | Log 22 hành động | Mở nguồn mảnh 3–6; tạo hai tag riêng; quay lại đổi phân loại; lưu sau **1 phút 39 giây** từ lúc vào màn 2. | Chưa xác nhận họ tên đầy đủ, ý nghĩa tag và mức hữu ích; chưa có feedback đủ B/C. |

> Bộ dữ liệu hiện có chưa phải ba Feedback Note độc lập mà mỗi tester đều thử đủ A/B/C. Vì vậy nhóm chỉ rút ra pattern hành vi, chưa tuyên bố một option “chiến thắng”.

### Bài học rút ra

1. Người dùng ở các phiên đều có hành vi quay về **nguồn/ngữ cảnh** trước hoặc trong lúc ra quyết định.
2. Quyết định ban đầu thường được sửa lại; vì vậy edit, reject, back và reset là chức năng cốt lõi.
3. Option A cho mức kiểm soát cao nhưng có nguy cơ tạo thêm effort thủ công.
4. Cơ chế hỏi–đáp của B không mặc nhiên làm co-create dễ hơn; với tester không thích gõ, nó có thể sinh ghi chú trống.
5. AI draft của C có tín hiệu giảm effort, nhưng cần làm phần note rõ hơn và không được che khuất evidence.

### Next Change

> **Giữ cơ chế AI tạo nháp và người dùng review của Option C, nhưng thiết kế bước review theo từng mục: đặt nguồn và mức chắc ngay cạnh nội dung, cho phép Edit/Reject/tạo tag riêng trước khi xác nhận, buộc mở nguồn đối với mục chắc thấp, đồng thời làm vùng note rõ và gọn hơn.**

### Still Unproven

- Người học có tìm lại thông tin nhanh hơn cách ghi chú hiện tại hay không.
- Ghi chú đã lưu có giúp ôn tập hoặc nhớ kiến thức tốt hơn sau vài ngày hay không.
- Review nháp AI có thực sự ít effort hơn tự tổ chức khi số mảnh tăng lên hay không.
- Mức chắc và source có được hiểu đúng, đồng thời có giảm automation bias hay không.
- Option B có cân bằng tốt hơn A/C với nhóm người dùng khác hay không.
- Kết quả có lặp lại khi ba tester độc lập đều thử cùng một fixture trên đủ A/B/C hay không.

**Lưu ý dữ liệu:** Shared Spec ban đầu dùng bài “Gán nhãn dữ liệu 3D”, trong khi prototype/log hiện tại dùng bài “AI Foundation – Large Language Models”. Fixture cần được đồng bộ trước vòng test so sánh tiếp theo.

---

## 6. AI Support Log

| Công cụ AI | AI hỗ trợ hiệu quả | Phần tôi trực tiếp kiểm tra và chỉnh sửa |
|---|---|---|
| **ChatGPT** | Brainstorm cơ chế Option A; phân biệt spectrum User-led / Co-create / AI-led; gợi ý source, uncertainty và recovery; cấu trúc tài liệu theo rubric. | Chọn Option A theo hướng user-led; quyết định taxonomy, quyền giữ/bỏ và cách người dùng lấy lại kiểm soát; kiểm tra nội dung cuối. |
| **ChatGPT/Codex** | Hỗ trợ triển khai HTML/CSS/JavaScript, chuyển flow thành prototype tương tác, rà các Quality Gates và phân tích timestamp trong log. | Chạy thử prototype; đối chiếu từng nhận định với log; sửa các kết luận vượt quá evidence; giữ URL hoặc feedback còn thiếu ở trạng thái chưa xác nhận. |

AI hỗ trợ tốt nhất ở khâu hệ thống hóa rubric, tạo cấu trúc prototype, so sánh mức tự trị của ba phương án và chuyển log thao tác thành evidence dễ kiểm tra. Tôi tự chỉnh các lỗi/rủi ro sau:

- Không suy diễn hành vi “mở nguồn” thành “tin tưởng AI hơn”.
- Không xem thao tác “bấm lưu” là bằng chứng ghi chú hữu ích khi ôn tập.
- Không biến một tester chọn C thành kết luận “C thắng”.
- Không coi ba log rời rạc là ba Feedback Note đầy đủ.
- Không tự tạo URL public, tên người thử hoặc phản hồi không có trong dữ liệu.
- Ghi rõ mismatch giữa Shared Spec 3D labeling và fixture AI Foundation của prototype để nhóm sửa trước vòng test tiếp theo.

---

### Tài liệu liên quan

- [Three-option Design Sheet](./three-option-design-sheet.md)
- [Prototype Feedback Note](./prototype-feedback-note.md)
- [Group Feedback Synthesis](./group-feedback-synthesis.md)
- [AI Support Log](./ai-support-log.md)
