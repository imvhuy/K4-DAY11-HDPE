# Quan sát vạch ô đỗ

- Hai vạch `parking_line` đã vẽ (mô tả vị trí trong ảnh): Các vạch sơn phân chia từng ô đỗ ở tiền cảnh (góc dưới bên phải) và dãy ô đỗ ở trung cảnh (khu vực bên trái).
- Một vạch/dấu sơn hoặc biên **không** vẽ, và vì sao: Các vạch sơn quá mờ ở hậu cảnh xa (khu vực gần xe đỏ và hàng rào cây) do độ phân giải thấp/mất nét, cùng các mép đường bao bãi vì không có vai trò chia ô đỗ riêng lẻ.
- Polygon `free_space` dừng ở đâu; có phần bị che nào không: Phủ kín bề mặt mặt đường của lối xe chạy chính ở tiền cảnh và các dải lối đi giữa các dãy ô đỗ; ranh giới dừng sát mép đầu các vạch ô đỗ; không có xe hay vật cản nào che khuất trong vùng đã vẽ.
- Ca chưa chắc cần hỏi người soát (nếu không có, ghi “không có”): không có
