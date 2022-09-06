# Tổng quan về Linux
Linux là HĐH được phát triển bởi Linus Torvarlds tại trường đại học Helsinki (Phần Lan) vào năm 1991 dựa trên kiến trúc của HDH Unix nhưng viết lại toàn bộ mã nguồn. Linux được tạo ra với mục đích cung cấp cho người dùng 1 giải pháp phần mềm miễn phí thay thế cho UNIX. Linux có thể chạy trên rất nhiều nền tảng khác nhau như x86 và x64 từ Intel/AMD trong khi UNIX chỉ chạy trên 1 hoặc 2 kiến trúc nhất định.
# Phân biệt giữa UNIX và Linux
UNIX là một HĐH đa nhiệm, đa người dùng có kiến trúc nguyên khối được phát triển vào năm 1969 bởi một nhóm nhân viên của công ty AT&T tại phòng thí nghiệm Bell Labs.Ban đầu, UNIX được phân phối cho các trường đại học và những doanh nghiệp có nhu cầu, với đầy đủ mọi thứ từ mã nguồn đến các công cụ lập trình. Từ đây Unix có nhiều phiên phản được các công ty phát triển nhằm tối ưu với phàn cứng của họ, một vài phiên bản có thể kể đến như : HP-UX, AIX, Solaris, Mac OS X. Đến đầu những năm 90, Unix được thương mại hóa và trở thành 1 HDH đóng,[dẫn nguồn](https://vi.wikipedia.org/wiki/Unix). Hầu hết các phiên bản UNIX hiện nay đều là những biến thể của UNIX gốc và được các nhà phát triển sửa đổi, viết lại hoặc thêm các tính năng, công nghệ riêng biệt.
![unix](https://upload.wikimedia.org/wikipedia/commons/7/77/Unix_history-simple.svg)
Trái ngược với UNIX, Linux mặc dù vẫn dựa trên kiến trúc của Unix để xây dựng nhưng là 1 HDH mã nguồn mở, mới mục đích cung cấp người dùng 1 giải pháp miễn phí thay thế Unix. Linux coi Unix như đối thủ của mình.HDH Linux hiện nay là các HDH có nhân là Linux [được cung cấp trên trang chủ Kernel](https://www.kernel.org/). Do Linux chỉ cung cấp mã nguồn kernel mà không có trình biên dịch, lớp vỏ shell, không có bootloader, môi trường desktop,...
Khi lấy nhân HDH Linux kết hợp với các phần còn thiếu, ta được các bản phân phối Linux như Ubuntu, Fedora, ArchLinux,....
# Kiến trúc tổng quan hệ thống Linux: 

Hệ điều hành là một phần mềm máy tính phức tạp để giúp người sử dụng có thể tương tác và điều khiển những phần cứng máy tính và các phần mềm chạy trên đó. Những hệ điều hành được xây dựng trên Linux Kernel được gọi là các distro (bản phân phối) của Linux.Cấu trúc của các distro Linux được chia làm 3 thành phần chính, đó là: Kernel Linux, Shell, Applications.
## Kernel Linux
Đây là thành phần quan trọng của mọi hệ điều hành, và được ví như trái tim của HĐH, kernel sẽ chứa các module hay các thư viện để quản lý và giao tiếp giữa phần cứng máy tính và các ứng dụng.
## Shell
Đây là một chương trình có chức năng thực thi các lệnh (command) từ người dùng hoặc từ các ứng dụng yêu cầu, chuyển đến cho Kernel xử lý. Có thể hiểu Shell chính là trung gian nằm giữa Kernel và Application, có nhiệm vụ "phiên dịch" các lệnh từ Application gửi đến Kernel để thực thi.
Các loại shell như sau:

> sh (the Bourne Shell): đây là shell nguyên thủy của UNIX được viết bởi Stephen Bourne vào năm 1974. Đến nay shell sh vẫn sử dụng rộng rãi.

> bash(Bourne-again shell): đây là shell mặc định trên linux.

> csh (C shell): shell được viết bằng ngôn ngữ lập trình C, được viết bởi Bill Joy vào năm 1978.

Ngoài ra còn có các loại shell khác như: ash (Almquist shell), tsh (TENEX C shell), zsh (Z shell).

## Applications 
là các ứng dụng, phần mềm, và tiện ích mà người dùng cài đặt trên máy và sử dụng nó. 

