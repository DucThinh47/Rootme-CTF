# Web Client

## Content

- [HTML - disabled buttons](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/Web_Client.md#html---disabled-buttons)
- [Javascript - Authentication](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/Web_Client.md#javascript---authentication)

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








