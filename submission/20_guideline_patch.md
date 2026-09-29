# Guideline patch

- **Rule mới đề xuất:** R11 — Quy chuẩn chi tiết phân định Rider trên xe hai bánh và nhận diện ThreeWheeler vùng méo rìa (`edge_zone`). 
  1. *Quy tắc Rider (bổ trợ R03):* Khi phương tiện hai bánh đang vận hành hoặc dừng chờ mà người ngồi trên yên xe, box duy nhất là `Bike` bao trọn cả người điều khiển và xe. Không chấp nhận box `Pedestrian` độc lập cho người lái kể cả khi model gợi ý. Chỉ vẽ tách `Pedestrian` khi người hoàn toàn đứng cạnh và dùng tay dắt xe.
  2. *Quy tắc ThreeWheeler ở biên (bổ trợ R04):* Ở vùng `edge_zone = true` chịu biến dạng fisheye nặng (vật bị kéo dài theo phương tiếp tuyến), các loại xe ba bánh thương mại (auto-rickshaw, chở hàng nhỏ) thường bị model nhận diện nhầm thành `Truck`. Nếu quan sát thấy kết cấu tay lái hoặc buồng lái hở/3 bánh, bắt buộc gán nhãn `ThreeWheeler`.
- **Áp dụng cho:** Các class `Bike`, `Pedestrian`, `ThreeWheeler`, `Truck`, và attribute `edge_zone`.
- **Vì sao luật hiện tại (`docs/02-rules-vi.md`) không đủ:** Luật R03 và R04 chưa có ngưỡng phân định hình học cụ thể và chưa có hướng dẫn đối phó với hiện tượng model prefill (như YOLO COCO) tự động tách rider thành pedestrian, khiến annotator dễ bị sai sót đồng loạt (chiếm tới 19 lỗi spurious).
- **`rules_version` mới:** v1.1.0
- **Hiệu lực từ:** Bắt đầu từ round `rework` và áp dụng cho toàn bộ các round gán nhãn tiếp theo.
