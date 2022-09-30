# Định nghĩa

DirectAdmin là một trong số những Control Panel dành cho người quản trị Web Hosting và được sử dụng phổ biến hiện nay với giao diện đơn giản, trực quan, dễ dàng sử dụng. 

# Cài đặt Direct Admin

* Cài đặt các gói cần thiết cho Direct Admin : 

```
yum install wget gcc gcc-c++ flex bison make bind bind-libs bind-utils openssl openssl-devel perl quota libaio libcom_err-devel libcurl-devel gd zlib-devel zip unzip libcap-devel cronie bzip2 cyrus-sasl-devel perl-ExtUtils-Embed autoconf automake libtool which patch mailx bzip2-devel lsof glibc-headers kernel-devel expat-devel

yum install -y psmisc net-tools systemd-devel libdb-devel perl-DBI xfsprogs rsyslog logrotate crontabs file
```
* Tải Direct Admin và cài đặt :

```
get http://www.directadmin.com/setup.sh
chmod 755 setup.sh
./setup.sh
```
Trong quá trình cài đặt Direct Admin, License Key sẽ phải nhập vào để hoàn tất quá trình cài đặt.

Sau khi cài đặt, vào đường dẫn sau để lấy thông tin đăng nhập trang quản trị `vi /usr/local/directadmin/scripts/setup.txt`

Có thể dùng thử tại `https://demo.directadmin.com:2222/` với thông tin các loại user như sau :

Users demo : login: demo_user   password: demo
Resellers demo : login: demo_reseller   password: demo
Admins demo : login: demo_admin     password: demo

Đăng nhập bằng link sau : `https://demo.directadmin.com:2222/login?redirect=%2F`

