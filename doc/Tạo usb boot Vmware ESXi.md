# Tạo usb boot Vmware ESXi

Tải bản iso trên [trang chủ Vmware](https://customerconnect.vmware.com/en/downloads/info/slug/datacenter_cloud_infrastructure/vmware_vsphere/7_0)

Sau khi tải, cài vmware vào server, ta dùng rufus ver 3.20 để tạo usb boot. Khởi chạy rufus với quyền admin.
Chọn usb ta đã chuẩn bị, chọn file iso vừa tải về theo link trên. Nhấn `START`

![rufus_vmware](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/fb98152022cf6255545cc4175d318496533f5700/images/rufus_vmware.png)

Sau khi rufus chạy xong, ta đã có usb boot cài Vmware ESXi

![rufus_vmware](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/fb98152022cf6255545cc4175d318496533f5700/images/rufus_vmwar12.png)

# Tiến hành cài Vmware ESXi

## Cấu hình RAID 0

Cắm usb boot vừa tạo vào máy chủ.

Khởi động máy chủ, đối với máy chủ Dell có iDRAC ,cấu hình iDRAC xong có thể truy cập từ xa.
Sau khi khởi động máy chủ, nhấn `Ctrl + R` để vào giao diên `RAID Controller`

![config_raid](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/fb98152022cf6255545cc4175d318496533f5700/images/raid_conffig.png)

Trong giao diện `RAID Controller`, mục `VD Mgmt` chọn `Vỉtual Disks`.Nhấn F2 và chọn `Delete VD` -> `Yes` để xóa cấu hình RAID trước đó.

![clear_raid](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/fb98152022cf6255545cc4175d318496533f5700/images/clear_raid.png)

Sau khi xóa cấu hình Raid trước đó , trong hệ thống hiển thị 2 ổ cứng đã cắm vào server từ trước.

![no_raid](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/fb98152022cf6255545cc4175d318496533f5700/images/no_raid.png)

Nhấn F2 và chọn `Create new VD`, trong giao diện cấu hình RAID, chọn kiểu RAID-0 và thêm các ổ đĩa có sẵn vào, đặt tên cho RAID mới tạo.

![setup_raid](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/fb98152022cf6255545cc4175d318496533f5700/images/setup_raid.png)

Kiểm tra lại Raid đã tạo

![info_raid](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/fb98152022cf6255545cc4175d318496533f5700/images/info_raid.png)

Để lưu cấu hình raid vừa tạo, ta nhấn F2 chọn `Initialization` -> `Fast Init`

![save_raid](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/fb98152022cf6255545cc4175d318496533f5700/images/save_raid.png)

Khởi động lại máy chủ

## Cài đặt VMware ESXi

Sau khi khởi động lại máy chủ, nhấn F11 để vào `Boot Manager`

Chọn `BIOS Boot Menu` để chọn chế độ boot

![boot_nemu](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/fb98152022cf6255545cc4175d318496533f5700/images/boot_menu.png)

Trong `Boot Menu`, chọn `Hard drive C :` -> `Front USB: USB Flash Drive` là USB đã tạo file boot ở trên

![usb_boot](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/fb98152022cf6255545cc4175d318496533f5700/images/usb_boot.png)

Trong giao diện boot usb, chọn install VMware ESXi-7

![install_vmware0]([images\install_vmware.png](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/fb98152022cf6255545cc4175d318496533f5700/images/install_vmware0.png))

* Chọn phân vùng 

![install_vmware](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/fb98152022cf6255545cc4175d318496533f5700/images/install_vmware.png)


* Chọn bàn phím

![install_vmware2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/fb98152022cf6255545cc4175d318496533f5700/images/install_vmware2.png)

* Xác nhận cài đặt, nhấn F11

![install_vmware4](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/fb98152022cf6255545cc4175d318496533f5700/images/install_vmware4.png)

* Sau khi cài đặt xong, hệ thống yêu càu reboot lại, nhấn `Enter`

![install_vmware5](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/fb98152022cf6255545cc4175d318496533f5700/images/install_vmware5.png)

Sau khi hệ thống restart lần đầu thành công. Hệ thống hiển thị thông tin server như sau :

![start_vmware](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/fb98152022cf6255545cc4175d318496533f5700/images/start_vmware.png)

## Cấu hình VMWare 

* Nhấn F2 và đăng nhập vào hệ thống :

![login_config_vmware](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/fb98152022cf6255545cc4175d318496533f5700/images/login_config_vmware.png)

* Sau khi đăng nhập, chọn `Configure Management Network` để cấu hình network cho server VMWare

![ipconfig_vmware](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/fb98152022cf6255545cc4175d318496533f5700/images/ipconfig_vmware.png)

* Chọn tiếp `IPv4 Configuration` nhấn Enter

![ipconfig_vmware2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/fb98152022cf6255545cc4175d318496533f5700/images/ipconfig_vmware2.png)

* Cấu hình IP phù hợp với mạng thực tế, sau đó nhấn Enter để lưu cấu hình

![ipconfig_vmware3](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/fb98152022cf6255545cc4175d318496533f5700/images/ipconfig_vmware3.png)

* Cấu hình DNS: Chọn `DNS Configuration`, nhấn Enter. Cấu hình DNS để DNS của google (như hình), sau đó nhấn Enter để lưu.

![DNS_config_vmware](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/fb98152022cf6255545cc4175d318496533f5700/images/DNS_config_vmware.png)

![DNS_config_vmware2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/fb98152022cf6255545cc4175d318496533f5700/images/DNS_config_vmware2.png)

* Sau khi cấu hình xong DNS, nhấn Esc để thoát, khi đó hệ thống sẽ hỏi lưu lại cấu hình không, chọn Y

![save_config_vmware](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/fb98152022cf6255545cc4175d318496533f5700/images/save_config_vmware.png)

Sau khi cấu hình xong network cho server VMware, nhấn F12 -> F11 để reload lại server.

![reload_vmware](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/fb98152022cf6255545cc4175d318496533f5700/images/reload_vmware.png)

## Đăng nhập VMware ESXi 7.0 trên trình duyệt

Sau khi khởi động lại server VMware,trên giao diện máy chủ hiện thị các thông tin như sau :

![page_main_vmware](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/fb98152022cf6255545cc4175d318496533f5700/images/page_main_vmware.png)

trong đó có link url : https://172.16.3.139 (ip cấu hình cho host VMware).Nhập url trên vào trình duyệt, ta đến trang ligin của VMware :

![login_vmware](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/fb98152022cf6255545cc4175d318496533f5700/images/login_vmware.png)

Sau khi đăng nhập, ta truy cập được trang quản trị server VMware.

![mai_vmware](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/fb98152022cf6255545cc4175d318496533f5700/images/mai_vmware.png)

# Tạo máy ảo trên VMware ESXi 7.0

## Tạo thư mục lưu trữ file ISO

* Bước 1 : Chọn Storage, chọn mục `Datastore browser` -> `Create directory`

![Create_directory](images\Create_directory.png)

Nhập tên foder xong nhấn `Create directory`.

* Bước 2 : Trong thư mục vừa tạo nhấn `Upload` , chọn file đuôi .iso để đẩy lên server.

![Upload_ISO](\images\Upload_ISO.png)

* Bước 3 : Tạo máy ảo

### Tạo máy ảo trên trình duyệt

 * Bước 1 : Trong mục `Virtual Machines` , chọn mục `Create / Register VM` 
 * Bước 2 : Trong trang tạo máy ảo mới, nhấn `Next`, nhập tên máy ảo mới và các tùy chọn tương ứng, nhấn `Next`

 ![setup_CentOS](images\setup_CentOS.png)

 * Bước 3 : Chọn nơi lưu trữ

 ![setup_CentOS12](images\setup_CentOS12.png)

 * Bước 4 : Cấu hình các thông số cho máy ảo, sau đó nhấn `Next`

 ![setup_CentOS3](images\setup_CentOS3.png)

 __Lưu ý_ : Mục `CD/DVD Driver 1` ta chọn đúng file iso đã tải lên trên

 ![setup_CentOS4](images\setup_CentOS4.png)

 * Bước 5 :  Rà soát các thông số lần cuối cùng, sau đó nhấn `Finish`

 Máy ảo đã được tạo
 ![setup_CentOS6](images\setup_CentOS6.png)

### Tạo máy ảo trên VMware Workstation

 * Bước 1 : Kết nối VMware Workstation với VMware ESXi
 
 ![setup_Win10](images\setup_Win10.png)
 
 * Bước 2 : Sau khi kết nối thành công, chọn `Create a new vitual machine`

 

 * Bước 3 : Tạo máy ảo với các bước như bình thường, đến mục cấu hình phần cứng, mục `New CD/DVD (SATA)` ta chọn file iso đã upload lên server.

 ![setup_Win10_3](images\setup_Win10_3.png)

 * Bước 4 :  Rà soát các thông số lần cuối cùng, sau đó nhấn `Finish`


 
