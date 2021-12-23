# Some keyword should know

<b>NPM</b>: Manages packages, you can install node.js packages, but doesn't make life easy executing any.

<b>NPX</b>: A tool for executing Node packages.

It doesn't matter whether you install that package globally or locally. NPX will temporarily install and run it. NPM also run package if you configure a package.json file and include it in the script section
> So remember this, if you want to check/run a node package quickly without installing locally or globally use NPX.

[NPM vs. NPX](https://stackoverflow.com/questions/50605219/difference-between-npx-and-npm)

<b>API</b>: Nếu ứng dụng web là 1 tòa nhà kiến cố, vậy API là con đường ra vào toàn thành đó.

<b>Main In The Middle(MITM)</b>: Kẻ chặn Web API thông qua việc can thiệp vào con đường vận chuyển của mạng máy tính.

<b>Web Crawler</b>: Là bọn làm hàng hóa nhái chuyên thu thập hoàng hóa xịn, sau đó làm giả hoặc sử dụng cho mục đích riêng

<b>IPN:</b> Instant Payment Notification

<b>API:</b> Application Programing Interface

<b>SDK:</b> Software Development Kit

<b>Deep link:</b> Deep link là các đường dẫn được chia sẻ trên nền tảng mobile, vận hành khá giống hyperlink nhưng thay vì dẫn người dùng đến ngay một địa chỉ web page nào đó, deep link dẫn họ tới một màn hình cụ thể ngay trong ứng dụng.

Có 3 loại deep link:

- Basic deep link
- Deferred deep link
- Contextual deep link

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

# REST APIs standard
Best practice APIs endpoint
[Read here](https://stackoverflow.blog/2020/03/02/best-practices-for-rest-api-design/)

The standard best practice for REST APIs is to have a hyphen, not camelcase or underscores. [Link](https://stackoverflow.com/questions/10302179/hyphen-underscore-or-camelcase-as-word-delimiter-in-uris)

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

# Network

## Ping

Ping là 1 phần của ICMP (Internet Control Message Protocol) được sử dụng để khắc phục sự cố mạng TCP/IP. Ping cho phép kiểm tra xem máy chủ có còn **sống hay không**

## Telnet

Telnet là một chương trình TCP/IP. Cho phép chúng ta kết nối với máy tính từ xa trên **một cổng cụ thể**. Khi kết nối, nó lấy deamon đang chạy trên cổng đó.
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

- Why `null >= 0 && null <= 0` but not `null == 0`?

  + explained: https://stackoverflow.com/questions/2910495/why-null-0-null-0-but-not-null-0
  + Summary:
      + Relational Comparison: if both values are not type String, ToNumber is called on both. This is the same as adding a + in front, which for null coerces to 0.
      + Equality Comparison: only calls ToNumber on Strings, Numbers, and Booleans.

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

#### Brute Force Attack

Hacker nắm trong tay một danh sách rất lớn các username và password phổ biến hay được sử dụng. Sau đó họ gửi liên tục các truy vấn đăng nhập vào trang web, nếu tài khoản nào sai thì bỏ qua và tiếp tục thử lại với tài khoản khác. Cứ lần lượt như vậy sau đó "trộn" mật khẩu đến khi đăng nhập được thì thôi. Đó gọi là Brute force. Phương thức này là 1 cách để dò mật khẩu và tài khoản. Hay được khai thác bởi các website wordpress bởi hình thức tấn công này nhắm vào các mã nguồn thông dụng.

## Web server

### Nginx

Đóng vai trò như một cổng kết nối giữa internet và back-end

## Phân biệt Web Server vs. Application Server

![](images/webserver-vs-applicationserver.png 'The difference of web server and application server')

![](images/Webexplain.png 'Web Server and Application Server | Explained')
Application server không require. nhưng nó được require khi ứng dụng được yêu cầu xử lý 'logic kinh doanh' mà web server không thể xử lý được

ref:

- https://hiepsharing.com/phan-biet-web-server-vs-application-server/
- https://www.youtube.com/watch?v=thJSev60yfg

## Mã hóa và giải mã đường truyền

- Mã hóa và giải mã: bảo đảm tính bảo mật (encryption vs decryption): bảo đảm tính bảo mật của dữ liệu
- Ký và xác minh (Signing And Verification): (signature or checksum) Signing is different from encryption, in that it enables you to assert authenticity, rather than confidentiality. Bảo đảm tính xác thực thay vì bảo mật
- Note that only the party with the private key can sign a message, but anyone with the public key can verify it.

ref:

- https://www.sohamkamani.com/nodejs/rsa-encryption/#rsa-encryption-in-a-nutshell

## Unicode, UTF-8, UTF-16

ref:

- https://kipalog.com/posts/Unicode-la-charset--UTF8--UTF16-la-phuong-thuc-Encode-Decode

## Blockchain

## Binance chain vs Binance smart chain architecture

- `Binance Chain`: Nền tảng blockchain riêng được tối ưu hóa tốc độc giao dịch(ultra-fast trading) và thông lượng giao dịch(high tx throughput). Chưa đủ linh hoạt vì không support smart contract. Tuy nhiên đây là cách thiết kế hệ thống có chủ đích để ngăn chặn sự tắt nghẽn (như Ether do CryptoKitties). primary focus, its native decentralized application (“dApp”) Binance DEX

- `Binance Smart Chain`: Nền tảng blockchain có thể chạy smart contract chạy song song với Binace Chain. Use Proof of Staked Authority (PoSA) ~3s/block. Tương thích với (EVM). Có thể chạy độc lập khi không có Binace Chain. No block rewards. Validator stake BNB and accumulate tx fees.

Binance Chain and BSC have a dual-chain architecture with cross-chain compatibility. 2 nền tảng bổ sung cho nhau và có thể chuyển tài sản qua lại giữa các nền tảng

- Compare:
![](images/BC_BSC.png 'compare BC_BSC')

- Interactive:
![](images/cross_chain.png 'cross chain')


### Smart Contract

- ERC-20: 

docs: https://eips.ethereum.org/EIPS/eip-20
- ERC-721: NFTs

docs: https://eips.ethereum.org/EIPS/eip-721
- ERC-1155: Có thể được coi là một cải tiến trên cả ERC-721 và ERC-20. Nó tạo ra một tiêu chuẩn hỗ trợ cả token có thể thay thế lẫn nhau và không thể thay thế trong cùng một hợp đồng.

docs: https://eips.ethereum.org/EIPS/eip-1155
- Hỗ trợ cả ERC-20(fugiable) và ERC721(non-fungiable) 
- Cho phép gửi nhiều loại token cùng lúc. đến cùng 1 địa chỉ
- Cho phép quản lý nhiều loại token trên cùng một smart contract

- BEP-2 chuẩn token trên binance chain
- BEP-20 chuẩn token trên binance smart chain

The ERC721 Standard states that:

> “Every ERC-721 compliant contract must implement the ERC721 and ERC165 interfaces”

#### Interfaces

An <b>interface</b> is basically an abstract contract, but the only thing you can define are unimplemented functions. It’s an outline, written in Solidity code, which ensures contracts written by other developers all work well together, without having to know each other’s code base.

So by just using an interface, you’re telling other developers about some of the functions your contract has, and how to use them. Easy!

#### ERC 165

It only has one function! The ERC165 Standard is just a way of checking if your contract’s fingerprints match the fingerprint of any given interface. Let’s have a look at the ERC165 Standard interface in its entirety:

```
interface ERC165 {
 /// @notice Query if a contract implements an interface
 /// @param interfaceID The interface identifier, as
 ///  specified in ERC-165
 /// @dev Interface identification is specified in
 ///  ERC-165. This function uses less than 30,000 gas.
 /// @return `true` if the contract implements `interfaceID`
 ///  and `interfaceID` is not 0xffffffff, `false` otherwise
 function supportsInterface(bytes4 interfaceID) external view returns (bool);
}
```
- **Overflow**: Ví dụ uint8 chỉ chứa các giá trị trong khoảng [0, 255]. Nếu giá trị hiện tại của uint8 là 255, khi tăng lên 1 đơn vị thì giá trị **không phải** là 256 mà là 1. Hiện tượng này được gọi là Overflow.

- **Underflow**: Nếu giá trị hiện tại của uint8 là 0 khi giảm 1 đơn vị thì giá trị **không phải** là 0 mà là 255. Hiện tượng này được gọi là Underflow.

Các lỗ hổng này có thể được attaker khai thác ở các hàm transfer hay increaseTimeLock,.... Lỗ hổng này tạm gọi là tràn số trong toán học. Các phiên bản Solidity từ 0.8.0 đã khắc phục được lỗi này, các phiên bản trở về trước phải sử dụng thư viện SafeMath để handle các lỗi liên quan đến các phép toán trong solidity

- Abstract contract: biếu thị contract là trừ tượng, contract phải được khai báo là `abtract` khi có ít nhất 1 function không được implemented.
- Interfase: Khác với `abstract`, toàn bộ function trong interface đều không được implement.
- `virtual` and `override`: Một hàm chỉ được ghi đè nếu nó được khai báo là `virtual` hoặc được định nghĩa trong `interface` hay `abstract` contract. Khi muốn thay đổi hoặc ghi đè ta sửu dụng từ khóa `overrice`

#### DEFI 
Model:
![](images/defi-model.png 'Defi model')
Explain:
-  Bridge: Thông những cái blockchain với nhau. Vì các block chain có nhu cầu giao tiếp với nhau (cross-chain)
- Assets: Tài sản (finace). Tiền…
- Liquidity Provider: cung cấp thanh khoản cho sàn
- AMM – DEX: Sàn giao dịch (binance - kubi)
- Oracle: Cấp dữ liệu vào bộ máy để Dapp hoạt đông (chainLink)
- Indexer: Ngược lại với Oracle. Đọc dữ liệu từ dapp đưa ra ngoài
- NFT:  Đưa tài sản thật vào hệ thống để lấy tiền (Giống như đi vay - bán)
- RWA: read world asset
- Insurance: Bảo hiểm dapp. Có trách nhiệm bảo hiểm
- Audit: Kiểm tra hợp đồng thông minh. K có trách nhiệm đền bù
- Predict market: Thị trường tương lai

##### topic 
- lending
- dexes
- dericatives
- payements
- assets

Các positions ( tài sản trong các pool) sẽ được tracked theo một loại token được gọi là cToken. cToken là một loại ERC-20 nó thì đại diện cho một loại tài trong Compound. Ví dụ như nếu bạn deposit ETH vào Compound thì nó sẽ sinh ra lượng cETH tương ứng để chuyển vào tài khoản của bạn. Hay nếu bạn deposit một stablecoin DAI thì bạn cũng sẽ nhận được một lượng cDAI tương tự. Các loại cToken này được gọi là các đồng quản trị nó theo dõi các dòng tiền vào ra của liquidity pool, có thể hiểu là khi một lượng tài sản được deposit vào pool thì một lượng cToken tương ứng của loại tài sản đó sẽ được mint (in) ra và ngược lại khi một lượng tài sản được withdraw ra khỏi pool thì một lượng cToken tương ứng cũng sẽ bị burn (đốt) đi. Điều này giúp các smart contract có thể nắm được số lượng tài sản hiện có trong pool một cách dễ dàng.
cToken này là đại diện cho lượng tài sản mà người dùng đã đóng góp vào pool nên họ có thể sử
