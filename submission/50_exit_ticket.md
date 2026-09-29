# Exit ticket

Đọc `docs/10-svm360-reading-vi.md` trước khi trả lời câu 1–2. Các câu về zone, `why`, rework, parking và sampling đã nằm trong file tương ứng nên không hỏi lại ở đây.

1. **Một vật ở vùng seam giữa hai camera thật xuất hiện với hai box khác nhau: đó là lỗi `DUPLICATE` hay cần một quy tắc riêng? Vì sao?**
   - Đây **không phải lỗi `DUPLICATE`**, mà là trường hợp đa góc nhìn hợp lệ cần một **quy tắc riêng (Cross-camera / Multi-view Policy)**.
   - *Lý do:* Hai camera fisheye đặt ở các vị trí khác nhau (ví dụ camera Front và Left) có góc chụp, cự ly và độ méo quang sai khác biệt (vật có thể ở `edge` trên Front nhưng ở `mid` trên Left). Ở tầng 2D object detection độc lập, mỗi camera phải nhận diện đúng phần hiển thị của vật trên mặt phẳng ảnh của camera đó để huấn luyện mô hình perception 2D. Việc gộp chung hai box thành một cá thể duy nhất (object fusion/association) thuộc về tầng Sensor Fusion / 3D BEV dựa trên ma trận ngoại chuẩn calibration và timestamp đồng bộ, chứ annotator không được tùy tiện xóa bỏ một bên coi như duplicate.

2. **Một vật đi qua nhiều frame trên cùng camera: khi nào giữ cùng track ID, khi nào thêm keyframe hoặc trạng thái Outside? Nêu bằng chứng sẽ cần trước khi nối track qua hai camera.**
   - *Giữ cùng track ID:* Khi vật thể liên tục di chuyển trong trường nhìn của camera hoặc chỉ bị che khuất tạm thời rất ngắn (< vài frame) mà quỹ đạo chuyển động có thể nội suy chắc chắn.
   - *Thêm keyframe:* Khi vật thể có sự biến đổi hình học lớn (ví dụ xe rẽ góc, thay đổi góc nhìn từ đầu xe sang thân xe), tiếp cận gần camera khiến kích thước thay đổi nhanh, hoặc điểm bắt đầu/kết thúc che khuất.
   - *Trạng thái Outside:* Khi vật thể di chuyển hoàn toàn vượt ra ngoài vòng kính quang học hoặc biên ảnh và không còn điểm ảnh quan sát được.
   - *Bằng chứng cần trước khi nối track qua hai camera:* (1) Đồng bộ thời gian phần cứng chính xác giữa các camera (hardware timestamp synchronization); (2) Ma trận hiệu chuẩn nội suy/ngoại chuẩn (intrinsic & extrinsic calibration) để chiếu tọa độ hai camera về cùng mặt phẳng hệ tọa độ xe (Vehicle Coordinate Frame); (3) Sự liên tục về vận tốc/hướng di chuyển và độ tương đồng đặc trưng thị giác (re-identification embedding) của vật thể khi cắt ngang qua vùng seam.

3. **Nhìn lại cả buổi: một chỗ bạn tin nhãn mình đúng nhưng reference hoặc người soát nghĩ khác (dẫn frame/`object_ref`), bạn đã xử lý thế nào, và nếu làm lại slice này bạn sẽ đổi gì trong cách làm?**
   - *Tình huống đối chiếu:* Tại frame `adasind_310008.jpg` (`L6/L7`), model và ban đầu tôi nhận diện đối tượng là `Truck` (do thân sau vuông vức như thùng tải nhỏ), trong khi reference xác định là `ThreeWheeler` (xe ba bánh chuyên chở đặc thù tại Ấn Độ).
   - *Cách xử lý:* Tôi đã tra cứu đặc điểm bối cảnh dữ liệu ADASIND, lập mục theo dõi trong `40_decision_log.csv` và `30_escalation_ticket.md` giải thích nguyên nhân méo thấu kính rìa (`E2_guideline_gap` / `E4_model_domain`). Ở pha `rework`, tôi chuẩn hóa lại nhãn theo reference và đề xuất quy tắc nhận diện xe ba bánh trong `20_guideline_patch.md`.
   - *Điểm sẽ thay đổi nếu làm lại:* Tôi sẽ không để kết quả prefill của model YOLO chi phối nhận định, mà sẽ thực hiện rà soát hình học độc lập ngay từ đầu; đặc biệt chú trọng các quy tắc rider (R03) để loại bỏ sớm các box `Pedestrian` thừa đè lên xe máy/xe đạp trước khi khóa nhãn bản draft.
