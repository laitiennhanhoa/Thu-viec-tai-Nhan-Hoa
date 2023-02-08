Với con SW Cisco3750 kia em bố trí lab cho anh:

+ Thao tác cơ bản đặt hostname, IP mngt, clock time, NTP đồng bộ thời gian

+ Reset factory switch về mặc định, reset password admin xử lý trường hợp quên pass admin

+ Tạo/sửa/xóa VLAN

+ Backup/restore cấu hình switch

+ Cấu hình backup định kỳ tự động.

+ QoS limit băng thông theo port của switch


======================================================================================



## Lệnh Cisco truy cập vào các chế độ
|Mô tả	|Lệnh|
| ----------- | ----------- |
|User mode (chế độ user)|	Switch>|
|Enter Privilege mode (vào chế độ đặc quyền)|	Switch>enable|
|Privileged mode (chế độ đặc quyền)|	Switch#|
|Enter configuration mode (vào chế độ cấu hình)|	Switch#configure terminal|
|Global Config mode|	Switch(config)#|
|Vào Interface mode|	Switch(config)#interface fa0/1|
|Interface mode|	Switch(config-if)|
|Return to global configuration (Trở về Global Config)|	Switch(config-if)exit|
|Exit Global Config mode (Thoát Global Config)|	Switch(config)#exit|
|Return to user mode (Trở về user mode)|	Switch#disable|
|Logout (Đăng xuất)|	Switch>exit|

## Các phím tắt thông dụng

|Mô tả|	Phím tắt|
| ----------- | ----------- |
|Recall Previous command| (Gọi lệnh Previous)	Mũi tên lên hoặc <Ctrl> p|
|Recall Next command (Gọi lệnh Next)|	Mũi tên xuống hoặc <Ctrl> n|
|Bắt đầu lệnh|	<Ctrl> a|
|Kết thúc lệnh|	<Ctrl> e|
|Xóa input|	<Ctrl> d|
|Thoát Configuration Mode|	<Ctrl> z|
|Làm mới output trên màn hình|	<Ctrl> R|
|Hoàn thành lệnh|	TAB|

## Lệnh cấu hình Switch Cisco

|Mô tả|	Lệnh|
| ----------- | ----------- |
|Configure device system name (Cấu hình tên thiết bị)|	Switch(config)#hostname sw1|
|Sets the encrypted enable password (Thiết lập mật khẩu mã hóa)|	Switch(config)#enable secret cisco|
|Sets the unencrypted enable password (Đặt mật khẩu không mã hóa)|	Switch(config)#enable password cisco|
|Enable password encryption on all clear text password within the configuration file (mã hóa tất cả các mật khẩu trong file cấu hình)|	Switch(config)#service password-encryption|
|Configure a Message Of The Banner, with an ending character of $ (cài thông báo cho banner, kết thúc bằng $)|	Switch(config)#banner motd $|
|Assign IP address to vlan (gán ip cho vlan)|	Switch(config)#int vlan 1   Switch(config-if)#ip addr 172.22.1.11 255.255.255.0|
|Assign Default gateway, note the mode: gán default gateway.|	Switch(config)#ip default-gateway 10.1.1.1|
|Select one interface: chọn 1 interface.|	Switch(config)#int fa0/1|
|Select a range of interfaces (version dependant): chọn 1 dải interface.|	Switch(config)#int range fa0/1 – 12|
|Set the interface description: Viết mô tả cho interface.|	Switch(config-if)#description|
|Add vlan using config mode: thêm vlan sử dụng config mode.|	switch(config)#vlan 11 switch(config-vlan)#name test|
|Configure Interface fa0/1 @ speed 100 Mbps and full duplex: Cấu hình int fa0/1 tốc độ 100Mbps và full duplex.|	Switch(config-if)#speed 100 Switch(config-if)#duplex full|
|Assign interface to vlan: gán int cho vlan.|	switch(config-if)#switchport access vlan 11|
|Enable Port Security: Bật bảo mật port.|	Switch(config-if)#switchport mode access Switch(config-if)#switchport port-security Switch(config-if)#switchport port-security mac-address sticky|
|Disable Interface: tắt int|	Switch(config-if)shutdown|
|Enable Interface: cho phép int hoạt động.|	Switch(config-if)no shutdown
|Configures 5 Telnet sessions each with a password of ‘cisco’: cho phép 5 phiên Telnet một lúc, mật khẩu là cisco.|	Switch(config)#line vty 0 4 Switch(config-line)#login   Switch(config-line)#password cisco|
|Enable and define console password of ‘cisco’: Kích hoạt và đặt mật khẩu cho console là cisco.|	Switch(config)#line con 0   Switch(config-line)#login   Switch(config-line)#password cisco|
|Synchronise console messages (keep what you have typing on the screen): Đồng bộ thông báo console, giữ những gì bạn đã gõ trên màn hình.|	Switch(config-line)#logging synchronous|
|Set the timezone and automatically adjust: Thiết lập timezone và tự động thay đổi.|	Switch(config)#clock timezone gmt 0 Switch(config)#clock summer-time gmt recurring|
|Sets the switch priority for the vlan: Thiết lập priority cho vlan.|	Switch(config)#spanning-tree vlan 1 priority 4096|
|Enables portfast: Kích hoạt portfast.|	Switch(config)#int fa0/1    Switch(config-if)#spanning-tree portfast|
|Enables RSTP: Bật RSTP, có tùy chọn khác là PVST và MST.|	Switch(config)#spanning-tree mode rapid-pvst|
|Creates a vlan: Tạo vlan. Lệnh này được thực hiện trong config mode, không phải trong vlan database và lệnh int vlan không tạo vlan.|	Switch(config)#vlan 2 Switch(config-vlan)#name sales|
|Assign an interface to vlan 2: Gán int cho vlan 2.|	Switch(config-if)#switchport access vlan 2|
|Buộc int là trunk vô điều kiện. Có thể chọn chế độ khác là access và dynamic.|	Switch(config-if)#switchport mode trunk|
|Gán thủ công switch vào miền VTP. Switch tự động trở thành 1 phần của miền VTP nếu nó đang trong miền “null” và nhận VTP frame.|	Switch(config)#vtp domain lab|
|Thay đổi VTP mode từ chế độ mặc định là server sang client. Trong client mode thì không thay đổi được nữa.|	Switch(config)#vtp mode client|


## Các lệnh đặc quyền (Privilege Commands) trên Switch

|Mô tả|	Lệnh|
| ----------- | ----------- |
|Bật hộp thoại setup tự động khi thiết bị khởi động mà không có cấu hình.|	Switch#setup|
|Displays the config held in DRAM. Which is lost if not copy run start command is not used: Hiển thị cấu hình lưu trong DRAM. Cấu hình này bị mất khi lệnh not copy run start không được sử dụng.|	Switch#show running-config|
|Displays the NVRAM (None volatile) config: Hiển thị cấu hình NVRAM.|	Switch#show startup-config|
|Saves the config: Lưu cấu hình, nếu không có lệnh này tất cả các thay đổi, cấu hình sẽ bị mất.|	Switch#copy running-config startup-config|
|Saves the running config to a TFTP server: Lưu cấu hình đang chạy vào TFTP server.|	Switch#copy running-config tftp|
|Copies IOS files to a TFTP server: Sao chép file IOS vào TFTP server.|	Switch#copy flash tftp|
|Copies files from a TFTP server the device flash: Copy file từ TFTP vào thiết bị flash.|	Switch#copy tftp flash|
|Erase the config held in NVRAM: Xóa cấu hình lưu trong VNRAM. Nếu thực hiện lệnh này kèm với reload thì tất cả cấu hình sẽ bị mất.|	Switch#erase startup-config|
|Reboots the device: Khởi động lại switch.|	Switch#reload|
|Abort sequence: Hủy một lệnh, thủ tục|	<Shift> <Ctrl> 6|
|Suspend Telnet Session: Tạm dừng phiên telnet|	Nhấn cùng lúc <Shift> <Ctrl> 6, thả hết các phím ra và nhấn ngay x|
|Show the current sessions: Xem phiên hiện tại, phiên nào có * là phiên hiện hoạt.|	Switch#show sessions|
|Forcible closes a telnet session: Buộc đóng một phiên telnet.|	Switch#disconnect|
|Set the device local clock: Thiết lập giờ địa phương cho thiết bị. Lệnh này không được thực hiện trong chế độ cấu hình.|	Switch#clock set 10:00:00 april 2 2008|
|Display the IOS version along with other useful info: Xem phiên bản IOS và các thông tin hữu ích khác như uptime hệ thống, cấu hình register…|	Switch#show version|
|Xem nội dung file của flash.|	Switch#show flash|
|Xem giờ.|	Switch#show clock|
|Xem user hiện đang đăng nhập.|	Switch#show users|
|By default displays the last 10 commands: Xem 10 lệnh vừa dùng.|	Switch#show history|
|Displays the ARP cache: Xem cache ARP.|	Switch#show arp|
|Displays the spanning tree status on vlan 1: Xem trạng thái spanning tree trên vlan 1.|	Switch#show spanning-tree vlan 1|
|Lists all the configured vlans: Liệt kê tất cả vlan đã cấu hình.|	Switch#show vlan|
|Displays VTP info such as VTP mode, VTP domain, VTP counter: Xem thông tin VTP như chế độ, miền, bộ đếm.|	Switch#sh vtp status|
|Ping selected address: Ping một địa chỉ IP.|	Switch#ping 10.1.1.1|
|Extended ping: Phải thực hiện trong chế độ privilege.|	Switch#ping|
|Display the interface status: Hiển thị trạng thái interface.|	Switch#show int fa0/1|
|Displays the vlan status and the IP address VLAN 1 (often the management vlan): Xem trạng thái VLAN 1.|	Switch#show interfaces vlan 1|
|Displays a list of CDP neighbours: Xem danh sách CDP.|	Switch#show cdp neighbors|
|Extended information on the above: Xem nhiều thông tin hơn lệnh trên.|	Switch#show cdp neighbors details|
|Display CDP packets as they arrive: Xem các gói CDP khi chúng đến.|	Switch#debug cdp packets|
|Display ping packets as they arrive: Hiển thị các gói ping khi chúng đến.|	Switch#debug icmp packets|
|Display switch MAC Addresses table. These entries are learnt from the source mac address in the Ethernet frames: Xem bảng địa chỉ MAC, lấy từ địa chỉ MAC nguồn trong Ethernet frame.|	Switch#show mac address-table|


