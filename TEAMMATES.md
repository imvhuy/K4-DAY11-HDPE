# Thành viên và phân vai — Day11 SVM 360 Fisheye

## 1. Thông tin nhóm

- Khóa/lớp: K4
- Tên nhóm: HDPE
- Repo Public: https://github.com/imvhuy/K4-DAY11-HDPE
- Máy giữ hồ sơ chính / người quản lý: Đặng Văn Huy
- Slice chung lấy từ mode.json: B2-center
- Tên định danh vai A dùng cho --self: huy
- Kênh trao đổi nội bộ: Nhóm trao đổi trực tiếp / Zalo
- Đại diện nộp (vai C): Nhữ Đình Chiến (MSSV: 2A202602130)
- Commit chốt bài: [Cập nhật khi hoàn thành P6]

## 2. Ba vai chính

| Vai | Họ và tên | MSSV | Tên định danh trong mode | Trách nhiệm | Bằng chứng đóng góp |
|---|---|---|---|---|---|
| A · Gán nhãn | Đặng Văn Huy | 2A202602270 | huy | Parking/C0/slice, self-QC, lock, rework | Trực tiếp thao tác CVAT, gán nhãn parking, C0, slice B2-center, self-QC và export |
| B · QA độc lập | Khúc Việt Anh | 2A202602088 | anh | Review trước reference, finding QA, kiểm lại ca sửa | Đọc kỹ guideline, review độc lập bản khóa r1_craft, ghi nhận xét qa_review.md |
| C · Chẩn đoán & điều phối | Nhữ Đình Chiến | 2A202602130 | chien | Báo cáo, phân xử, kế hoạch, tích hợp, check và nộp | Chạy báo cáo P4, điều phối phân loại lỗi, lập sampling/gold set plan, kiểm tra và nộp bài |

Bảng này xác định vai của nhóm. Vòng QA tự sinh trong team.json thuộc quy trình nhiều hồ sơ của CLI; nhóm dùng một slice chung và quy trình A → B → C đã nêu trong hướng dẫn.

## 3. Bàn giao theo pha

| Mốc | Người giao → nhận | File / commit / mã khóa | Người nhận đã kiểm gì? | Trạng thái / vướng mắc |
|---|---|---|---|---|
| P0 · Chốt môi trường và vai | C → A, B | mode.json, slice B2-center, phân vai | Môi trường CVAT local 2.75.1, doctor pass, slice chung B2-center | Đã chốt xong bước 1 & môi trường |
| P2 · Khóa bản đầu | A → B, C | [XML, lock.txt, slice B2-center, mã khóa] | [Chờ A bàn giao ở P2] | Chưa đến mốc |
| P3 · Chốt QA mù | B → C, A | [qa_review.md, findings, ảnh] | [Chờ B bàn giao ở P3] | Chưa đến mốc |
| P4 · Quyết định sửa | C → A, B | [findings.csv, decision log] | [Chờ C phân xử ở P4] | Chưa đến mốc |
| P5 · Kiểm bản sửa | A → B → C | [v2, lock2.txt, delta.md] | [Chờ A/B bàn giao ở P5] | Chưa đến mốc |
| P6 · Chốt nộp | A, B → C | [manifest.json, commit chốt] | [Cả nhóm duyệt trước khi nộp] | Chưa đến mốc |

## 4. Bất đồng và phối hợp

- Một ca đã phân xử: [Cập nhật sau pha P4]
- Ca còn mở: Không có
- Đóng góp của A/B/C vào kế hoạch và exit ticket: Cả ba thành viên cùng thảo luận xây dựng phân bổ sampling 200 frame và kế hoạch gold set
- Thay đổi phân công nếu có: Không có

## 5. Xác nhận trước khi nộp

- [ ] A xác nhận nhãn và export đúng phiên bản: Đặng Văn Huy
- [ ] B xác nhận đã QA độc lập trước reference và kiểm lại ca sửa: Khúc Việt Anh
- [ ] C xác nhận báo cáo đúng bản khóa, các file đầy đủ và check exit 0: Nhữ Đình Chiến
- [ ] manifest.json tại commit chốt có failed_gates rỗng.
- [ ] Repo nhóm Public, ảnh và các bằng chứng mở được.
- [ ] C đã push và gửi link repo nhóm + commit qua kênh lớp công bố.

Chỉ đánh dấu việc đã kiểm thật. Nhóm nộp một hồ sơ chung; check không tự chấm đóng góp từng người. Giữ nguyên header/các cột enum của findings.csv; tên người được ghi trong tài liệu này hoặc phần note thích hợp.
