# Web - server

## Content

- [HTML - Source code](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#html---source-code)

- [HTTP - IP restriction bypass](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#http---ip-restriction-bypass)

- [HTTP - Open redirect]()

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

![img](8)

Start the challenge:

![img](9)

Xem source page: 

![img](10)

Có thể thấy 3 URL dẫn đến từng domain tương ứng Facebook, Twitter, Stack, nhưng lại có một tham số `h` đằng sau, giá trị tham số này trông như đã được băm. 

Thử băm `https://facebook.com` sử dụng thuật toán `md5`, thu được giá trị băm `a023cfbf5f1c39bdf8407f28b60cd134`, giống với giá trị `h` tương ứng với domain Facebook. 

Theo mô tả thử thách "Find a way to make a redirection to a domain other than those showed on the web page.". Thử request đến 1 domain khác là `https://youtube.com` với giá trị băm là `e62e24467ebdddf3fe7cc0e6970f01af`:

![img](11)

**Password: e6f8a530811d5a479812d7b82fc1a5c5**














