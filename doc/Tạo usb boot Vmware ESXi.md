# Tạo usb boot Vmware ESXi

Tải bản iso trên trang chủ Vmware

[Nguồn](https://customerconnect.vmware.com/en/downloads/info/slug/datacenter_cloud_infrastructure/vmware_vsphere/7_0)

Sau khi tải, cài vmware vào server, ta dùng rufus ver 3.20 để tạo usb boot. Khởi chạy rufus với quyền admin.
Chọn usb ta đã chuẩn bị, chọn file iso vừa tải về theo link trên. Nhấn `START`

[rufus_vmware]()

Sau khi rufus chạy xong, ta đã có usb boot cài Vmware ESXi

# Tiến hành cài Vmware ESXi

## Cấu hình RAID 0

Cắm usb boot vừa tạo vào máy chủ.

Khởi động máy chủ, đối với máy chủ Dell có iDRAC ,cấu hình iDRAC xong có thể truy cập từ xa.
Sau khi khởi động máy chủ, nhấn `Ctrl + R` để vào giao diên `RAID Controller`

[config_raid]()

Trong giao diện `RAID Controller`, mục `VD Mgmt` chọn `Vỉtual Disks`.Nhấn F2 và chọn `Delete VD` -> `Yes` để xóa cấu hình RAID trước đó.

[clear_raid]()

Sau khi xóa cấu hình Raid trước đó , trong hệ thống hiển thị 2 ổ cứng đã cắm vào server từ trước.

[no_raid]()

Nhấn F2 và chọn `Create new VD`, trong giao diện cấu hình RAID, chọn kiểu RAID-0 và thêm các ổ đĩa có sẵn vào, đặt tên cho RAID mới tạo.

[setup_raid]()

Kiểm tra lại Raid đã tạo

[info_raid]()

Để lưu cấu hình raid vừa tạo, ta nhấn F2 chọn `Initialization` -> `Fast Init`

[save_raid]()

Khởi động lại máy chủ

## Cài đặt VMware ESXi

Sau khi khởi động lại máy chủ, nhấn F11 để vào `Boot Manager`

Chọn `BIOS Boot Menu` để chọn chế độ boot

[boot_nemu]()

Trong `Boot Menu`, chọn `Hard drive C :` -> `Front USB: USB Flash Drive` là USB đã tạo file boot ở trên

[usb_boot]()

Trong giao diện boot usb, chọn install VMware ESXi-7

[install_vmware0](images\install_vmware.png)

* Chọn phân vùng 

[install_vmware]()


* Chọn bàn phím

[install_vmware2]()

* Xác nhận cài đặt, nhấn F11

[install_vmware4]()

* Sau khi cài đặt xong, hệ thống yêu càu reboot lại, nhấn `Enter`

[install_vmware5]()

Sau khi hệ thống restart lần đầu thành công. giao diện này sẽ được hiển thị

[start_vmware](images\start_vmware.png)

## Cấu hình VMWare 

* Nhấn F2 và đăng nhập vào hệ thống :

[login_config_vmware](images\login_config_vmware.png)

* Sau khi đăng nhập, chọn `Configure Management Network` để cấu hình network cho server VMWare

[ipconfig_vmware](images\ipconfig_vmware.png)

* Chọn tiếp `IPv4 Configuration` nhấn Enter

[ipconfig_vmware2](images\ipconfig_vmware2.png)

* Cấu hình IP phù hợp với mạng thực tế, sau đó nhấn Enter để lưu cấu hình

[ipconfig_vmware3](images\ipconfig_vmware3.png)

* Cấu hình DNS: Chọn `DNS Configuration`, nhấn Enter. Cấu hình DNS để DNS của google (như hình), sau đó nhấn Enter để lưu.

[DNS_config_vmware](images\DNS_config_vmware.png)

[DNS_config_vmware2](images\DNS_config_vmware2.png)

* Sau khi cấu hình xong DNS, nhấn Esc để thoát, khi đó hệ thống sẽ hỏi lưu lại cấu hình không, chọn Y

[save_config_vmware](images\save_config_vmware.png)

Sau khi cấu hình xong network cho server VMware, nhấn F12 -> F11 để reload lại server.

[reload_vmware](images\reload_vmware.png)

## Đăng nhập VMware ESXi 7.0 trên trình duyệt

Sau khi khởi động lại server VMware,trên giao diện máy chủ hiện thị các thông tin như sau :

[page_main_vmware](images\page_main_vmware.png)

trong đó có link url : https://172.16.3.139 (ip cấu hình cho host VMware).Nhập url trên vào trình duyệt, ta đến trang ligin của VMware :

[login_vmware](images\login_vmware.png)

Sau khi đăng nhập, ta truy cập được trang quản trị server VMware.

[mai_vmware](images\mai_vmware.png)

# Tạo máy ảo trên VMware ESXi 7.0

## Tạo thư mục lưu trữ file ISO

* Bước 1 : Chọn Storage, chọn mục `Datastore browser` -> `Create directory`

[Create_directory](images\Create_directory.png)

Nhập tên foder xong nhấn `Create directory`.

* Bước 2 : Trong thư mục vừa tạo nhấn `Upload` , chọn file đuôi .iso để đẩy lên server.

[Upload_ISO](images\Upload_ISO.png)

* Bước 3 : Tạo máy ảo

__Tạo máy ảo trên trình duyệt__

