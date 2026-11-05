# Phòng thí nghiệm Deepfake

Demo deepfake chạy trên trình duyệt, dùng cho bài giảng **an toàn thông tin cho trẻ em**.

## Cách dùng trong lớp

1. **Chụp ảnh "người cần giả dạng"**: bấm *Bật camera*, canh mặt vào khung oval rồi bấm ①. Có thể tải ảnh lên thay cho chụp. AI sẽ đánh dấu 478 điểm trên khuôn mặt.
2. **Quay clip**: cho người khác ngồi vào khung, bấm ② và nói gì đó trong 8 giây.
3. **Tạo deepfake**: chọn kiểu giọng, đánh dấu ô "đã đồng ý", rồi bấm ③. Bản gốc và bản giả hiện cạnh nhau để so sánh.

Sau đó dùng mục **"Làm sao nhận ra video giả?"** ngay trên trang để cả lớp cùng soi các dấu hiệu.

## Cách hoạt động

- **Khuôn mặt**: [MediaPipe Face Landmarker](https://ai.google.dev/edge/mediapipe/solutions/vision/face_landmarker) tìm 478 điểm mốc trên ảnh và trên từng khung hình video. Khuôn mặt trong ảnh được chia thành lưới tam giác và uốn theo mặt trong clip bằng WebGL. Sau đó app khớp màu da và làm mờ viền. Phần trong miệng được để trống, nên miệng thật vẫn cử động khi nói.
- **Giọng nói**: đổi cao độ trên máy bằng thuật toán chồng ghép hạt âm (granular overlap-add). Có các kiểu trầm, cao và robot.
- **Riêng tư**: ảnh, video và âm thanh không rời khỏi máy. Lần đầu mở trang, trình duyệt chỉ tải về thư viện và mô hình AI (khoảng 4 MB).
- Mọi video tạo ra đều có dấu **"DEEPFAKE · VIDEO GIẢ"** và không tắt được.

## Bật GitHub Pages

Vào **Settings → Pages**, phần *Source* chọn **Deploy from a branch**, nhánh `main`, thư mục `/ (root)`, rồi bấm **Save**. Sau khoảng 1 phút, trang chạy tại:

https://bangnl152.github.io/deepfake-demo/

Camera chỉ hoạt động qua `https`, và GitHub Pages đã đáp ứng điều này. Muốn chạy thử trên máy, dùng `npx serve .` rồi mở `http://localhost:3000`.

## Lưu ý cho buổi demo

- Nên dùng Chrome hoặc Edge bản mới trên laptop. Safari vẫn chạy được nhưng viền mặt sẽ sắc hơn.
- Phòng cần đủ sáng, nhìn thẳng vào camera, và tránh quay đầu quá nhanh.
- Đây là bản mô phỏng cho mục đích giáo dục. Các deepfake thật mà kẻ gian dùng còn giống thật hơn nhiều.
