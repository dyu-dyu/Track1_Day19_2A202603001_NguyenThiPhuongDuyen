# Three-option Design Sheet — Case B · AI Notes

> **Phiên bản nội dung:** Shared Spec v2 trong `message.txt`.  
> **Thay đổi chính:** thay bài “Gán nhãn dữ liệu 3D” bằng **“AI Foundation — LLM hoạt động thế nào”** và sửa phạm vi ảnh chụp từ slide 6–9 thành **slide 5–8**. Các nguyên tắc về giao diện, ba màn hình, quyền kiểm soát và luật build của `SHARED-SPEC.md` vẫn được giữ nguyên.

## 1. Problem Anchor

### 1.1. Năm thành tố

| Thành tố | Nội dung |
|---|---|
| **Situation** | Sau khi học xong một bài và cần xem lại hoặc ôn tập trước kỳ thi. |
| **User** | Học viên có thói quen lưu screenshot, highlight, câu hỏi hoặc note ngắn trong lúc học. |
| **Job** | Biến những dấu vết đã lưu thành một bản ghi chú có cấu trúc, dễ hiểu và dùng lại được. |
| **Barrier** | Các dấu vết được tạo rời rạc theo từng thời điểm hoặc slide, thiếu kết nối và ngữ cảnh nên phải tổ chức lại thủ công. |
| **Consequence** | Người học mất thời gian tìm và gom nội dung, có thể quên lý do đã lưu hoặc bỏ không sử dụng lại note. |

### 1.2. Hypothesis Problem

> **Khi học xong một bài và cần xem lại nội dung đã học, những học viên có thói quen lưu các ghi chú ngắn, hình ảnh hoặc điểm chưa hiểu gặp khó khăn trong việc biến những mảnh ghi chú đó thành một bản note có thể sử dụng để ôn tập, bởi vì chúng được tạo rời rạc theo từng thời điểm và thiếu sự kết nối/ngữ cảnh, dẫn đến người học phải tốn thêm thời gian để tìm và tổ chức lại thủ công, thậm chí không nhớ lý do đã lưu hoặc bỏ không sử dụng lại.**

### 1.3. Evidence Anchor từ Day 17

- P01 chụp màn hình và để trong folder, sau đó không nhớ ảnh nào là ảnh nào; có lần mất khoảng 10 phút để tìm lại.
- P02 lưu các phần chưa hiểu rồi quay lại xử lý và hỏi ChatGPT.
- P03 ghi note theo từng slide rồi phải chuyển thủ công sang một file tổng hợp.

Evidence xác nhận hành vi lưu dấu vết rời rạc và phát sinh công sức xử lý lại. Evidence chưa chứng minh người dùng sẽ tin hoặc sử dụng lâu dài một bản note do AI tạo.

---

## 2. Comparison Contract — Những gì phải giống nhau ở A/B/C

| Thành phần | Đặc tả chung |
|---|---|
| **Nền tảng** | Nền tảng học online kiểu vlearn.dev, có trình xem slide và panel trợ giảng AI bên phải. |
| **Người dùng** | Học viên đã lưu screenshot, highlight, note nhanh và câu hỏi trong lúc học. |
| **Bài học** | **AI Foundation — LLM hoạt động thế nào**, gồm 8 slide. |
| **Tình huống** | Người dùng vừa học xong bài; kỳ thi còn 4 ngày. |
| **Nhiệm vụ** | Tạo ghi chú ôn thi từ 6 dấu vết đã lưu. |
| **Kết quả mong muốn** | Có bản ghi chú dùng lại được, giữ nguồn/ngữ cảnh và những điểm người học chưa hiểu. |
| **Flow** | Màn 1: Common Context → Màn 2: Critical Interaction → Màn 3: Result/User Decision. |
| **Dữ liệu** | Cùng 8 slide, cùng 6 mảnh, cùng wording và cùng trạng thái ban đầu. |
| **Kỹ thuật** | Không dùng model/API thật; toàn bộ phản hồi là canned output. |

### Task chung cho tester

> **“Tình huống: bạn vừa học xong bài này, 4 ngày nữa thi. Dùng từng phương án để tạo ghi chú ôn thi từ những gì bạn đã lưu.”**

Người điều phối chỉ đọc task trên, không giải thích tính năng hoặc gợi ý tester nên chọn, sửa hay bỏ mục nào.

---

## 3. Shared Content Fixture

### 3.1. Nội dung 8 slide

| Slide | Tiêu đề | Nội dung bắt buộc |
|---:|---|---|
| **1** | AI, Machine Learning, Deep Learning | AI: máy làm việc cần trí thông minh của người; ML: máy học quy luật từ dữ liệu thay vì viết luật tay; Deep Learning: ML dùng mạng nơ-ron nhiều lớp; `DL ⊂ ML ⊂ AI`. |
| **2** | Ba cách máy học | Có giám sát: học từ dữ liệu đã gắn nhãn đúng/sai; không giám sát: tự tìm nhóm trong dữ liệu chưa gắn nhãn; học tăng cường: thử, nhận thưởng/phạt rồi chỉnh lại. |
| **3** | LLM là gì | LLM là Large Language Model, học từ lượng văn bản rất lớn; “LLMs predict the next token based on context”; câu trả lời dài được tạo bằng cách dự đoán lần lượt từng token; model không tự kiểm tra sự thật. |
| **4** | Token và context window | Token là mảnh chữ, có thể là một từ, một phần từ hoặc dấu câu; tiếng Việt thường tốn nhiều token hơn tiếng Anh; context window là số token tối đa model nhìn thấy một lần; vượt giới hạn có thể làm phần đầu bị quên. |
| **5** | Training, fine-tuning và inference | Training làm model học từ dữ liệu và thay đổi trọng số; fine-tuning là train thêm trên dữ liệu riêng cho một việc cụ thể; inference dùng model đã train để trả lời và không đổi trọng số; mỗi lần chat là inference. |
| **6** | Prompt | Prompt là toàn bộ chỉ dẫn và ngữ cảnh gửi cho model; prompt tốt nêu vai trò, nhiệm vụ, ví dụ và định dạng đầu ra; đổi prompt chỉ đổi đầu vào, không đổi model; cùng model có thể trả lời khác khi prompt khác. |
| **7** | Temperature | Temperature điều chỉnh độ ngẫu nhiên khi chọn token; mức thấp cho câu trả lời ổn định hơn; mức cao sáng tạo hơn nhưng dễ lạc ý; việc cần chính xác nên dùng temperature thấp. |
| **8** | Hallucination và cách kiểm chứng | Hallucination là câu trả lời trôi chảy nhưng sai sự thật; xảy ra vì model dự đoán chuỗi chữ hợp lý chứ không tự kiểm tra sự thật; giảm rủi ro bằng cách đưa nguồn, yêu cầu trích dẫn và kiểm lại số liệu, tên riêng, trích dẫn. |

**Quy tắc uncertainty:** slide 8 cố ý hiển thị mờ trong cả ba prototype. Nội dung này vẫn cần cho kỳ thi và được dùng để kiểm tra cách user/AI xử lý nguồn không chắc chắn.

### 3.2. Sáu mảnh người dùng đã lưu

| # | Mảnh | Loại | Nguồn |
|---:|---|---|---|
| **1** | 4 ảnh chụp màn hình slide 5–8: `IMG_0243.png` … `IMG_0246.png` | Screenshot | Folder “Ảnh thi” |
| **2** | “chưa hiểu slide 5: training khác inference chỗ nào” | Note nhanh lúc học | Slide 5 · `04:12` |
| **3** | “cần nail phần fine-tuning vs. prompt cho thi” | Câu hỏi của user | Tự gõ |
| **4** | Highlight: “LLMs predict the next token based on context” | Highlight | Slide 3 |
| **5** | “thắc mắc: token có phải là 1 từ không?” | Câu hỏi | Slide 3 · `01:24` |
| **6** | “slide 8: ảnh mờ, đọc không rõ” | Trạng thái không chắc | Slide 8 |

### 3.3. Hai bẫy nội dung cần giữ nguyên

1. **Mảnh 2 và mảnh 3 liên quan nhưng không đồng nghĩa.** Training/inference nói về lúc model học so với lúc model được dùng; fine-tuning/prompt nói về hai cách làm kết quả phù hợp hơn, trong đó chỉ fine-tuning thay đổi trọng số. Prototype không được gộp hai ý này thành một kết luận duy nhất.
2. **Mảnh 5 gắn với slide 3 nhưng câu trả lời nằm ở slide 4.** Thiết kế phải cho phép người dùng lần sang nguồn liên quan; không được kết luận “token là một từ”.

---

## 4. Shared Experience Spec

### 4.1. Bố cục Màn 1

- **Sidebar trái:** tên bài học, danh sách slide, mục “Bài giảng” và trạng thái “Đã học xong”.
- **Vùng giữa:** header “Ngày 2 · Day 18 · AI Notes — Notes để ôn thi”, badge đề bài và statement: *“Sau khi học xong, hệ thống giúp bạn biến các dấu vết bạn để lại trong bài thành ghi chú ôn thi.”*
- **Panel phải:** vùng AI nơi critical interaction diễn ra.

### 4.2. Visual Style

| Thành phần | Chuẩn chung |
|---|---|
| Nền app | `#f4f2ed` |
| Thẻ/slide | Nền `#fff`, bo 16px, shadow nhẹ |
| Màu AI chính | Xanh olive `#2f6f6a`; avatar tròn chữ “AI”; bubble `#eef4f3` |
| Cảnh báo uncertainty | Nền `#fbf3e6`, viền `#ecd9b5`, chữ `#7a5a1e` |
| Chữ nguồn | Uppercase 11px, màu `#9a6b2f` |
| Font | Segoe UI hoặc system sans |
| Khung desktop | Sidebar trái 220px và panel phải 340px |

### 4.3. Cấu trúc ba màn hình

```text
SCREEN 1 — COMMON CONTEXT
    ↓
SCREEN 2 — CRITICAL INTERACTION
    ↓
SCREEN 3 — RESULT / USER DECISION
```

- Màn 1 phải giống nhau 100% ở A/B/C.
- Chỉ critical interaction tại Màn 2 được khác nhau.
- Màn 3 có cùng bố cục nhưng nội dung phản ánh đúng cơ chế của từng option.
- Mỗi option có ít nhất một đường reset về Màn 1.
- Điểm user lấy lại quyền kiểm soát phải hiện trực tiếp trên giao diện.
- Không thêm màn hình thứ tư.

---

## 5. Ba Option trên Spectrum of Control

```text
USER CREATES                       USER + AI                         AI CREATES
Option A ───────────────────────── Option B ─────────────────────── Option C
User tự tổ chức                    Hai bên cùng tạo                  AI soạn, user review
```

| Thuộc tính | A · User-led Tagging | B · User + AI Co-create | C · AI-led Draft |
|---|---|---|---|
| **Cơ chế** | Hệ thống gom dấu vết; user tự tổ chức và gắn tag. | AI đặt câu hỏi có nguồn; câu trả lời của user tạo thành note. | AI tự tạo nháp có nguồn và mức chắc; user duyệt từng mục. |
| **Bên khởi tạo nội dung** | User | AI khởi tạo câu hỏi, user khởi tạo câu trả lời | AI |
| **AI/hệ thống được làm** | Tập hợp, hiển thị và giữ liên kết nguồn; không suy luận. | Chọn câu hỏi làm rõ và định dạng câu trả lời. | Phân loại và viết bản nháp có thể đảo ngược. |
| **User làm việc chính** | Mở nguồn, giữ/bỏ, gắn/bỏ tag, tạo tag riêng. | Mở nguồn, trả lời/bỏ qua, sửa và tag. | Đối chiếu nguồn, sửa, bỏ hoặc duyệt từng mục. |
| **Kết quả** | Note phản ánh taxonomy và quyết định của user. | Note được tạo từ câu trả lời của user. | Note gồm các mục AI soạn đã được user chấp nhận. |
| **Trade-off** | Control cao nhưng effort thủ công cao. | Chia sẻ effort nhưng có thể tạo friction do hỏi/gõ. | Effort tạo thấp nhưng effort kiểm chứng và rủi ro automation bias cao hơn. |
| **Giả định cần test** | User có chịu tự tổ chức nếu nguồn được giữ không? | Trả lời câu hỏi AI có nhanh và dễ hơn tự tổ chức không? | Review nháp AI có ít effort hơn mà vẫn đủ đúng không? |
| **Prototype** | [option-a.html](./option-a.html) | [option-b.html](./option-b.html) | [Option-C.html](./Option-C.html) |

---

## 6. Critical Interaction theo từng Option

### 6.1. Option A — User-led Tagging

**Mục tiêu thiết kế:** kiểm tra willingness-to-organize khi hệ thống chỉ cung cấp nguồn và công cụ tổ chức, không diễn giải thay người học.

#### Flow

1. User xem danh sách đúng 6 mảnh đã lưu.
2. User mở slide hoặc ảnh nguồn khi cần.
3. User tự kéo/thêm mảnh vào slide hoặc mốc liên quan.
4. User chọn một hoặc nhiều tag: **Quan trọng**, **Chưa hiểu**, **Hỏi giảng viên**; có thể tạo tag riêng.
5. User có thể bỏ mảnh, đổi/bỏ tag hoặc hoàn tác.
6. Màn 3 chỉ hiển thị kết quả từ các quyết định của user để review và lưu.

#### Ranh giới vai trò

- Hệ thống **không** tự giải thích training/inference, fine-tuning/prompt hoặc token.
- Hệ thống **không** gán tag sẵn và không quyết định mảnh nào quan trọng.
- Mỗi mảnh luôn giữ nhãn nguồn; mảnh 5 cho phép mở tiếp slide 4 nếu user tìm nội dung liên quan.

#### Annotation ngoài frame

```text
OPTION A — USER-LED TAGGING
We expect: user tự tổ chức khi có nguồn và công cụ tag.
Watch for: số lần mở nguồn, đổi/bỏ tag, tạo tag riêng và burden thủ công.
Do not explain: tag nào đúng hoặc mảnh nào nên giữ.
```

### 6.2. Option B — User + AI Co-create

**Mục tiêu thiết kế:** kiểm tra liệu câu hỏi làm rõ có giúp user tự diễn đạt hiểu biết nhanh hơn so với tự tổ chức hoàn toàn hay không.

#### Flow

1. User bắt đầu review session.
2. AI lần lượt hỏi 2–3 câu và hiển thị chip nguồn tương ứng.
3. User mở nguồn, nhập câu trả lời hoặc bỏ qua.
4. Hệ thống định dạng câu trả lời thành note nhưng không thêm kiến thức mà user chưa viết.
5. User sửa, tag, bỏ mục hoặc quay lại câu hỏi trước khi lưu.

#### Bộ câu hỏi canned bắt buộc

| Câu | Câu hỏi AI | Nguồn hiển thị | Điều cần quan sát |
|---:|---|---|---|
| **1** | “Theo cách bạn hiểu, training khác inference ở điểm nào?” | Mảnh 2 + slide 5 | User có phân biệt thay đổi trọng số với lúc dùng model hay không. |
| **2** | “Fine-tuning khác việc đổi prompt như thế nào?” | Mảnh 3 + slide 5 + slide 6 | User có gộp nhầm mảnh 2 và 3 hay không. |
| **3** | “Token có luôn là một từ không? Bạn muốn ghi lại điều gì để ôn?” | Mảnh 5 + slide 3; cho phép mở slide 4 | User có tìm đến nguồn trả lời đúng và sửa hiểu nhầm hay không. |

Mảnh 1, 4 và 6 vẫn hiển thị trong vùng nguồn chung. Slide 8 mờ phải được cảnh báo, không được AI tự trả lời thay như thể nguồn đã rõ.

#### Annotation ngoài frame

```text
OPTION B — USER + AI CO-CREATE
We expect: câu hỏi có nguồn giúp user tự diễn đạt note nhanh hơn.
Watch for: typing friction, bỏ qua, câu trả lời trống, mở nguồn và quay lại sửa.
Do not explain: câu trả lời đúng hoặc chip nguồn dùng để làm gì.
```

### 6.3. Option C — AI-led Draft

**Mục tiêu thiết kế:** kiểm tra liệu review một bản nháp AI có giảm effort nhưng vẫn khiến user kiểm chứng các điểm sai hoặc không chắc hay không.

#### Flow

1. AI tạo sẵn bản nháp từ 6 mảnh và nội dung bài học.
2. Mỗi mục có nguồn, mức chắc và các thao tác **Mở nguồn / Sửa / Bỏ / Duyệt**.
3. User đối chiếu rồi quyết định từng mục.
4. Mục **Mức chắc: Thấp** bị khóa duyệt đến khi user đã mở mảnh gốc.
5. User có thể bỏ toàn bộ nháp hoặc reset về Màn 1.
6. Màn 3 chỉ đưa vào bản cuối các mục được user chấp nhận.

#### Bản nháp canned bắt buộc

| Mục nháp | Nội dung đề xuất | Nguồn | Mức chắc | Rào chắn |
|---:|---|---|---|---|
| **1** | Training làm model học và thay đổi trọng số; inference dùng model đã học để trả lời và không đổi trọng số. | Mảnh 2 + slide 5 | Cao | Cho phép sửa/bỏ/duyệt. |
| **2** | Fine-tuning train thêm và làm đổi trọng số; thay đổi prompt chỉ thay đầu vào, không thay model. | Mảnh 3 + slide 5–6 | Trung bình | Giữ tách biệt với mục 1; không tự gộp. |
| **3** | LLM tạo câu trả lời bằng cách dự đoán token kế tiếp dựa trên ngữ cảnh. | Mảnh 4 + slide 3 | Cao | Cho phép mở đúng câu highlight. |
| **4** | Token không nhất thiết là một từ; nó có thể là một phần từ hoặc dấu câu. | Mảnh 5 + slide 4 | Trung bình | Nêu rõ câu hỏi bắt nguồn ở slide 3 nhưng evidence trả lời nằm ở slide 4. |
| **5** | Hallucination là output nghe hợp lý nhưng có thể sai; cần kiểm lại số liệu, tên riêng và trích dẫn. | Mảnh 1 + mảnh 6 + slide 8 | **Thấp** | Chặn duyệt đến khi user mở nguồn; giữ cảnh báo slide mờ. |

#### Annotation ngoài frame

```text
OPTION C — AI-LED DRAFT
We expect: user review nháp nhanh hơn nhưng vẫn kiểm tra mục không chắc.
Watch for: mở nguồn, hiểu mức chắc, edit/reject và automation bias.
Do not explain: mục nào nên duyệt hoặc vì sao mục mức thấp bị khóa.
```

---

## 7. Human–AI Decision Table

| Thời điểm quyết định | Option A | Option B | Option C | Rào chắn chung |
|---|---|---|---|---|
| **Chọn dữ liệu đầu vào** | User xem/chọn mảnh. | User xem; AI chỉ dùng mảnh để hỏi. | AI dùng mảnh để tạo nháp; user có thể bỏ. | Luôn cho xem đủ 6 mảnh gốc. |
| **Diễn giải ý nghĩa** | User tự diễn giải. | User diễn giải qua câu trả lời. | AI đề xuất; user kiểm tra. | Không che nguồn; không trình bày suy đoán như fact. |
| **Phân biệt mảnh 2 và 3** | User tự tổ chức thành các mục riêng. | AI hỏi thành hai câu riêng. | AI tạo hai mục riêng. | Không gộp training/inference với fine-tuning/prompt. |
| **Giải quyết câu hỏi token** | User tìm slide liên quan. | AI dẫn nguồn slide 3 và cho mở slide 4. | AI đề xuất từ slide 4 để user duyệt. | Luôn hiện đường về evidence trả lời. |
| **Xử lý slide 8 mờ** | User đánh dấu/chọn cách xử lý. | AI hỏi lại hoặc để user bỏ qua. | AI gắn mức chắc thấp. | Cảnh báo uncertainty; không tự khẳng định nguồn đã rõ. |
| **Tổ chức nội dung** | User gắn tag và cấu trúc. | AI định dạng câu trả lời; user sửa. | AI phân nhóm; user duyệt. | Mỗi mục sửa/bỏ được độc lập. |
| **Quyết định bản cuối** | User | User | User | Preview trước lưu và có đường quay lại. |
| **Phục hồi** | Bỏ/đổi tag, hoàn tác, reset. | Bỏ qua, quay lại sửa, hủy, reset. | Edit/reject, mở nguồn, bỏ nháp, reset. | Không có hành động AI không thể đảo ngược. |

---

## 8. Distance Check

- **A ↔ B:** A không suy luận hoặc hỏi; B dùng AI để chọn câu hỏi làm rõ và định dạng câu trả lời của user.
- **B ↔ C:** B yêu cầu user tạo nội dung qua câu trả lời; C để AI viết nội dung trước rồi user review.
- **A ↔ C:** A đặt cả diễn giải và tổ chức ở user; C chuyển hai việc đó sang AI nhưng giữ quyết định cuối ở user.

Ba option phải khác nhau về **solution mechanism** và cách phân chia công việc, không chỉ khác màu, layout hoặc wording. Không option nào được cố tình làm yếu để option khác thắng.

---

## 9. Test Protocol & Success Signals

### 9.1. Quy trình

1. Reset prototype về Màn 1 trước mỗi lượt.
2. Đọc đúng task chung, không hướng dẫn thêm.
3. Cho tester thao tác đủ A/B/C trên cùng fixture.
4. Cân bằng thứ tự A/B/C giữa các tester để giảm order effect.
5. Ghi fact và câu nói nguyên văn trước khi diễn giải.
6. Sau ba option, hỏi lựa chọn và trade-off mà tester chấp nhận.

### 9.2. Dữ liệu cần ghi

| Nhóm dữ liệu | Chỉ báo |
|---|---|
| **Completion** | Hoàn thành/không hoàn thành; thời gian đến màn kết quả và thời gian lưu. |
| **First action** | Mở nguồn, bắt đầu tổ chức, trả lời hay duyệt ngay. |
| **Evidence checking** | Số lần mở nguồn; có mở slide 4 cho câu token và slide 8 cho mục không chắc không. |
| **Control** | Số lần sửa, bỏ, đổi tag, bỏ qua, quay lại hoặc reset. |
| **Breakdown** | Dừng lâu, hiểu sai vai trò AI, câu trả lời trống, duyệt mà không đọc nguồn. |
| **Output quality** | Có tách đúng training/inference và fine-tuning/prompt; có sửa hiểu nhầm “token = một từ”. |
| **Trade-off** | Lý do chọn option; effort, trust và control mà user sẵn sàng đánh đổi. |

### 9.3. Success Signals theo option

- **A:** user hoàn thành mà không cần trợ giúp, dùng nguồn khi cần và có thể thay đổi quyết định; effort thủ công vẫn ở mức chấp nhận được.
- **B:** user trả lời bằng hiểu biết của mình, không tạo nhiều mục trống và thấy câu hỏi giúp làm rõ thay vì gây phiền.
- **C:** user hiểu output là bản nháp, kiểm tra mục chắc thấp, phát hiện/sửa được lỗi và không duyệt máy móc.

Không dùng “thích nhất” làm kết luận duy nhất. Một option chỉ có tín hiệu tốt khi tester hoàn thành, hiểu vai trò AI, dùng được đường kiểm soát và giải thích được trade-off.

---

## 10. Build Rules & Definition of Done

### Luật không được thay đổi

- Annotation bốn dòng `OPTION / We expect / Watch for / Do not explain` đặt trong comment đầu file HTML, không hiển thị trong UI.
- Không narrate hộ tester và không thêm sidebar hướng dẫn thao tác.
- Prototype phải có thao tác thật: mở nguồn, sửa, bỏ mục, duyệt và reset; không chỉ là mockup tĩnh.
- Không thêm màn hình ngoài ba màn đã thống nhất.
- Không gọi model/API thật; mọi output phải xác định trước và có thể lặp lại.

### Checklist trước khi test

- [ ] A/B/C cùng tên bài **AI Foundation — LLM hoạt động thế nào**.  
  **Chưa đạt:** B và C dùng đúng tên; A vẫn hiển thị **“AI Foundation — Large Language Models”**.
- [ ] A/B/C có đúng 8 slide và nội dung từng slide giống nhau.  
  **Chưa đạt:** B có đủ fixture v2; A vẫn dùng bộ slide cũ về Prompt/Tokenization, Self-Attention và RAG; C chưa có dữ liệu/render đầy đủ 8 slide trong JavaScript nên vùng `slideBox` chưa chứng minh được nội dung giống B.
- [ ] A/B/C có đúng 6 mảnh; mảnh 1 là ảnh slide **5–8**, không phải 6–9.  
  **Chưa đạt:** B và C dùng 6 mảnh v2; A có 6 mảnh nhưng là fixture cũ, trong đó mảnh 1 gắn Slide 2 thay vì 4 ảnh slide 5–8.
- [ ] Slide 8 mờ giống nhau ở cả ba option.  
  **Chưa đạt:** B làm mờ Slide 8; A làm mờ Slide 7; C có CSS `.blurry` nhưng chưa có logic render 8 slide để xác nhận Slide 8 được áp dụng giống B.
- [ ] Mảnh 2 và 3 không bị gộp nhầm.  
  **Chưa đạt:** C tách hai mục nháp; B đang đưa mảnh 2 và 3 vào cùng câu hỏi `Training, inference và fine-tuning vs. prompt`; A chưa dùng hai mảnh theo fixture v2.
- [ ] Câu hỏi token có đường từ mảnh 5/slide 3 đến evidence ở slide 4.  
  **Chưa đạt đồng bộ:** C ghi rõ evidence nằm ở Slide 4; B cho phép mở Slide 4 từ mục lục nhưng chip của mảnh 5 chỉ mở Slide 3; A chưa dùng mảnh 5 theo fixture v2.
- [ ] Chỉ Màn 2 khác về critical interaction.  
  **Chưa đạt:** layout, wording, sidebar, trình xem slide và trạng thái Màn 1/Màn 3 hiện chưa đồng nhất giữa A/B/C.
- [x] Mỗi option có source, recovery và reset hoạt động được.  
  **Đạt ở mức mã nguồn:** A có xem slide, hoàn tác và `triggerReset()`; B có chip nguồn, quay lại/hoàn tác và `reset()`; C có mở nguồn, Edit/Reject/Back và `resetAll()`.
- [x] Option C chặn duyệt mục mức chắc thấp cho đến khi mở nguồn.  
  **Đạt:** nút duyệt bị `disabled` khi `requiresSource` là `true` và mục chưa có trong `state.opened`.
- [x] Ba prototype mở được bằng đường dẫn repository hoặc URL public đã kiểm tra.  
  **Đạt với repository:** `option-a.html`, `option-b.html` và `Option-C.html` đều tồn tại; cú pháp JavaScript của ba file hợp lệ. **Chưa có URL public được xác nhận.**

---

## 11. Still Unproven trước vòng test tiếp theo

- Barrier chính có thật sự là thiếu ngữ cảnh với nhiều người học hay không.
- User có chịu effort tự tổ chức khi số mảnh lớn hơn 6 hay không.
- Câu hỏi của AI có giảm effort hay lại tạo thêm typing friction.
- AI có diễn giải đúng ý nghĩa cá nhân của note và tách đúng các khái niệm gần nhau hay không.
- Source và mức chắc có làm user kiểm tra kỹ hơn, hay vẫn xuất hiện automation bias.
- Bản note cuối có giúp ôn nhanh hơn hoặc nhớ tốt hơn sau vài ngày hay không.
- Kết quả có lặp lại với các tester khác khi thứ tự A/B/C được cân bằng hay không.
