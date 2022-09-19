# Định nghĩa

DNS là viết tắt của cụm từ Domain Name System, mang ý nghĩa đầy đủ là hệ thống phân giải tên miền. DNS được phát minh vào năm 1984 cho Internet, chỉ một hệ thống cho phép thiết lập tương ứng giữa địa chỉ IP và tên miền.

![1](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/DNS/1.jpg)

# Chức năng :

Mỗi máy tính khi kết nối vào Internet sẽ được gán cho 1 địa chỉ IP (Ví dụ: 1414.1158.62462) riêng biệt và không trùng lẫn với bất kỳ máy tính nào khác trên thế giới. Cũng giống như vậy đối với website cũng có địa chỉ IP riêng biệt của website đó (địa chỉ IP của host đặt website).

Tuy nhiên, mỗi website đều có một địa chỉ IP là các con số khá dài và khó nhớ khiến bạn không thể nhớ rõ con số IP đó.

> Ví dụ địa chỉ IP là 103.28.36.250 dẫn đến website nhanhoa.com, thay vì gõ 103.28.36.250 trên url trình duyệt. Lúc này là lúc DNS “trổ tài chuyển đổi” (ánh xạ) dãy số địa chỉ IP thành những ký tự thân thiện hơn. Chính vì nhờ có giao thức DNS nên bạn không cần phải nhớ địa chỉ IP để vào website Nhân Hòa mà chỉ cần nhớ nhanhoa.com là được.

Nói cách khác, DNS cũng giống như một danh bạ điện thoại dành riêng cho Internet. Nếu bạn biết tên của một người nhưng không biết số điện thoại hay ngược lại, bạn có thể tham khảo trong sổ danh bạ dễ dàng.

## Tra cứu thông tin 

Dùng trang `https://infowebstats.com/dns-lookup` để tra cứu thông tin DNS của 1 domain

VD : Tra cứu thông tin của nhanhoa.com

![2](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/DNS/2.png)

# Cách thức hoạt động

* Bước 1 : Người dùng nhập một website vào cửa sổ trình duyệt, trình duyệt sẽ kiểm tra bộ nhớ cache cục bộ của trình duyệt xem có IP của của trang web được đề cập không. Nếu không có thông tin IP website trên, trình duyệt sẽ gửi 1  yêu cầu phân dải  địa chỉ website trên đến DNS Recursor (DNS - Đệ quy) thường đặt ở ISP. 

![3](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/DNS/3.png)

* Bước 2 : DNS Recursor kiểm tra trong cache memory xem có thông tin về website đấy không. Nếu DNS Recursor không có IP của website trên, nó sẽ hỏi DNS Root (cũng thường được gọi là Name Server). DNS Root sẽ tìm kiếm và gửi lại DNS Recursor thông tin các TLD Name server (Top-level Domain Name server) quản lý các domain có phần mở rộng khớp với phần mở rộng website đang tìm kiếm.

![4](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/DNS/4.png)

* Bước 3 : DNS Recursor tiếp tục hỏi các TLD Name server về thông tin website, TLD Name server kiểm tra và gửi lại địa chỉ Authoritative Name server là server quản lý tên miền đó.

* Bước 4 : DNS Recursor tiếp tục hỏi Authoritative Name server về thông tin website, Authoritative Name server kiểm tra và gửi lại DNS Recursor địa chỉ IP của miền được yêu cầu ban đầu.

* Bước 5 : DNS Recursor lưu lại thông tin tên miền và địa chỉ IP vừa phân giải, đồng thời gửi thông tin trêm về trình duyệt của người dùng. Trình duyệt dựa vào địa chỉ IP nhận được, tạo kết nối HTTP/HTTPS đến server chứa trang web mà người dùng yêu cầu.

![5](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/DNS/5.png)

# Các giao thức phổ biến

DNS chủ yếu sử dụng giao thức UDP trên cổng số 53 để phục vụ các yêu cầu dịch vụ. Truy vấn DNS bao gồm một yêu cầu UDP duy nhất từ ​​các máy khách, theo sau là một UDP trả lời duy nhất từ máy chủ. Giao thức TCP được sử dụng khi kích thước dữ liệu phản hồi vượt quá 512 byte hoặc cho các tác vụ khác.
# Các loại bản ghi trên DNS server

DNS record là bản ghi nằm trong DNS servers cung cấp thông tin về cơ sở dữ liệu DNS, cho biết các tên miền, địa chỉ IP gắn với tên miền và cách xử lý các yêu cầu với tên miền đó… Tất cả các tên miền trên internet đều phải có một vài bản ghi DNS cần thiết để người dùng có thể truy cập trang web khi nhập tên miền và thực hiện các mục đích khác.

Có 11 loại bản ghi :

* SOA (START OF AUTHORITY) : Trong mỗi tập tin cơ sở dữ liệu DNS phải có một và chỉ một record SOA (Start of Authority). Bao gồm các thông tin về domain trên DNS Server, thông tin về zone transfer.

* NS (Name Server) : NS chứa địa chỉ IP của DNS Server cùng với các thông tin về domain đó.NS record là một loại DNS record giúp xác định thông tin của một tên miền cụ thể được khai báo và quản lý trên máy chủ nào.

__VD__ : nhanhoa.com IN NS  ns2011.nhanhoa.com
     nhanhoa.com IN NS  nhanhoa-rl.nhanhoa.com
     => có 2 server có domain nhanhoa.com
* A : là một record căn bản và quan trọng, dùng để ánh xạ từ một domain thành địa chỉ IP cho phép có thể truy cập website. Đây là chức năng cốt lõi của hệ thống DNS. Nếu không có các bản ghi này, URL sẽ không trỏ đến địa chỉ IP của máy chủ và sẽ không hiển thị trang web. Hiện tượng này còn được gọi là “không phân giải”. Ngoài tên miền chính, bạn có thể sẽ thêm bản ghi A cho tên máy chủ của mình và bất kỳ tên miền phụ nào phân giải đến một máy chủ khác. Trường Data của bản ghi A sẽ luôn là địa chỉ IP.

__VD__ : nhanhoa.com    IN	A	103.28.36.250

* AAAA : tương tự như bản ghi A, nhưng thay vì địa chỉ IPv4 sẽ là địa chỉ IPv6.

* PTR :  Bản ghi PTR giúp chuyển đổi từ địa chỉ IP sang tên miền.

* SRV : được sử dụng để xác định vị trí các dịch vụ đặc biệt trong 1 domain, ví dụ tên máy chủ và số cổng của các máy chủ cho các dịch vụ được chỉ định.

* CNAME (Canonical Name) : CNAME được giải thích là một dạng bản ghi tài nguyên trong Hệ thống tên miền (DNS), quy định một tên miền là bí danh của một tên miền chuẩn khác.

__VD__ : nhanhoa.com   	    IN  A	    	103.28.36.250
         www.nhanhoa.com	IN  CNAME		nhanhoa.com
        => IP của website www.nhanhoa.com được truy vấn thông qua nhanhoa.com tương đương với IP 103.28.36.250

* MX  (Mail Exchange) : có tác dụng xác định, chuyển thư đến domain hoặc subdomain đích.

* TXT : được sử dụng để cung cấp khả năng liên kết văn bản tùy ý với máy chủ. Chủ yếu dùng trong mục đích xác thực máy chủ với tên miền.

* DKIM : Là bản ghi dùng để xác thực người gửi bằng cách mã hóa một phần email gửi bằng một chuỗi ký tự, xem như là chữ ký.Khi email được gửi đi máy chủ mail sẽ kiểm so sánh với thông tin bản ghi đã được cấu hình trong DNS để xác nhận.

* SPF : được tạo ra nhầm đảm bảo các máy chủ mail sẽ chấp nhận mail từ tên miền của khách hàng chỉ được gửi đi từ server của khách hàng.

![6](https://github.com/laitiennhanhoa/Thu-viec-tai-Nhan-Hoa/blob/main/images/DNS/6.png)


Nguồn tham khảo 1[1](https://blog.cloud365.vn/linux/dns-record/#2-ns-name-server) và 2[2](https://zonedns.vn/faq.html)

# Cài đặt DNS Server

## Trên Linux

## Trên windows server
