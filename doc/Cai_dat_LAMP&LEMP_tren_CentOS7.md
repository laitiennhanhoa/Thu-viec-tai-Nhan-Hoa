# Giới thiệu LAMP 

LAMP là chữ viết tắt thường được dùng để chỉ sự sử dụng các phần mềm Linux, Apache, MySQL và ngôn ngữ văn lệnh PHP hay Perl hay Python để tạo nên một môi trường máy chủ Web có khả năng chứa và phân phối các trang Web động.

![LAMP](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/LAMP_CentOS7/LAMP_software_bundle.png)

 - Linux : quản lý và phân bổ tài nguyên, xử tất các các lệnh trên server

 - Apache : là một phần mềm máy chủ web quản lý các trao đổi giữa client và server qua giao thức HTTP.

 - MySQL : phần mềm quản trị cơ sở dữ liệu.

 - PHP : ngôn ngữ lập trình kịch bản

# Cài đặt LAMP trên CentOS 7

## Cài Apache

* Bước 1 : CHeck và cập nhập `httpd`, dùng lệnh 

```
sudo yum update httpd
```

![1](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/LAMP_CentOS7/1.png)

Sau đó cài đặt các gói :

```
sudo yum install httpd
```

Sau khi xác nhận cài đặt, yum sẽ cài đặt Apache và tất cả các dependencies bắt buộc.

* Bước 2 :  Cài đặt `firewalld` trên server và mở cổng 80 cho các request HTTP

```
sudo firewall-cmd --permanent --add-service=http
```

Để nhận các request HTTPs thì mở cổng 443 

```
sudo firewall-cmd --permanent --add-service=https
```

Reload firewall để update các rule vừa tạo

```
sudo firewall-cmd --reload
```

Khởi động lại web server.

![2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/LAMP_CentOS7/2.png)

* Bước 3 : Kiểm tra lại web server.

 - Khởi động web server : 

 ```
sudo systemctl start httpd
 ```

 - Kiểm tra trạng thái :

 ```
 sudo systemctl status httpd
 ```

 ![3](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/LAMP_CentOS7/3.png)

Truy cập thử bằng cách nhập IP web server.

 ![4](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/LAMP_CentOS7/4.png)

 - Kiểm tra file cấu hình chính của Apache 

 ```
 vi /etc/httpd/conf/httpd.conf
 ```

### Virtual Hosts trên Apache

Virtual Hosts được sử dụng để giúp cho một web server có thể chạy được nhiều website khác nhau. Các bước tạo Virtual Hosts : 

* Bước 1 : Tạo thư mục chứa website :

```
sudo mkdir -p /var/www/html/tienlk
```

![VPS_1](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/LAMP_CentOS7/VPS_1.png)

* Bước 2 : Thêm quyền vào thư mục 

```
sudo chown -R apache:apache /var/www/html/tienlk
```

* Bước 3 : Cài đặt Virtual Hosts bằng cách sửa file cấu hình của Apache :

```
sudo vi /etc/httpd/conf/httpd.conf
```

Hoặc tạo thêm 1 file cấu hình mới trong `/etc/httpd/conf.d/` , mỗi file config tạo trong thư mục trên được gọi là Virtual host. Mỗi file Virtual host sẽ quy định cho 1 domain riêng.

```
sudo vi /etc/httpd/conf.d/tienlk.conf
```
Sau khi tạo xong file hoặc truy cập file config của Apache thành công, ta thêm đoạn text sau vào cuối file :

```
<VirtualHost *:80>
     DocumentRoot /var/www/tienlk
     ServerName www.tienlk.com
     ServerAlias tienlk.com
     ErrorLog /var/www/tienlk.com/error.log
     CustomLog /var/www/tienlk.com/requests.log common
</VirtualHost>
```

Sau khi suwar xong file cấu hình, ta dùng lệnh `apachectl configtest` để kiểm tra cấu hình. Kết qủa báo về `Symtax OK` tức là cấu hình đã đúng.

![VPS_2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/LAMP_CentOS7/VPS_2.png)

Trong đó :

- Listen 80 - Lắng nghe trên port 80
- ServerName www.tienlk.com - Khai báo địa chỉ URL
- ServerAlias tienlk.com - Khai báo các biến thể của URL
- DocumentRoot /var/www/html/tienlk - Thư mục gốc của webserver
- ErrorLog /var/log/httpd/tienlk/error.log - Khai báo thư mục chứa nhật ký lỗi 
- CustomLog /var/log/httpd/tienlk/requests.log common Khai báo thư mục chứa nhật ký tùy chỉnh

![VPS_4](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/LAMP_CentOS7/VPS_4.png)

* Bước 4 : Tạo file `.html` để test thử domain, gõ lệnh `vi /var/www/html/tienlk/index.html` nhập đoạn code sau :

```
<html>
  <head>
    <title>www.tienlk.com</title>
  </head>
  <body>
    <h1>Hi: Welcome to Nhan Hoa!</h1>
  </body>
</html>
```

Trên trình duyệt nhập `tienlk.com`

![VPS_3](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/LAMP_CentOS7/VPS_3.png)

## Cài đặt MariaDB

MariaDB là một sản phẩm mã nguồn mở tách ra từ mã mở do cộng đồng phát triển của hệ quản trị cơ sở dữ liệu quan hệ MySQL nhằm theo hướng không phải trả phí với GNU GPL. MariaDB được phát triển với sự dẫn dắt của những nhà phát triển ban đầu của MySQL.

### Đối với MariaDB Server 5.5

Khi chạy câu lệnh cài đặt MariaDB sau, hệ thống tự nhận gói cài đặt ver 5.5

```
sudo yum install mariadb-server
```

### Cài đặt MariaDB Server 10.0 trở lên

Do từ ver 10.0 -> 10.4 có nhiều cập nhập đáng kể, nên việc cài đặt MariaDB Server 10.4 khác hơn nhiều so với ver 5.5

Để cài đặt các ver MariaDB Server mới nhất, ta có thể cài đặt thông qua các repository có sẵn.

* Bước 1 : Cập nhập key rpm của CentOS 7 :

```
```

Cài đặt EPEL Repository (Kho chương trình cộng đồng mã nguồn mở do Fedora phát triển và duy trì)

```
yum -y install epel-release
```

![Maria_1](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/LAMP_CentOS7/Maria_1.png)

* Bước 2 : Cài đặt gói máy chủ MariaDB

```
yum -y install mariadb-server mariadb
```

![Maria_2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/LAMP_CentOS7/Maria_2.png)

* Bước 3 : Đặt mật khẩu root , chạy các lệnh sau : 

```
systemctl enable mariadb
systemctl start mariadb
mysql_secure_installation
```

> Enter current password for root (enter for none): Nhấn phím Enter
> Set root password? [Y/n]: Y
> New password: Nhập password root các bạn muốn tạo
> Re-enter new password: Nhập lại password root
> Remove anonymous users? [Y/n] : Y
> Disallow root login remotely? [Y/n]: Y
> Remove test database and access to it? [Y/n] : Y
> Reload privilege tables now? [Y/n]: Y

![Maria_3](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/LAMP_CentOS7/Maria_3.png)

## Cài đặt PHP-FPM và các Module cần thiết

### Cài đặt PHP-FPM

Để cài đặt PHP-FPM chạy các lệnh sau :

```
yum -y install yum-utils
rpm -Uvh http://rpms.remirepo.net/enterprise/remi-release-7.rpm
yum -y update

yum-config-manager --enable remi-php73
yum -y install php php-fpm php-ldap php-zip php-embedded php-cli php-mysql php-common php-gd php-xml php-mbstring php-mcrypt php-pdo php-soap php-json php-simplexml php-process php-curl php-bcmath php-snmp php-pspell php-gmp php-intl php-imap perl-LWP-Protocol-https php-pear-Net-SMTP php-enchant php-pear php-devel php-zlib php-xmlrpc php-tidy php-mysqlnd php-opcache php-cli php-pecl-zip unzip gcc
```

Sau khi cài đặt xong, vào file `/etc/php.ini` để cấu hình PHP :

```
date.timezone = Asia/Ho_Chi_Minh
expose_php = Off
short_open_tag = On
max_input_vars = 3000
disable_functions = exec,system,passthru,shell_exec,proc_close,proc_open,dl,popen,show_source,posix_kill,posix_mkfifo,posix_getpwuid,posix_setpgid,posix_setsid,posix_setuid,posix_setgid,posix_seteuid,posix_setegid,posix_uname
```
Mở file `/etc/httpd/conf.d/php.conf` tìm dòng `SetHandler application/x-httpd-php` sửa thành `SetHandler “proxy:fcgi://127.0.0.1:9000”`

![php_1](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/LAMP_CentOS7/php_1.png)

Khởi động lại Apache và load lại config : 

```
systemctl restart httpd
```

### Khởi động PHP-FPM

Chạy 2 lệnh sau để khởi động PHP-FPM

```
systemctl start php-fpm
systemctl enable php-fpm
```
Tạo file /var/www/html/tienlk/info.php với nội dung :

```
<?php
phpinfo();
```

![php_2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/LAMP_CentOS7/php_2.png)
## Cài đặt Wordpress

* Bước 1 : Tạo data base cho Wordpress, đăng nhập vào maria db

```
mysql -u root -p
CREATE DATABASE wordpress;
SHOW DATABASES;
```

![wp_1](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/LAMP_CentOS7/wp_1.png)

* Bước 2 : Tạo acc truy cập database và thêm quyền cho acc wordpress

```
CREATE USER wordpress@localhost IDENTIFIED BY '0123456a@';
GRANT ALL PRIVILEGES ON wordpress.* TO 'wordpress'@'localhost' IDENTIFIED BY '0123456a@' WITH GRANT OPTION;
FLUSH PRIVILEGES;
exit;
```

* Bước 4 : Cài đặt WordPress, cài đặt từ `yum package`

```
yum -y install wordpress
```
Chuyển thư mục WordPress đã cài `/usr/share/wordpress/`  về thư mục mặc định của web `/var/www/html/` bằng rsync :

```
yum install rsync
rsync -avP /usr/share/wordpress/ /var/www/html/tienlk/
```
Cập nhập lại quyền cho nhóm người dùng Apache:

```
chown -R apache:apache /var/www/html/
```

* Bước 5 : Cấu hình wordpress qua tệp `wp-config.php`
Lưu ý : Phải cấu hình ở tệp gốc theo đường dẫn `/usr/share/wordpress/wp-config.php`

```
vi /usr/share/wordpress/wp-config.php
systemctl reload httpd
```

Sửa các dòng đánh dấu như ảnh sau đó khởi động lại apache

![wp_2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/LAMP_CentOS7/wp_2.png)

Check lại bằng trình duyệt với link `http://tienlk.com/wp-admin/` ta có kết quả như ảnh

![wp_3](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/LAMP_CentOS7/wp_3.png)
