# Công nghệ ảo hóa máy chủ
Trong môi trường đám mây, ảo hóa là yếu tố bắt buộc để tạo ra tầng trung gian giữa hệ thống phần cứng máy chủ và phần mềm chạy trên nó.

## Khái niệm về ảo hóa
Hiểu một cách đơn giản, ảo hóa (VM – Virtual Machine) đề cập đến quá trình tạo phiên bản ảo của hệ điều hành (Operating System – OS), máy chủ, tài nguyên mạng hay thiết bị lưu trữ,...

Công nghệ ảo hóa Server sẽ cho phép phân chia một máy chủ vật lý thành nhiều máy chủ ảo độc lập. Mỗi máy chủ ảo có thể được thiết lập chạy trên một hệ điều hành riêng.

![3](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/Ảo_hóa_KVM/image/3.png)

### CÁC MỨC ĐỘ ẢO HÓA

1. Full Virtualization - Ảo hóa toàn phần.

    Ảo hóa toàn phần là một loại ảo hóa phổ biến, về cơ bản là phương pháp tách biệt hoàn toàn phần cứng, hệ điều hành, dịch vụ của máy ảo với máy chủ. Trong Ảo hóa toàn phần, máy ảo sẽ không khác nhiều so với một máy thật.

Một số công nghệ ảo hóa toàn phần phổ biến: KVM, VirtualBox, VMware ESXi, MS Hyper-V

2. Paravirtualization - Ảo hóa song song

    Ảo hóa song song là loại ảo hóa mà trong đó nó không ảo hóa phần cứng để chạy hệ điều hành ảo mà thay vào đó tạo ra một lớp giao diện phần mềm để các hệ điều hành ảo và hypervisor giao tiếp với nhau.

Một số công nghệ phổ biến: Xen serverBM LPAR, Oracle VM for SPARC (LDOM), Oracle VM for X86 (OVM),…

3. Operating System Virtualization - Ảo hóa hệ điều hành

    Ảo hóa hệ điều hành là công nghệ ảo hóa mà máy ảo sử dụng một phần của hệ điều hành máy chủ để có thể sử dụng tất cả các tính năng như ảo hóa toàn phần. Tuy nhiên ở mức độ ảo hóa này, máy ảo phải chạy cùng hệ điều hành với máy chủ. Mọi máy chủ ảo vẫn độc lập với các máy chủ ảo khác trong hệ thống.

Một số công nghệ phổ biến: Docker, Linux LXC, AIX WPAR,…

4. Hypervisor - Ảo hóa ứng dụng.

    Hypervisor hay còn có tên khác là Virtual machine monitor (VMM) là từ dùng để chỉ các phần mềm , firmware hoặc thậm chí là một phần cứng chuyên dụng dùng để tạo, theo dõi và quản lý các máy ảo ( virtual machine) .

Có hai dạng Hypervisor:

 * Bare-Metal Hypervisor: Hypervisor tương tác trực tiếp với phần cứng của máy chủ để quản lý, phân phối và cấp phát tài nguyên.Loại ảo hóa này bao gồm các giải pháp như Vmware ESXi, Microsoft Hyper-V, Xen Server, KVM.

 * Hosted Architecture: Đây là loại ảo hóa Hypervisor giao tiếp với phần cứng thông qua hệ điều hành. Hypervisor lúc này được xem như một ứng dụng của hệ điều hành và các phương thức quản lý, cấp phát tài nguyên đều phải thông qua hệ điều hành. Loại ảo hóa này bao gồm các giải pháp như Vmware WorkStation, Oracle VirtualBox, Microsoft Virtual PC, …

Vì ở loại thứ 1, Hypervisor tương tác trực tiếp với phần cứng nên việc quản lý và phân phối tài nguyên được tối ưu và hiệu quả hơn so với loại 02, vì vậy khi triển khai trong thực tế, ảo hóa Loại 01 (Bare-Metal Hypervisor) được sử dụng, loại 02 chỉ sử dụng trong các trường hợp thử nghiệm, hoặc mục đích học tập.

![2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/Ảo_hóa_KVM/image/2.png)

# Phân loại công nghệ ảo hóa máy chủ
Có 2 kiểu ảo hóa máy chủ cơ bản:

* Virtualization Management Layer hay thường được gọi là “Hosted”: Là hình thức ảo hóa ban đầu của máy chủ. Chức năng ảo hóa trong Hosted được xây dựng trên một nền hệ điều hành – OS thông dụng.

* Dedicated Virtualization hay thường được gọi là “Bare-metal”: Là hình thức ảo hóa được chạy trực tiếp trên phần cứng của máy chủ. Do vậy, so với Hosted, nó có ưu điểm là giúp sử dụng tối ưu tài nguyên máy và tốc độ xử lý nhanh hơn.

## Phương thức hoạt động
Ảo hóa máy chủ hoạt động dựa trên việc phân tách phần cứng và phần mềm. Sẽ có một lớp ảo hóa ở tầng trung gian được gọi là Hypervisor.

![1](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/Ảo_hóa_KVM/image/1.png)


# Cài đặt KVm trên CentOs 7

Chuẩn bi 1 server đã cài CentOS 7, update OS trước khi cài.

Kiểm tra CPU hỗ trợ KVM hay không :

```
lscpu | grep Virtualization
egrep -c "svm|vmx" /proc/cpuinfo
```

Kết quả như sau là có hỗ trợ

![4](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/Ảo_hóa_KVM/image/4.png)

Cài KVM và các gói phụ trợ liên quan: 

```
yum install -y qemu-kvm libvirt bridge-utils virt-manager
```

Sau khi cài đặt, kiểm tra lại bằng lệnh : 

` lsmod | grep kvm `

![5](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/Ảo_hóa_KVM/image/5.png)

Đối với bản Minimal để dùng được công cụ đồ họa virt-manager người dùng phải cài đặt gói x-window bằng câu lệnh
`yum install "@X Window System" xorg-x11-xauth xorg-x11-fonts-* xorg-x11-utils -y`

Start dịch vụ libvirt và cho nó khởi động cùng hệ thống
```
systemctl start libvirtd
systemctl enable libvirtd
```

## Tạo card mạng ảo publish mạng cty

Di chuyển đến thư mục `/etc/sysconfig/network-scripts` tạo file mới có tên `ifcfg-lancty`
Dùng vim để sửa file thành nội dung như sau :

```
DEVICE=lancty
BOOTPROTO=none
IPADDR=172.16.7.14
PREFIX=20
GATEWAY=172.16.10.1
DNS1=8.8.8.8
DNS2=8.8.4.4
ONBOOT=yes
TYPE=Bridge
NM_CONTROLLED=no
```
đồng thời sửa file `ifcfg-enp7s0
` thành :

```
TYPE=Ethernet
BOOTPROTO=none
DEFROUTE=yes
PEERDNS=yes
PEERROUTES=yes
IPV4_FAILURE_FATAL=no
IPV6INIT=yes
IPV6_AUTOCONF=yes
IPV6_DEFROUTE=yes
IPV6_PEERDNS=yes
IPV6_PEERROUTES=yes
IPV6_FAILURE_FATAL=no
NAME=enp7s0
UUID=200f97a5-4332-48c8-bc20-9c3a9b55b3a0
DEVICE=enp7s0
ONBOOT=yes
#IPADDR=172.16.7.14
#PREFIX=20
#GATEWAY=172.16.10.1
#DNS1=8.8.8.8
#DNS2=8.8.4.4
#DEFROUTE=yes
BRIDGE=lancty
NM_CONTROLLED=no
```

Chạy `systemctl restart network` update lại cấu hình.
Kiểm tra lại cấu hình mạng ta thấy đã nhận bridge lancty : 

![6](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/Ảo_hóa_KVM/image/6.png)

