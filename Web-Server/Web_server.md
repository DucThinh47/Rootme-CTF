# Web - server

## Content

- [HTML - Source code](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#html---source-code)

- [HTTP - IP restriction bypass](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#http---ip-restriction-bypass)

- [HTTP - Open redirect](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#http---open-redirect)

- [HTTP - User-agent](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#http---user-agent)

- [Weak password](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#weak-password)

- [PHP - Command injection]()

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

![img](19)

Start the challenge: 

![img](20)

Dựa vào mô tả thử thách "Find a vulnerabilty in this service and exploit it. You must manage to read index.php", thử truy cập `/index.php`:

![img](21)

-> Không đọc được. Thử nhập `index.php` và click submit:

![img](22)

-> Cũng không xem được. 

Thử nhập `127.0.0.1`:

![img](23)

Thử nhập `127.0.0.1&&pwd`:

![img](24)

-> Câu lệnh `pwd` được thực thi, có thể website tồn tại lỗ hổng `Command Injection`. Thử nhập `127.0.0.1&&ls`:

![img](25)

-> Tìm được file `index.php`, thử nhập `127.0.0.1&&ls&&cat index.php`:

![img](26)

Xem response trong Burp Suite: 

![img](27)

-> Nội dung `index.php`:

    <?php 
    $flag = "".file_get_contents(".passwd")."";
    if(isset($_POST["ip"]) && !empty($_POST["ip"])){
            $response = shell_exec("timeout -k 5 5 bash -c 'ping -c 3 ".$_POST["ip"]."'");
            echo $response;
    }
    ?>

Qua nội dung đoạn mã, có thể flag nằm trong file `.passwd`, thử nhập `127.0.0.1&&cat .passwd`:

![img](28)

**Password: S3rv1ceP1n9Sup3rS3cure**





















