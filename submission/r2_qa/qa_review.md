# QA review · B4-edge

Mã khóa: 6458-728F

| frame | object_ref | rule_id | nhận xét |
|---|---|---|---|
| adasind_236370.jpg | L2 | R03 | Box Pedestrian L2 tại (665;727)-(778;1008) trùng rider đang lái Bike L1 — vi phạm quy tắc R03 (người lái và xe hai bánh gộp làm một box Bike duy nhất). |
| adasind_258420.jpg | L5 | R03 | Box Pedestrian L5 tại (128;797)-(157;852) là người ngồi điều khiển xe Bike L3 — vi phạm R03, cần loại bỏ box Pedestrian thừa. |
| adasind_310008.jpg | L7 | R04 | Box Bus L7 trùng tọa độ với Truck L6 tại (253;827)-(364;971) — bị duplicate và nghi vấn sai class theo R04. |

Ghi finding r2_qa: cell=L_only, rule_id có giá trị, why để trống.
