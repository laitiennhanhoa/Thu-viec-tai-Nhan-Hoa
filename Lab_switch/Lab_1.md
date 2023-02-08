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
|Assign IP address to vlan (gán ip cho vlan)|	Switch(config)#int vlan 1   
Switch(config-if)#ip addr 172.22.1.11 255.255.255.0|
|Assign Default gateway, note the mode: gán default gateway.|	Switch(config)#ip default-gateway 10.1.1.1|
|Select one interface: chọn 1 interface.|	Switch(config)#int fa0/1|
|Select a range of interfaces (version dependant): chọn 1 dải interface.|	Switch(config)#int range fa0/1 – 12|
|Set the interface description: Viết mô tả cho interface.|	Switch(config-if)#description|
|Add vlan using config mode: thêm vlan sử dụng config mode.|	switch(config)#vlan 11
switch(config-vlan)#name test|
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