# Tạo usb boot Vmware ESXi

Tải bản iso trên trang chủ Vmware

[Nguồn](https://customerconnect.vmware.com/en/downloads/info/slug/datacenter_cloud_infrastructure/vmware_vsphere/7_0)

Sau khi tải, cài vmware vào server, ta dùng rufus ver 3.20 để tạo usb boot. Khởi chạy rufus với quyền admin.
Chọn usb ta đã chuẩn bị, chọn file iso vừa tải về theo link trên. Nhấn `START`

[rufus_vmware]()

Sau khi rufus chạy xong, ta đã có usb boot cài Vmware ESXi

# Tiến hành cài Vmware ESXi

## Cấu hình RAID 1

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

