# Zone table (slice của bạn)

Lệnh `python3 lab11.py model` tự ghi bảng số (cùng cách đếm với `r1_craft/compare.md` và `model_compare.md`); chạy lại lệnh sẽ cập nhật bảng và giữ nguyên phần nhận xét. Bạn chỉ viết mục Nhận xét.

| Zone | n_ref | L missing | L spurious | M missing (`LR_noM` + `R_only`) | M thừa (`LM_noR` + `M_only`) | Lỗi L chính (`what`) |
|---|---:|---:|---:|---:|---:|---|
| center | 4 | 2 | 2 | 2 | 2 | WRONG_CLASS (2) |
| mid | 9 | 3 | 8 | 3 | 8 | SPURIOUS (5) |
| edge | 7 | 1 | 1 | 1 | 1 | WRONG_CLASS (1) |

## Nhận xét

- **Zone gãy nhiều nhất:** Vùng `mid` zone là nơi cả người (L) và model (M) đều gãy nhiều nhất. Với tổng số 9 vật reference (`n_ref=9`), có tới 3 vật bị missing (`L missing = 3`, `M missing = 3`) và 8 vật bị thừa/spurious (`L spurious = 8`, `M thừa = 8`). Lỗi chính của L là `SPURIOUS` (5 trường hợp), tập trung chủ yếu vào việc tách người điều khiển xe (rider) thành một box `Pedestrian` độc lập đè lên xe máy/xe đạp `Bike`.
- **Giả thuyết nguyên nhân & giới hạn:**
  1. *Nguyên nhân mid zone:* Mật độ giao thông cao ở cự ly trung bình, kết hợp các phương tiện di chuyển đan xen làm thuật toán detection nhầm lẫn người lái là người đi bộ riêng rẽ.
  2. *Nguyên nhân edge/center zone:* Tại `edge` zone, độ méo thấu kính fisheye cực đại làm méo dạng hình học phương tiện dẫn đến nhầm class (`WRONG_CLASS`), ví dụ xe ba bánh (ThreeWheeler) bị méo dài trông giống xe tải nhỏ (Truck).
  3. *Giới hạn slice 3 frame:* Tập dữ liệu 3 frame của slice B4-edge có quy mô rất nhỏ, chỉ phản ánh một đoạn đường ban ngày với góc nhìn camera sau/hông, chưa đại diện cho các điều kiện ban đêm, thời tiết xấu hay các góc đặt camera khác trên xe.
