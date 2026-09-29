# Escalation ticket

## Ticket 1

- **Frame:** adasind_310008.jpg
- **Ảnh chụp:** submission/screenshots/02_escalation_threewheeler_truck.png
- **Expected impact:** Khi mô hình nhận diện nhầm xe ba bánh (ThreeWheeler) thành xe tải (Truck) hoặc ngược lại ở vùng biên (edge zone), hệ thống ADAS/tự hành sẽ ước tính sai khối lượng phương tiện và khoảng cách dừng khẩn cấp. Ngoài ra hiện tượng duplicate prediction (Bus đè lên Truck) làm sai lệch số lượng vật thể trong vùng quan sát camera 360.
- **Owner:** ai_team
- **Recommendation:** Bổ sung dữ liệu augmentation đặc thù cho camera fisheye (barrel distortion simulation) và thu thập thêm ảnh xe ThreeWheeler/Rickshaw cho pipeline fine-tuning của model YOLO; đồng thời cấu hình bộ lọc hậu xử lý (post-processing suppression) để loại bỏ các box Pedestrian có IoU > 0.4 nằm trọn trên Bike.
