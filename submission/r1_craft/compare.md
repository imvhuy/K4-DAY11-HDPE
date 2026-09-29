# So sánh L với R

Chỉ số L/R là thứ tự box cao ≥ H=40 trong từng frame, theo thứ tự XML; bắt đầu từ 1.
Box L trong ignore_region được báo IGNORE_SCOPE, không tính SPURIOUS.

## adasind_236370.jpg
- L9 edge IGNORE_SCOPE
- L2 mid SPURIOUS
## adasind_258420.jpg
- L1 edge IGNORE_SCOPE
- L3+R3 mid BOX_GEOMETRY
- L4+R1 edge WRONG_CLASS
- L5 mid SPURIOUS
- L6+R5 mid BOX_GEOMETRY
- L7 mid SPURIOUS
- L8+R4 center WRONG_CLASS
- L10 mid SPURIOUS
- L11+R8 center WRONG_CLASS
## adasind_310008.jpg
- L5 edge IGNORE_SCOPE
- L6+R1 mid WRONG_CLASS
- L7 mid SPURIOUS

## Theo zone
| zone | n_ref | matched | missing | spurious |
|---|---|---|---|---|
| center | 4 | 2 | 2 | 2 |
| mid | 9 | 6 | 3 | 8 |
| edge | 7 | 6 | 1 | 1 |
