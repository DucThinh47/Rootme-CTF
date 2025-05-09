# Web Client

## Content

- [HTML - disabled buttons](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/Web_Client.md#html---disabled-buttons)
- [Javascript - Authentication](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/Web_Client.md#javascript---authentication)
- [Javascript - Source](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/Web_Client.md#javascript---source)
- [Javascript - Authentication 2](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/Web_Client.md#javascript---authentication-2)
- [Javascript - Obfuscation 1](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/Web_Client.md#javascript---obfuscation-1)
- [Javascript - Obfuscation 2](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/Web_Client.md#javascript---obfuscation-2)
- [Javascript - Native code](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/Web_Client.md#javascript---native-code)
- [Javascript - Webpack]()

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
### Javascript - Native code

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image27.png?raw=true)

Start the challenge:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image28.png?raw=true)

Thử nhập 1 chuỗi bất kỳ:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image29.png?raw=true)

Xem source page:

    <html>
    <head>
    <title>Plop</title>
    </head>
    <body><link rel='stylesheet' property='stylesheet' id='s' type='text/css' href='/template/s.css' media='all' /><iframe id='iframe' src='https://www.root-me.org/?page=externe_header'></iframe>

    <script>
    É=-~-~[],ó=-~É,Ë=É<<É,þ=Ë+~[];Ì=(ó-ó)[Û=(''+{})[É+ó]+(''+{})[ó-É]+([].ó+'')[ó-É]+(!!''+'')[ó]+({}+'')[ó+ó]+(!''+'')[ó-É]+(!''+'')[É]+(''+{})[É+ó]+({}+'')[ó+ó]+(''+{})[ó-É]+(!''+'')[ó-É]][Û];Ì(Ì((!''+'')[ó-É]+(!''+'')[ó]+(!''+'')[ó-ó]+(!''+'')[É]+((!''+''))[ó-É]+([].$+'')[ó-É]+'\''+''+'\\'+(ó-É)+(É+É)+(ó-É)+'\\'+(þ)+(É+ó)+'\\'+(ó-É)+(ó+ó)+(ó-ó)+'\\'+(ó-É)+(ó+ó)+(É)+'\\'+(ó-É)+(É+ó)+(þ)+'\\'+(ó-É)+(É+ó)+(É+ó)+'\\'+(ó-É)+(ó+ó)+(ó-ó)+'\\'+(ó-É)+(ó+ó)+(É+É)+'\\'+(É+ó)+(ó-ó)+'\\'+(É+É)+(þ)+'\\'+(ó-É)+(ó-ó)+(É+ó)+'\\'+(ó-É)+(É+ó)+(ó+ó)+'\\'+(ó-É)+(ó+ó)+(É+É)+'\\'+(ó-É)+(ó+ó)+(É)+'\\'+(ó-É)+(É+É)+(É+ó)+'\\'+(ó-É)+(þ)+(É)+'\\'+(É+É)+(ó-ó)+'\\'+(ó-É)+(É+ó)+(É+É)+'\\'+(ó-É)+(É+É)+(É+ó)+'\\'+(É+É)+(ó-ó)+'\\'+(ó-É)+(É+ó)+(É+ó)+'\\'+(ó-É)+(É+ó)+(þ)+'\\'+(ó-É)+(ó+ó)+(É+É)+'\\'+(É+É)+(ó-ó)+'\\'+(ó-É)+(É+É)+(É+É)+'\\'+(ó-É)+(É+É)+(É+ó)+'\\'+(É+É)+(ó-ó)+'\\'+(ó-É)+(ó+ó)+(ó-ó)+'\\'+(ó-É)+(É+É)+(ó-É)+'\\'+(ó-É)+(ó+ó)+(ó)+'\\'+(ó-É)+(ó+ó)+(ó)+'\\'+(ó-É)+(É+É)+(É+ó)+'\\'+(É+É)+(þ)+'\\'+(É+ó)+(ó-É)+'\\'+(þ)+(ó)+'\\'+(ó-É)+(É+ó)+(ó-É)+'\\'+(ó-É)+(É+É)+(ó+ó)+'\\'+(É+ó)+(ó-ó)+'\\'+(ó-É)+(É+É)+(ó-É)+'\\'+(þ)+(É+ó)+'\\'+(þ)+(É+ó)+'\\'+(É+É)+(þ)+'\\'+(ó-É)+(ó+ó)+(É+É)+'\\'+(ó-É)+(É+ó)+(þ)+'\\'+(ó-É)+(ó+ó)+(É+É)+'\\'+(ó-É)+(É+ó)+(þ)+'\\'+(ó+ó)+(ó-É)+'\\'+(ó+ó)+(É)+'\\'+(ó+ó)+(ó)+'\\'+(ó-É)+(É+ó)+(É+É)+'\\'+(ó-É)+(É+ó)+(þ)+'\\'+(ó-É)+(É+ó)+(É+É)+'\\'+(É+É)+(þ)+'\\'+(É+ó)+(ó-É)+'\\'+(ó-É)+(þ)+(ó)+'\\'+(ó-É)+(É+É)+(ó-É)+'\\'+(ó-É)+(É+ó)+(É+É)+'\\'+(ó-É)+(É+É)+(É+ó)+'\\'+(ó-É)+(ó+ó)+(É)+'\\'+(ó-É)+(ó+ó)+(É+É)+'\\'+(É+ó)+(ó-ó)+'\\'+(É+É)+(þ)+'\\'+(ó-É)+(É+É)+(É)+'\\'+(ó-É)+(ó+ó)+(É)+'\\'+(ó-É)+(É+É)+(ó-É)+'\\'+(ó-É)+(ó+ó)+(ó+ó)+'\\'+(ó-É)+(É+ó)+(þ)+'\\'+(É+É)+(þ)+'\\'+(É+ó)+(ó-É)+'\\'+(þ)+(ó)+'\\'+(ó-É)+(þ)+(É+ó)+'\\'+(ó-É)+(É+É)+(É+ó)+'\\'+(ó-É)+(É+ó)+(É+É)+'\\'+(ó-É)+(ó+ó)+(ó)+'\\'+(ó-É)+(É+É)+(É+ó)+'\\'+(ó-É)+(þ)+(ó)+'\\'+(ó-É)+(É+É)+(ó-É)+'\\'+(ó-É)+(É+ó)+(É+É)+'\\'+(ó-É)+(É+É)+(É+ó)+'\\'+(ó-É)+(ó+ó)+(É)+'\\'+(ó-É)+(ó+ó)+(É+É)+'\\'+(É+ó)+(ó-ó)+'\\'+(É+É)+(þ)+'\\'+(ó-É)+(É+É)+(ó+ó)+'\\'+(ó-É)+(É+É)+(ó-É)+'\\'+(ó-É)+(É+ó)+(ó-É)+'\\'+(ó-É)+(É+ó)+(É+É)+'\\'+(É+ó)+(ó+ó)+'\\'+(É+ó)+(ó+ó)+'\\'+(É+ó)+(ó+ó)+'\\'+(É+É)+(þ)+'\\'+(É+ó)+(ó-É)+'\\'+(þ)+(ó)+'\\'+(ó-É)+(þ)+(É+ó)+'\'')())()
    </script>

    </body>
    </html>

Tìm được 1 đoạn mã JS có vẻ đã bị fuzz, thử truy cập https://www.dcode.fr/javascript-unobfuscator để giải mã nội dung:

![img](https://github.com/DucThinh47/Rootme-CTF/blob/main/Web-Client/images/image30.png?raw=true)

Kết quả thu được: 

    function anonymous( ) { a=prompt('Entrez le mot de passe');if(a=='toto123lol'){alert('bravo');}else{alert('fail...');} }

Sau khi format lại:

    function anonymous() {
        a = prompt('Entrez le mot de passe');
        if (a == 'toto123lol') {
            alert('bravo');
        } else {
            alert('fail...');
        }
    }
**Password: toto123lol**
### Javascript - Webpack

![img](32)

Start the challenge:

![img](33)

Xem source page:

    <!DOCTYPE html>
    <html>
    <head>
        <meta charset=utf-8>
        <meta name=viewport content="width=device-width,initial-scale=1">
        <title>Javascript - Webpack</title>
        <link href=./static/css/app.f213bed71a5d27ded35fdf00a1963840.css rel=stylesheet>
    </head>
    <body>
        <link rel='stylesheet' property='stylesheet' id='s' type='text/css' href='/template/s.css' media='all' />
        <iframe id='iframe' src='https://www.root-me.org/?page=externe_header'></iframe>
        <div id=app></div>
        <script type=text/javascript src=./static/js/manifest.2ae2e69a05c33dfc65f8.js></script>
        <script type=text/javascript src=./static/js/vendor.458c9f5863b8f28e5570.js></script>
        <script type=text/javascript src=./static/js/app.a92c5074dafac0cb6365.js></script>
    </body>
    </html>
Tìm được 3 file khả nghi:
- /static/css/app.f213bed71a5d27ded35fdf00a1963840.css
- /static/js/manifest.2ae2e69a05c33dfc65f8.js
- /static/js/vendor.458c9f5863b8f28e5570.js
- /static/js/app.a92c5074dafac0cb6365.js

Thử truy cập `/static/js/app.a92c5074dafac0cb6365.js`:

![img](34)

Tìm được 1 URL mapping tới 1 file .js khác ` sourceMappingURL=app.a92c5074dafac0cb6365.js.map`. Thử truy cập file này:

![img](35)

Xuất hiện yêu cầu tải file. Tải về và xem nội dung file: 

![img](36)

Tìm được flag!

**Password: BecauseSourceMapsAreGreatForDebuggingButNotForProduction**













































