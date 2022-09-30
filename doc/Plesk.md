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
#sh <(curl https://autoinstall.plesk.com/one-click-installer || wget -O – https://autoinstall.plesk.com/one-click-installer)
```


# Hướng dẫn dùng Plesk cơ bản


# Đánh giá

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

