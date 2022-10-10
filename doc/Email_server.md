# Định nghĩa

Mail Server hay Email Server là hệ thống máy chủ được cấu hình riêng theo tên miền của doanh nghiệp dùng để gửi và nhận thư điện tử.

# Cách thức hoạt động

* Bước 1 : Sau khi tạo và gửi email, email của bạn sẽ kết nối với Server SMTP mang tên miền của mình. SMTP sẽ đặt tên cho tất cả mọi thứ, ví dụ: smtp.tenmien.com.

* Bước 2 : Email của bạn sẽ "giao tiếp" với SMTP server. Và cung cấp cho SMTP Server mọi thông tin như: địa chỉ mail người gửi, địa chỉ mail người nhận, nội dung email và file đính kèm.

* Bước 3 : Tại đây có 2 trường hợp xảy ra:

 - Trường hợp 1: Tên miền (domain email) của người gửi và người nhận giống nhau. 
 VD : tenemail_1@tenmienA.com tới tenemail_2@tenmienA.com. Mail này sẽ được gửi trực tiếp đến POP3 hoặc IMAP Server có tên miền của bạn. 

 - Trường hợp 2: Tên miền của người gửi và người nhận khác nhau.
 VD : tenemail_1@tenmienA.com tới tenemail_2@tenmienB.com. SMTP Server sẽ phải "liên lạc" với một server tên miền khác.

* Bước 4 : Để tìm ra Server của người nhận, SMTP Server của người gửi sẽ phải giao tiếp với DNS (Domain Name Server).

 Server mail người gửi tạo ra một truy vấn đến máy chủ DNS để hỏi về thông tin record MX của domain tenmienB.com. Giả sử rằng không có thông tin về domain tenmienB.com trong bộ nhớ cache của máy chủ DNS .Máy chủ DNS lần lượt tạo ra một truy vấn đệ quy đối với máy chủ DNS có thẩm quyền và tìm hiểu về chi tiết các record MX của domain tenmienB.com. Thông tin này sẽ được trả về cho server mail tenmienA.com .
 
SMTP Server người gửi không thể thực hiện gửi email chính xác mà chỉ dựa trên tên miền thêm vào đó sẽ là địa chỉ IP. Địa chỉ IP (đơn nhất) sẽ giúp SMTP hoạt động chính xác và hiệu quả hơn.

* Bước 5 : Sau khi có địa chỉ IP của người nhận, tức STMP người gửi đã có thể kết nối STMP Server người nhận.

Trong quá trình gửi đi, email sẽ được kiểm tra spam và virus bởi firewall trước khi vượt qua firewall. Nếu có virus, email sẽ được cách ly và người gửi sẽ nhận được một thông báo. Nếu bị đánh dấu là spam, email sẽ bị xóa mà không cần có thông báo tới người gửi. Vì spam khá khó để phát hiện, do đó bộ lọc sẽ kiểm tra dựa trên một loạt các tiêu chí.

* Bước 6 : SMTP server người nhận sẽ quét (scan) thư gửi đến. Nếu nhận ra tên miền và tên người gửi, nó sẽ chuyển tiếp (forward) mail thuộc POP3 hoặc IMAP server mang tên miền của bạn. 

Nếu sử dụng POP3 thì toàn bộ email trên mail server sẽ được tải về máy cá nhân và xóa toàn bộ email đã tải về trên mail server. Tuy nhiên các mail server đều có thêm lựa chọn giữ lại 1 bản copy chứ không xóa hẳn.

Nếu sử dụng IMAP thì email sẽ vẫn được lưu trữ trên mail server, tuy nhiên sẽ có bản ánh xạ trên máy cá nhân, khi xem email nào thì email đó sẽ được tải về và lưu ở chế độ tạm thời trên máy cá nhân, khi tắt mail client thì bản tạm đó cũng bị xóa đ

Từ đây, email đã được gửi đến mục hộp thư đến của người nhận.

![1](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/eMail/10-02-vai-tro-mail-server-trong-gui-nhan-mail.jpg)


Ngày nay, đa phần chúng ta đều sử dụng những dịch vụ mail miễn phí như Gmail hay Outlook,... Nhược điểm của những dịch vụ này là bạn sẽ phải sử dụng những tên miền cố định của họ (dạng @gmail.com hoặc @outlook.com). Nếu như bạn muốn sử dụng những email theo tên miền riêng của bạn (dạng @viettelidc.com.vn) thì lúc này bạn sẽ cần đến dịch vụ email riêng biệt. 

# Tìm hiểu về Zimbra

Zimbra Collaboration là giải pháp Mail Server mã nguồn mở hàng đầu thế giới về tính năng, độ ổn định và bảo mật cao. Ngoài ra, Zimbra không chỉ là một ứng dụng về email server mà nó còn là một giải pháp hoàn chỉnh để triển khai môi trường chia sẻ phục vụ cho quản lý và công việc nội bộ của mỗi doanh nghiệp.

Các tính năng chính của Zimbra Mail Server:

 - Thư điện tử
 - Lịch
 - Sổ địa chỉ
 - Danh mục công việc (task cá nhân, nhóm)
 - Tài liệu lưu dưới dạng wiki
 - Cặp hồ sơ lưu file dùng chung hoặc riêng
 - Chat
 - Client desktop hoặc web
 - Hỗ trợ trên điện thoại
 - Nhiều Zimlet (tương tự như extension)

 # Cài đặt Zimbra

 ## Chuẩn bị Domain : 

Thêm các bản ghi cho doamin trên DNS Server :

![1](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/eMail/1.png)

 ## Cài đặt server :

 * Bước 1 : Update OS : 
 ```
 yum install epel-release -y
 yum update -y
 ```
 * Bước 2 : Đồng bộ thời gian : 

 ```
 yum install chrony -y 
systemctl start chronyd 
systemctl enable chronyd
systemctl restart chronyd 
ln -f -s /usr/share/zoneinfo/Asia/Ho_Chi_Minh /etc/localtime
```

Kiểm tra lại múi giờ và độ trễ :
```
chronyc sources -v
```

* Bước 3 : Tắt firewall, selinux, và 1 số dịch vụ khác :
```
vi /etc/selinux/config
systemctl stop postfix
yum remove postfix -y
```

![2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/eMail/2.png)

![3](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/eMail/3.png)

* Bước 4 : Cài đặt các package cần thiết

```
yum -y install unzip net-tools sysstat openssh-clients perl-core libaio nmap-ncat libstdc++.so.6 nano wget 
```

* Bước 5 : Đặt hostname 
```
hostnamectl set-hostname mail.hongson2.xyz
```
Thêm địa chỉ IP vào file host 
```
vi /etc/hosts
103.170.122.67 mail.hongson2.xyz mail
```
* Bước 6: Cài đặt Zimbra Mail.

Tải zimbra tại link [này](https://www.zimbra.com/downloads/zimbra-collaboration-open-source/).

Sau khi tải thực hiện transfer sang vps qua MobaXterm

![4](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/eMail/4.png)

Giải nén và cài đặt : 

```
tar -vxzf zcs-8.8.15_GA_3869.RHEL7_64.20190918004220.tgz
cd zcs-8.8.15_GA_3869.RHEL7_64.20190918004220
./install.sh
```

![5](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/eMail/5.png)

Ở bước này lưu ý một số tùy chọn cài đặt : 
```
Do you agree with the terms of the software license agreement? [N] Y

Use Zimbra's package repository [Y] Y

Select the packages to install

Install zimbra-ldap [Y] Y

Install zimbra-logger [Y] Y

Install zimbra-mta [Y] Y

Install zimbra-dnscache [Y] N

Install zimbra-snmp [Y] Y

Install zimbra-store [Y] Y

Install zimbra-apache [Y] Y

Install zimbra-spell [Y] Y

Install zimbra-memcached [Y] Y

Install zimbra-proxy [Y] Y

Install zimbra-drive [Y] Y

Install zimbra-imapd (BETA - for evaluation only) [N] N


Install zimbra-chat [Y] Y


The system will be modified.  Continue? [N] Y
```

![6](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/eMail/6.png)

 - Thiết lập domain mới, nhập `hongson2.xyz` => `yes`

![7](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/eMail/7.png)

 - Đặt mật khẩu admin : Chọn `6` -> `4 `-> Nhập pass mới và nhấn `Enter`

 ![8](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/eMail/8.png)

 ![9](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/eMail/9.png)

 Sau khi đặt xong mật khẩu, ta nhập `r` và `a` để quay lại và lưu cấu hình : 
  ![10](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/eMail/10.png)

Hệ thống load lại cấu hình và kiểm tra lại

 ![11](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/eMail/11.png)

 khởi động lại dịch vụ Zimbra với lệnh sau:

 ```
su zimbra
cd && zmcontrol restart
 ```

Một số lỗi hay gặp khi cài Zimbra :

 ![12](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/eMail/12.png)

 - Lỗi : Starting zmconfigd...Failed :
 Kiểm tra và bỏ kích hoạt Ipv6 trong `/etc/hosts` và thêm # như dòng sau :
 ```
##::1 localhost localhost.localdomain localhost6 localhost6.localdomain6
```
Kiểm tra trong host đã đủ dòng sau chưa :

```
127.0.0.1 localhost
192.168.1.1 mail.hốngn2.xyz mail
```

 - Lỗi : Starting mailbox...Failed 

 ![13](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/eMail/13.png)

 Check log zimbra trong `/var/log/zimbra.log` 

  ![14](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/eMail/14.png)

  Do cài bản Zimbra 9.0.0 lỗi repository (zimbra chặn 1 số gói cài đặt liên quan đến vấn đề bản quyền) nên cài lại bản 8.8.15

* Bước 7 : Hoàn tất cài đặt : 

![16](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/eMail/16.png)

Đăng nhập vào Zimbra với thông tin acc sau : Tên đăng nhập : admin@hongson2.xyz . Mật khẩu : đặt ở bước trên.

* Bước 8: Kiểm tra lại các dịch vụ trên máy chủ, nếu các dịch vụ trên chưa hoạt động, reboot lại VPS.

![17](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/eMail/17.png)

# Test gửi nhận mail trên Zimbra

Đăng nhập webmail qua link : https://mail.hongson2.xyz/
![18](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/eMail/18.png)

Soạn mail gửi vào email có địa chỉ : `admin@hongson2.xyz`
ta thấy hòm mail `admin@hongson2.xyz` trên Zimbra đã nhận được thư.
![19](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/eMail/19.png)

Soạn mail có nội dung là `Test gửi mail` gửi vào địa chỉ email `tienlk@nhanhoa.com.vn`, kiểm tra trong hòm mail trên thấy có mail gửi từ `admin@hongson2.xyz`.

![20](https://github.com/laitiennhanhoa/
Thu-viec-tai-Nhan-Hoa/blob/main/images/eMail/20.png)