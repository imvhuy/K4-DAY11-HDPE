# Kế hoạch review từ lỗi quan sát được

Từ `findings.csv` và `zone_table.md`, chọn **hai lát cắt của bài ADASIND một camera** cần review trước. Bảng này giải thích dữ liệu thật bạn vừa làm; nó không thay cho kế hoạch bốn camera giả lập ở `45_sampling_plan.csv`.

| Lát cắt / frame | Số ca và loại lỗi | Vì sao review trước | Bằng chứng cần giữ |
|---|---|---|---|
| adasind_236370.jpg & adasind_258420.jpg (Mid zone - Rider/Bike) | 13 ca SPURIOUS (Pedestrian tách khỏi Bike), 2 ca BOX_GEOMETRY | Đây là nhóm lỗi có số lượng lớn nhất trong slice, xuất phát từ sai lệch nhận thức phổ biến khi áp dụng mô hình pre-trained (YOLO COCO); gây sai lệch nghiêm trọng số lượng đối tượng tham gia giao thông. | Ảnh chụp màn hình overlay thể hiện các box Pedestrian trùng khít vị trí người ngồi trên Bike, chỉ số IoU và đối chiếu quy tắc R03. |
| adasind_310008.jpg (Edge zone - Phân loại phương tiện ở rìa) | 2 ca WRONG_CLASS (ThreeWheeler vs Truck/Bus) và DUPLICATE box | Vùng rìa thấu kính fisheye chịu biến dạng cong quang học cực đại khiến thuật toán nhầm lẫn giữa xe ba bánh nhỏ và xe tải trọng lớn, tiềm ẩn nguy cơ an toàn va chạm nghiêm trọng khi xe tự hành đưa ra quyết định chuyển làn. | File XML export, ảnh crop vùng biên quang sai thấu kính, tọa độ bounding box tương ứng. |

**Giới hạn của kết luận từ ba frame ADASIND:** Mẫu quan sát chỉ có 3 frame trên một hướng camera duy nhất trong điều kiện ban ngày tiêu chuẩn, góc nhìn không đổi; chưa đại diện cho các điều kiện môi trường bất lợi (ngược sáng, ban đêm, trời mưa) hay các camera ở góc khác.

## Chuyển sang kế hoạch bốn camera giả lập

- **Cách soát độ phủ của 200 frame ở `45_sampling_plan.csv`:** Phân bổ phủ đều 4 hướng camera (front, rear, left, right) và cân đối 2 mức độ điều kiện (normal vs hard). Để tránh sai số tự tương quan (temporal autocorrelation) do lấy các frame quá sát nhau trong cùng một clip video (khiến nhiều frame liên tiếp chỉ là một tình huống duy nhất nhưng bị đếm thành nhiều ca độc lập), cần áp dụng quy tắc lấy mẫu giãn cách tối thiểu 3 đến 5 giây giữa các frame được chọn, hoặc phân tán lấy mẫu qua nhiều hành trình lái xe độc lập.
- **Vì sao kế hoạch đó chỉ giúp tìm ca cần soi, chưa đo được tỷ lệ lỗi:** Kế hoạch lấy mẫu 200 frame là phương pháp lấy mẫu phân tầng có chủ đích (targeted/stratified sampling), trong đó cố tình gia tăng tỷ trọng các trường hợp khó ("hard slices" như chói sáng, góc khuất, đường hẹp) để tối ưu hóa việc "bắt lỗi" (defect hunting). Do phân phối mẫu không đại diện ngẫu nhiên cho tần suất xuất hiện thực tế trên đường, ta chỉ xác định được các biên lỗi (edge cases) cần can thiệp xử lý, chứ không thể suy rộng thành tỷ lệ lỗi tổng thể (unbiased overall error rate) của mô hình.
