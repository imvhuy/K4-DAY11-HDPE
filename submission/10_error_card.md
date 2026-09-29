# Error analysis card

## Zone × block

| zone | block | what | count |
|---|---|---|---:|
| center | B4 | MISSING | 2 |
| center | B4 | SPURIOUS | 2 |
| center | B4 | WRONG_CLASS | 2 |
| center | C0 | MISSING | 1 |
| center | C0 | SPURIOUS | 3 |
| edge | B4 | IGNORE_SCOPE | 3 |
| edge | B4 | MISSING | 1 |
| edge | B4 | SPURIOUS | 1 |
| edge | B4 | WRONG_CLASS | 1 |
| edge | C0 | WRONG_CLASS | 1 |
| mid | B4 | BOX_GEOMETRY | 2 |
| mid | B4 | MISSING | 3 |
| mid | B4 | SPURIOUS | 13 |
| mid | B4 | WRONG_CLASS | 1 |
| mid | C0 | WRONG_CLASS | 1 |

## Top defects
- SPURIOUS: 19 (ví dụ frame adasind_019560.jpg)
- MISSING: 7 (ví dụ frame adasind_019560.jpg)
- WRONG_CLASS: 6 (ví dụ frame adasind_019560.jpg)

## Phân tích của bạn

- **Nguyên nhân khả dĩ (`why`) và vì sao bạn nghĩ vậy:** Lỗi nổi bật nhất là `SPURIOUS` (19 lỗi, tập trung ở `mid` zone B4 và `center` C0), điển hình là frame `adasind_236370.jpg` (`L2`), `adasind_258420.jpg` (`L5`), `adasind_019560.jpg` (`L2`). Nguyên nhân là `E4_model_domain` kết hợp `E1_annotator_error`: Model YOLO (huấn luyện trên tập COCO chuẩn) luôn phát hiện người lái (rider) thành một box `Pedestrian` tách biệt nằm đè lên `Bike`. Người gán nhãn khi dùng prefill hoặc tham chiếu model đã không kiểm tra kỹ quy tắc R03 dẫn đến giữ lại box người đi bộ thừa.
- **Cách sửa và ai nhận việc (`owner`):** 
  - `owner: annotator`: Thực hiện rà soát thủ công hoặc script lọc (nếu IoU giữa Pedestrian và Bike > 0.4 mà chân người gác trên xe thì gộp/xóa Pedestrian).
  - `owner: guideline`: Bổ sung hình ảnh ví dụ cụ thể về rider trên xe máy/xe đạp ở góc nhìn fisheye vào tài liệu quy chuẩn hướng dẫn (R03).
- **Bằng chứng (ảnh trong `screenshots/`, dòng findings, rule):** 
  - Ảnh minh chứng: `screenshots/01_cvat_rider_spurious.png` hiển thị box Pedestrian L2 trùng vị trí Bike L1 trên frame `adasind_236370.jpg`.
  - Dòng findings: `r1_craft,B4-edge,adasind_236370.jpg,L2` và `calib,C0,adasind_019560.jpg,L2`.
  - Quy chuẩn vi phạm: Luật R03 (Rider: người lái + xe hai bánh = một box Bike duy nhất).
