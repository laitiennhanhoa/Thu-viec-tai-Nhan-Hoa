# Yêu cầu
https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/Share/1.jpg
 Cài đặt Cloudlinux 7
 2 ổ OS cài raid1 :240Gb Samsung
 2 ổ home cũng cài raid 1 : 960Gb Samsung
 1 ổ backup sau mount vào backup sau : 1.2Tb
 # Cài Raid
 - chọn f2
 vào device settings
 Chọn RAID Controller
 ## Clear raid
 Chọn Configuration Management
 Chọn Clear Configuration
 Tick vào Confirm => Yes => Ok
 Tương tự với Foreign Configuration

 ## Cài Raid

  Chọn Configuration Management
  Chọn Create Virtual Disk
  Trong mục Select RAID Level chọn Raid 1, chọn Select Phyzical Disks, Chọn thẻ SSD và chọn 2 ổ dung lượng nhỏ hơn.
  Đặt tên cho RAID và nhấn Create Virtual Disk
  Chọn Confirm và Yes
  Tương tự cho Home
  Kiểm tra lại các RAID đã cấu hình, vào Virtual Disk Managenent, kiểm tra các thông tin trên từng RAID
  Nhấn Back và reboot lại server để vào phần cài đặt CloudLinux
# Cài OS

Chọn Install Cloudlinux7.9
