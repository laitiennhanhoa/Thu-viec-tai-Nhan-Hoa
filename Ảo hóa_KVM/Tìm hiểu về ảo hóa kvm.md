# Công nghệ ảo hóa máy chủ
Trong môi trường đám mây, ảo hóa là yếu tố bắt buộc để tạo ra tầng trung gian giữa hệ thống phần cứng máy chủ và phần mềm chạy trên nó.

## Khái niệm về ảo hóa
Hiểu một cách đơn giản, ảo hóa (VM – Virtual Machine) đề cập đến quá trình tạo phiên bản ảo của hệ điều hành (Operating System – OS), máy chủ, tài nguyên mạng hay thiết bị lưu trữ,...

Công nghệ ảo hóa Server sẽ cho phép phân chia một máy chủ vật lý thành nhiều máy chủ ảo độc lập. Mỗi máy chủ ảo có thể được thiết lập chạy trên một hệ điều hành riêng.

# Phân loại công nghệ ảo hóa máy chủ
Có 2 kiểu ảo hóa máy chủ cơ bản:

* Virtualization Management Layer hay thường được gọi là “Hosted”: Là hình thức ảo hóa ban đầu của máy chủ. Chức năng ảo hóa trong Hosted được xây dựng trên một nền hệ điều hành – OS thông dụng.
* Dedicated Virtualization hay thường được gọi là “Bare-metal”: Là hình thức ảo hóa được chạy trực tiếp trên phần cứng của máy chủ. Do vậy, so với Hosted, nó có ưu điểm là giúp sử dụng tối ưu tài nguyên máy và tốc độ xử lý nhanh hơn.

## Phương thức hoạt động
Ảo hóa máy chủ hoạt động dựa trên việc phân tách phần cứng và phần mềm. Sẽ có một lớp ảo hóa ở tầng trung gian được gọi là Hypervisor.

[1]{https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/Ảo hóa_KVM/image/1.png}
