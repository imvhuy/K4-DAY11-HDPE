# Thành viên và phân vai — Day11 SVM 360 Fisheye

## 1. Thông tin nhóm

- Khóa/lớp: K4
- Tên nhóm: HDPE
- Repo Public: https://github.com/imvhuy/K4-DAY11-HDPE
- Máy giữ hồ sơ chính / người quản lý: Đặng Văn Huy (Vai B)
- Slice chung lấy từ mode.json: B4-edge
- Tên định danh vai A dùng cho --self: chien
- Kênh trao đổi nội bộ: Discord / Zalo
- Đại diện nộp (vai C): Khúc Việt Anh, 2A202602088
- Commit chốt bài: [Cập nhật khi hoàn thành P6]

## 2. Ba vai chính

| Vai | Họ và tên | MSSV | Tên định danh trong mode | Trách nhiệm | Bằng chứng đóng góp |
|---|---|---|---|---|---|
| A · Gán nhãn | Nhữ Đình Chiến | 2A202602130 | chien | Parking/C0/slice, self-QC, lock, rework | Commit `c90ae8c`: Tạo task CVAT, hoàn thành 22 vạch parking_line, 3 polygon free_space, hoàn thiện observations.md và sensor_context.md |
| B · QA độc lập | Đặng Văn Huy | 2A202602270 | huy | Review trước reference, finding QA, kiểm lại ca sửa | Đã review độc lập parking annotations & observations của A; rà soát guideline vạch đỗ và fisheye taxonomy |
| C · Chẩn đoán & điều phối | Khúc Việt Anh | 2A202602088 | anh | Báo cáo, phân xử, kế hoạch, tích hợp, check và nộp | Cấu hình mode.json, tổng hợp kế hoạch lấy mẫu 45_sampling_plan.csv 200 frame, điều phối mốc P0 |

## 3. Bàn giao theo pha

| Mốc | Người giao → nhận | File / commit / mã khóa | Người nhận đã kiểm gì? | Trạng thái / vướng mắc |
|---|---|---|---|---|
| P0 · Chốt môi trường và vai | A, C → B, C | Commit `c90ae8c`; mode.json, sensor_context.md, parking/annotations.xml, observations.md | B kiểm tra 22 polyline parking_line và 3 polygon free_space không xuyên xe/curb, observations không còn TODO; C kiểm tra doctor.txt và mode.json | Hoàn thành đạt chuẩn P0 |
| P2 · Khóa bản đầu | A → B, C | [XML, lock.txt, slice, code, commit] | [Chờ A hoàn thành slice B4-edge và lock] | [Đang tiến hành] |
| P3 · Chốt QA mù | B → C, A | [review, findings, ảnh, commit] | [Chờ B thực hiện QA review sau lock P2] | [Chưa bắt đầu] |
| P4 · Quyết định sửa | C → A, B | [finding, decision log, commit] | [Chờ C chạy local-quality và model compare] | [Chưa bắt đầu] |
| P5 · Kiểm bản sửa | A → B → C | [v2, lock2, review kiểm lại, delta] | [Chờ A rework và B kiểm tra lại] | [Chưa bắt đầu] |
| P6 · Chốt nộp | A, B → C | [manifest, commit chốt] | [Chờ duyệt bài toàn diện và check exit 0] | [Chưa bắt đầu] |

## 4. Bất đồng và phối hợp

- Một ca đã phân xử: [Sẽ cập nhật chi tiết ở P4 sau khi đối chiếu kết quả QA và chẩn đoán model]
- Ca còn mở: Không có vướng mắc ở P0; A đã bàn giao đầy đủ dữ liệu vạch ô đỗ và cấu hình cảm biến
- Đóng góp của A/B/C vào kế hoạch và exit ticket: A phụ trách dữ liệu gán nhãn thực địa; B phản biện chất lượng và rà soát lỗi; C tổng hợp kế hoạch phân bổ 200 frame cho 4 camera
- Thay đổi phân công nếu có: Không thay đổi vai; giữ nguyên A (Chiến), B (Huy), C (Việt Anh)

## 5. Xác nhận trước khi nộp

- [ ] A xác nhận nhãn và export đúng phiên bản: Nhữ Đình Chiến
- [ ] B xác nhận đã QA độc lập trước reference và kiểm lại ca sửa: Đặng Văn Huy
- [ ] C xác nhận báo cáo đúng bản khóa, các file đầy đủ và check exit 0: Khúc Việt Anh
- [ ] manifest.json tại commit chốt có failed_gates rỗng.
- [ ] Repo nhóm Public, ảnh và các bằng chứng mở được.
- [ ] C đã push và gửi link repo nhóm + commit qua kênh lớp công bố.
