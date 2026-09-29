# Đối chiếu chất lượng cục bộ — rectangle

Teaching reference, không phải gold set đã phê duyệt; không có điểm đạt tự động.
Nguồn: export r1_craft đã khóa SHA256 `6458728f7f58126f8cd8f05cbe8bd346ff9f8031bc4f7738fc33635017ddbb07`; slice `B4-edge`.
Ghép hình học greedy một-một theo IoU ≥ 0.50, rồi so class; H ≥ 40 px.
Box trái nằm chủ yếu trong ignore_region reference không tính. Polygon, polyline, track không được chấm.
Đây là phép tính offline của lab, không phải báo cáo hay kết quả tương đương CVAT Premium.

Frame được tính: adasind_236370.jpg, adasind_258420.jpg, adasind_310008.jpg. Frame thiếu trong export: không.
TP=14; FP=11; FN=6; số lần đối chiếu=26; mean IoU của TP=0.790.

| Chỉ số | Micro | Macro | Nhãn thấp nhất |
|---|---:|---:|---:|
| accuracy | 0.538 | 0.891 | 0.846 |
| precision | 0.560 | 0.338 | 0.000 |
| recall | 0.700 | 0.542 | 0.000 |
| jaccard | 0.452 | 0.299 | 0.000 |
| dice | 0.622 | 0.395 | 0.000 |

| Nhãn | TP | FP | FN | Accuracy | Precision | Recall | Jaccard | Dice |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| Bike | 3 | 1 | 1 | 0.923 | 0.750 | 0.750 | 0.600 | 0.750 |
| Bus | 0 | 1 | 0 | 0.962 | 0.000 | 0.000 | 0.000 | 0.000 |
| Car | 1 | 2 | 1 | 0.885 | 0.333 | 0.500 | 0.250 | 0.400 |
| Pedestrian | 9 | 4 | 0 | 0.846 | 0.692 | 1.000 | 0.692 | 0.818 |
| ThreeWheeler | 0 | 0 | 4 | 0.846 | 0.000 | 0.000 | 0.000 | 0.000 |
| Truck | 1 | 3 | 0 | 0.885 | 0.250 | 1.000 | 0.250 | 0.400 |

| Frame | TP | FP | FN | Accuracy | Precision | Recall |
|---|---:|---:|---:|---:|---:|---:|
| adasind_236370.jpg | 7 | 1 | 0 | 0.875 | 0.875 | 1.000 |
| adasind_258420.jpg | 3 | 8 | 5 | 0.250 | 0.273 | 0.375 |
| adasind_310008.jpg | 4 | 2 | 1 | 0.667 | 0.667 | 0.800 |

Confusion matrix: hàng = teaching reference; cột = export đã khóa.
`<missing>` là thiếu box; `<extra>` là box thừa. Xem `local_quality_confusion.csv`.

| Reference \ Export | Bike | Bus | Car | Pedestrian | ThreeWheeler | Truck | <missing> |
|---|---:|---:|---:|---:|---:|---:|---:|
| Bike | 3 | 0 | 0 | 1 | 0 | 0 | 0 |
| Bus | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| Car | 0 | 0 | 1 | 0 | 0 | 0 | 1 |
| Pedestrian | 0 | 0 | 0 | 9 | 0 | 0 | 0 |
| ThreeWheeler | 0 | 0 | 1 | 0 | 0 | 3 | 0 |
| Truck | 0 | 0 | 0 | 0 | 0 | 1 | 0 |
| <extra> | 1 | 1 | 1 | 3 | 0 | 0 | 0 |

Chi tiết xung đột trong `local_quality_conflicts.csv`; dữ liệu máy đọc trong `local_quality.json`.
Mismatching label đóng góp một FP cho class vẽ và một FN cho class reference; attribute khác được báo riêng.
Micro accuracy đếm mỗi cặp ghép sai class là một lần đối chiếu; Jaccard đếm cả FP và FN.
Macro/worst bỏ nhãn không xuất hiện ở cả hai phía; chỉ số không có mẫu là N/A.
