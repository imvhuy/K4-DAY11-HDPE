# Phân công trách nhiệm nhóm (TEAMMATES)

Bài thực hành Day 11 — SVM/360 Fisheye Lab

---

## 1. Thông tin thành viên & Phân vai

| Ký hiệu vai | Họ và tên | Mã học viên | Vai trò trong đợt làm | Trách nhiệm chính | Đầu ra phải bàn giao | Người kiểm tra đầu ra |
|---|---|---|---|---|---|---|
| **Vai A** | **Nhữ Đình Chiến** | **2A202602130** | Gán nhãn (Annotator) | Tạo task CVAT, vẽ parking / C0 / slice được giao, thực hiện self-QC, export, lock và rework | XML + mã khóa; self-QC; ghi chú parking; finding `r1_craft`; nhãn v2 | **B** soát nhãn; **C** kiểm đúng phiên bản |
| **Vai B** | **Đặng Văn Huy** | **2A202602270** | QA độc lập (QA Reviewer) | Review bản đã khóa của A dựa trên ảnh và guideline, không xem reference/model trước | `r2_qa/qa_review.md`, overlay HTML, finding `r2_qa`, ảnh chụp bằng chứng | **C** kiểm đủ frame/object/rule; **A** phản hồi sau khi B chốt QA |
| **Vai C** *(Đại diện nộp bài)* | **Khúc Việt Anh** | **2A202602088** | Chẩn đoán & Điều phối (Diagnostician & Coordinator) | Quản lý bản hồ sơ chung, theo dõi mốc thời gian, chạy báo cáo sau QA, phân xử, lập hồ sơ và đại diện nộp bài | Báo cáo `r3_diag`, finding `r3_diag`, delta, kế hoạch (sampling/gold set), decision log, manifest | **A** và **B** đối chiếu quyết định với ảnh và ký xác nhận đóng góp |

---

## 2. Quy trình phối hợp và nguyên tắc bàn giao

1. **Giữ vai cố định trong suốt lượt làm:**
   - Vai A, B, C được giữ nguyên trong suốt chu trình thực hiện để đảm bảo tính khách quan và độc lập (B review độc lập không phụ thuộc vào người vẽ A).
   - Nếu nhóm luân phiên vai để học tập, việc đổi vai sẽ thực hiện ở lượt/slice tiếp theo sau khi đã hoàn tất và chốt hồ sơ của lượt này.

2. **Nguyên tắc QA mù:**
   - Người làm vai B tuyệt đối không mở teaching reference hoặc model overlay trước khi hoàn thành và chốt xong biên bản QA độc lập.

3. **Điều phối & Bàn giao:**
   - Người làm vai C hỗ trợ kỹ thuật, giám sát các mốc thời gian (P0–P6), tổng hợp hồ sơ trong thư mục `submission/`, đảm bảo lệnh `python lab11.py check` đạt exit 0 trước khi nộp repo.
