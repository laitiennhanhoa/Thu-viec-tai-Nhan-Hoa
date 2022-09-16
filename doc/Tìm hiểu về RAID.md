# Định nghĩa

RAID là viết tắt của Redundant Array of Inexpensive Disks (Hệ thống đĩa dự phòng). Đây là hệ thống hoạt động bằng cách kết nối một dãy các ổ cứng có chi phí thấp lại với nhau để hình thành một thiết bị lưu trữ đơn có dung lượng lớn nhằm tăng hiệu quả hệ thống và phương án sao lưu dự phòng.

# Phân loại

## Software RAID 

Hay còn được gọi là `RAID mềm`, thường là các phần mềm được cài đặt trên các hệ điều hành, có hiệu suất thấp do sử dụng nguồn tài nguyên từ máy chủ, nó cần tải để đọc dữ liệu từ software RAID volumes.

![1](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/RAID/1.png)

Ưu điểm : 

* Chi phí thấp: Không phải tốn thêm tiền cho chức năng RAID, do nó đã được tích hợp vào HĐH. Khoản phí duy nhất đó là trang bị thêm ổ đĩa.

* Dễ triển khai : Do RAID hoạt động như một phần mềm trên OS nên khi triển khai chỉ cần cài đặt trên OS là được.

Nhược điểm :

* Tăng tải trên hệ thống máy chủ

* Phụ thuộc vào OS : bất kỳ thay đổi nào của OS cũng có thể ảnh hưởng đến tính toàn vẹn của hệ thống RAID (nâng cấp OS có thể gây lỗi RAID)

* Dễ nhiêm virus/ransomware : Do RAID chạy như 1 tính năng/ phần mềm trên OS nên nếu máy tính nhiễm virus hoặc các phần mềm nguy hại khác đều có thể tác động đến chức năng RAID.

* Tính toàn vẹ dữ liệu không được đảm bảo : Các vấn đề phần mềm và phần cứng trên server đều có thể ảnh hươngr đến tính nhất quán và toàn vẹn dữ liệu.

* Dữ liệu không được bảo vệ khi boot

* không hỗ trợ nhiều cấp độ RAID và tính năng mở rộng

Một số Software RAID hiện nay :

> Windows : Storage Space

> Linux : mdadm

## Hardware RAID

Hay còn gọi là `RAID cứng` , đây là một bộ điều khiển (controller) RAID chuyên dụng được xây dựng về mặt vật lý bằng cách sử dụng thẻ PCI express, có NVRAM cho bộ nhớ cache để đọc và viết. Lưu trữ bộ đệm để xây dựng lại ngay cả khi mất điện, nó sẽ lưu trữ bộ đệm bằng các bản sao lưu sử dụng năng lượng pin.

![2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/RAID/2.png)

Ưu điểm : 

* Hiệu năng được nâng cao do có bộ nhớ độc lập, tốc độ truy xuất cao hơn do không phải chia sẻ tài nguyên.

* Có cơ chế an toàn khi boot

* Không dễ nhiễm virus/ransomware : do RAID chạy độc lập với OS và host.

* Đảm bảo tính toàn vẹn dữ liệu 

* Hỗ trợ nhiều cấp độ RAID, có tính năng mở rộng : Do có phần mềm chuyên biệt riêng nên hỗ trợ được nhiều tính năng hơn như : thay nhanh ổ đĩa, mở rộng dung lượng trực tuyến,...

Nhược điểm : 

* Chi phí triển khai cao

Một số loại Hardware RAID hiện nay :

> LSI MegaRAID

> Dell PERC H730P RAID Controller Adapter

# Các cấp độ RAID (RAID levels) [](https://dzone.com/articles/what-is-raid-in-linux#:~:text=Working%20of%20RAID%20in%20Linux,of%20the%20disks%20may%20vary.)

## RAID 0 

