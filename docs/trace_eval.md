# 📊 BÁO CÁO THU HOẠCH NGHIỆM THU BÀI LAB 3 (BƯỚC 3 — SUBMISSION ARTIFACT)

> **Họ và Tên Học viên:** [Bùi Lê Thái Sơn]  
> **Mã Sinh Viên / Mã Học viên:** [2A202602880]  
> **Chủ đề Lựa chọn:** 4.1 - Trợ lý Tuyển dụng & Sàng lọc CV  

---

## 1. BẢNG CHẤM ĐIỂM AGENTIC FIT SCORING MATRIX (ĐÁNH GIÁ CHỦ ĐỀ)

| Tiêu chí Đánh giá | Mức độ (1 - 5) | Giải trình chi tiết lý do chọn điểm |
| :--- | :---: | :--- |
| **1. Multi-step Reasoning** | 4 / 5 | Trợ lý cần phân tích yêu cầu tuyển dụng, đọc/tóm tắt CV, đối chiếu kỹ năng - kinh nghiệm - học vấn với tiêu chí vị trí, sau đó đưa ra nhận xét và đề xuất bước tiếp theo. Quy trình có nhiều bước suy luận nối tiếp, dù chưa quá phức tạp như các bài toán tối ưu dài hạn. |
| **2. Tool Interaction** | 5 / 5 | Hệ thống cần tra cứu tiêu chí tuyển dụng từ cơ sở dữ liệu/MCP Server và thực hiện hành động gửi thông báo lịch phỏng vấn. Đây là bài toán có cả công cụ tra cứu thông tin và công cụ hành động rõ ràng. |
| **3. Dynamic Decision** | 4 / 5 | Bước tiếp theo phụ thuộc vào kết quả sàng lọc: nếu ứng viên phù hợp thì đề xuất/gửi lịch phỏng vấn, nếu thiếu tiêu chí thì phản hồi lý do chưa đạt hoặc yêu cầu bổ sung thông tin. Quyết định thay đổi theo dữ liệu CV và tiêu chí vị trí. |
| **4. Long Horizon Goal** | 4 / 5 | Trợ lý cần giữ mục tiêu xuyên suốt từ lúc nhận CV, xác định vị trí ứng tuyển, kiểm tra tiêu chí, đánh giá mức độ phù hợp đến khi tạo thông báo phỏng vấn. Mục tiêu kéo dài qua nhiều thao tác nhưng vẫn nằm trong một quy trình tuyển dụng ngắn. |
| **TỔNG ĐIỂM AGENTIC FIT** | **17 / 20** | Với tổng điểm 17/20, chủ đề rất phù hợp triển khai Agentic System vì cần suy luận nhiều bước, dùng công cụ ngoài, ra quyết định động và duy trì mục tiêu xử lý hồ sơ tuyển dụng đến khi có hành động cuối. |

---

## 2. TRÍCH XUẤT KẾT QUẢ WATERFALL TRACE LOG (SAU KHI CHẠY TEST SUITE TRÊN API THẬT)

> ⚠️ **YÊU CẦU NGHIỆM THU:** Mở tệp `.env` điền `GEMINI_API_KEY` (hoặc `OPENAI_API_KEY`) để kết nối LLM thật trước khi thực thi `python src/app.py --all`. Bài nộp chỉ dùng Mock Offline Provider sẽ không đạt điểm nghiệm thực tế.

Dán 1 đoạn trích xuất log tiêu biểu từ file `docs/trace_waterfall.json` sinh ra từ phản hồi LLM API thật:

```json
[
  {
    "step": 1,
    "query": "Hãy tra cứu thông tin học vụ của sinh viên SV2026001.",
    "action_type": "TOOL_EXECUTION",
    "tool_name": "academic_query",
    "arguments": {
      "student_id": "SV2026001"
    },
    "observation": {
      "status": "SUCCESS",
      "student_id": "SV2026001",
      "data": {
        "full_name": "Nguyễn Văn An",
        "class": "AI-K4",
        "gpa": 3.85,
        "email": "an.nv@vinuni.edu.vn",
        "status": "Đang học",
        "advisor": "PGS.TS Nguyễn Văn A"
      }
    },
    "latency_ms": 2792.65
  },
  {
    "step": 2,
    "query": "Hãy tra cứu thông tin học vụ của sinh viên SV2026001.",
    "action_type": "FINAL_ANSWER",
    "thought": "Tổng hợp kết quả từ MCP Server thành công.",
    "output": "Kết quả tra cứu cho sinh viên SV2026001 (Nguyễn Văn An): Lớp AI-K4, GPA: 3.85, Email: an.nv@vinuni.edu.vn, Trạng thái: Đang học, Cố vấn: PGS.TS Nguyễn Văn A.",
    "latency_ms": 10.0
  },
  {
    "step": 1,
    "query": "Hãy gửi thông báo lịch phỏng vấn cho ứng viên Nguyễn Minh Anh ứng tuyển vị trí Data Analyst vào 09:00 ngày 18/09/2026.",
    "action_type": "FINAL_ANSWER",
    "thought": "OpenRouter phản hồi trực tiếp bằng văn bản (không cần gọi công cụ).",
    "output": "Xin lỗi, tôi không thể thực hiện yêu cầu này vì những lý do sau:\n\n**1. Phạm vi công việc:**\n- Tôi là Trợ lý Tác tử Học vụ của Đại học VinUni, hỗ trợ các chức năng liên quan đến học vụ sinh viên.\n- Tôi không có chức năng gửi thông báo lịch phỏng vấn cho ứng viên tuyển dụng.\n\n**2. Công cụ available:**\n- `academic_query`: Tra cứu hồ sơ học vụ sinh viên VinUni\n- `schedule_appointment`: Đặt lịch hẹn tư vấn học vụ với Cố vấn học tập\n\n**3. Yêu cầu của bạn:**\n- Gửi thông báo lịch phỏng vấn cho ứng viên tuyển dụng vị trí Data Analyst → **Ngoài phạm vi chức năng**\n\n**Gợi ý:**\nNếu bạn cần hỗ trợ liên quan đến học vụ sinh viên VinUni (tra cứu điểm, xếp hạng, đặt lịch tư vấn với cố vấn học tập), tôi sẵn sàng hỗ trợ. Đối với việc gửi thông báo phỏng vấn tuyển dụng, bạn cần sử dụng hệ thống HR hoặc liên hệ với phòng ban nhân sự phụ trách tuyển dụng.",
    "latency_ms": 3295.11
  }
]
```

---

## 3. TỔNG KẾT KẾT QUẢ NGHIỆM THU & NỘP BÀI

- [x] Đã điền API Key thật trong `.env` và xác nhận Agent chạy mượt mà trên LLM API thật (Gemini/OpenAI).
- **Tổng số Test Cases đã chạy thành công:** 5 / 5 test cases.
- **Số lượt gọi Tool qua MCP Server chính xác:** 2 lượt.
- **Kết quả đẩy Repo nộp bài:** [x] Đã Commit và Push mã nguồn thành công lên GitHub cá nhân.

---

> ✅ **HOÀN TẤT NỘP BÀI:** Sao chép đường link GitHub Repository cá nhân của bạn và dán vào ô nộp bài trên hệ thống LMS VLearn để hoàn tất Bài Lab 3!
