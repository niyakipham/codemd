# Bài Học 14: Ports và Sockets - Cánh Cửa và Ổ Cắm Vào Mạng 🚪🔌

## Mục Tiêu Bài Học

*   Ôn tập và hiểu sâu hơn về vai trò của **Số hiệu cổng (Port Numbers)** trong việc định danh ứng dụng tại Tầng Giao Vận.
*   Phân loại các dải Port Number: **Well-known Ports**, **Registered Ports**, **Dynamic/Private Ports**.
*   Nắm vững khái niệm **Socket** như một điểm cuối (endpoint) của giao tiếp mạng hai chiều.
*   Hiểu mối quan hệ giữa Socket, Địa chỉ IP và Port Number (Socket Address).
*   Tìm hiểu về **API Lập trình Socket (Socket Programming API)** - cách các ứng dụng tương tác với tầng mạng thông qua hệ điều hành.
*   Phân biệt giữa **Stream Sockets (TCP)** và **Datagram Sockets (UDP)** từ góc độ lập trình.

## Nội Dung Chi Tiết

### 1. Ôn Tập Về Số Hiệu Cổng (Port Numbers)

Như chúng ta đã biết từ Bài 12, Tầng Giao Vận sử dụng Port Numbers để thực hiện chức năng **Multiplexing** (gom dữ liệu từ nhiều ứng dụng tại máy gửi) và **Demultiplexing** (phân phối dữ liệu đến đúng ứng dụng tại máy nhận).

*   **Định danh Ứng dụng:** Port Number là một số nguyên **16 bit** (từ 0 đến 65535) dùng để xác định một **tiến trình (process) hoặc ứng dụng cụ thể** đang chạy trên một máy tính và muốn sử dụng dịch vụ mạng của Tầng Giao Vận (TCP hoặc UDP).
*   **Cặp {IP Address, Port Number}:** Sự kết hợp giữa địa chỉ IP (xác định máy tính trên mạng - Layer 3) và Port Number (xác định ứng dụng trên máy tính đó - Layer 4) tạo thành một **định danh duy nhất** cho một điểm cuối của giao tiếp mạng.

### 2. Phân Loại Các Dải Port Number

Không phải tất cả các Port Number đều được sử dụng như nhau. Tổ chức IANA (Internet Assigned Numbers Authority) quản lý và phân chia các Port Number thành ba dải chính:

*   **a. Well-known Ports (Cổng nổi tiếng / Cổng hệ thống): 0 - 1023**
    *   Đây là các cổng được **dành riêng** cho các dịch vụ và giao thức mạng **phổ biến và tiêu chuẩn hóa**.
    *   Việc gán cổng trong dải này được kiểm soát chặt chẽ bởi IANA.
    *   Trên nhiều hệ điều hành, chỉ các tiến trình chạy với **quyền quản trị (root/administrator)** mới được phép lắng nghe (bind) trên các cổng này.
    *   **Ví dụ quen thuộc:**
        *   `20/21`: FTP (File Transfer Protocol)
        *   `22`: SSH (Secure Shell)
        *   `23`: Telnet
        *   `25`: SMTP (Simple Mail Transfer Protocol - gửi email)
        *   `53`: DNS (Domain Name System) - cả TCP và UDP
        *   `80`: HTTP (HyperText Transfer Protocol - Web)
        *   `110`: POP3 (Post Office Protocol v3 - nhận email)
        *   `143`: IMAP (Internet Message Access Protocol - nhận email)
        *   `443`: HTTPS (HTTP Secure - Web bảo mật)
    *   Khi bạn kết nối đến một dịch vụ chuẩn (như web server), trình duyệt của bạn mặc định sẽ kết nối đến Port 80 (HTTP) hoặc 443 (HTTPS) trên server đó.

*   **b. Registered Ports (Cổng đã đăng ký): 1024 - 49151**
    *   Các cổng này được IANA khuyến nghị **đăng ký** cho các ứng dụng hoặc dịch vụ cụ thể của các công ty hoặc tổ chức, nhưng việc đăng ký **không bắt buộc** và **ít được kiểm soát chặt chẽ hơn** so với Well-known Ports.
    *   Người dùng thông thường (không cần quyền quản trị) thường có thể chạy ứng dụng lắng nghe trên các cổng này.
    *   Mục đích là tránh xung đột cổng giữa các ứng dụng khác nhau.
    *   **Ví dụ:**
        *   `3306`: MySQL Database
        *   `3389`: RDP (Remote Desktop Protocol)
        *   `5432`: PostgreSQL Database
        *   `8080`, `8000`: Thường dùng cho web server thay thế hoặc ứng dụng web development.

*   **c. Dynamic / Private / Ephemeral Ports (Cổng động / Riêng tư / Tạm thời): 49152 - 65535**
    *   Dải cổng này **không được đăng ký** và được hệ điều hành **sử dụng tự do** để gán làm **Source Port (Cổng nguồn)** một cách **tự động và tạm thời** cho các kết nối đi ra (outbound connections) từ phía Client.
    *   Ví dụ: Khi trình duyệt của bạn (Client) kết nối đến web server (Server Port 80), hệ điều hành sẽ chọn một cổng ngẫu nhiên từ dải này (ví dụ: 51234) để làm Source Port cho kết nối đó. Điều này cho phép Server biết gửi phản hồi về cổng nào trên máy Client, và cũng cho phép Client mở nhiều kết nối đến cùng một Server (mỗi kết nối có Source Port khác nhau).
    *   Các cổng này chỉ tồn tại trong thời gian kết nối diễn ra.

### 3. Socket - Điểm Cuối Của Giao Tiếp Mạng

Khái niệm "Socket" thường được sử dụng trong ngữ cảnh **lập trình mạng (Network Programming)**.

*   **Định nghĩa:** Một Socket đại diện cho một **điểm cuối (endpoint) của một kênh giao tiếp mạng hai chiều**. Nó là một **cấu trúc dữ liệu trừu tượng** được cung cấp bởi hệ điều hành, cho phép các ứng dụng gửi và nhận dữ liệu qua mạng.
*   **Socket không phải là Port:** Port là một con số định danh ứng dụng. Socket là "cái ổ cắm" mà ứng dụng dùng để "cắm" vào tầng mạng tại một Port cụ thể.
*   **Socket Address (Địa chỉ Socket):** Để một Socket có thể tham gia giao tiếp mạng, nó cần được gắn (bind) với một địa chỉ cụ thể. Địa chỉ này bao gồm:
    *   **Địa chỉ IP (Layer 3)**
    *   **Số hiệu cổng (Port Number - Layer 4)**
    *   **Giao thức (TCP hoặc UDP - Layer 4)**
    *   Sự kết hợp `(IP Address, Port Number)` thường được gọi là Socket Address.

*   **Một kết nối TCP đầy đủ được xác định bởi một cặp Socket:**
    *   Socket phía Client: `(Client_IP, Client_Port)`
    *   Socket phía Server: `(Server_IP, Server_Port)`
    *   => Bộ 5 giá trị `(Protocol, Client_IP, Client_Port, Server_IP, Server_Port)` xác định duy nhất một kết nối TCP.

*   **Ví dụ đời thường:**
    *   Địa chỉ IP giống như địa chỉ đường phố của một tòa nhà.
    *   Port Number giống như số căn hộ trong tòa nhà đó.
    *   Socket giống như ổ cắm điện thoại hoặc mạng trong căn hộ đó. Bạn cần cắm thiết bị vào Socket để giao tiếp.

### 4. API Lập Trình Socket (Socket Programming API)

Hệ điều hành cung cấp một bộ các hàm (functions) và thủ tục (procedures) chuẩn để các lập trình viên có thể tạo và sử dụng Socket trong ứng dụng của mình. Đây được gọi là Socket API.

*   **API phổ biến nhất:** Berkeley Sockets API (xuất phát từ HĐH BSD Unix), đã trở thành chuẩn de facto trên hầu hết các hệ điều hành (Linux, macOS, Windows - với Winsock API tương tự).
*   **Các thao tác cơ bản với Socket API (Ví dụ cho TCP Client-Server):**
    *   **Server:**
        1.  `socket()`: Tạo một Socket mới.
        2.  `bind()`: Gắn Socket với một địa chỉ IP và Port cụ thể (ví dụ: lắng nghe trên tất cả IP của máy, Port 80).
        3.  `listen()`: Báo cho HĐH biết Socket này sẵn sàng chấp nhận kết nối đến, và đặt giới hạn hàng đợi kết nối chờ.
        4.  `accept()`: Chờ đợi và chấp nhận một kết nối đến từ Client. Thao tác này thường tạo ra một *Socket mới dành riêng* cho việc giao tiếp với Client vừa kết nối, còn Socket gốc vẫn tiếp tục `listen()` để chờ Client khác.
        5.  `recv()` / `read()`: Nhận dữ liệu từ Client qua Socket kết nối.
        6.  `send()` / `write()`: Gửi dữ liệu đến Client qua Socket kết nối.
        7.  `close()`: Đóng Socket kết nối khi hoàn tất.
    *   **Client:**
        1.  `socket()`: Tạo một Socket mới. (Không cần `bind()` vì HĐH sẽ tự gán Source Port động).
        2.  `connect()`: Chủ động yêu cầu kết nối đến địa chỉ IP và Port của Server. Quá trình three-way handshake diễn ra ngầm tại đây.
        3.  `send()` / `write()`: Gửi dữ liệu (yêu cầu) đến Server.
        4.  `recv()` / `read()`: Nhận dữ liệu (phản hồi) từ Server.
        5.  `close()`: Đóng Socket khi hoàn tất.

*   **API cho UDP:** Quy trình đơn giản hơn, không có `listen()`, `accept()`, `connect()`. Chủ yếu dùng `socket()`, `bind()` (cho Server để lắng nghe ở Port cố định), `sendto()` (gửi dữ liệu kèm địa chỉ đích), và `recvfrom()` (nhận dữ liệu kèm địa chỉ nguồn).

### 5. Stream Sockets vs. Datagram Sockets

Socket API thường phân biệt hai loại Socket chính tương ứng với TCP và UDP:

*   **Stream Sockets (TCP):**
    *   Cung cấp một kênh giao tiếp **hai chiều, tuần tự, tin cậy, dựa trên luồng (stream-based)**.
    *   Dữ liệu được gửi và nhận như một **luồng byte liên tục**, không có ranh giới thông điệp rõ ràng được giữ lại. Bên gửi ghi một chuỗi byte, bên nhận đọc một chuỗi byte. Kích thước đọc/ghi không nhất thiết phải giống nhau.
    *   Tương ứng với giao thức **TCP**. Phù hợp cho việc truyền dữ liệu cần đảm bảo tính toàn vẹn và đúng thứ tự.
    *   Ví dụ: Truyền file, tải trang web.

*   **Datagram Sockets (UDP):**
    *   Cung cấp một kênh giao tiếp **không kết nối, không tin cậy, dựa trên thông điệp (message-based)**.
    *   Dữ liệu được gửi và nhận dưới dạng các **Datagram (gói tin) riêng lẻ**. Ranh giới của mỗi Datagram được bảo toàn. Nếu bên gửi gửi 3 Datagram, bên nhận (nếu nhận được) cũng sẽ nhận được 3 Datagram riêng biệt.
    *   Có thể bị mất mát, trùng lặp hoặc sai thứ tự.
    *   Tương ứng với giao thức **UDP**. Phù hợp cho các truy vấn ngắn, dữ liệu thời gian thực không yêu cầu độ tin cậy cao.
    *   Ví dụ: DNS query, cập nhật vị trí game.

## Tóm Tắt & Bài Học Tiếp Theo

Port Numbers là chìa khóa để Tầng Giao Vận phân phối dữ liệu đến đúng ứng dụng. Các dải cổng Well-known, Registered và Dynamic giúp tổ chức và quản lý việc sử dụng cổng. Sockets là giao diện lập trình cho phép ứng dụng tương tác với mạng tại một cặp IP:Port cụ thể, thông qua Socket API do hệ điều hành cung cấp. Có hai loại Socket chính là Stream (TCP) và Datagram (UDP) tương ứng với hai giao thức vận chuyển chính.

Sau khi đã hiểu cách Tầng Giao Vận vận chuyển dữ liệu đến đúng "căn hộ" (Port/Socket) của ứng dụng, chúng ta sẽ cùng bước vào "căn hộ" đó ở bài học tiếp theo (`BaiHoc_15_TangUngDung.md`). Chúng ta sẽ khám phá **Tầng Ứng Dụng (Application Layer)** - nơi các giao thức mạng quen thuộc như HTTP, DNS, SMTP... hoạt động và cung cấp các dịch vụ trực tiếp cho người dùng. Hãy sẵn sàng gặp gỡ những "người nổi tiếng" của thế giới mạng nhé! ✨🏆
