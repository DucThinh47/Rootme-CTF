# Web Client

## Content

- [HTML - disabled buttons](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/Web_Client.md#html---disabled-buttons)
- [Javascript - Authentication]()

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

![img](4)

Start the challenge:

![img](5)

Xem source page:

![img](6)

![img](7)

Tìm được file `/login.js`, xem nội dung file này:

![img](8)

Tìm được `username=4dm1n` và `password=sh.org`, đăng nhập:

![img](9)

**Password: sh.org**








