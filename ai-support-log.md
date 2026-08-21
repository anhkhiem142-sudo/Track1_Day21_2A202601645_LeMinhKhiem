# AI Support Log

> Ghi lại bạn đã dùng AI (ChatGPT/Claude/Kimi...) ở những bước nào khi làm deliverables.
> Trung thực là một phần của bài nộp — không ai làm một mình, quan trọng là bạn giữ
> quyền kiểm soát chất lượng.

**Không được dùng AI để:**
- Tự chọn dimensions, combinations hoặc coverage strategy thay nhóm.
- Gắn nhãn thay con người ở Phase 2 — human baseline phải là của con người.
- Quyết định verdict hoặc threshold thay nhóm.
- Bịa số liệu, trace hay kết quả chạy không tồn tại.

## AI Support Log — mỗi thành viên viết ngắn

### Lê Minh Khiêm

**AI đã giúp tôi ở đâu?**

AI hỗ trợ các việc thao tác/kỹ thuật: cài môi trường và chạy 44/45 test offline; đọc
`tutor/corpus/` để đề xuất *draft* 18 câu hỏi bám slide id/title thật (tôi và Tuyết mới
là người chốt lưới nhóm-user × intent và duyệt từng câu); chạy `run_eval.py`/`judge.py`
qua các vòng, tự retry khi gặp lỗi API tạm thời; tổng hợp pass rate, chi phí, latency
từ đúng dữ liệu thật trong `results.jsonl`; soạn draft `judge_prompt.md` v1→v2 và tự
chẩn đoán lỗi hệ thống từ confusion matrix; soạn draft phần Rubric/Routing/Scorecard
trong REPORT.md dựa trên số liệu thật đã chạy, không phải rubric chung chung.

**AI sai, hời hợt hoặc làm mất coverage ở đâu?**

- Bộ 18 câu do AI đề xuất ban đầu **thiếu ô rủi ro cao nhất**: câu mơ hồ mà KHÔNG gắn
  slide context (mọi câu deixis ban đầu đều có slide). Tuyết và tôi đọc lại mới phát
  hiện và tự thêm sc-13.
- `judge_prompt.md` vòng 1 do AI soạn **hời hợt** ở 2 điểm: chấm fail oan mọi câu bị từ
  chối đúng (hiểu nhầm "sources rỗng = thiếu nguồn") và pass oan các vi phạm
  groundedness/adversarial (thiếu rule nghiêm) — kết quả agreement vòng 1 chỉ 50%,
  thấp hơn hẳn mức tôi kỳ vọng.
- Ở vòng chạy lại (calibrate), có lúc DeepSeek/OpenRouter trả lỗi 401 — AI báo đúng lỗi
  thay vì tự bịa số liệu v2 để lấp chỗ trống; tôi giữ nguyên việc không công bố kết quả
  giả cho đến khi có key thật chạy lại.

**Tôi đã tự sửa hoặc quyết định lại điều gì?**

- Tự thêm sc-13 vào dataset sau khi phát hiện thiếu coverage (AI không tự chọn thay).
- Gán nhãn tay 18/18 câu trên `report.html` **hoàn toàn tự làm, độc lập với Tuyết,
  không dùng AI** — đây là bước bắt buộc phải là của người.
- Định nghĩa groundedness "nghiêm" (mọi chi tiết không truy được nguồn đều fail) là
  **quyết định của tôi và Tuyết** sau khi thảo luận 3 case bất đồng (sc-03/08/11); AI
  chỉ giúp tìm căn cứ trong corpus (chuẩn hallucination 0% ở module-03), không phải AI
  chọn hướng.
- Tự đặt các ngưỡng gate (schema/citation/quote ≥95%, scope ≥90%, groundedness ≥90%,
  từ chối adversarial = 100% không ngoại lệ) và tự ra verdict **Hold** — dựa trên số
  liệu tôi tự kiểm lại bằng script Python, không lấy nguyên văn kết luận AI đề xuất.
- Sau vòng v2 (agreement với regression baseline chỉ 56%), tôi quyết định **không tổ
  chức chấm tay lại** mà dùng `labels.csv` v1 làm baseline — tự nêu rõ đây là đánh đổi,
  không phải một vòng calibration người mới.

### La Thị Thanh Tuyết

*(phần này Tuyết viết riêng ở file ngoài desktop — ghép vào đây trước khi nộp.)*

**AI đã giúp tôi ở đâu?**

..............................................................................

**AI sai, hời hợt hoặc làm mất coverage ở đâu?**

..............................................................................

**Tôi đã tự sửa hoặc quyết định lại điều gì?**

..............................................................................
