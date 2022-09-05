# Kiến trúc tổng quan hệ thống Linux: 

Hệ điều hành là một phần mềm máy tính phức tạp để giúp người sử dụng có thể tương tác và điều khiển những phần cứng máy tính và các phần mềm chạy trên đó. Những hệ điều hành được xây dựng trên Linux Kernel được gọi là các distro (bản phân phối) của Linux.Cấu trúc của các distro Linux được chia làm 3 thành phần chính, đó là: Kernel, Shell, Applications.
# Sự khác nhau giữa Linux, Unix và Windows

> Trong khi Unix được cung cấp cho doanh nghiệp với đầy đủ mọi thứ để đc triển khai & sửa đổi trong nội bộ doanh nghiệp thì Linux đc phát hành chỉ dưới dạng kernel, ko có trình biên dịch (biên dich bằng gcc của GNU project), không có hệ vỏ (shell) - bởi vậy nên mới tồn tại nhiều shell khác nhau: sh, bash, csh, ksh, không có bootloader (nên phải xài bootloader riêng ở ngoài nhu GRUB, LILO, syslinux), không có môi trường desktop (nên phải xài đồ ngoài như GNOME, KDE...), không có hệ thống khởi dậy tiến trình ban đầu (mà phải dùng init, upstart, systemd là những cái ngoài)...
Khi lấy cái Linux kernel, gộp chung với mấy thứ "dùng ngoài" kia nữa thì ta có các bản phân phối Linux như Ubuntu, Fedora, ArchLinux v.v...

![unix](https://upload.wikimedia.org/wikipedia/commons/7/77/Unix_history-simple.svg)