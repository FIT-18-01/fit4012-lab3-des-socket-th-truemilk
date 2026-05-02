# Peer Review Response

## Thông tin nhóm
- Thành viên 1: Nguyễn Việt Hoàng-1871020253
- Thành viên 2: Mạc Đức Thắng-1871020530

## Thành viên 1 góp ý cho thành viên 2
Mạc Đức Thắng đã trình bày rõ phần Receiver và giải mã DES-CBC. Tuy nhiên, cần làm rõ hơn trong tài liệu về các bước tách key/IV và xử lý lỗi khi giải mã không hợp lệ.

## Thành viên 2 góp ý cho thành viên 1
Nguyễn Việt Hoàng demo phần Sender tốt, đặc biệt là cách tạo packet và trình diễn gửi key/IV/plaintext. Cần nhấn mạnh thêm trong báo cáo rằng việc gửi key/IV cùng gói tin là lỗ hổng và không an toàn trong thực tế.

## Nhóm đã sửa gì sau góp ý
Nhóm đã cập nhật báo cáo và threat model để làm rõ lỗ hổng bảo mật khi key/IV được truyền plaintext. Chúng tôi cũng bổ sung câu mô tả rõ ràng rằng nhóm chủ yếu thực hiện demo local và phân tích hệ thống thay vì phát triển thêm tính năng mới.
