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

## Virtual Hosts trên Apache

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


