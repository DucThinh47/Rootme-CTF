# Web Client

## Content

- [HTML - disabled buttons](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/Web_Client.md#html---disabled-buttons)
- [Javascript - Authentication](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/Web_Client.md#javascript---authentication)
- [Javascript - Source](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/Web_Client.md#javascript---source)
- [Javascript - Authentication 2](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/Web_Client.md#javascript---authentication-2)

### HTML - disabled buttons

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image.png?raw=true)

Start the lab:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image1.png?raw=true)

Xem source page:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image2.png?raw=true)

Để ý trong 2 thẻ `<input>` có trường `disabled`, xóa 2 trường này đi và nhập 1 giá trị tùy ý rồi click `Member access`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image3.png?raw=true)

**Password: HTMLCantStopYou**

### Javascript - Authentication

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image4.png?raw=true)

Start the challenge:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image5.png?raw=true)

Xem source page:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image6.png?raw=true)

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image7.png?raw=true)

Tìm được file `/login.js`, xem nội dung file này:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image8.png?raw=true)

Tìm được `username=4dm1n` và `password=sh.org`, đăng nhập:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image9.png?raw=true)

**Password: sh.org**

### Javascript - Source

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image10.png?raw=true)

Start the challenge:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image11.png?raw=true)

Thử nhập một chuỗi ngẫu nhiên và click `OK`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image12.png?raw=true)

Thông báo sai mật khẩu. 

Xem source page:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image13.png?raw=true)

Tìm được password cho cả website và challenge là `123456azerty`

**Password: 123456azerty**

### Javascript - Authentication 2

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image14.png?raw=true)

Start the challenge:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image15.png?raw=true)

Xem source page:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image16.png?raw=true)

Tìm được file `login.js`, thử xem nội dung file:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image17.png?raw=true)

Dựa vào đoạn mã, có thể thấy `username` và `password` được so sánh với các phần tử trong mảng `TheLists`, biến `TheSplit` sẽ tách các phần tử trong mangr này khỏi dấu `:`, tương đương với `TheUsername=GODEN` và `ThePassword=HIDDEN`, nhập 2 giá trị này vào trang Login:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image18.png?raw=true)

**Password: HIDDEN**















