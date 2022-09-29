# cPanel là gì : 

Để vận hành một website, ta cần các thành phần như: Tên miền, hosting (hoặc server), mã nguồn (source code) + cơ sở dữ liệu (database). Việc kết nối các thành phần đòi hỏi phải có kiến thức chuyên sâu và phức tạp. Để đơn giản hóa việc quản trị cho mọi người, các control panel đã được tạo ra như: Cpanel, Directadmin, Webmin, Plesk, VestaCP,… Trong đó, cPanel là control panel được sử dụng phổ biến nhất hiện nay.

cPanel là web hosting control panel (công cụ quản trị web hosting) trên nền tảng Linux phổ biến nhất hiện nay.

Công cụ quản trị web hosting này có giao diện thân thiện với người dùng và hoạt động trên hệ thống phân cấp ba lớp như sau:

* Hosting Company (Nhà cung cấp dịch vụ Hosting).
* Reseller.
* End User (Người dùng cuối).

# Cài đặt

## Nhận 15 ngày cPanel miễn phí
 Đăng ký tại Link : https://cpanel.net/products/trial/

 ## Cài đặt

* Bước 1 : Update Hệ điều hành Centos 7 và cài đặt một số dịch vụ cần thiết

```
yum update -y
yum install perl
yum install curl
```

* Bước 2 : Cài đặt cPanel, chạy các câu lệnh sau:

```
cd /home
curl -o latest -L https://securedownloads.cpanel.net/latest
sh latest
```

Sau khi quá trình cài đặt hoàn tất, truy cập cPanel theo link `https://[ip]:2087`, trong hình là `https:103.170.122.32:2087`

![1](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/1.png)

Trong trang đăng nhập, nhấn `Login`

![2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/2.png)

Trong giao diện nhấn `Forgot Password` , nhập email đã đăng ký theo link, để lấy pass đăng nhập. Sau khi có mail chứa đường link khôi phục mật khẩu như hình, nhấp vào đường link và nhập mật khẩu mới cho email trên.

![3](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/3.png)

Sau khi lấy mật khẩu, nhập emai và mật khẩu vào trang đăng nhập, ta sẽ đăng nhập và kích hoạt bản quyền 15 ngày trên localhost đồng thời có mail xác nhận thông tin mua hàng gửi về email. 

![4](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/4.png)

![5](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/5.png)

Xác nhận lại lần nữa thông tin server 

![6](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/6.png)

Trong giao diện đăng nhập cPanel, đăng nhập vào hệ thống với acc là acc `root` trên server.

![7](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/7.png)

Trong trang cấu hình tiếp theo, nhấn `Finish` để kết thúc quá trình cài đặt.

![8](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/8.png)

Giao diên chính của cPanel :

![9](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/9.png)

# Sử dụng cPanel căn bản :

## Tạo acc mới cho 1 domain

Tại trang quản trị hosting, chọn `Account Information` -> `List Accounts` -> `Create a New Account`

![10](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/10.png)

Điền đầy đủ các thông tin về domain, tên account, mật khẩu,... Xong nhấn `Creat`. Hệ thống sẽ tự tạo acc và thông báo khi xong.

![11](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/11.png)

Sau khi acc được tạo xong, nhấn vào `Account Information` -> `List Accounts` -> `cPanel` để truy cập trang quản trị website.

* Lưu ý : Kiểm tra bản ghi DNS của domain đã trỏ sang IP cPanel chưa, nếu chưa trỏ thỉ sửa lại bản ghi DNS.

## Cài đặt WordPress trên cPanel

Truy cập link `https://[ip]/2082` . VD : `https://103.170.122.32:2083/`, đăng nhập bằng acc đã tạo từ trước.
Sáu khi đăng nhập, trong giao diện quản trị, chọn `Wordpress Toolkit` -> `Install WordPress`. Hệ thống sẽ tự sinh các thông tin như acc truy cập WordPress, thông tin về database, người dùng có thể tự đặt lại các thông số, sau đó nhấn `Install`.

![14](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/14.png)

Sau khi cài đặt xong, truy cập thử trang web ta sẽ thấy giao diện `WordPress`.

![15](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/15.png)

## Sao lưu và phục hổi wordpess qua cPanel

Xem trong wordpess hiện có 5 bài post, ta thực hiện back up qua cPanel sau đó xóa bài post.

![16](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/16.png)

* Sao lưu qua cPanel: 
 Trong trang quản lý domain, chọn `Back Up/Restore` . Chọn nơi lưu file backup và nhấn `Back Up`.

 ![17](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/17.png)

 Sau khi back up xong ta có file backup như hình :

![18](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/18.png)

* Thực hiện xóa post, truy cập trang admin wordpress, chọn post và đưa vào thùng rác (Trash), truy nhập vào thùng rác và xóa hẳn các bài post trên, sau đó check lại. 

![19](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/19.png)

* Restore wordpress

Trong trang quản lý domain, chọn `Back Up/Restore` . Chọn file backup và nhấn `Restore`. Sau khi restore xong, load lại trang `https:[domain]/ưp-admin` để kiểm tra.

![20](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/20.png)

## Thêm tài khoản Email

cPanel giúp dễ dàng tạo một địa chỉ email cho riêng bạn, sử dụng domain duy nhất của bạn. Chọn Email Account trong mục Email. Nhập địa chỉ mail mà bạn muốn lập cũng như mật khẩu và click Create Account.
Sau đó, bạn có thể truy cập tài khoản webmail ngay từ cPanel hoặc thiết lập tài khoản mail mới để làm việc với ứng dụng email độc lập.

![21](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/21.png)

## Upload và quản lý file

Để truy cập, tìm tùy chọn `File Manager` trong mục `File`.
Bạn click vào `File Manager` để chuyển sang một giao diện mới giúp bạn thực hiện.

![22](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/22.png)

Đến các vị trí khác nhau bằng cách sử dụng cây thư mục ở bên trái.
Quản lý các tệp riêng lẻ trong giao diện trung tâm.
Thực hiện các tác vụ khác nhau, bao gồm tải lên và chỉnh sửa tệp, trên thanh top bar.

![23](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/23.png)

## Backup website 

Miễn là site của bạn không quá lớn (một số host áp đặt giới hạn), bạn luôn có thể backup web của mình theo cách thủ công từ dashboard của cPanel.

Để bắt đầu, tìm tùy chọn `Backup` hoặc `Backup Wizard` trong mục `Files`. Sau đó, làm theo trình hướng dẫn để hoàn thành back up.

![24](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/24.png)

# Đổi mật khẩu tài khoản qua Web Host Manager

Tại trang quản trị hosting, chọn `Account Information` -> `List Accounts` , chọn domain chứa acc cần đổi pass, nhập pass word mới và nhấn nhấn `Change`.

# Tạo subdomain

Trong trang quản lý domain, chọn `Domain` -> `Subdomains`, nhập thông tin subdomain mới và nhấn `Create`

![27](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/27.png)

# Cài SSL trên cPanel

Trong trang quản lý domain, chọn mục `Security` -> `SSL/TLS`, chọn trình mặc định, nhấn `Save` để hệ thông tự tạo khóa SSL, sau đó trở về trang quản lý domain. Trong trang quản lý domain, chọn `Security` -> `SSL/TLS Status` -> click các domain cần thêm SSL, nhấn `Run AutoSSL`.

![25](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/25.png)


Sau khi chạy xong, kết quả domain sẽ có thông báo hình ổ khóa xanh như ảnh.

![26](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/26.png)

## Quản trị người dùng trong domain
 Chọn `Preferences` =>`User Manager` 

 # Quản trị domain

 * `Metrics` -> `Errors` : lỗi website

 * `Metrics` -> `Bandwidth` : Thống kee băng thông

 * `Metrics` -> `Raw Access` : Log truy cập website

 * `Advanced` -> `Terminal` : hỗ trợ chương trình giao diện cửa sổ dòng lệnh

 * `Software` -> `MultiPHP Manager` : Quản lý nhiều version PHP trên website.

![29](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/cPanel/29.png)
 
 * roundcube/horde : Phần mềm webmail

# Tổng kết 

## Ưu điểm 

* Dễ sử dụng

* cPanel được thử nghiệm kỹ càng, các tính năng tương tác với filer/foder phản hồi nhanh

* Có trình cài đặt tự động

* Có tính bảo mật cao

## Nhược điểm 

* nhiều chức năng không cần thiết gây lãng phí tài nguyên

* người dùng vẫn sử dụng các phiên bản cũ nhiều

* là phần mềm trả phí

