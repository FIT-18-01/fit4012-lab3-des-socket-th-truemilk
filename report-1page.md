# Report 1 page - Lab 3

## Thông tin nhóm
- Thành viên 1: Nguyễn Việt Hoàng-1871020253
- Thành viên 2: Mạc Đức Thắng-1871020530

## Mục tiêu
Bài lab tập trung vào hiểu luồng giao tiếp giữa Sender và Receiver qua TCP socket, cùng với cơ chế mã hoá DES-CBC và padding PKCS#7. Mục tiêu rõ ràng là nắm được cách tạo key/IV, đóng gói packet với header độ dài, và giải mã chính xác ở phía Receiver. Một phần quan trọng là nhận diện hạn chế bảo mật khi gửi key và IV plaintext cùng luồng truyền. Nhóm đã chuẩn bị demo để trình bày hoạt động hệ thống và threat model.

## Phân công thực hiện
- Nguyễn Việt Hoàng: demo phần Sender, giải thích cách tạo packet và gửi dữ liệu mã hoá.
- Mạc Đức Thắng: demo phần Receiver, giải thích cách nhận packet, tách key/IV và giải mã DES-CBC.
- Cả hai cùng phối hợp viết threat model, báo cáo và phản hồi peer review dựa trên nội dung README.

## Cách làm
Nhóm triển khai theo hướng dẫn: Sender nhận input từ bàn phím hoặc biến môi trường `MESSAGE`, sinh DES key 8 byte và IV 8 byte, mã hoá bản tin bằng DES-CBC với padding PKCS#7, rồi gửi tuần tự key + IV + độ dài + ciphertext. Receiver lắng nghe socket, nhận dữ liệu đủ theo header, tách các thành phần và giải mã. Để demo, chúng tôi chạy hai terminal riêng: một cho Receiver, một cho Sender, và kiểm tra đầu ra bản rõ hiển thị đúng.

## Kết quả
Demo local thành công khi Receiver nhận packet và hiển thị lại bản tin gốc sau giải mã. Nhóm trình bày rõ ràng cách gửi key/IV plaintext cùng gói tin, đồng thời chỉ ra lỗ hổng bảo mật này. Vì nhóm chỉ thực hiện demo và phân tích, báo cáo tập trung vào kết quả trình diễn và nhận diện threat model thay vì phát triển thêm feature mới.

## Kết luận
Bài lab giúp nhóm hiểu sâu về mã hoá đối xứng, cơ chế DES-CBC và ý nghĩa của IV, padding, header độ dài. Thực tế demo cho thấy hệ thống này hoạt động về mặt kỹ thuật nhưng không an toàn nếu dùng ngoài môi trường học tập. Nhóm rút ra rằng cần thêm cơ chế xác thực và bảo vệ khóa khi triển khai hệ thống tương tự trong thực tế.
