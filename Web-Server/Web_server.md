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




























































