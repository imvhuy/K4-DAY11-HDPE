# Tự soát

- Slice: B4-edge (3 frame: adasind_236370, adasind_258420, adasind_310008)
- Nguồn nhãn: YOLO26m model predictions + prefill ignore regions + ego_body thủ công
- Cảnh báo: model source thay vì manual CVAT annotation

## Checklist thủ công
- [x] Phạm vi H=40 và vật cần vẽ — đã lọc box có H < 40 px; giữ các box ≥ 40 px
- [x] lens_border và ego_body — lens_border từ prefill (2 polygon/frame); ego_body thêm cho frame có thân xe (trừ adasind_271039 không thuộc slice này)
- [x] Class sáu nhãn — sử dụng 6 class: Bus, Bike, Car, Pedestrian, Truck, ThreeWheeler
- [x] Rider và Bike — cảnh báo: model có thể tách rider thành Pedestrian riêng chồng lấp Bike (đã thấy ở C0 calib); cần kiểm tra thủ công
- [x] Geometry trên ảnh fisheye gốc — box vẽ trên ảnh gốc 1080×1920; edge_zone tự tính dựa trên khoảng cách tới tâm lens
- [x] truncated và occluded — truncated=true khi box chạm mép ảnh (≤2px từ biên); occluded chưa được model đánh giá chính xác (mặc định false)
- [x] Vật thiếu hoặc box trùng — có thể thiếu ThreeWheeler (class hiếm, đã thấy MISSING ở C0); cần review thủ công
- [x] ignore_region có reason — tất cả ignore_region có attribute reason (ego_body hoặc lens_border)
- [x] Tên task raw_fisheye và export CVAT 1.1 — export format CVAT 1.1; tên task cần kiểm lại

## Fill ratio (K12)
chưa vẽ polygon K12 (degrade)

