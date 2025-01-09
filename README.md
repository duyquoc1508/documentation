# Some keyword should know

- [Some keyword should know](#some-keyword-should-know)
  - [Abbreviation keywords](#abbreviation-keywords)
- [REST APIs standard](#rest-apis-standard)
- [Docker](#docker)
  - [Lưu ý](#lưu-ý)
  - [Các khái niệm liên quan](#các-khái-niệm-liên-quan)
    - [Murable Infrastructure:](#murable-infrastructure)
    - [Immurable Infrastructure](#immurable-infrastructure)
    - [Infrastructure as code (code: dockerfile)](#infrastructure-as-code-code-dockerfile)
    - [Các lỗi hay gặp với docker](#các-lỗi-hay-gặp-với-docker)
- [Kubernestes](#kubernestes)
  - [Hardware](#hardware)
    - [Nodes](#nodes)
    - [Clusters](#clusters)
    - [Persistent Volumes](#persistent-volumes)
  - [Software](#software)
    - [Containers](#containers)
    - [Pods](#pods)
    - [Deployment](#deployment)
- [Jenkins](#jenkins)
- [Gitlab CI/CD](#gitlab-cicd)
    - [Runner execution flow](#runner-execution-flow)
    - [GitLab CI/CD flow](#gitlab-cicd-flow)
    - [Docker-in-Docker (dind)](#docker-in-docker-dind)
- [System architecture](#system-architecture)
  - [Process vs. Thread](#process-vs-thread)
    - [Key difference](#key-difference)
  - [Concurrency vs. Parallelism](#concurrency-vs-parallelism)
    - [Key difference](#key-difference-1)
  - [How concurrency work](#how-concurrency-work)
  - [How nodejs handle 10k concurrent request](#how-nodejs-handle-10k-concurrent-request)
- [Node.js](#nodejs)
  - [Stream](#stream)
  - [Binary data](#binary-data)
    - [Character sets](#character-sets)
    - [Character encoding](#character-encoding)
  - [Buffer](#buffer)
- [Network](#network)
  - [Ping](#ping)
  - [Telnet](#telnet)
  - [OSI model](#osi-model)
- [Git](#git)
- [Google Search Skills](#google-search-skills)
- [Javascript](#javascript)
- [Web security knowledge (HTTPS, TLS, SSL, CORS, CSP)](#web-security-knowledge-https-tls-ssl-cors-csp)
    - [HTTPS](#https)
    - [Mã hóa API](#mã-hóa-api)
    - [TLS (Transport Layer Security)](#tls-transport-layer-security)
    - [SSL (Secure Sockets Layer)](#ssl-secure-sockets-layer)
    - [What is the difference between TLS and SSL?](#what-is-the-difference-between-tls-and-ssl)
    - [CORS (Cross-origin resource sharing)](#cors-cross-origin-resource-sharing)
    - [CSP (Content Security Policy)](#csp-content-security-policy)
    - [Set Access-Control-Allow-Origin header.](#set-access-control-allow-origin-header)
    - [XSS (Cross-Site Scripting)](#xss-cross-site-scripting)
    - [Data injection attacks](#data-injection-attacks)
    - [Click jacking || UI redress attack (Tấn công chỉnh sửa giao diện người dùng)](#click-jacking--ui-redress-attack-tấn-công-chỉnh-sửa-giao-diện-người-dùng)
    - [Brute Force Attack](#brute-force-attack)
- [Elastic search](#elastic-search)
- [Web server](#web-server)
  - [Nginx](#nginx)
  - [Phân biệt Web Server vs. Application Server](#phân-biệt-web-server-vs-application-server)
  - [Mã hóa và giải mã đường truyền](#mã-hóa-và-giải-mã-đường-truyền)
  - [Hash](#hash)
  - [Unicode, UTF-8, UTF-16](#unicode-utf-8-utf-16)
- [Blockchain](#blockchain)
  - [Binance chain vs Binance smart chain architecture](#binance-chain-vs-binance-smart-chain-architecture)
    - [Blockchain layers (L0, L1, L2, L3) in a Diagram](#blockchain-layers-l0-l1-l2-l3-in-a-diagram)
    - [Smart Contract](#smart-contract)
      - [Interfaces](#interfaces)
      - [ERC 165](#erc-165)
      - [DEFI](#defi)

## Abbreviation keywords

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

<b>IP:</b> Internet Protocol address

<b>DNS:</b> Domain Name System is a phonebook of Internet

<b>OS:</b> Operating system

<b>AMQP:</b> Advanced message queue protocol

<b>CDN:</b> Content delivery network

<b>OSI</b>: Operating system interconnection model

<b>gRPC</b>: Remote Procedure Call: là 1 giao thức request-response, thường được dùng để giao tiếp server-server, thường thấy trong kiến trúc microservices. gRPC sử dụng binary để truyền đi
thay vì phải encode/decode thành các ngôn ngữ trung gian JSON/XML... như các request truyền thống. Vì vậy, tối ưu hóa về tài nguyên và tốc độ

<b>ERC:</b> Amazon Elastic Container Registry: là 1 private docker registry của Amazon. Dockerhub là 1 public docker registry. Docker registry là nới để host các image

<b>CCU:</b> Concurrent users (số lượng user đang hoạt động cùng một thời điểm)

<b>C2S:</b> Client-to-Server Encryption: Phương thức mã hóa dữ liệu trong đó người gửi mã hóa dữ liệu gửi đi và server giải mã gửi lại cho người nhận

<b>E2E | E2EE:</b> End-to-End Encryption: Dữ liệu gửi đi được mã hóa tại điểm cuối của người gửi. Người nhận là người duy nhất có thể giải mã được dữ liệu đó. Server chỉ có nhiệm vụ vận chuyển dữ liệu

<b>CI</b>: Continuous Integration: Là quá trình tự động build, test application một cách tự động dựa vào các scrips đã viết sẵn mỗi khi repository có thay đổi

<b>CD</b>: Continuous Delivery: A step beyond CI. Ứng dụng không chỉ build, test mỗi khi code thay đổi, mà còn deploy liên tục. CD sẽ kiểm tra code 1 cách tự động. Tuy nhiên, phải kích hoạt deploy theo cách thủ công

<b>CD</b>: Continuous Deployment: An another step beyond CI. Tương tự như Continuous Delivery nhưng ứng dụng sẽ được deploy 1 cách tự động. Không có sự can thiệp của con người

<b>Concurrency</b>: Đa luồng là khả năng 1 chương trình có thể **điều phối (dealing)** nhiều tác vụ trong cùng 1 khoảng thời gian và trong quá trình điều phối chỉ cho phép **1 tác vụ chạy trong 1 thời điểm**

<b>Parallelism</b>: Là khả năng 1 chương trình có thể **thực thi (doing)** 2 hoặc nhiều task trong **cùng một thời điểm** với điều kiện cpu phải có từ 2 core trở lên

<b>Race condition</b>: Lỗi xảy ra khi 2 hoặc nhiều threads cùng thay đổi dữ liệu của 1 biến (vùng nhớ). Dẫn tới tính không chính xác của dữ liệu. Là 1 vấn đề cần lưu ý trong lập trình concurrency.

<b>Deadlock</b>: Xảy ra khi 2 hoặc nhiều threads cùng chờ dữ liệu của nhau (A đợi B và B cũng đợi A), dẫn tới đợi mãi mà không làm gì. Là 1 lỗi cần lưu ý trong lập trình concurrency

<b>Deep link:</b> Deep link là các đường dẫn được chia sẻ trên nền tảng mobile, vận hành khá giống hyperlink nhưng thay vì dẫn người dùng đến ngay một địa chỉ web page nào đó, deep link dẫn họ tới một màn hình cụ thể ngay trong ứng dụng.

Có 3 loại deep link:

- Basic deep link
- Deferred deep link
- Contextual deep link

<b>2FA:</b> Two-Factor Authentication

<b>OTP:</b> One-time Password

<b>HOTP:</b> HMAC-based One-Time Password.

<b>TOTP:</b> Time-based One-time Password

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

> Docker uses a client-server architecture. The Docker client talks to the Docker daemon, which does the heavy lifting of building, running, and distributing your Docker containers. The Docker client and daemon can run on the same system, or you can connect a Docker client to a remote Docker daemon. The Docker client and daemon communicate using a REST API, over UNIX sockets or a network interface.

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

### Các lỗi hay gặp với docker

- Ví dụ khi dockerize 1 server nodejs. Khi chạy và expose port ra thì server chạy hoàn toàn bình thường. Nhưng khi gọi đến resource từ máy vật lý thì không được và bị lỗi
  `curl : The underlying connection was closed: The connection was closed unexpectedly.`. Lúc này cần kiểm tra host của server đang chạy là gì. Nếu là `localhost` hay `127.0.0.1` thì sẽ bị lỗi này. Fix: Thay đổi host thành `0.0.0.0`

![](images/docker-host-error.png 'docker error because host')

# Kubernestes

Ref: https://medium.com/google-cloud/kubernetes-101-pods-nodes-containers-and-clusters-c1509e409e16

## Hardware

### Nodes

![](images/kubernestes-node.png 'kubernestes node')

Nodes is a concept of hardware. A node is the smallest unit of computing hardware in Kubernestes. It is a representation of a single machine in cluster. In most production system, a node will likely be either a physical machine in a datacenter or virtual machine hosted on a clound.
Thinking of a machine as a "node" allow us to insert a layer of abstraction. Now, instead of worrying about the unique characteristics of individual machine, we can simply view each machine as a set of CPU and RAM resource that can be utilized. In this way, any machine can substitute any other machine in kubernetes cluster

### Clusters

![](images/kubernestes-cluster.png 'kubernestes cluster')

Although working with individual nodes can be useful, it's not the Kubernetes way. In general, you should think about cluster as a whole, instead worrying about the state of individual nodes.
In kubernetes, nodes pool together their resource to form a powerful machine. When program deployed onto cluster, it intelligently handles distributing work to the individual nodes for you. If any nodes are added or removed, the cluster will shift around work as necessary. It shouldn't matter to program, our the programmer, wich individual machines are actually running the code

### Persistent Volumes

![](images/kubernestes-persistent-volume.png 'kubernestes persisten volume')

Because programs running on your cluster aren't guaranteed to run on a specific node, data can't be saved to any arbitrary in the file system. If a program tries to save data to a file for later, but is then relocated onto a new node, the file will no longer be where the program expects it to be. To store data permanently, Kubernetes uses Presistent Volumes. Presistent Volumes provide a file system that can be mounted to the cluster, without being associated with any particular node.

## Software

### Containers

![](images/kubernestes-container.png 'kubernestes container')

Programs running on k8s are packaged as Linux Container. Containerization allows you create self-contained Linux execution environments. Any program and all its dependencies can be bundled up into a single file.

### Pods

![](images/kubernestes-pods.png 'kubernestes pods')

Kubernetes doesn't run containers directly, instead it wraps one or more containers onto a higher-level structure called a **pod**. Any containers in the same pod will share the same resource an local network. Container can easily communicate with other container in the same pod as though they were on the same machine while maintaining a degree of isolation from others.

Pods are used as the unit of replication in Kubernetes. If you want to have multiple copies of a pod running at any time in a production system, Kubernetes can be configured to deploy new replica of your pod to the cluster as necessary.

Pods can hold multiple containers, but you should limit it when possible. Because pods are scale up and down as a unit, all container in a pod must scale together, regardless of their container need. This leads to wasted resources and an expensive bill.

### Deployment

![](images/kubernestes-deployment.png 'kubernestes deployment')

Although pods are the basic unit of computation in K8s. They are not typically directly launched on a cluster. Instead, pods are usually managed by one more layer of abstraction: **Deployment**

# Jenkins

1. Run jenkins and keep start automatically when Docker daemon restarts

```
docker run -it -d --restart=always --name myjenkins -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home  jenkins/jenkins
```

# Gitlab CI/CD

- Gitlab runner: is an application that works with GitLab CI/CD to run jobs in a pipeline.

When you register a runner, you are setting up **communication** between your _GitLab instance_ and the _machine_ where GitLab Runner is installed.
Runners usually process jobs on the _same machine_ where you installed GitLab Runner.

- Executors: When you register a runner, you must choose an executor. An executor determines the environment each job runs in.
  When you install GitLab Runner in a Docker container and choose the Docker executor to run your jobs, it’s sometimes referred to as a “Docker-in-Docker” configuration

Sau khi commit code có chứa file `.gitlab-ci.yml` thì quá trình CI/CD được khỏi động. Gitlab sẽ tạo ra 1 pipeline. pineline chính là toàn bộ những gì được viết trong file
`.gitlab-ci.yml`, pipeline sẽ chứa nhiều jobs, các jobs này sẽ đươc gửi đến các `Gitlab runners`, mỗi con runner sẽ tạo ra 1 môi trường riêng để chạy job và sau khi kết thúc
thì sẽ trả kết quả lại cho Gitlab

Mặc định Gitlab có nhiều Shared Runners dùng cho tất cả mọi người, chúng ta có thể dùng runner này hoặc có thể cài Gitlab runner về server riêng để build cho nhanh

### Runner execution flow

This diagram shows how runners are registered and how jobs are requested and handled

![](images/gitlab-runner-flow.png 'gitlab runner execution flow')

### GitLab CI/CD flow

![](images/gitlab-ci-cd-flow.png 'gitlab ci/cd flow')

### Docker-in-Docker (dind)

"Docker-in-Docker" (dind) means:

- Your registered runner uses the Docker executor.
- The executor uses a container image of Docker, provided by Docker, to run your CI/CD jobs.

Tại sao phải dùng docker-in-docker

- Giải thích ngắn gọn
  Trong môi trường `docker:19` mà job chúng ta đang chạy, theo lý thuyết nó có docker, nhưng để chạy được command với docker trong đó thì ta cần 1 container để support đó là `docker:dind` đóng vai trò như kiểu cầu nối giữa `docker-cli` và `docker deamon` (Docker Server) vậy. (`docker-cli` hay còn gọi là Docker Client là thứ mà ta chạy ở command line `docker build`...)
- Giải thích chi tiết + demo
  https://gitlab.com/duyquoc1508/gitlab-ci
  ![](images/runner-docker-only.png 'Gitlab runner docker only')
  ![](images/runner-docker-in-docker.png 'Gitlab runner docker-in-docker')

# System architecture

## Process vs. Thread

![](images/process-vs-thread-diagram.png 'process vs. thread diagram')

- **Process**: 1 process đại diện cho 1 chương trình được running trong hệ điều hành. Ví dụ mở app chrome thì chrome đại diện cho 1 process. Trong process có nhiều thread
- **Static**: Các biến được khai báo là static trong code được lưu vào đây
- **Heap**: Vùng nhớ cho các vấn đề cấp phát động
- **Code**: Để chương trình chạy được thì code phải được nạp lên process. Nên code toàn bộ source code của chương trình phải được lưu lại tại đây
- **Thread**: Là tập con của 1 process
  - **Registers**: Thanh ghi. Có 2 thanh ghi chính là `PC-Program Counter` và `Status Register`
    - Program Counter: Quản lý dòng lệnh nào sẽ chạy tiếp theo (giống lúc debug)
    - Status Register: Lưu lại trạng thái của thread đó. Ví dụ như lập trình đa luồng, các tác vụ xen kẽ lẫn nhau, thì khi tạm dừng tác vụ này để tác vụ khác chạy, `status register` có tác dụng lưu lại trạng thái của tác vụ dừng (ví dụ download: 30%), để khi tác vụ được chạy lại thì thread sẽ biết chạy tác vụ đó từ đâu (ví dụ chạy lần sau, download từ 30% trở đi)
  - **Stack**: Dùng để lưu trữ các biến cục bộ trong hàm, tham số truyền vào...

### Key difference

![](images/process-vs-thread.png 'process vs. thread')

## Concurrency vs. Parallelism

### Key difference

![](images/concurrency-vs-parallelism.png 'concurrency vs. parallelism')

![](images/concurrency-vs-parallelism-compare.png 'concurrency vs. parallelism compare')

## How concurrency work

Mô hình mô tả cách hoạt động của các thread trong concurrency
![](images/how-concurrency-work.png 'how concurrency work')

- T1, T2 ... đại diện cho các thread đang chạy trong 1 chương trình đa luồng
- Khi switch context bước thứ 2 (Lưu context) là nhiệm vụ của thanh ghi `Status Register` đề cập phía trên

## How nodejs handle 10k concurrent request

Ref: - https://stackoverflow.com/questions/34855352/how-in-general-does-node-js-handle-10-000-concurrent-requests - https://javascript.plainenglish.io/how-many-requests-can-handle-a-real-world-nodejs-server-side-application-55da7a2f06f3

# Node.js

Ref: https://www.freecodecamp.org/news/do-you-want-a-better-understanding-of-buffer-in-node-js-check-this-out-2e29de2968e8/

## Stream

Stream trong node.js là một chuỗi dữ liệu được di chuyển từ điểm này đến điểm khác theo thời gian.
Khái niệm này phát sinh khi bạn có 1 lượng lớn dữ liệu cần phải xử lý, nhưng bạn không cần phải đợi tất cả dữ liệu có sẵn rồi mới bắt đầu xử lý. (memory efficiency + time efficiency)

## Binary data

Máy tính lưu trữ và biểu diễn dữ liệu trong các tệp nhị phân. Để lưu trữ hoặc biểu diễn dữ liệu, máy tính cần chuyển đổi dữ liệu đó sang dạng biểu diễn nhị phân của nó.
Máy tính biết cách biểu diễn các dữ liệu number, strings, images, videos... dưới dạng nhị phân dựa vào **character sets** và **character encoding**
Ví dụ: Ký tự (L) > "L".chartCodeAt(0) = 97 (dựa vào character sets (unicode)) > biểu diễn nhị phân là (01001100) (dựa vào charater encoding)

### Character sets

Xác định quy tắc về 1 số đại diện cho 1 kí tự nào. Những bộ kí tự phổ biến **Unicode**, **ASCII**. Javascript hoạt động tốt với bộ mã Unicode

### Character encoding

Chứa các quy tắc cách số đó nên được biểu diễn trong các mã nhị phân, cụ thể là dùng bao nhiêu bit để biểu diễn số.
Một trong những định nghĩa cho mã hóa kí tự là **UTF-8**. UTF-8 định nghĩa rằng các kí tự phải được mã hóa theo byte. Một byte là tập hợp 8 bits.
Để tham chiếu đến các kí tự một cách rõ ràng, mỗi kí tự được liên kết với 1 số được gọi là 1 **code point**

Ví dụ: biểu diễn nhị phân của số 12 là 1100. UTF-8 nói rằng số 12 phải ở 8 bits, nếu số được biểu diễn chưa đủ thì máy tính cần thêm các bit 0 vào bên trái của biểu diễn nhị phân
để nó trở thành 1 byte, vì vậy 12 nên được biểu diễn là 00001100.

Tương tự như vậy, máy tính cũng có các quy tắc cụ thể về cách hình ảnh và video nên được chuyển đổi hoặc mã hóa và lưu trữ dưới trong các tệp nhị phân.

## Buffer

Lớp buffer được giới thiệu như 1 phần của API node.js để giúp nó có thể thao tác hoặc tương tác với các luồng dữ liệu nhị phân
Một luồng di chuyển dữ liệu (stream) là sự di chuyển dữ liệu từ điểm này sang điểm khác, sự di chuyển dữ liệu thường với mục đích xử lý hoặc đọc nó và đưa ra quyết định dựa trên nó.
Nhưng có 1 lượng dữ liệu **tối thiểu** và **tối đa** mà một quá trình có thể mất theo thời gian. Vì vậy nếu tốc độ dữ liệu tới **nhanh hơn** tốt độ xử lý dữ liệu thì dữ liệu thừa cần phải đợi
ở đâu đó để tới lượt nó được xử lý. Mặc khác, nếu tốc độ dữ liệu đến **chậm hơn** quá trình xử lý dữ liệu, thì một số ít dữ liệu đến sớm hơn cần phải 1 đợi lượng dữ liệu đến nữa để nó được xử lý.
Nơi dữ liệu chờ xử lý được gọi là **buffer**. Đó là 1 vị trí nhỏ trong máy tính, thường là trong RAM, nơi dữ liệu tạm thời được thu thập, chờ đợi và cuối cùng được gửi đi để xử lý.

Ví dụ: Chúng ta coi toàn bộ stream và buffer process như là 1 trạm xe bus. Xe bus không được phép khởi hành cho đến khi có một lượng khách nhất định (tối thiểu) hoặc đến đến một giờ khởi hành cụ thể.
Hành khách có thể đến vào các thời điểm khác nhau với tốc độ khác nhau. Hành khách và bến xe đều không kiểm soát được việc hành khác đến bến. Trong mọi trường hợp những hành khách đến sớm sẽ phải đợi
cho đên khi xe bus đủ số lượng hành khách tối thiểu để khởi hành hoặc khi xe đã khởi hành thì phải đợi chuyến khác.

Ví dụ điển hình để cho thấy cách hoạt động của buffer. Nếu internet đủ nhanh, tốc độ của stream đủ nhanh để lấp đầy buffer ngay lập tức và gửi nó ra ngoài để xử lý, video sẽ được phát thuận lơi đến khi kết thúc. Nhưng nếu kết nối chậm lúc đó sẽ hiện chữ "loading..." hoặc "buffering..." có nghĩa là đang thu thập thêm dữ liêu hoặc chờ dữ liệu đến khi buffer được lấp đầy để xử lý

# MongoDB
[Thiết kế cơ sở dữ liệu với mongodb Best Practice](https://duthanhduoc.com/blog/thiet-ke-co-so-du-lieu-voi-mongodb)

## MongoDB index
### `autoIndex` trong Mongoose

Trong Mongoose, **`autoIndex`** là một tùy chọn được sử dụng để tự động tạo các chỉ mục (indexes) cho các trường đã được định nghĩa trong **schema** khi mô hình (model) được sử dụng lần đầu tiên. Tuy nhiên, hành vi của `autoIndex` có thể được điều chỉnh tùy theo môi trường phát triển hay môi trường sản xuất của bạn.

### **Khi nào `autoIndex` hoạt động?**

1. **Khi Mongoose Khởi Tạo Mô Hình (Model)**
   
   Khi bạn tạo mô hình từ schema trong Mongoose, các chỉ mục sẽ tự động được tạo nếu bạn không tắt tùy chọn `autoIndex`. Điều này có nghĩa là khi bạn gọi `mongoose.model()` để tạo mô hình, Mongoose sẽ tự động tạo các chỉ mục được định nghĩa trong schema nếu chúng chưa tồn tại trong cơ sở dữ liệu.

   ```javascript
   const userSchema = new mongoose.Schema({
     username: { type: String, unique: true },
     email: { type: String, index: true },
   });

   // Mongoose sẽ tự động tạo chỉ mục khi model này được khởi tạo
   const User = mongoose.model('User', userSchema);
   ```

2. **Khi `autoIndex` Được Bật**

   Mặc định, trong môi trường phát triển (development), **`autoIndex`** được bật, tức là các chỉ mục sẽ được tạo tự động khi mô hình lần đầu tiên được sử dụng.

   ```javascript
   const userSchema = new mongoose.Schema({
     username: { type: String, unique: true },
     email: { type: String, index: true },
   });

   const User = mongoose.model('User', userSchema);  // Các chỉ mục tự động được tạo khi gọi model lần đầu tiên
   ```

3. **Khi `autoIndex` Bị Tắt**

   Trong môi trường **sản xuất (production)**, **`autoIndex`** thường được tắt để tránh việc tạo chỉ mục mỗi lần ứng dụng khởi động, điều này có thể làm ảnh hưởng tới hiệu suất của cơ sở dữ liệu. Việc tạo chỉ mục trong quá trình khởi tạo có thể gây chậm và làm tắc nghẽn ứng dụng, đặc biệt khi bạn đã có dữ liệu trong cơ sở dữ liệu.

   ```javascript
   const userSchema = new mongoose.Schema({
     username: { type: String, unique: true },
     email: { type: String, index: true },
   }, { autoIndex: false });  // Tắt tính năng tạo chỉ mục tự động trong môi trường production

   const User = mongoose.model('User', userSchema);  // Không tạo chỉ mục tự động khi model được gọi
   ```

   Nếu bạn tắt `autoIndex`, bạn sẽ phải tự tay tạo chỉ mục bằng cách sử dụng phương thức `createIndexes()`.

   ```javascript
   // Sau khi model đã được tạo, bạn có thể tạo chỉ mục thủ công nếu cần
   User.createIndexes().then(() => {
     console.log('Indexes created successfully');
   }).catch(err => {
     console.error('Error creating indexes:', err);
   });
   ```

### **Các Tùy Chọn `autoIndex`**
`autoIndex` có thể được cấu hình với các giá trị sau:

- **`autoIndex: true` (Mặc định trong môi trường phát triển)**: Tự động tạo chỉ mục khi mô hình được sử dụng lần đầu tiên. Đây là lựa chọn mặc định và hữu ích trong môi trường phát triển khi bạn liên tục thay đổi cấu trúc schema.
  
- **`autoIndex: false` (Thường dùng trong môi trường sản xuất)**: Tắt tính năng tạo chỉ mục tự động. Điều này có thể cải thiện hiệu suất trong môi trường sản xuất khi bạn không muốn chỉ mục được tạo lại mỗi lần ứng dụng khởi động.

### **Khi nào bạn nên tắt `autoIndex`?**

- **Trong môi trường sản xuất**: Nếu bạn đã có một lượng dữ liệu lớn trong cơ sở dữ liệu, việc tạo chỉ mục tự động có thể ảnh hưởng đến hiệu suất của ứng dụng khi khởi động hoặc thay đổi cấu trúc. Bạn có thể tắt `autoIndex` và tạo chỉ mục thủ công trong quá trình triển khai hoặc khi cập nhật ứng dụng.
  
- **Khi bạn đã kiểm tra và tối ưu hóa các chỉ mục**: Trong môi trường phát triển, bạn có thể bật `autoIndex` để dễ dàng thử nghiệm và tối ưu hóa các chỉ mục, nhưng khi bạn chuyển sang môi trường sản xuất, bạn nên tắt nó để kiểm soát chính xác quá trình tạo chỉ mục.

### **Tóm lại:**

- **Mặc định**: `autoIndex` được bật, và các chỉ mục sẽ tự động được tạo khi mô hình được khởi tạo.
- **Trong môi trường sản xuất**: Thường tắt `autoIndex` để tránh làm giảm hiệu suất khi khởi động ứng dụng. Việc tạo chỉ mục nên được thực hiện thủ công sau khi triển khai.

Tùy vào môi trường và yêu cầu của ứng dụng, bạn có thể quyết định có nên sử dụng `autoIndex` hay không, hoặc chỉ bật nó trong quá trình phát triển và tắt nó trong quá trình triển khai sản phẩm.

# Network

## Ping

Ping là 1 phần của ICMP (Internet Control Message Protocol) được sử dụng để khắc phục sự cố mạng TCP/IP. Ping cho phép kiểm tra xem máy chủ có còn **sống hay không**

## Telnet

Telnet là một chương trình TCP/IP. Cho phép chúng ta kết nối với máy tính từ xa trên **một cổng cụ thể**. Khi kết nối, nó lấy deamon đang chạy trên cổng đó.

## OSI model

![](images/osi-model-7-layers.svg 'Osi model simple explained')

OSI model là gì: https://www.cloudflare.com/learning/ddos/glossary/open-systems-interconnection-model-osi/

# Git

`Git`: là Version control/source control systems

`Github`: là Repo Hosting Services

[git] Keep empty directory by .gitkeep
<code>.gitkeep</code> là một file giả dùng để giữ chỗ. Vì git không theo dõi thư mục nên có thể bỏ qua các thư mục trống, git chỉ theo dõi sự thay đổi của các file.

Git không phân biệt được sự khác biệt khi thay đổi tên file chỉ khác với teen cũ các kí tự viết hoa và viết thường. Để git biết được sự thay đổi này thì dùng lệnh git để rename file.

```
git mv BlackList.sol Blaclist.sol
```

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

# Javascript

- JS array vs object vs map

  - Cần truy cập vào 1 mảng bằng khóa mà không quan tâm đến thứ tự => dùng object
  - Nếu quan tâm đến thứ tự chèn => dùng Map (new Map())

- Why `null >= 0 && null <= 0` but not `null == 0`?

  - explained: https://stackoverflow.com/questions/2910495/why-null-0-null-0-but-not-null-0
  - Summary:
    - Relational Comparison: if both values are not type String, ToNumber is called on both. This is the same as adding a + in front, which for null coerces to 0.
    - Equality Comparison: only calls ToNumber on Strings, Numbers, and Booleans.

- Javascript event loop explained
  ![JS event loop](https://res.cloudinary.com/practicaldev/image/fetch/s--BLtCLQcd--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://devtolydiahallie.s3-us-west-1.amazonaws.com/gif14.1.gif)

  - **Stack** là nơi lưu giữ các con trỏ hàm đang thực hiện,. Khi hàm bắt đầu chạy thì nhảy vào đây, hàm nào xong rồi thì đi ra. Do bản chất `stack` nên thằng nào vào sau sẽ ra trước.
  - **Queue** là hàng đợi sự kiện, mỗi thằng sự kiện mới sẽ chui vào đây, thằng nào vào trước lấy trước. Sự kiện có thể là I/O event, timeout event, interval event, v.v..
  - **Event loop** là 1 thằng chuyên đi nhặt các sự kiện trong hàng đợi (`queue`) để xử lý. Tuy nhiên nó chỉ nhặt khi và chỉ khi `stack` trống.

# Web security knowledge (HTTPS, TLS, SSL, CORS, CSP)

https://dev.to/ahmedatefae/web-security-knowledge-you-must-understand-it-part-i-https-tls-ssl-cors-csp-298l

### HTTPS

The secure version of HTTP, It uses encryption communication protocol, named Transport Layer Security (TLS), was known as Secure Sockets Layer (SSL).

### Mã hóa API

Mặc dù HTTPS là giao thức HTTP đi kèm mã hóa đầu cuối để phòng chống MITM. Tuy nhiên các dev thấy đây vẫn là chưa đủ, và họ đã đi thêm 1 bước nữa trên con đường phòng chống những kẻ tò mò.
Chung quy lại là phương pháp này bao gồm các bước:

1. Tạo 1 Secret Key trên server.
2. Chia sẻ Secret Key giữa client và server (Qua fix cứng trong code, file config, API).
3. Dùng Secret Key với mã hóa AES (hoặc bất kỳ thuật toán mã hóa tin cậy nào đó) mã hóa response trả về từ server.
4. Dùng Secret Key để giải mã trở lại lấy thông tin từ Response.

Về cơ bản thì nó không khác gì concept của HTTPS, tức là mã hóa và giải mã đầu cuối để người ở giữa không đọc được. Cái khác ở đây chính là HTTPS được trình duyệt thực hiện tự động, còn mã hóa API ta phải tự thực hiện trong code client.

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

### Set Access-Control-Allow-Origin header.

Đây là header được <b>server trả về</b> để báo cho trình duyệt biết: "Tao chỉ cho phép trang web có domain này gọi đến tao thôi". Phương thức lưu giữ phiên đăng nhập sử dụng cookie sẽ có đặc điểm của cookie đó là tự gắn cookie vào request khi gọi tới domain gốc. Do vậy nếu bạn vào trang web fakezalo.com, trang web này hoàn toàn có thể gọi lên API của Zalo để lấy thông tin người dùng đang đăng nhập hiện tại của bạn (do khi gọi API của Zalo sẽ tự có cookie của Zalo). Access-Control-Allow-Origin header sinh ra là để phòng chống việc này.

### XSS (Cross-Site Scripting)

Lỗ hổng cho phép hacker chèn script vào trang web để client thự thi nó để lấy các dữ liệu nhạy cảm như cookie, session’s info and site-specific information. Vì web-app không sử dụng đủ các phương thức xác thực và mã hóa. trình duyệt của người dùng thì không thể phát hiện ra 1 đoạn script người dùng chèn vào có nguy hiểm hay không

### Data injection attacks

là một mã được được đưa vào mạng. mã này lấy tất cả thông tin từ database đến kẻ tấn công. SQL injection là một loại

### Click jacking || UI redress attack (Tấn công chỉnh sửa giao diện người dùng)

attacker đành lừa người dùng nhấp vào nút hoặc liên kết trên 1 trang khác sử dụng nhiều lớp trong suốt. có thể redirect tới các trang mà người dùng không mong muôn

### Brute Force Attack

Hacker nắm trong tay một danh sách rất lớn các username và password phổ biến hay được sử dụng. Sau đó họ gửi liên tục các truy vấn đăng nhập vào trang web, nếu tài khoản nào sai thì bỏ qua và tiếp tục thử lại với tài khoản khác. Cứ lần lượt như vậy sau đó "trộn" mật khẩu đến khi đăng nhập được thì thôi. Đó gọi là Brute force. Phương thức này là 1 cách để dò mật khẩu và tài khoản. Hay được khai thác bởi các website wordpress bởi hình thức tấn công này nhắm vào các mã nguồn thông dụng.

# Elastic search

- **Elasticsearch**: là công cụ tìm kiếm và phân tích phân tán

- **Kibana**: là một nền tảng phân tích hiển thị dữ liệu từ Elasticsearch một cách trực quan dễ sử dụng, cung cấp cho người dùng quản lý như biểu đồ cột, biểu đồ đường,...

- **Filebeat**: là một dịch vụ gửi hàng gọn nhẹ để chuyển tiếp và tập trung dữ liệu logs. Filebeat giám sát các tệp nhật kí hoặc vị trí mà bạn chỉ định, thu thập các sự kiện nhật ký và chuyển tiếp chúng tới `Elasticsearch` hoặc `Logstash` để lập chỉ mục

- **Logstash**: Logstash là một đường dẫn xử lý dữ liệu phía máy chủ, nhập dữ liệu từ nhiều nguồn đồng thời, biến đổi dữ liệu và sau đó gửi dữ liệu đó đến một "kho lưu trữ" như Elasticsearch

- **ELK stack**: Elasticsearch + Logstash + Kibana

![](images/ELK_filebeat.png 'ELK + filebeat')

# Web server

## Nginx

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

## Hash

- Hash (crypto.createHash) vs. HMac (crypto.createHmac): HMAC is a keyed hash of data. Mã hóa có key. Secret key cung cấp cho bên tin cậy, thì ta có thể tin rằng chỉ có bên đáng tin cậy (bên giữ key) mới có thể tạo ra chữ ký đó. Hash thường dùng để đảm bảo tính toàn vẹn dữ liệu, dữ liệu không bị thay đổi trên đường truyền. Nếu chỉ hash các field của payload, hacker có thể dò ra thứ tự đúng của các field, sau đó hacker có thể lợi dụng kẽ hở này để gian lận được. Vậy nên thêm secret key vào hash (Hmac) có để đảm bảo hơn dữ liệu chỉ đến từ nguồn đáng tin cậy. Nguồn được chia sẻ key

## Unicode, UTF-8, UTF-16

ref:

- https://kipalog.com/posts/Unicode-la-charset--UTF8--UTF16-la-phuong-thuc-Encode-Decode

# Blockchain

## Binance chain vs Binance smart chain architecture

- `Binance Chain`: Nền tảng blockchain riêng được tối ưu hóa tốc độc giao dịch(ultra-fast trading) và thông lượng giao dịch(high tx throughput). Chưa đủ linh hoạt vì không support smart contract. Tuy nhiên đây là cách thiết kế hệ thống có chủ đích để ngăn chặn sự tắt nghẽn (như Ether do CryptoKitties). primary focus, its native decentralized application (“dApp”) Binance DEX

- `Binance Smart Chain`: Nền tảng blockchain có thể chạy smart contract chạy song song với Binace Chain. Use Proof of Staked Authority (PoSA) ~3s/block. Tương thích với (EVM). Có thể chạy độc lập khi không có Binace Chain. No block rewards. Validator stake BNB and accumulate tx fees.

Binance Chain and BSC have a dual-chain architecture with cross-chain compatibility. 2 nền tảng bổ sung cho nhau và có thể chuyển tài sản qua lại giữa các nền tảng

- Compare:
  ![](images/BC_BSC.png 'compare BC_BSC')

- Interactive:
  ![](images/cross_chain.png 'cross chain')

### Blockchain layers (L0, L1, L2, L3) in a Diagram

![](images/blockchain_layers.png 'blockchain layers diagrams')
ref: https://medium.com/@nick.5montana/blockchain-layers-l0-l1-l2-l3-in-a-diagram-569162398db

### Smart Contract

- ERC-20:

docs: https://eips.ethereum.org/EIPS/eip-20

- ERC-721: NFTs

Non-fungible means not completely interchangeable. Không thể hoán đổi hoàn toàn cho nhau.

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

Why we need to check contract support an interface or not? => Solidity already provides a way for a contract to call functions from another contract. To make sure the called contract supports a function that you want to call. What we can do is add a validation check.

That is what ERC165 is for — a standard to publish and detect what interfaces a smart contract implements.

More: https://medium.com/@chiqing/ethereum-standard-erc165-explained-63b54ca0d273

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

- Bridge: Thông những cái blockchain với nhau. Vì các block chain có nhu cầu giao tiếp với nhau (cross-chain)
- Assets: Tài sản (finace). Tiền…
- Liquidity Provider: cung cấp thanh khoản cho sàn
- AMM – DEX: Sàn giao dịch (binance - kubi)
- Oracle: Cấp dữ liệu vào bộ máy để Dapp hoạt đông (chainLink)
- Indexer: Ngược lại với Oracle. Đọc dữ liệu từ dapp đưa ra ngoài
- NFT: Đưa tài sản thật vào hệ thống để lấy tiền (Giống như đi vay - bán)
- RWA: read world asset
- Insurance: Bảo hiểm dapp. Có trách nhiệm bảo hiểm
- Audit: Kiểm tra hợp đồng thông minh. K có trách nhiệm đền bù
- Predict market: Thị trường tương lai

Topic:

- lending
- dexes
- dericatives
- payements
- assets

Các positions ( tài sản trong các pool) sẽ được tracked theo một loại token được gọi là cToken. cToken là một loại ERC-20 nó thì đại diện cho một loại tài trong Compound. Ví dụ như nếu bạn deposit ETH vào Compound thì nó sẽ sinh ra lượng cETH tương ứng để chuyển vào tài khoản của bạn. Hay nếu bạn deposit một stablecoin DAI thì bạn cũng sẽ nhận được một lượng cDAI tương tự. Các loại cToken này được gọi là các đồng quản trị nó theo dõi các dòng tiền vào ra của liquidity pool, có thể hiểu là khi một lượng tài sản được deposit vào pool thì một lượng cToken tương ứng của loại tài sản đó sẽ được mint (in) ra và ngược lại khi một lượng tài sản được withdraw ra khỏi pool thì một lượng cToken tương ứng cũng sẽ bị burn (đốt) đi. Điều này giúp các smart contract có thể nắm được số lượng tài sản hiện có trong pool một cách dễ dàng.
cToken này là đại diện cho lượng tài sản mà người dùng đã đóng góp vào pool nên họ có thể sử

#### Zero knowledge prove (ZKP)
- Short: Zero-Knowledge Proof (Bằng chứng không tri thức) là một phương pháp mà một bên (người chứng minh) có thể chứng minh cho một bên khác (người xác minh) rằng một tuyên bố là đúng mà không cần tiết lộ bất kỳ thông tin bổ sung nào. 
- Read more: https://academy.binance.com/vi/articles/what-is-zero-knowledge-proof-and-how-does-it-impact-blockchain

#### Zk rollup 
Là giải pháp mở rộng Layer 2 giúp giải quyết vấn đề mở rộng trên Ethereum bằng cách đưa các giao dịch ra ngoài chuỗi (off-chain)

* Các thành phần chính
- Sequencer: Đóng vai trò là thực thi, tổng hợp và đóng gói các giao dịch trên Layer 2 lại thành các Batch (lô)
- Proposer: Đóng vai trò đăng tải trạng thái mạng (State Root) lên Ethereum. 
- Prover: Đóng vai trò là tạo bằng chứng chứng minh tính đúng đắn của State Root.

* Cơ chế hoạt động
- Thực thi & Tổng hợp giao dịch
- Gửi về Layer 1
- Tạo ra bằng chứng giao dịch (Validity Proof)
Mỗi khi Proposer gửi State Root về Layer 1 thì họ cần các Prover có thể tạo bằng chứng cho những State Root đó. Chính vì vậy, khi State Root được gửi cùng với Validity Proof xuống Ethereum thì nền tảng Verifier Contract sẽ chỉ cần xác minh những Validity Proof đó.

Vì sao ZK Rollup giải quyết bài toán mở rộng trên Ethereum?
- Nén dữ liệu giao dịch: Thay vì thực thi trực tiếp hàng trăm các giao dịch trên Ethereum thì tính toán đó sẽ được mang ra off-chain và xử lý trên ZK Rollup. Biến hàng trăm giao dịch thành một giao dịch duy nhất rồi gửi về Ethereum làm tiết kiệm một lượng lớn phí giao dịch của người dùng từ đó cải thiện khả năng mở rộng cho Ethereum theo hướng off-chain.
- ZK Proof: ZK Proof có thể là bằng chứng để chứng minh các bằng chứng khác. Hiện tại, mỗi một State Root được gửi từ ZK Rollup xuống Layer 1 thì sẽ được gửi kèm với một bằng chứng giao dịch hợp lệ (Validity Proof). Tuy nhiên, vấn đề là các On-chain Contract trên Ethereum cứ phải xác minh từng bằng chứng một làm cho mạng lưới trở nên chậm chạp hơn. Với Recursive Proofs nó có thể tạo ra nhiều khối và mỗi khối có 1 bằng chứng giao dịch đi kèm sau đó kết hợp nhiều State Root đó và nhiều bằng chứng giao dịch đó, từ nhiều bằng chứng giao dịch tạo ra một bằng chứng giao dịch duy nhất đại diện cho nhiều State Root đó

read more: https://hakresearch.com/zk-rollup-la-gi/
