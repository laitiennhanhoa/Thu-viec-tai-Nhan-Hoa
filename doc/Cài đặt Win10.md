# Cài đặt win 10 trên Vmware ESXi

* Bước 1 : Trong `Windows Setup` ; chọn ngôn ngữ, thời gian và kiểu bàn phím phù hợp, nhấn `Next`.

![setup_Win10_3](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/74d05bc9c4ab19c5817c4d907443e798b7c97acc/images/setup_Win10_4.png)

* Bước 2 : Nhấn `Install now` để bắt đầu quá trình cài đặt

![1](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/bfe2f5f06eaac5afb0b0d1c088d18a64f96abc80/images/Win_10/1.png)

* Bước 3 : Nhập product key, không có key có thể bỏ qua

![2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/bfe2f5f06eaac5afb0b0d1c088d18a64f96abc80/images/Win_10/2.png)

* Bước 4 : Chọn bản windows muốn cài

![3](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/bfe2f5f06eaac5afb0b0d1c088d18a64f96abc80/images/Win_10/3.png)

* Bước 5 : Chấp nhận điều khoản

![5](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/bfe2f5f06eaac5afb0b0d1c088d18a64f96abc80/images/Win_10/5.png)

* Bước 6 : Chọn cách cài windows, chọn Custom

![6](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/bfe2f5f06eaac5afb0b0d1c088d18a64f96abc80/images/Win_10/6.png)

* Bước 7 : Chia phân vùng, ở đây có 1 ổ đĩa 100GB, sẽ chia làm 2 phân vùng chính bao gồm phân vùng 50GB là ổ C chứa file OS, 50GB ổ D chứa data.
Kết quả như ảnh.

![7](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/bfe2f5f06eaac5afb0b0d1c088d18a64f96abc80/images/Win_10/7.png)

Bước 8 : Tiến hành cài đặt

![8](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/bfe2f5f06eaac5afb0b0d1c088d18a64f96abc80/images/Win_10/8.png)



Sau khi cài đặt xong, máy sẽ tự reboot và chuyển sang giao diện setup ban đầu. 

![8.1](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/bfe2f5f06eaac5afb0b0d1c088d18a64f96abc80/images/Win_10/8.1.png)

Sau khi tạo và đăng nhập tài khoản thì ta đã cài xong windows 10.

![8.2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/bfe2f5f06eaac5afb0b0d1c088d18a64f96abc80/images/Win_10/8.2.png)


# Đổi password khi quên pass

Khi quên pass đăng nhập vào windows 10, để xử lý, ta tận dụng lỗ hổng của Utilman.exe trên windows. 
Nguyên lý thực hiện : Utilman là một ứng dụng trên windows được thiết kế để người dùng có thể tùy chỉnh các trợ năng hỗ trợ người khuyết tật (người khiếm thị, khiếm thính hoặc hạn chế về khả năng vận động) có thể tự đăng nhập vào windows mà không cần sự trợ giúp từ bên ngoài. Nhưng đây là một lỗ hổng bảo mật có thể khai thác được để vượt qua yêu cầu đăng nhập của Windows.

__Utilman có thể khởi chạy ngay cả khi người dùng chưa đăng nhập vào windows bằng cách nhấn phím `Windows Key + U` hoặc biểu tượng bánh xe, bằng cách này, nếu chúng ta hoán đổi Utilman.exe với file thực thi khác như cmd.exe thì chúng ta có quyền truy cập công cụ dòng lệnh của windows với tài khoản có đặc quyền cao nhất (tương tự user `root` trên Linux).__

Các bước thực hiện :

__Giai đoạn 1 : Thay thế file Utilman.exe (trên ổ C của Windows) bằng file cmd.exe (trên usb boot windows)

* Bước 1 :  Trong giao diện màn hình đăng nhập, nhấn giữ phím `Shift` và chọn `Restart` -> `Restart anyway`

![9.1]()

Bước 2 : Chọn `Use a device`

![9.2]()

* Bước 3 : Chọn `Next`

![9.3]()

* Bước 4 : Chọn `Next`

![setup_Win10_3](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/74d05bc9c4ab19c5817c4d907443e798b7c97acc/images/setup_Win10_4.png)

* Bước 5 : Chọn `Repair your computer`

![9.5]()

* Bước 6 : Chọn `Troubleshoot`

![9.6]()

* Bước 7 : Chọn `Command Propt`

![9.7]()


# Thêm ổ đĩa

# Gỡ ổ đĩa

# Sao lưu và khôi phục
