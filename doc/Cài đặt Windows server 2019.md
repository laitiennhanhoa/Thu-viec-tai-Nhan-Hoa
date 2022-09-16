# Cài đặt windows server 2019 trên Vmware ESXi

* Bước 1 : Trong `Windows Setup` ; chọn ngôn ngữ, thời gian và kiểu bàn phím phù hợp, nhấn `Next`.

![1](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/cbf45e543f52287ffbdc6f237228ac2131f4a08a/images/win_server_19/1.png)

* Bước 2 : Nhấn `Install now` để bắt đầu quá trình cài đặt

![2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/ee3cc697bbfd1bf8e1e75f1e6526267a26a0c1a9/images/win_server_19/2.png)

* Bước 3 : Chọn bản windows muốn cài

![3](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/ee3cc697bbfd1bf8e1e75f1e6526267a26a0c1a9/images/win_server_19/3.png)

* Bước 4 : Chấp nhận điều khoản

![4](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/ee3cc697bbfd1bf8e1e75f1e6526267a26a0c1a9/images/win_server_19/4.png)

* Bước 5 : Chọn cách cài windows, chọn Custom

![5](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/win_server_19/5.png)

* Bước 6 : Chia phân vùng, ở đây có 1 ổ đĩa 100GB, sẽ chia làm 2 phân vùng chính bao gồm phân vùng 60GB là ổ C chứa file OS, 40GB ổ D chứa data.
Kết quả như ảnh.
Chia phân vùng ổ C (nơi chứa windows)

![6.1](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/win_server_19/6.1.png)

Kết quả 

![6.2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/win_server_19/6.2.png)

Bước 7 : Tiến hành cài đặt

![7](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/win_server_19/7.png)

Sau khi cài đặt xong, máy sẽ tự reboot và chuyển sang giao diện setup ban đầu. 

Điền các thông tin theo trình tự là hoàn thành việc cài đặt :
 
__Set account Admin__ 

![8.1](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/win_server_19/8.1.png)

Ấn `Finish` và đăng nhập vào hệ thống, đây la giao diện sau khi đăng nhập.

![8.2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/win_server_19/8.2.png)

# Đổi password khi quên pass

Xử lý theo lỗ hổng leo thang đặc quyền từ Utilman như trên Windows 10 : https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/doc/Cài đặt Win10.md

