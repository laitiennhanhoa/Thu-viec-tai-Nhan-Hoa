# Giới thiệu

Mail kerio-connect là một mail server thể được cài đặt trên nhiều hệ điều hành, bao gồm Windows, Mac OS và Linux Kerio connect hỗ trợ đầy đủ các tính năng và tương thích với các công cụ check mail như là out look, thunderbird.

# Cài đặt server :

## Trên CentOS 7 :

 * Bước 1 : Update OS : 
 ```
 yum install epel-release -y
 yum update -y
 ```

 * Bước 2: Cấu hình time-zone cho hệ thống
```
ln -sf /usr/share/zoneinfo/Asia/Ho_Chi_Minh /etc/localtime
```

 Download mail Kerio-connect tại http://www.kerio.com/support/kerio-connect

 * Bước 3 : Upload file rpm lên server

 [1]{https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/kerio/1.png}

 Kiểm tra và tắt các dịch vụ mail như là sendmail và postfix
```
/etc/init.d/sendmail stop && /sbin/chkconfig sendmail off
/etc/init.d/postfix stop && /sbin/chkconfig postfix off
```

 * Bước 4 : Chạy lệnh :

 ```
 yum makecache
 yum -y install cryptsetup
 rpm -i kerio-connect-9.4.2-6498-linux-x86_64.rpm
```
[2]{https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/kerio/2.png}

 * Bước 5 : Truy cập link `http:[IP]:4040` để thực hiện các bước cài đặt tiếp theo.

[3]{https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/kerio/3.png}

[4]{https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/kerio/4.png}

[5]{https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/kerio/5.png}

[6]{https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/kerio/6.png}