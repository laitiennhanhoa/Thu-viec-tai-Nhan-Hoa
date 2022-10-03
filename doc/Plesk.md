# Giới thiệu về Plesk

Plesk là một Web Hosting Control Panel phổ biết hiện nay. Hỗ trợ trên cả 2 nền tảng hệ điều hành chính hiện nay là Windows và Linux.

# Cài đặt Plesk

## Trên Windows server

Đăng ký dùng thử Plesk trên trang : `https://www.plesk.com/plesk-free-download/`.
Sau khi đăng ký và xác nhận emaiil, từ email đăng ký sẽ nhận được liên kết tải Plesk theo đường dẫn : `https://get.plesk.com/ `

![0](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Plesk/w1.png)

Tại trang download, chọn `Manual installation on Windows and Linux Servers` để tải gói cài đặt tự động của Windows.

![2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Plesk/w2.png)

Sau khi tải xuống thành công, chạy bộ cài đặt, trên công cụ Command Prompt của Windows hiện thông tin truy cập vào Plesk.

![3](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Plesk/w3.png)

Truy cập theo Link, ta đến trang đăng nhập, dùng acc `Administrator` của Windows để đăng nhập.

![4](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Plesk/w4.png)

Chọn `Install or Upgrade Product` để cài đặt :

![5](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Plesk/w5.png)

Chọn version cài đặt 

![5.5](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Plesk/w5.5.png)

Chi tiết các dịch vụ được cài đặt, phụ thuộc vào từng gói cài đặt phía trên. Nhấn Continue để tiếp tục quá trình cài đặt.


![6](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Plesk/w6.png)

![6.5](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Plesk/w6.5.png)

Cấu hình thư mục cài đặt và nơi lưu dữ liệu người dùng, tạo mới Password cho User Admin để quản lý.

![7](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Plesk/w7.png)

Nhấn `Continue`, quá trình cài đặt diễn ra : 

![8](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Plesk/w8.png)



## Cài Plesk trên Linux

Update hệ thống :

```
yum update -y
yum install wget
```

Cài đặt Plesk

```
sh <(curl https://autoinstall.plesk.com/one-click-installer || wget -O – https://autoinstall.plesk.com/one-click-installer)
```
Sau khi trình cài đặt chạy xong sẽ có thông báo thông tin đăng nhập quản trị cho bạn. Bạn đăng nhập với thông tin là SSH của mình.

![c1](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Plesk/c1.png)

Đăng nhập qua link : https://[ip]:8443/
Sau khi nhập các thông tin cần thiết để kích hoạt plesk, hệ thống sẽ bắt đầu khởi tạo, sau khi hoàn tất sẽ hiện ra giao diện quản lý của Plesk.

1[c3](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Plesk/c3.png)

# Hướng dẫn dùng Plesk cơ bản

## Thêm website 

Trong trang quản trị Plesk, chọn mục `Trang web và tên miền` => `Thêm tên miền`

![c4](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Plesk/c4.png)

Nếu đã có tên miền có sẵn, chọn phần `Tên miền đã đăng ký` , nếu chưa có tên miền, chọn `Tên miền tạm thời`, bổ sung thông tin người dùng hệ thống và nhấn `Thêm ten miền`

## Thêm SSL cho website

Trong trang quản trị Website, mục `An ninh` click vào `Chứng nhận SSL/TLS` ,điền thông tin và nhấn `Tạo miễn phí` . 

![c8](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Plesk/c8.png)

Sau khi hệ thống tạo xong có thể kiểm tra lại như hình.

![c9](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Plesk/c9.png)

## Up code, build website lên hosting Plesk 

Chuẩn bị scource và file database, đăng nhập vào Plesk, chọn domain cần up code, chọn `Trình quản lý tập tin và thư mục`=>`Tải lên tập tin`=> chọn file cần tải và tải lên.
![c10](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Plesk/c10.png)
![c11](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Plesk/c11.png)

Thêm database cho website, chọn `Cơ sở dữ liệu` => `Mở trong phpMyAdmin`.

![c12](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Plesk/c12.png)
Trong trang quản trị phpMyAdmin, chọn `Nhập` => `Duyệt máy tính của bạn`, chọn file data và đợi hệ thống import vào.

![c13](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Plesk/c13.png)

Sửa các dòng có giá trị là `siteurl` và `home` bảng wp_options bằng phpMyAdmin

![c14](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Plesk/c14.png)

Xóa hết file trong thư mục `/htttpdoc` sau đó giải nén scource code đã tải lên trước đó vào. Sửa file wp-config.php theo cấu hình database trên host.

![c15](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Plesk/c15.png)

Ngoài ra có thể tùy chỉnh version PHP cho phù hợp nếu sử dụng các bản code wordpress version cũ.

![c16](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Plesk/c16.png)

Sau khi sửa cấu hình, check lại trang web ta có thành quả sau.

![c17](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Plesk/c17.png)
# Tạo email

Tại trang quản trị Plesk, chọn `Mail` => `Create Email Address`, nhập thông tin cho email mới, nhấn ok.

![e1](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Plesk/e1.png)

sau khi tạo xong tài khoản, nhấn biểu tượng email trong hình để vào trang webmail. 

![e2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Plesk/e2.png)

Trong gian diện này có thể gửi nhận email qua mail vừa tạo.

![e3](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Plesk/e3.png)

## Ưu điểm :

 - Dễ dàng sử dụng trên cả hai nền tảng hệ điều hành là Window và Linux.

 - Có độ ổn định và tin cậy cao.

 - Có đầy đủ các tính năng hữu ích từ cơ bản đến nâng cao, hỗ trợ việc quản lý hosting và website.

 - Giao diện đơn giản, thân thiện với người dùng.

 - Tính linh hoạt và tiện dụng cao. Phần mềm Plesk là hệ thống quản lý hosting có tích hợp thiết kế website, thanh toán tự động và giao diện storefront SaaS.

 - Dễ dàng thiết lập nhiều hosting cùng một lúc dễ dàng dựa trên cấu hình định sẵn.

 - Có thể tạo ra nhiều tài khoản FTP kết hợp với cấu trúc web linh hoạt.

## Nhược điểm 

 - Về bảo mật : Plesk được đánh giá không cao về độ bảo mật.

 - Sao lưu và khôi phục : Các tiệp sao lưu và khôi phục của Plesk chiếm khá nhiều tài nguyên, đặc biệt là không gian ổ đĩa.

 - Hệ thống phức tạp : Không có các tool cài đặt hoặc trình hướng dẫn bằng thao tác đơn giản nên gây khó khăn trong vấn đề tiếp cận và vận hành.

