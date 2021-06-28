# Some keyword should know

<b>API</b>: Nếu ứng dụng web là 1 tòa nhà kiến cố, vậy API là con đường ra vào toàn thành đó.

<b>Main In The Middle(MITM)</b>: Kẻ chặn Web API thông qua việc can thiệp vào con đường vận chuyển của mạng máy tính.

<b>Web Crawler</b>: Là bọn làm hàng hóa nhái chuyên thu thập hoàng hóa xịn, sau đó làm giả hoặc sử dụng cho mục đích riêng

<b>IPN:</b> Instant Payment Notification

<b>API:</b> Application Programing Interface

<b>SDK:</b> Software Development Kit

<b>Deep link:</b> Deep link là các đường dẫn được chia sẻ trên nền tảng mobile, vận hành khá giống hyperlink nhưng thay vì dẫn người dùng đến ngay một địa chỉ web page nào đó, deep link dẫn họ tới một màn hình cụ thể ngay trong ứng dụng.

#### Set Access-Control-Allow-Origin header.

Đây là header được <b>server trả về</b> để báo cho trình duyệt biết: "Tao chỉ cho phép trang web có domain này gọi đến tao thôi". Phương thức lưu giữ phiên đăng nhập sử dụng cookie sẽ có đặc điểm của cookie đó là tự gắn cookie vào request khi gọi tới domain gốc. Do vậy nếu bạn vào trang web fakezalo.com, trang web này hoàn toàn có thể gọi lên API của Zalo để lấy thông tin người dùng đang đăng nhập hiện tại của bạn (do khi gọi API của Zalo sẽ tự có cookie của Zalo). Access-Control-Allow-Origin header sinh ra là để phòng chống việc này.

#### Mã hóa API

Mặc dù HTTPS là giao thức HTTP đi kèm mã hóa đầu cuối để phòng chống MITM. Tuy nhiên các dev thấy đây vẫn là chưa đủ, và họ đã đi thêm 1 bước nữa trên con đường phòng chống những kẻ tò mò.
Chung quy lại là phương pháp này bao gồm các bước:

1. Tạo 1 Secret Key trên server.
2. Chia sẻ Secret Key giữa client và server (Qua fix cứng trong code, file config, API).
3. Dùng Secret Key với mã hóa AES (hoặc bất kỳ thuật toán mã hóa tin cậy nào đó) mã hóa response trả về từ server.
4. Dùng Secret Key để giải mã trở lại lấy thông tin từ Response.

Về cơ bản thì nó không khác gì concept của HTTPS, tức là mã hóa và giải mã đầu cuối để người ở giữa không đọc được. Cái khác ở đây chính là HTTPS được trình duyệt thực hiện tự động, còn mã hóa API ta phải tự thực hiện trong code client.

# Docker

Docker cải thiện quá trình development and deployment

Development: quá trình code giữa các member trong team không

<b>Before container:</b>

- Install nhiều phần mềm
- Quá trình install qua nhiều step
- Khác hệ điều hành
- Cồng kềnh phức tạp => tốn nhiều thời gian

<b>After container</b>

- One command to install the app
- Packaged with all needed configuration
- Run same app with 2 diff version

Deployment:
<b>Before container</b>

- Dependency version conflict
- ...

Docker Compose takes care of creating a common Network

1. Build images

```
docker build . -t name_image:v1
```

2. Running the image locally

```
docker run -d -it -p 3000:3000 name_image:v1
```

3. update container <b>created</b>

```
docker update --restart=always 0576df221c0b
```

- Volume

$ docker run -v /home/mount/data:/var/lib/mysql/data

$ docker run -v host_volumes:container_volumes

- host_volumes: where on the host file system the reference is made
- container_volumes: auto create by docker, each container a folder is generated the gets amounted
- Can reference volumes by name

## Lưu ý

Mỗi lệnh `RUN` chạy sẽ sinh ra 1 image layer, Nên gom các lệnh `RUN` lại => giảm số lượng imange layer sinh ra => giảm được size, tối ưu hóa thời gian build

Các instruction hay thay đổi thì nên để phía dưới để tối ưu

## Các khái niệm liên quan

### Murable Infrastructure:

Tức là: có sự thay đổi giữa các server (dev - production ...) dẫn tới sự hoạt động không ổn định của application, hay là app sẽ chạy lỗi => docker có thể khắc phục

### Immurable Infrastructure

Infrastructure: không thay đổi cho dù deploy lên môi trường nào đi chăng nữa

### Infrastructure as code (code: dockerfile)

Sử dụng dockerfile để quản lý runtime enviroment

Docker = Immurable Infrastructure + Infrastructure as code

# Jenkins

1. Run jenkins and keep start automatically when Docker daemon restarts

```
docker run -it -d --restart=always --name myjenkins -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home  jenkins/jenkins
```

# Git

[git] Keep empty directory by .gitkeep
<code>.gitkeep</code> là một file giả dùng để giữ chỗ. Vì git không theo dõi thư mục nên có thể bỏ qua các thư mục trống, git chỉ theo dõi sự thay đổi của các file.

# Google Search Skills

- Notes:
  - Thứ tự xuất hiện từ khóa khác nhau sẽ cho ra kết quả khác nhau
  - Viết thường viết hoa không quan trọng
  - Có một số kí tự đặc biệt mà google chưa phân biệt được
  - Không cần quan tâm đến chính tả, ngữ pháp (search tiếng anh)
  - Chú ý đến mạo từ đầu câu
- Tips:

  - Định nghĩa nhanh

    `[define blockchain]` thay vì `[what is blockchain]`

  - Tìm từ trang cụ thể

    `[nodejs site:stackoverflow.com]` kèm với domain

  - Tìm theo loại file

    `[UML filetype:pdf]` kèm với file type

  - Loại bỏ từ khóa bất kì (đặt dấu “-” trước từ khóa)

    `[sách nguyễn ngọc thuần -tiki -fahasa -lazada -vinabook]`

  - Tìm câu trích dẫn (đặt câu trích dẫn vào dấu ngoặc kép)
  - Tìm kiếm theo nhiều từ khóa (kết hợp keyword với 'or')

    `[keywordA OR keywordB]`

  - Kết quả trả ra bắt buộc phải có từ khóa đó (dùng 'intext' trước keyword cần có)

    `[TừKhóa1 TừKhóa2 intext:TừKhóa3]`

## Javascript

- JS array vs object vs map
  - Cần truy cập vào 1 mảng bằng khóa mà không quan tâm đến thứ tự => dùng object
  - Nếu quan tâm đến thứ tự chèn => dùng Map (new Map())

## Web security knowledge (HTTPS, TLS, SSL, CORS, CSP)

https://dev.to/ahmedatefae/web-security-knowledge-you-must-understand-it-part-i-https-tls-ssl-cors-csp-298l

### HTTPS

The secure version of HTTP, It uses encryption communication protocol, named Transport Layer Security (TLS), was known as Secure Sockets Layer (SSL).

### TLS (Transport Layer Security)

Bất kì ứng dụng hoặc trang web nào sử dụng TLS đều phải cài đặt chứng chỉ TLS (còn được gọi là chứng chỉ SSL) trên máy chủ. được cấp cho người sở hữu Domain để cài đặt chứng chỉ đó trên máy chủ.

Nó chứa thông tin rất quan trọng về chủ sở hữu, các khóa riêng tư và công khai để sử dụng trong việc mã hóa và giải mã thông tin liên lạc.

![](images/https-handshake.png 'https handshake')

### SSL (Secure Sockets Layer)

### What is the difference between TLS and SSL?

SSL is the older version of the TLS, the name changed after the Internet Engineering Task Force (IETF) be the owner of the SSL development after Netscape, some developer nowadays uses the SSL and TLS to referring for the same thing.

### CORS (Cross-origin resource sharing)

Bọn cướp trên núi giả dạng nông dân để dùng hàng hóa từ thị trấn. CORS không chống việc bất kỳ ai đó gọi API, CORS header chỉ có tác dụng với <b>request từ trình duyệt.</b>

### CSP (Content Security Policy)

lớp bảo mật hơn giúp phát hiện và giảm thiểu các loại tấn công khác nhau như (Cross-Site Scripting (XSS), injection attacks, ClickJacking, ETC ...).

CSP sử dụng khái niệm Directives mà mọi Chỉ thị phải chỉ định tài nguyên có thể tải từ đâu, ngăn trình duyệt tải dữ liệu từ bất kỳ vị trí nào khác.

#### XSS (Cross-Site Scripting)

Lỗ hổng cho phép hacker chèn script vào trang web để client thự thi nó để lấy các dữ liệu nhạy cảm như cookie, session’s info and site-specific information. Vì web-app không sử dụng đủ các phương thức xác thực và mã hóa. trình duyệt của người dùng thì không thể phát hiện ra 1 đoạn script người dùng chèn vào có nguy hiểm hay không

#### Data injection attacks

là một mã được được đưa vào mạng. mã này lấy tất cả thông tin từ database đến kẻ tấn công. SQL injection là một loại

#### Click jacking || UI redress attack (Tấn công chỉnh sửa giao diện người dùng)

attacker đành lừa người dùng nhấp vào nút hoặc liên kết trên 1 trang khác sử dụng nhiều lớp trong suốt. có thể redirect tới các trang mà người dùng không mong muôn

## Web server

### Nginx
