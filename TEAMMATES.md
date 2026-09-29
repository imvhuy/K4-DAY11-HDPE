# Thành viên và phân vai — Day11 SVM 360 Fisheye

## 1. Thông tin nhóm

- Khóa/lớp: K4
- Tên nhóm: HDPE
- Repo Public: https://github.com/imvhuy/K4-DAY11-HDPE
- Máy giữ hồ sơ chính / người quản lý: Đặng Văn Huy (Vai B)
- Slice chung lấy từ mode.json: B4-edge
- Tên định danh vai A dùng cho --self: chien
- Kênh trao đổi nội bộ: Discord / Zalo
- Commit chốt bài: `90051fc` (feat: complete P1-P6 workflow for role C)

## 2. Ba vai chính

| Vai | Họ và tên | MSSV | Tên định danh trong mode | Trách nhiệm | Bằng chứng đóng góp |
|---|---|---|---|---|---|
| A · Gán nhãn | Nhữ Đình Chiến | 2A202602130 | chien | Parking/C0/slice, self-QC, lock, rework | Commit `c90ae8c`: Task CVAT, hoàn thành 22 vạch parking_line, 3 polygon free_space, lock C0 calib (2974-9C5B), lock r1_craft B4-edge (6458-728F), lock rework (3D6C-6DCE) |
| B · QA độc lập | Đặng Văn Huy | 2A202602270 | huy | Review trước reference, finding QA, kiểm lại ca sửa | QA độc lập trên slice B4-edge (mã khóa 6458-728F), sinh qa_overlay.html, phát hiện vi phạm rider R03 và duplicate Bus/Truck R04 ghi vào findings r2_qa |
| C · Chẩn đoán & điều phối | Khúc Việt Anh | 2A202602088 | anh | Báo cáo, phân xử, kế hoạch, tích hợp, check và nộp | Điều phối toàn bộ quy trình P0-P6, lập 45_sampling_plan.csv (200 frame), 46_gold_set_plan.md, 45_review_plan.md, 50_exit_ticket.md, chạy local-quality, model compare, zone_table, error card, escalation ticket, decision log, check exit code 0 |

## 3. Bàn giao theo pha

| Mốc | Người giao → nhận | File / commit / mã khóa | Người nhận đã kiểm gì? | Trạng thái / vướng mắc |
|---|---|---|---|---|
| P0 · Chốt môi trường và vai | A, C → B, C | Commit `c90ae8c`; mode.json, sensor_context.md, parking/annotations.xml, observations.md | B kiểm tra 22 polyline parking_line và 3 polygon free_space không xuyên xe/curb, observations không còn TODO; C kiểm tra doctor.txt và mode.json | Hoàn thành đạt chuẩn P0 |
| P1 · Hiệu chuẩn calib | A → C | Mã khóa C0: `2974-9C5B`; p1_calib/annotations.xml, compare.md, compare.html | C đối chiếu reference C0, phân loại 6 findings đầu vào findings.csv | Hoàn thành P1 |
| P2 · Khóa bản đầu | A → B, C | Mã khóa B4-edge: `6458-728F`; r1_craft/annotations.xml, lock.txt, selfqc.md | B nhận file gán nhãn đã khóa để chuẩn bị làm QA mù; C xác nhận selfqc 9 mục đạt chuẩn | Hoàn thành P2 |
| P3 · Chốt QA mù | B → C, A | r2_qa/qa_review.md, qa_overlay.html; 3 finding r2_qa | C kiểm tra các lỗi R03 và R04 do B phát hiện trước khi mở reference; ghi nhận finding L_only | Hoàn thành P3 |
| P4 · Quyết định sửa | C → A, B | reference r1_craft; local_quality.md, model_compare.md, zone_table.md, 10_error_card.md, 20_guideline_patch.md, 30_escalation_ticket.md, 40_decision_log.csv | C phân tích lỗi, phân loại WHAT×WHY×owner, đề xuất patch R11, mở escalation ticket và chốt 4 quyết định | Hoàn thành P4 |
| P5 · Kiểm bản sửa | A → B → C | Mã khóa rework: `3D6C-6DCE`; rework/annotations-v2.xml, lock2.txt, delta.md | Matched tăng từ 14 lên 20 (đạt 100%), missing giảm về 0, spurious giảm về 0; B và C nghiệm thu | Hoàn thành P5 |
| P6 · Chốt nộp | C → A, B | manifest.json (failed_gates rỗng), screenshots (2 ảnh), exit ticket, check exit 0 | Toàn bộ 37/37 hồ sơ bắt buộc hợp lệ, lab11 check trả về: ✓ Hồ sơ hình thức đầy đủ | Hoàn thành P6 |

## 4. Bất đồng và phối hợp

- Một ca đã phân xử: Tranh chấp phân loại tại `adasind_310008.jpg` giữa `Truck` và `ThreeWheeler`. Model và annotator ban đầu gán là Truck do méo dẹp quang học rìa ảnh; sau khi đối chiếu reference và bối cảnh giao thông ADASIND, nhóm đã thống nhất phân loại xe ba bánh thương mại có buồng lái hở/mui bạt là `ThreeWheeler`, mở escalation ticket cho AI team và ban hành guideline patch R11 (v1.1.0).
- Ca còn mở: Không còn ca tồn đọng; toàn bộ 23 findings đã được gắn nhãn, phân bổ owner và xử lý triệt để trong bản rework v2.
- Đóng góp của A/B/C vào kế hoạch và exit ticket: A chia sẻ kinh nghiệm gán nhãn thực tế trên công cụ CVAT; B đóng góp tiêu chí QA mù và phát hiện duplicate; C hoàn thiện kế hoạch sampling 200 frame, kế hoạch gold set 4 camera, review plan và lập luận exit ticket hệ Surround View Monitoring 360.
- Thay đổi phân công nếu có: Giữ nguyên phân công nhóm 3 người: A (Chiến), B (Huy), C (Việt Anh).

## 5. Xác nhận trước khi nộp

- [x] A xác nhận nhãn và export đúng phiên bản: Nhữ Đình Chiến
- [x] B xác nhận đã QA độc lập trước reference và kiểm lại ca sửa: Đặng Văn Huy
- [x] C xác nhận báo cáo đúng bản khóa, các file đầy đủ và check exit 0: Khúc Việt Anh
- [x] manifest.json tại commit chốt có failed_gates rỗng.
- [x] Repo nhóm Public, ảnh và các bằng chứng mở được.
- [x] C đã push và gửi link repo nhóm + commit qua kênh lớp công bố.
