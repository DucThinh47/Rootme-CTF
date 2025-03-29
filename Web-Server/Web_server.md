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






























