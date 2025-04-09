# Bài Học 16: DNS (Domain Name System) - Danh Bạ Khổng Lồ Của Internet 📖☎️

## Mục Tiêu Bài Học

*   Hiểu rõ mục đích và tầm quan trọng của Hệ thống Tên Miền (DNS).
*   Nắm vững các thành phần chính của hệ thống DNS:
    *   DNS Resolver (Client-side)
    *   Root Name Servers
    *   TLD (Top-Level Domain) Name Servers
    *   Authoritative Name Servers
*   Hiểu hai cơ chế truy vấn DNS chính: **Recursive Query (Truy vấn đệ quy)** và **Iterative Query (Truy vấn tương tác)**.
*   Tìm hiểu về **DNS Caching (Bộ nhớ đệm DNS)** và vai trò của nó.
*   Biết về các loại **Bản ghi DNS (DNS Records)** phổ biến và chức năng của chúng (A, AAAA, CNAME, MX, NS, TXT, SOA).
*   Hiểu sơ lược về cách cập nhật DNS và khái niệm DNS Propagation.

## Nội Dung Chi Tiết

### 1. Tại Sao Cần DNS? Tên Miền vs. Địa Chỉ IP

*   Máy tính và các thiết bị mạng giao tiếp với nhau bằng **Địa chỉ IP (Internet Protocol)** - những con số như `172.217.160.142` (IPv4) hoặc `2404:6800:4003:c07::63` (IPv6). Địa chỉ IP logic và cần thiết cho việc định tuyến trên mạng.
*   Tuy nhiên, con người lại dễ nhớ và làm việc với những cái **tên (Tên miền - Domain Names)** hơn, ví dụ: `www.google.com`, `facebook.com`, `vnexpress.net`.
*   **Vấn đề:** Làm thế nào để chuyển đổi qua lại giữa tên miền dễ nhớ và địa chỉ IP khó nhớ mà máy tính cần?
*   **Giải pháp:** **DNS (Domain Name System - Hệ thống Tên Miền)** ra đời. DNS hoạt động như một **dịch vụ danh bạ phân tán toàn cầu**, chuyên **phân giải (resolve)** tên miền thành địa chỉ IP và ngược lại.

=> DNS là một trong những dịch vụ nền tảng thiết yếu, nếu DNS ngừng hoạt động, việc truy cập Internet bằng tên miền sẽ trở nên gần như không thể.

### 2. Các Thành Phần Chính Của Hệ Thống DNS

DNS không phải là một máy chủ đơn lẻ mà là một hệ thống phân cấp, phân tán phức tạp bao gồm các loại máy chủ (Name Servers) khác nhau:

*   **a. DNS Resolver (hay DNS Client, Stub Resolver):**
    *   Là thành phần nằm trên **máy tính của người dùng** (hoặc trong router gia đình).
    *   Nó **nhận yêu cầu phân giải tên miền** từ các ứng dụng (ví dụ: trình duyệt khi bạn gõ `google.com`).
    *   Nó **gửi truy vấn DNS** đến các máy chủ DNS khác (thường là Recursive DNS Server) để tìm ra địa chỉ IP tương ứng.
    *   Nó **lưu kết quả vào bộ nhớ đệm (cache)** để tăng tốc cho các lần truy vấn sau.

*   **b. Recursive DNS Server (hay Caching DNS Server):**
    *   Đây thường là máy chủ DNS do **ISP (Nhà cung cấp dịch vụ Internet)** hoặc các **bên thứ ba** (như Google DNS - `8.8.8.8`, Cloudflare DNS - `1.1.1.1`, OpenDNS) cung cấp.
    *   Nó **nhận yêu cầu Recursive Query** từ DNS Resolver của người dùng.
    *   Nó chịu trách nhiệm **thực hiện toàn bộ quá trình truy vấn** (hỏi Root Server, TLD Server, Authoritative Server) thay cho Client để tìm ra câu trả lời cuối cùng (địa chỉ IP).
    *   Nó cũng **lưu kết quả vào cache** để phục vụ nhanh hơn cho các yêu cầu tương tự từ những người dùng khác.

*   **c. Root Name Servers (Máy chủ Tên Gốc):**
    *   Nằm ở **đỉnh cao nhất** của hệ thống phân cấp DNS.
    *   Có **13 cụm Root Server logic** (được đặt tên từ A đến M) được quản lý bởi các tổ chức khác nhau trên toàn thế giới (nhưng mỗi cụm logic có thể bao gồm hàng trăm máy chủ vật lý phân tán nhờ công nghệ Anycast).
    *   Chúng **không trực tiếp biết địa chỉ IP** của `www.google.com`.
    *   Vai trò chính của chúng là **chỉ dẫn (referral)**: Khi nhận truy vấn, chúng sẽ cho biết **địa chỉ của TLD Name Server** chịu trách nhiệm cho phần đuôi tên miền cấp cao nhất (ví dụ: `.com`, `.org`, `.net`, `.vn`).

*   **d. TLD (Top-Level Domain) Name Servers (Máy chủ Tên Miền Cấp Cao Nhất):**
    *   Quản lý thông tin cho các tên miền cấp cao nhất như `.com`, `.org`, `.net`, `.edu`, `.gov`, và các mã quốc gia như `.vn`, `.uk`, `.jp`.
    *   Khi nhận truy vấn (ví dụ: cho `google.com`), TLD Server của `.com` sẽ **không biết địa chỉ IP** của `www.google.com`.
    *   Vai trò của chúng là **chỉ dẫn tiếp**: Cho biết **địa chỉ của Authoritative Name Server** chịu trách nhiệm cho tên miền cụ thể đó (`google.com`).

*   **e. Authoritative Name Servers (Máy chủ Tên có Thẩm quyền):**
    *   Đây là các máy chủ DNS **chứa thông tin gốc và chính thức** (các bản ghi DNS) cho một tên miền cụ thể (ví dụ: `google.com`, `vnexpress.net`).
    *   Thường được quản lý bởi chính chủ sở hữu tên miền hoặc bởi nhà cung cấp dịch vụ DNS hosting cho họ.
    *   Khi nhận truy vấn cho một tên miền mà nó quản lý (ví dụ: `www.google.com`), nó sẽ **trả về câu trả lời cuối cùng** (ví dụ: địa chỉ IP của `www`) từ các bản ghi DNS mà nó lưu giữ.
    *   Mỗi tên miền thường có ít nhất hai Authoritative Name Server (Primary và Secondary) để đảm bảo tính sẵn sàng.

### 3. Quá Trình Phân Giải Tên Miền (DNS Resolution)

Khi bạn gõ `www.example.com` vào trình duyệt:

1.  **Trình duyệt/HĐH:** Kiểm tra cache cục bộ (browser cache, OS cache), file `hosts` xem có thông tin IP của `www.example.com` chưa. Nếu có -> Dùng luôn, kết thúc. Nếu không -> Chuyển yêu cầu đến DNS Resolver.
2.  **DNS Resolver (Client):** Gửi một **Recursive Query (Truy vấn đệ quy)** đến **Recursive DNS Server** (ví dụ: `8.8.8.8`). Yêu cầu: "Hãy tìm IP của `www.example.com` và trả lời cho tôi."
3.  **Recursive DNS Server:**
    *   Kiểm tra cache của nó. Nếu có -> Trả lời ngay cho Resolver, kết thúc. Nếu không:
    *   **Gửi Iterative Query (Truy vấn tương tác)** đến một **Root Name Server**: "Làm sao để tìm `.com`?"
4.  **Root Name Server:** Trả lời cho Recursive Server: "Tôi không biết `www.example.com`, nhưng đây là địa chỉ của các **TLD Name Server** quản lý `.com`."
5.  **Recursive DNS Server:** Gửi Iterative Query đến một **TLD Name Server (.com)**: "Làm sao để tìm `example.com`?"
6.  **TLD Name Server (.com):** Trả lời: "Tôi không biết `www.example.com`, nhưng đây là địa chỉ của các **Authoritative Name Server** quản lý `example.com`."
7.  **Recursive DNS Server:** Gửi Iterative Query đến một **Authoritative Name Server** của `example.com`: "Địa chỉ IP của `www.example.com` là gì?"
8.  **Authoritative Name Server (example.com):** Tra cứu bản ghi DNS của mình và trả lời (ví dụ): "`www.example.com` có địa chỉ IP là `93.184.216.34`" (Đây là địa chỉ của bản ghi A).
9.  **Recursive DNS Server:** Nhận được câu trả lời cuối cùng. Nó **lưu kết quả này vào cache** (với thời gian sống TTL - Time To Live) và **trả về địa chỉ IP** (`93.184.216.34`) cho **DNS Resolver (Client)**.
10. **DNS Resolver (Client):** Lưu kết quả vào cache cục bộ và trả địa chỉ IP về cho ứng dụng (trình duyệt).
11. **Trình duyệt:** Sử dụng địa chỉ IP này để thiết lập kết nối TCP đến Web Server của `www.example.com` qua Port 80/443.

**Điểm mấu chốt:** Client (Resolver) chỉ gửi 1 truy vấn đệ quy. Recursive Server thực hiện nhiều truy vấn tương tác để tìm ra câu trả lời.

### 4. DNS Caching (Bộ Nhớ Đệm DNS)

*   DNS caching xảy ra ở nhiều cấp độ (Trình duyệt, HĐH, Recursive Server) để **tăng tốc độ phân giải** và **giảm tải** cho các Name Server cấp cao hơn.
*   Mỗi bản ghi DNS có một **TTL (Time To Live)** - thời gian (tính bằng giây) mà cache được phép lưu trữ và sử dụng lại thông tin đó trước khi phải hỏi lại Authoritative Server. TTL do quản trị viên của tên miền thiết lập.

### 5. Các Loại Bản Ghi DNS Phổ Biến (DNS Records)

Authoritative Name Server lưu trữ thông tin DNS dưới dạng các **bản ghi (records)**. Một số loại phổ biến:

*   **A (Address):** Ánh xạ một tên miền (hostname) sang một **địa chỉ IPv4**.
    *   `www.example.com A 93.184.216.34`
*   **AAAA (Quad A):** Ánh xạ một tên miền sang một **địa chỉ IPv6**.
    *   `www.example.com AAAA 2606:2800:220:1:248:1893:25c8:1946`
*   **CNAME (Canonical Name):** Tạo một **bí danh (alias)** cho một tên miền khác (tên miền gốc - canonical name). Khi truy vấn tên bí danh, DNS sẽ trả về tên miền gốc, và quá trình phân giải tiếp tục với tên miền gốc đó.
    *   `ftp.example.com CNAME www.example.com` (Nếu truy cập `ftp`, thực chất sẽ được phân giải ra IP của `www`)
*   **MX (Mail Exchanger):** Chỉ định các **máy chủ mail (Mail Servers)** chịu trách nhiệm nhận email cho một tên miền. Có thể có nhiều bản ghi MX với các mức ưu tiên (priority) khác nhau (số nhỏ hơn ưu tiên cao hơn).
    *   `example.com MX 10 mail1.example.com`
    *   `example.com MX 20 mail2.example.com`
*   **NS (Name Server):** Chỉ định các **Authoritative Name Servers** cho một tên miền (hoặc tên miền con - subdomain).
    *   `example.com NS ns1.exampledns.com`
    *   `example.com NS ns2.exampledns.com`
*   **TXT (Text):** Cho phép lưu trữ **dữ liệu dạng văn bản tùy ý**. Thường dùng cho mục đích xác minh (SPF, DKIM, DMARC - chống spam mail), hoặc các thông tin khác.
*   **SOA (Start of Authority):** Chứa thông tin quản trị quan trọng về một vùng DNS (zone), bao gồm Primary Name Server, email quản trị, các thông số thời gian (refresh, retry, expire, TTL mặc định). Mỗi zone phải có một bản ghi SOA.

### 6. Cập Nhật DNS & Propagation

*   Khi bạn thay đổi các bản ghi DNS (ví dụ: đổi IP của web server, đổi Mail Server), thông tin này cần được cập nhật trên các **Authoritative Name Server** của bạn.
*   Tuy nhiên, do cơ chế **Caching** ở các Recursive Server và các client khác nhau trên toàn cầu, thay đổi này **không có hiệu lực ngay lập tức** với tất cả mọi người.
*   **DNS Propagation (Lan truyền DNS):** Là quá trình các thay đổi DNS được cập nhật dần dần trên các DNS Cache toàn cầu. Quá trình này có thể mất từ vài phút đến **24-72 giờ**, tùy thuộc vào **TTL** của bản ghi đã được cache trước đó. Trong thời gian này, một số người dùng có thể thấy thông tin mới, trong khi những người khác vẫn thấy thông tin cũ.

## Tóm Tắt & Bài Học Tiếp Theo

DNS là một hệ thống phân cấp, phân tán phức tạp nhưng vô cùng quan trọng, giúp chuyển đổi tên miền dễ nhớ sang địa chỉ IP mà máy tính cần. Quá trình phân giải liên quan đến nhiều loại Name Server và hai kiểu truy vấn chính (Recursive & Iterative). DNS Caching giúp tăng tốc độ, còn các loại Bản ghi DNS định nghĩa các loại thông tin khác nhau cho tên miền.

Sau khi đã biết cách tìm ra địa chỉ IP của Web Server nhờ DNS, bài học tiếp theo (`BaiHoc_17_HTTP_Va_HTTPS.md`) sẽ đưa chúng ta đến với giao thức chính dùng để "nói chuyện" với Web Server đó: **HTTP (HyperText Transfer Protocol)** và phiên bản bảo mật **HTTPS**. Hãy sẵn sàng khám phá cách các trang web được tải về trình duyệt của bạn! 🌐📄🔒
