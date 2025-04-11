# Web Client

## Content

- [HTML - disabled buttons](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/Web_Client.md#html---disabled-buttons)
- [Javascript - Authentication](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/Web_Client.md#javascript---authentication)
- [Javascript - Source](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/Web_Client.md#javascript---source)
- [Javascript - Authentication 2](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/Web_Client.md#javascript---authentication-2)
- [Javascript - Obfuscation 1](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/Web_Client.md#javascript---obfuscation-1)
- [Javascript - Obfuscation 2](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/Web_Client.md#javascript---obfuscation-2)

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

### Javascript - Obfuscation 1

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image19.png?raw=true)

Start the challenge:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image20.png?raw=true)

Nhập 1 chuỗi bất kỳ và click `OK`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image21.png?raw=true)

Thông báo sai mật khẩu. Click `OK`:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image22.png?raw=true)

Xem source page:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image23.png?raw=true)

Tìm được chuỗi pass có giá trị được mã hóa `%63%70%61%73%62%69%65%6e%64%75%72%70%61%73%73%77%6f%72%64`. 

Giá trị này giống như đã được URL encode, sử dụng Cyberchef và tìm được bản gốc là `cpasbiendurpassword`

**Password: cpasbiendurpassword**

### Javascript - Obfuscation 2

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image24.png?raw=true)

Start the challenge:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image25.png?raw=true)

Xem source page:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image26.png?raw=true)

Tìm được mã Javascript:

    var pass = unescape("unescape%28%22String.fromCharCode%2528104%252C68%252C117%252C102%252C106%252C100%252C107%252C105%252C49%252C53%252C54%2529%22%29")

Giải chuỗi `unescape%28%22String.fromCharCode%2528104%252C68%252C117%252C102%252C106%252C100%252C107%252C105%252C49%252C53%252C54%2529%22%29`:

    %28 → (

    %22 → "

    %2528 → %28 → ( sau thêm 1 lần unescape

    %252C → %2C → , sau thêm 1 lần unescape

    %2529 → %29 → ) sau thêm 1 lần unescape

->Sau bước này được:

    unescape("String.fromCharCode%28104%2C68%2C117%2C102%2C106%2C100%2C107%2C105%2C49%2C53%2C54%29")

Giải mã tiếp:

Giải chuỗi bên trong:

    %28 → (

    %2C → ,

    %29 → )

Kết quả là: 

    String.fromCharCode(104,68,117,102,106,100,107,105,49,53,54)

Tiếp theo, thực thi hàm `String.fromCharCode(...)`:

    String.fromCharCode(104,68,117,102,106,100,107,105,49,53,54)

Tra bảng mã ASCII:

Số 104 -> Ký tự: h

Số 68 -> Ký tự: D

Số 117 -> Ký tự: u

Số 102 -> Ký tự: f

Số 106 -> Ký tự: j

Số 100 -> Ký tự: d

Số 107 -> Ký tự: k

Số 105 -> Ký tự: i

Số 49 -> Ký tự: 1

Số 53 -> Ký tự: 5

Số 54 -> Ký tự: 6

->Kết quả chuỗi là: "hDufjdki156"

**Password: hDufjdki156**





























