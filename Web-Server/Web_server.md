# Web - server

## Content

- [HTML - Source code](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/Web_server.md#html---source-code)

- [HTTP - IP restriction bypass]()

### HTML - Source code

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image.png?raw=true)

Start the challengenge:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image1.png?raw=true)

Xem source page: 

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Server/images/image2.png?raw=true)

**Password: nZ^&@q5&sjJHev0**

### HTTP - IP restriction bypass

![img](3)

Start the challenge: 

![img](4)

Xem source page: 

![img](5)

-> Không tìm được gì. 

Dựa vào mô tả thử thách "We’re now managing connections to the intranet using private IP addresses, so it’s no longer necessary to login with a username / password when you are already connected to the internal company network"

-> Có thể liên quan đến địa chỉ mặc định mạng nội bộ `192.168.0.1`

Dựa vào thông tin được cung cấp trên website của thử thách "You should authenticate because you're not on the LAN." Kết hợp cùng thông tin từ mô tả thử thách, có thể liên quan đến `X-Forwarded-For` header, header chứa địa chi IP của client mỗi lần request đi qua proxy, header này có thể chứa `IP LAN` nếu request xuất phát từ mạng nội bộ. 

Request login trông như sau: 

![img](6)

Thử thêm header `X-Forwarded-For: 192.168.0.1` và send request:

![img](7)

-> Khi thêm `X-Forwarded-For: 192.168.0.1`, server có thể nghĩ rằng request đến từ mạng nội bộ và cấp quyền truy cập đặc biệt. 

**Password: Ip_$po0Fing**









