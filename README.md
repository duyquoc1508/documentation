# Some keyword should know

<b>API</b>: Nếu ứng dụng web là 1 tòa nhà kiến cố, vậy API là con đường ra vào toàn thành đó.

<b>Main In The Middle(MITM)</b>: Kẻ chặn Web API thông qua việc can thiệp vào con đường vận chuyển của mạng máy tính.

<b>Cross-origin resource sharing (CORS)</b>: Bọn cướp trên núi giả dạng nông dân để dùng hàng hóa từ thị trấn. CORS không chống việc bất kỳ ai đó gọi API, CORS header chỉ có tác dụng với <b>request từ trình duyệt.</b>

<b>Web Crawler</b>: Là bọn làm hàng hóa nhái chuyên thu thập hoàng hóa xịn, sau đó làm giả hoặc sử dụng cho mục đích riêng

<b>IPN</b> - Instant Payment Notification

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
docker run -it -d --restart=always --name myjenkins -p 8080:8080 -p 50000:50000 -v /var/jenkins_home jenkins/jenkins
```

# Git

[git] Keep empty directory by .gitkeep
<code>.gitkeep</code> là một file giả dùng để giữ chỗ. Vì git không theo dõi thư mục nên có thể bỏ qua các thư mục trống, git chỉ theo dõi sự thay đổi của các file.
