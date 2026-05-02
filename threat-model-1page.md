# Threat Model - Lab 3

## Thông tin nhóm
- Thành viên 1: Nguyễn Việt Hoàng-1871020253
- Thành viên 2: Mạc Đức Thắng-1871020530

## Assets
- Dữ liệu plaintext của bản tin gửi từ Sender đến Receiver.
- DES key 8 byte và IV 8 byte được truyền cùng packet.
- Header độ dài giúp Receiver xác định kích thước ciphertext.
- Tính toàn vẹn và tính xác thực của gói tin tại Receiver.

## Attacker model
- Attacker có thể giám sát lưu lượng TCP giữa Sender và Receiver trên mạng nội bộ.
- Attacker có thể đọc, chặn và sửa đổi packet trong quá trình truyền.
- Attacker không truy cập trực tiếp vào máy Sender/Receiver, nhưng có thể chiếm đoạt kênh truyền.

## Threats
- Lộ key/IV: do gửi key và IV plaintext trên cùng luồng, attacker có thể dùng lại để giải mã ciphertext.
- Giả mạo packet: attacker sửa header hoặc ciphertext để gây lỗi hoặc thay đổi nội dung.
- Replay attack: packet cũ bị gửi lại khiến Receiver xử lý dữ liệu lặp.
- Padding oracle: nếu hệ thống trả về lỗi chi tiết khi giải mã thất bại, attacker có thể khai thác thông tin.

## Mitigations
- Không truyền key/IV plaintext cùng gói tin; dùng kênh riêng hoặc cơ chế trao đổi khóa an toàn.
- Thêm xác thực gói tin bằng MAC/HMAC hoặc chữ ký để phát hiện sửa đổi.
- Dùng thuật toán hiện đại hơn như AES-GCM thay vì DES-CBC, đồng thời giữ key dài đủ và IV ngẫu nhiên.
- Xử lý lỗi giải mã chung chung và không tiết lộ chi tiết về padding hoặc trạng thái giải mã.

## Residual risks
- DES vẫn là thuật toán yếu với khóa 56 bit, nên ngay cả khi thêm xác thực thì vẫn không đủ an toàn cho thực tế.
- Nếu attacker có quyền truy cập mạng nội bộ, kênh TCP vẫn có thể bị giám sát hoặc sửa đổi nếu không dùng TLS.
- Nếu hệ thống chỉ demo mà không kiểm thử đầy đủ, các lỗi triển khai khác có thể bị bỏ sót và dẫn đến khai thác.   
