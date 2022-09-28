# cPanel là gì : 

Để vận hành một website, ta cần các thành phần như: Tên miền, hosting (hoặc server), mã nguồn (source code) + cơ sở dữ liệu (database). Việc kết nối các thành phần đòi hỏi phải có kiến thức chuyên sâu và phức tạp. Để đơn giản hóa việc quản trị cho mọi người, các control panel đã được tạo ra như: Cpanel, Directadmin, Webmin, Plesk, VestaCP,… Trong đó, cPanel là control panel được sử dụng phổ biến nhất hiện nay.

cPanel là web hosting control panel (công cụ quản trị web hosting) trên nền tảng Linux phổ biến nhất hiện nay.

Công cụ quản trị web hosting này có giao diện thân thiện với người dùng và hoạt động trên hệ thống phân cấp ba lớp như sau:

* Hosting Company (Nhà cung cấp dịch vụ Hosting).
* Reseller.
* End User (Người dùng cuối).

# Cài đặt

## Nhận 15 ngày cPanel miễn phí
 Đăng ký tại Link : https://cpanel.net/products/trial/

 ## Cài đặt

* Bước 1 : Update Hệ điều hành Centos 7 và cài đặt một số dịch vụ cần thiết

```
yum update -y
yum install perl
yum install curl
```

* Bước 2 : Cài đặt cPanel, chạy các câu lệnh sau:

```
cd /home
curl -o latest -L https://securedownloads.cpanel.net/latest
sh latest
```

Sau khi quá trình cài đặt hoàn tất, truy cập cPanel theo link `https://[ip]:2087`, trong hình là `https:103.170.122.32:2087`

![1](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/1.png)

Trong trang đăng nhập, nhấn `Login`

![2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/2.png)

Trong giao diện nhấn `Forgot Password` , nhập email đã đăng ký theo link, để lấy pass đăng nhập. Sau khi có mail chứa đường link khôi phục mật khẩu như hình, nhấp vào đường link và nhập mật khẩu mới cho email trên.

![3](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/3.png)

Sau khi lấy mật khẩu, nhập emai và mật khẩu vào trang đăng nhập, ta sẽ đăng nhập và kích hoạt bản quyền 15 ngày trên localhost đồng thời có mail xác nhận thông tin mua hàng gửi về email. 

![4](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/4.png)

![5](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/5.png)

Xác nhận lại lần nữa thông tin server 

![6](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/6.png)

Trong giao diện đăng nhập cPanel, đăng nhập vào hệ thống với acc là acc `root` trên server.

![7](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/7.png)

Trong trang cấu hình tiếp theo, nhấn `Finish` để kết thúc quá trình cài đặt.

![8](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/8.png)

Giao diên chính của cPanel :

![9](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/9.png)