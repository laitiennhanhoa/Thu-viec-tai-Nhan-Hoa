# Cấu hình check hardware server dell qua idrac

## Cài đặt

Môi trường triển khia:
 - Centos 7
 - CPU : 1vCore
 - Ram : 2G
 - Disk : 15G
Cài đặt python 3.9.*
 * Update OS
```
sudo yum -y install epel-release
sudo yum -y update
sudo yum groupinstall "Development Tools" -y
sudo yum install openssl-devel libffi-devel bzip2-devel -y
sudo yum install wget -y

```

* Check ver gcc `gcc --version`

* Install python3.9.*
```
wget https://www.python.org/ftp/python/3.9.18/Python-3.9.18.tgz
tar xvf Python-*.tgz
cd Python-3.9*/
./configure --enable-optimizations --prefix=/usr/local --enable-shared LDFLAGS="-Wl,-rpath /usr/local/lib"
sudo make altinstall

```
* Set ver python3.9 làm mặc định
 `vi ~/.bash_profile`

Thêm dòng `alias python3='/usr/local/bin/python3.9'`
sau đó chạy lệnh
```
source ~/.bash_profile

```

Check lại version python bằng lệnh
python3.9 --version