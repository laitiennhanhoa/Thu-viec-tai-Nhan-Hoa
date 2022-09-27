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

__Giai đoạn 1__ : Thay thế file Utilman.exe thành file cmd.exe

* Bước 1 :  Trong giao diện màn hình đăng nhập, nhấn giữ phím `Shift` và chọn `Restart` -> `Restart anyway`

![9.1](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/9cc279141ad5efda26771bc999d24b691e3411ee/images/Win_10/9.1.png)

Bước 2 : Chọn `Use a device`

![9.2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/9cc279141ad5efda26771bc999d24b691e3411ee/images/Win_10/9.2.png)

* Bước 3 : Chọn `EFI VMware Virtual SATA CDROM Drive`

![9.3](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/9cc279141ad5efda26771bc999d24b691e3411ee/images/Win_10/9.3.png)

* Bước 4 : Chọn `Next`

![setup_Win10_3](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/74d05bc9c4ab19c5817c4d907443e798b7c97acc/images/setup_Win10_4.png)

* Bước 5 : Chọn `Repair your computer`

![9.5](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/9cc279141ad5efda26771bc999d24b691e3411ee/images/Win_10/9.5.png)

* Bước 6 : Chọn `Troubleshoot`

![9.6](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/9cc279141ad5efda26771bc999d24b691e3411ee/images/Win_10/9.6.png)

* Bước 7 : Chọn `Command Propt`

![9.7](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/9cc279141ad5efda26771bc999d24b691e3411ee/images/Win_10/9.7.png)

* Bước 8 : Mở phân vùng Windows bằng lệnh 
```
C:
```
Truy cập thư viện Windows :

```
cd windows\system32
```

Đổi tên file  chương trình Utilman nhằm mục đích phục hồi tiện ích sau này :

```
ren utilman.exe utilman.exe.bak
```

Thay thế Utilman bằng Command Prompt

```
copy cmd.exe Utilman.exe
```

![9.8](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/9cc279141ad5efda26771bc999d24b691e3411ee/images/Win_10/9.8.png)

Sau khi chạy xong lệnh trên, ta có kết quả như hình, đóng cửa sổ cmd và chọn `Continue` .

![9.2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/9cc279141ad5efda26771bc999d24b691e3411ee/images/Win_10/9.2.png)

__Giai đoạn 2__ : Đổi password bằng Utilman 

Bước 9 : Sau khi windows hoàn tất khởi động, nhấn phím `Windows Key + U` hoặc biểu tượng bánh xe sẽ vào được Command Prompt với acc có quyền hạn cao nhất (Administrator), vì vậy ta có thể đổi pass hoặc thêm mới/xóa người dùng bằng lệnh `net user` , thêm người dùng vào nhóm Administrators bằng lệnh `net localgroup Administrators` . 

__Ví dụ__ : đổi password acc

```
net user nhanhoa 123abc@A ( nhanhoa là acc người dùng, 123abc@A là password mới )
```

![9.9](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/9cc279141ad5efda26771bc999d24b691e3411ee/images/Win_10/9.9.png)

Sau đó ta đăng nhập bằng pass vừa đổi.


# Thêm ổ đĩa

Thêm 1 ổ đĩa mới khoảng 50GB trên máy ảo VMware với tên là Hard disk 2.

![10.1](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Win_10/10.1.png)

Nhấn `Windows Key + X` , chọn `Disk Management`

![10.2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Win_10/10.2.png)

Trong cửa sổ `Disk Management` , chọn chuẩn phân vùng cho ổ đĩa mới là __GPT__ sau đó chia ổ đĩa bằng cách : Click chuột phải vào `Disk 1` chọn `New Simple Volume...` -> `Next` 

![10.3](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Win_10/10.3.png)

Ở cửa sổ chia ổ đĩa, ta có thể thiết lập dung lượng ổ mới (tối đa = dung lượng trống của ổ đĩa). Sau đó nhấn `Next` -> `Next`.

Rà soát lại kiểu dữ liệu, kích thước khối và tên phân vùng, nhấn `Next` =>`Finish`.

![10.4](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Win_10/10.4.png)

Kiểm tra lại thấy windows đã nhận ổ cứng.

![10.5](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Win_10/10.5.png)
# Gỡ ổ đĩa

# Sao lưu và khôi phục
