# Cài đặt Ubuntu 22.4 trên Vmware ESXi

* Bước 1 : Khởi động máy ảo, trong tùy chọn của GRUBv2 chọn `Try or Install Ubuntu`

![1](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Ubuntu/1.png)

* Bước 2 : Chọn `Install Ubuntu`

![2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Ubuntu/2.png)

* Bước 3 : Chọn kiểu bản phím, nhấn `Continue`

![3](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Ubuntu/3.png)

* Bước 4 : Chọn `Continue`

![4](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Ubuntu/4.png)

* Bước 5 : Chọn `Something else` ->`Continue`

![5](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Ubuntu/5.png)

* Bước 6 :Chia phân vùng ổ đĩa đã cấp, ta chọn `New Partition Table...` ->`Continue` , ở đây có 1 không gian trống đã được tạo.

![6](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Ubuntu/6.png)

* Bước 7 : Chia phân vùng trống, ta chọn vào `free space`sẽ hiện 1 cửa sổ để tùy chỉnh phân vùng mới, trong đó :

__Size__ : Kích thước phân vùng mới, tính bằng MB.

__Type for the new partition__ : Loại phân vùng, có 2 tùy chọn là `Primary` và `Logical`.

__Location for the new partition__ : Nơi bắt đầu của phân vùng, có 2 tùy chọn là `Beginning of this space` (Đầu phân vùng) và `End of this space` (cuối phân vùng).

__Use as__ : kiểu định dạng của phân vùng, ta có thể chọc các kiểu định dạng dữ liệu mà Linux hỗ trợ.

__Mount point__ : Kết nối phân vùng vừa tạo với thư mục trong hệ thống

Sau khi phân vùng xong, ta nhấn `Install Now`

![7](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Ubuntu/7.png)

* Bước 8 : Chọn múi giờ 

![8](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Ubuntu/8.png)

* Bước 9 : Điền thông tin hệ thống 

![9](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Ubuntu/9.jpg)

* Bước 10 : Tiến hành cài đặt

![10](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Ubuntu/10.jpg)

* Bước 11 : Cài đặt xong, restart máy và đăng nhập

![11](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Ubuntu/11.png)

#  Đổi password khi quên pass

Khi quên mật khẩu acc `root` , Linux/Ubuntu cung cấp 1 chế độ khẩn khấp để khôi phục mật khẩu này. Các bước thực hiện như sau "

* Bước 1 : Khởi động lại mấy, nhấn `Esc` hoặc `Shift` để vào giao diện GNU GRUB

![12.1](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Ubuntu/12.1.png)

* Bước 2 : Nhấn `e` để vào cấu hình GRUB

![12.2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Ubuntu/12.2.png)

* Bước 3 : Tìm dòng bắt đầu bằng `linux` , sửa đoạn mã `ro quiet splash $vt_handoff` -> `rw init=/bin/bash`.  Mục đích là thiết lập lại hệ thống tệp gốc với quyền đọc và ghi được ký hiệu bằng rw.

![12.3](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Ubuntu/12.3.png)

* Bước 4 : Nhấn `Ctrl + x` hoặc `F10` để boot lại hệ thống. Trong giao diện dòng lệnh được đăng nhập sẵn acc `root`, kiểm tra lại quyền đọc ghi với hệ thống tệp gốc bằng câu lệnh 
```
mount| grep -w /
```
![12.4](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Ubuntu/12.4.png)

Ta thấy đã có quyền đọc ghi với phân vùng /dev/sda2

* Bước 5 : Đổi password bằng lệnh `passwd`

![12.5](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Ubuntu/12.5.png)

* Bước 6 : Khởi động lại Ubuntu, dùng lệnh `reboot -f`

