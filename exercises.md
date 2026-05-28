# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Khi temperature thấp như 0.0, câu trả lời thường ổn định, ngắn gọn và ít khác biệt giữa các lần gọi. Khi temperature tăng lên 1.0 hoặc 1.5, phản hồi có xu hướng sáng tạo hơn, đa dạng hơn, nhưng cũng dễ lan man hoặc chọn chi tiết ít chắc chắn hơn.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi sẽ đặt temperature khoảng 0.2 đến 0.4 cho chatbot hỗ trợ khách hàng, vì mục tiêu chính là trả lời nhất quán, chính xác và dễ kiểm soát. Mức này vẫn đủ tự nhiên trong hội thoại nhưng giảm rủi ro model bịa hoặc trả lời quá sáng tạo.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Workload mỗi ngày là 10.000 x 3 x 350 = 10.500.000 token. Theo bảng giá trong lab, GPT-4o có giá input/output lần lượt cao hơn GPT-4o-mini khoảng 33,3 lần, nên nếu tỉ lệ input và output tương tự nhau thì GPT-4o đắt hơn GPT-4o-mini khoảng 33 lần cho workload này.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o xứng đáng dùng khi tác vụ cần suy luận phức tạp, chất lượng cao hoặc ảnh hưởng lớn đến người dùng, ví dụ phân tích tài liệu quan trọng, tư vấn kỹ thuật khó, hoặc xử lý yêu cầu có nhiều ràng buộc. GPT-4o-mini phù hợp hơn cho tác vụ khối lượng lớn, chi phí nhạy cảm và rủi ro thấp như phân loại tin nhắn, trả lời FAQ đơn giản, tóm tắt ngắn hoặc chatbot hỗ trợ bước đầu.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất khi phản hồi dài hoặc người dùng đang tương tác trực tiếp, ví dụ chatbot, trợ lý viết nội dung, giải thích từng bước hoặc sinh code, vì người dùng thấy kết quả xuất hiện ngay và cảm giác chờ đợi giảm đi nhiều. Non-streaming phù hợp hơn khi cần nhận toàn bộ kết quả rồi mới xử lý tiếp, ví dụ gọi API backend, phân loại dữ liệu, trích xuất JSON, kiểm thử tự động hoặc các tác vụ mà giao diện không cần hiển thị từng phần.


## Danh Sách Kiểm Tra Nộp Bài
- [ ] Tất cả tests pass: `pytest tests/ -v`
- [ ] `call_openai` đã triển khai và kiểm thử
- [ ] `call_openai_mini` đã triển khai và kiểm thử
- [ ] `compare_models` đã triển khai và kiểm thử
- [ ] `streaming_chatbot` đã triển khai và kiểm thử
- [ ] `retry_with_backoff` đã triển khai và kiểm thử
- [ ] `batch_compare` đã triển khai và kiểm thử
- [ ] `format_comparison_table` đã triển khai và kiểm thử
- [ ] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
