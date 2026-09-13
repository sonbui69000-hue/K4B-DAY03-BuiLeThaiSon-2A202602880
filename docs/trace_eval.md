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
    "query": "Chào bạn, bạn có thể giới thiệu quy chế học vụ cơ bản của Đại học VinUni không?",
    "action_type": "FINAL_ANSWER",
    "thought": "OpenRouter phản hồi trực tiếp bằng văn bản (không cần gọi công cụ).",
    "output": "Chào bạn! Mình xin chia sẻ về một số đặc điểm chung của quy chế học vụ tại **Đại học VinUni** dựa trên kiến thức hiện có:\n\n---\n\n### 📚 **Tổng quan về Quy chế Học vụ VinUni**\n\n1. **Hệ thống tín chỉ**\n   - VinUni áp dụng **hệ thống đào tạo theo tín chỉ** (credit-based system), tương tự các trường đại học quốc tế.\n   - Mỗi môn học có số tín chỉ nhất định, sinh viên cần tích lũy đủ tín chỉ để tốt nghiệp.\n\n2. **Bậc đào tạo**\n   - **Cử nhân** (Bachelor's): từ 3–4 năm tùy ngành\n   - **Thạc sĩ** (Master's)\n   - **Tiến sĩ** (Doctoral)\n\n3. **Chương trình đào tạo**\n   - Chương trình **trong nước** theo chuẩn Việt Nam, được Bộ Giáo dục và Đào tạo cấp phép.\n   - Chương trình **quốc tế** liên kết với các đại học đối tác danh tiếng như: University of Buckingham (Anh), Đại học Pennsylvania (Mỹ)...\n\n4. **Đánh giá sinh viên**\n   - Sử dụng **thang điểm 4.0 GPA** theo chuẩn quốc tế.\n   - Kết quả học tập được đánh giá qua bài kiểm tra giữa kỳ, cuối kỳ, bài tập và tham gia thảo luận.\n\n5. **Chính sách học tập**\n   - Sinh viên có thể **chuyển đổi ngành** trong một khoảng thời gian nhất định.\n   - Hỗ trợ **học song song**, **đổi chỗ** giữa các chương trình nếu đủ điều kiện.\n\n6. **Cố vấn học tập (Academic Advisor)**\n   - Mỗi sinh viên được phân công một **Cố vấn học tập** để tư vấn về kế hoạch học tập, chọn ngành, và các vấn đề liên quan.\n\n---\n\n### ⚠️ Lưu ý quan trọng\nQuy chế học vụ cụ thể (như điều kiện tốt nghiệp, quy định chuyển ngành, chính sách khen thưởng/kỷ luật, thời hạn lưu trú học tập...) có thể thay đổi theo từng năm học và từng chương trình đào tạo.\n\nĐể có thông tin **chính xác và cập nhật nhất**, bạn nên:\n- Truy cập trang web chính thức: **www.vinu.edu.vn**\n- Liên hệ **Phòng Đào tạo** hoặc **Cố vấn học tập** của VinUni.\n\n---\n\nNếu bạn cần tra cứu **hồ sơ học vụ cá nhân** hoặc **đặt lịch hẹn tư vấn** với Cố vấn học tập, mình có thể hỗ trợ luôn! 😊",
    "latency_ms": 6738.6
  },
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
    "latency_ms": 3030.44
  },
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
