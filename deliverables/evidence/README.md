# evidence/ — data thô của từng bước eval loop

Thư mục này chứa **data thô** minh chứng cho mọi quyết định trong các file
`deliverables/REPORT.md`. File làm việc sinh ra ở **root repo**
(`dataset.jsonl`, `results.jsonl`, `verdicts.jsonl`, `labels.csv`) — chốt một vòng
là copy vào đây ngay, đặt tên theo version, KHÔNG ghi đè vòng cũ.

Cần có đủ:

| File | Lấy từ đâu | Là gì |
|---|---|---|
| `dataset-v1.jsonl` | `dataset.jsonl` (root) | Dataset nhóm chốt — đầu vào mọi lần chạy |
| `results-v1.jsonl` (v2, v3...) | `results.jsonl` (root) | Output tutor thật: input, output JSON, `tool_calls`, tokens, cost từng câu |
| `labels.csv` | Export từ `report.html` | Nhãn người của các thành viên (vòng chấm độc lập) |
| `judge-prompt-v1.md` (v2...) | `eval/judge_prompt.md` | Prompt judge TỪNG VÒNG — copy trước mỗi lần sửa |
| `verdicts-v1.jsonl` (v2...) | `verdicts.jsonl` (root) | Output judge từng vòng calibration |
| `braintrust-link.md` | tự tạo | Link project Braintrust/LangSmith — trace mọi run |

Số liệu trong mục 5 (Calibration Report) của `deliverables/REPORT.md` phải đối chiếu được với các
file ở đây (confusion matrix, % agreement in ra từ `eval/judge.py`).

Nhớ: chạy xong một vòng là copy ngay — cuối buổi mới gom là mất dấu các vòng trước.

## Trạng thái provenance hiện tại

- `labels.csv`, `labels-khiem.csv`, `labels-tuyet.csv` là nhãn người thật của vòng
  chấm độc lập (Tuyết + Khiêm, không bàn trước) trên `report.html`, đã được cả hai
  xác nhận — không phải dữ liệu tái dựng.
- Vòng v1 giữ raw evidence (`results-v1.jsonl`, `verdicts-v1/v2.jsonl`); HTML cũ
  không giữ lại vì có thể tái sinh và đã được thay bằng `report-v2.html` hiện hành.
- `braintrust-link.md` trỏ tới project LangSmith đã kiểm tra kết nối.

Vòng chạy mới bằng `openai/gpt-4o-mini` đã hoàn thành và được lưu thành:
`results-v2.jsonl`, `verdicts-v3.jsonl`, `judge-prompt-v3.md`, `report-v2.html`.
Project LangSmith đã nhận đủ 18 trace tutor và 18 trace judge của vòng này. Nhãn người
được chốt từ vòng v1 và được nhóm quyết định tái sử dụng làm regression baseline cho
vòng v2; không tạo `labels-v2.csv`.
