# AI Support Log

> Ghi lại bạn đã dùng AI (ChatGPT/Claude/Kimi...) ở những bước nào khi làm deliverables.
> Trung thực là một phần của bài nộp — không ai làm một mình, quan trọng là bạn giữ
> quyền kiểm soát chất lượng.

| # | Bước | AI dùng để làm gì | Bạn kiểm chứng kết quả thế nào |
|---|------|-------------------|-------------------------------|
| 1 | Setup môi trường | Cài dependencies, cấu hình `.env` (chọn model qua OpenRouter), chạy 44 test offline | Đọc log test thật (44 pass), không chỉ tin lời AI báo "xong" |
| 2 | P1 Input Grid + dataset v1 | AI đọc `tutor/corpus/` để soạn 18 câu hỏi bám nội dung thật (slide id/title có thật), đề xuất lưới nhóm user × intent | Đối chiếu tay vài slide id trong `report.html` xem đúng chủ đề không |
| 3 | P2 chạy tutor + gán nhãn | AI chạy `run_eval.py`, phát hiện 3 lỗi API tạm thời và tự retry | Tự đọc từng câu trả lời trong `report.html`, gán nhãn **độc lập với Khiêm** (không bàn trước) — đây là bước AI không thay được |
| 4 | Xử lý bất đồng nhãn (sc-03/08/11) | AI phân tích 3 case Tuyết/Khiêm chấm khác nhau, đề xuất 2 hướng (nghiêm/vừa phải) kèm lý do | Được hỏi trực tiếp, quyết định để AI chọn hướng dựa trên bằng chứng AI tìm trong corpus (chuẩn hallucination 0% ở module-03) thay vì tự đọc lại toàn bộ corpus |
| 5 | P3 Rubric + Routing Map | AI soạn draft dựa trên số liệu code_checks + nhãn người thật (không phải rubric chung chung) | Đọc lại bảng, thấy khớp với case thật đã gặp (sc-07, sc-14) nên chấp nhận |
| 6 | P4 calibrate judge | AI viết `judge_prompt.md` v1→v2, chạy `judge.py` 2 vòng, tự chẩn đoán 2 lỗi hệ thống của judge từ confusion matrix | Agreement in ra từ code thật (50%→83%), không phải AI tự khai |
| 7 | P5/P6 Scorecard, Gate, Verdict | AI tính pass rate/chi phí/latency từ `results.jsonl` thật, đề xuất Hold + 3 lỗi cần fix | Số liệu tự kiểm bằng script Python độc lập, không lấy nguyên văn AI nói |

- Phần AI gợi ý mà bị **bác bỏ**: chưa có — các đề xuất đều được chấp nhận sau khi đối
  chiếu số liệu thật, nhưng quyết định "groundedness nghiêm hay vừa phải" ban đầu là
  bất đồng thật giữa 2 người (không phải AI), AI chỉ giúp tìm căn cứ để chốt.
- Phần **hoàn toàn tự làm**: gán nhãn tay 18 câu ở `report.html` (cả Tuyết và Khiêm,
  độc lập) — đây là phần AI không được phép làm thay vì sẽ mất ý nghĩa "human
  baseline" của cả bài lab.
- **Rủi ro cần lưu ý khi nộp**: phần lớn thao tác kỹ thuật (chạy lệnh, sửa
  prompt, viết REPORT.md) do AI thực hiện trong một phiên làm việc — nhóm cần tự đọc
  lại toàn bộ `REPORT.md` trước khi nộp để đảm bảo hiểu và đồng ý với từng quyết định,
  không chỉ nộp nguyên văn AI viết.
