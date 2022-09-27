Cấu trúc bản ghi trong DNS :

Tạo bản ghi DNS

SOA (Start of Authority) : Cung cấp thông tin quản trị về Zone đó và các bản ghi DNS khác

A : Ánh xạ domain sang địa chỉ Ipv4 / Cung cấp IPv4 của Hosting

AAAA : Ánh xạ domain sang địa chỉ Ipv6 / Cung cấp IPv6 của Hosting 

CNAME : Đặt biệt danh cho host, chuyển hướng một tên miền sang một tên miền khác

NS : hướng người dùng đến các máy chủ DNS khác

SRV : Cho phép người dùng tìm một dịch vụ cụ thể

PTR : Ánh xạ  địa chỉ Ip sang domain / Cung cấp domain của Hosting có IP

SPF : Phương thức xác thực email  gửi đi: 
Tạo bản ghi SPF : 
Điều kiện :
 - v : version của spf
 - a : định danh địa chỉ gửi dạng ipv4 hoặc ipv6
 - ipv4 : địa chỉ ipv4
 - ipv6 :địa chỉ ipv4
 - mx : định danh server gửi mail
 - include : tham khảo thêm chính sách từ domain khác
 - all : tất cả các trường hợp còn lại
Tiền tố 
 * '+' : chỉ các trường hợp đúng với điều kiện, vượt qua xác thực
 * '?' : chỉ các trường hợp không rõ ràng
 * '~' : chỉ các trường hợp không rõ ràng được thông qua nhưng được đánh dấu.
 * '-' : chỉ các trường hợp không xác thực được

DKIM : Xác minh email và kiểm tra tính toàn vẹn của email.
Ý nghĩa phần tiêu đề 
 - DKIM-Signature: Thể hiện tin nhắn, email đã ký DKIM record
 - v= : phiên bản DKIM record đang sửa dụng
 - a= : Thuật toán hàm băm mà mẩu tin sử dụng
 - p= : khóa công khai
TXT

MX : Xác định Host Name cho một Mail Server. 
