# Cài đặt CentOS 7 trên Vmware ESXi

* Bước 1 : Trong giao diện boot CentOS 7, chọn `Install CentOS 7` , nhân `Enter`

![1](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/bfe2f5f06eaac5afb0b0d1c088d18a64f96abc80/images/CentOS_7/1.png)

* Bước 2 : Chọn ngôn ngữ sử dụng, sau đó chon `Continue`

![2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/bfe2f5f06eaac5afb0b0d1c088d18a64f96abc80/images/CentOS_7/2.png)

* Bước 3 : Chọn múi giờ, nhấn `Done`

![3](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/bfe2f5f06eaac5afb0b0d1c088d18a64f96abc80/images/CentOS_7/3.png)

* Bước 4 : Chia vùng ổ đĩa, chọn cấu hình thủ công như ảnh

![4.1](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/bfe2f5f06eaac5afb0b0d1c088d18a64f96abc80/images/CentOS_7/4.1.png)

![4.2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/bfe2f5f06eaac5afb0b0d1c088d18a64f96abc80/images/CentOS_7/4.2.png)

![4.3](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/bfe2f5f06eaac5afb0b0d1c088d18a64f96abc80/images/CentOS_7/4.3.png)

Chấp nhận thay đổi ổ đĩa

![4.4](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/bfe2f5f06eaac5afb0b0d1c088d18a64f96abc80/images/CentOS_7/4.4.png)

Bước 5 : Tiến hành cài đặt

![5](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/bfe2f5f06eaac5afb0b0d1c088d18a64f96abc80/images/CentOS_7/5.png)

Bước 6 : Cấu hình tài khoản `ROOT` và tạo người dùng khác

__Đặt pass cho acc `root` __ : 

![5.1](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/bfe2f5f06eaac5afb0b0d1c088d18a64f96abc80/images/CentOS_7/5.1.png)

__Tạo acc người dùng khác__ :

![5.2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/bfe2f5f06eaac5afb0b0d1c088d18a64f96abc80/images/CentOS_7/5.2.png)

Bước 7 : Cài đặt xong 

![7](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/bfe2f5f06eaac5afb0b0d1c088d18a64f96abc80/images/CentOS_7/7.png)

Bước 8 : Reboot máy ảo

![8](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/bfe2f5f06eaac5afb0b0d1c088d18a64f96abc80/images/CentOS_7/8.png)

Sau khi reboot xong, hệ thống hiển thị màn hình đăng nhập.

![8.1](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/bfe2f5f06eaac5afb0b0d1c088d18a64f96abc80/images/CentOS_7/8.1.png)

# Đổi password khi quên pass

Nguyên lý hoạt động : Khi bạn quên pass acc `root` cũng là acc có quyền cao nhất trong hệ thống, Linux hay CentOS cung cấp 1 môi trường đặc biệt để đổi pass acc `root` cũng như xử lý cho việc bảo trì hoặc sửa chữa khẩn cấp khi mà máy tính/server không có khả năng hoạt động bình thường. 

Chế độ này gọi là Single User Mode (đôi khi được gọi là Maintenance Mode) , nó là runlevel 1 trong hệ thống SysV init, và runlevel1.target hoặc rescue.target trong systemd. Một số lỗi khác cũng sửa dụng chế độ này để khắc phục là fix file /etc/fstab lỗi, fsck phân vùng ổ đĩa bị hỏng,...

## Các bước thực hiện

* Bước 1 : Khởi động lại CentOS, trong các option tùy chọn của GRUB2 , nhấn `e` để vào cấu hình tùy chỉnh khởi động GRUB2

![9.1](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/CentOS_7/9.1.png)

* Bước 2 : Trong phần cấu hình GRUB2, di chuyển đến đoạn bắt đầu bằng `linux16` (câu lệnh vào chế độ Single User Mode), sửa `ro` -> `rw init=/sysroot` mục đích để thay đổi quyền từ chỉ đọc (ro) sang đọc và ghi (rw) của acc `root` khi truy cập vào `/sysroot` . Sau khi sửa xong, nhấn `Ctrl-X` hoặc __F10__ để khởi động vào chế độ Single User Mode.

![9.2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/CentOS_7/9.2.png)

__Ghi chú__ : `/sysroot` là một folder chứa các file header, thư viện và các file cấu hình cho việc biên dịch chương trình .

* Bước 3 : Thay đổi thư mục gốc thành thư mục `/sysroot` , việc này là bắt buộc vì mỗi câu lệnh bất kỳ nào khi chạy đều cần kết nối đến `/sysroot` (thư viện), thực thi câu lệnh 

```
chroot /sysroot
```

![9.3](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/CentOS_7/9.3.png)

* Bước 4 : Sau khi trỏ lại thư mục gốc, bạn có thể chạy các câu lệnh liên quan đến hệ thống.

__Ví dụ__ : Đổi password acc root (là acc đang truy cập) , chạy lệnh

```
passwd
```

![9.4](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/CentOS_7/9.4.png)

__Lưu ý__ : Dòng thông báo `BAD PASSWORD: The... ` thể hiện password vừa đặt có độ bảo mật kém, dễ bị dò ra với các cuộc tấn công Dictionary Attack.

* Bước 5 : Khi đặt lại mật khẩu cho acc, ta gián tiếp thay đổi thuộc tính của file /etc/passwd (tệp passwd khộng trong chế độ SELinux). Theo mặc định, CentOS / RHEL 7 sử dụng SELinux trong chế độ enforcing nên nếu khởi động lại ngay thì có thể xảy ra sự cố do tệp passwd có các thông số SELINUX security contex khác với thông số ban đàu. Để khắc phục vấn đề này ta chạy lệnh :

```
touch /.autorelabel
```
![9.5](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/CentOS_7/9.5.png)

* Bước 6 : Thoát khỏi môi trường box chroot và môi trường Single User Mode bằng cách gõ 2 lần lệnh `exit` , sau đó reboot lại hệ thống

![9.6](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/CentOS_7/9.6.png)

* Bước 7 : Đăng nhập lại bằng pass vừa đổi 

![9.7](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/CentOS_7/9.7.png)

# Thêm ổ đĩa

# Gỡ ổ đĩa

# Sao lưu và khôi phục
