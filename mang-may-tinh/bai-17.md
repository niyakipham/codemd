# Bài Học 17: HTTP và HTTPS - Ngôn Ngữ Của World Wide Web 🌐💬🔒

## Mục Tiêu Bài Học

*   Hiểu rõ vai trò của HTTP (HyperText Transfer Protocol) là nền tảng giao tiếp cho World Wide Web.
*   Nắm vững mô hình yêu cầu/phản hồi (Request/Response) của HTTP.
*   Tìm hiểu cấu trúc của một Thông điệp HTTP (HTTP Message): Start Line, Headers, Body.
*   Biết về các Phương thức HTTP (HTTP Methods/Verbs) phổ biến: GET, POST, PUT, DELETE, HEAD, OPTIONS...
*   Hiểu ý nghĩa của các Mã trạng thái HTTP (HTTP Status Codes) phổ biến (1xx, 2xx, 3xx, 4xx, 5xx).
*   Nắm được khái niệm HTTP là giao thức **Stateless (Không trạng thái)** và cách **Cookies** được sử dụng để duy trì trạng thái.
*   Hiểu tại sao cần **HTTPS (HTTP Secure)** và cách nó hoạt động: Sử dụng **SSL/TLS** để mã hóa và xác thực.
*   Phân biệt giữa HTTP và HTTPS.

## Nội Dung Chi Tiết

### 1. HTTP (HyperText Transfer Protocol) - Nền Tảng Của Web

*   **Định nghĩa:** HTTP là một giao thức ở **Tầng Ứng Dụng** được thiết kế để truyền tải các **tài nguyên siêu văn bản (hypermedia resources)**, chủ yếu là các trang HTML, nhưng cũng bao gồm hình ảnh, video, file CSS, JavaScript, và bất kỳ loại dữ liệu nào khác qua mạng, đặc biệt là trên World Wide Web.
*   **Kiến trúc:** Hoạt động theo mô hình **Client-Server**.
    *   **Client:** Thường là trình duyệt web (Web Browser). Client gửi **HTTP Request (Yêu cầu HTTP)** đến Server để yêu cầu một tài nguyên.
    *   **Server:** Thường là máy chủ web (Web Server - như Apache, Nginx, IIS). Server xử lý yêu cầu, tìm tài nguyên được yêu cầu và gửi **HTTP Response (Phản hồi HTTP)** chứa tài nguyên đó (hoặc thông báo lỗi) về cho Client.
*   **Giao thức vận chuyển:** HTTP sử dụng **TCP (Transmission Control Protocol)** làm giao thức vận chuyển ở Layer 4. Điều này đảm bảo việc truyền dữ liệu diễn ra **tin cậy và đúng thứ tự**. Cổng TCP mặc định cho HTTP là **Port 80**.

### 2. Mô Hình Yêu Cầu/Phản Hồi (Request/Response)

Toàn bộ giao tiếp HTTP dựa trên chu trình này:

1.  **Client gửi HTTP Request:** Client (trình duyệt) muốn lấy tài nguyên tại một URL (ví dụ: `http://www.example.com/index.html`), nó sẽ mở một kết nối TCP đến Server (tại IP của `www.example.com`, Port 80) và gửi một thông điệp HTTP Request qua kết nối đó.
2.  **Server xử lý Request:** Server nhận Request, phân tích nó (muốn lấy tài nguyên nào? dùng phương thức gì?), tìm tài nguyên hoặc thực hiện hành động yêu cầu.
3.  **Server gửi HTTP Response:** Server tạo một thông điệp HTTP Response chứa kết quả (nội dung tài nguyên, trạng thái thành công/lỗi) và gửi lại cho Client qua cùng kết nối TCP.
4.  **Client xử lý Response:** Client (trình duyệt) nhận Response, đóng kết nối TCP (trừ khi dùng Persistent Connections), và xử lý nội dung nhận được (ví dụ: hiển thị trang HTML).

### 3. Cấu Trúc Thông Điệp HTTP (HTTP Message)

Cả Request và Response đều có cấu trúc tương tự, bao gồm (tùy chọn) các phần sau, viết dưới dạng văn bản thuần túy (plain text), các dòng cách nhau bởi `CRLF` (\r\n):

*   **a. Start Line (Dòng bắt đầu):** Dòng đầu tiên, cung cấp thông tin cơ bản về thông điệp.
    *   **Request Line:** `Method SP Request-URI SP HTTP-Version CRLF`
        *   `Method`: Phương thức HTTP (GET, POST...).
        *   `Request-URI`: Đường dẫn đến tài nguyên trên Server (ví dụ: `/index.html`, `/images/logo.png`).
        *   `HTTP-Version`: Phiên bản HTTP (ví dụ: `HTTP/1.1`, `HTTP/2`).
        *   Ví dụ: `GET /index.html HTTP/1.1`
    *   **Status Line (Chỉ có ở Response):** `HTTP-Version SP Status-Code SP Reason-Phrase CRLF`
        *   `HTTP-Version`: Phiên bản HTTP.
        *   `Status-Code`: Mã trạng thái (200, 404...).
        *   `Reason-Phrase`: Mô tả ngắn gọn bằng chữ của mã trạng thái (OK, Not Found...).
        *   Ví dụ: `HTTP/1.1 200 OK`

*   **b. HTTP Headers (Các trường tiêu đề):** Không bắt buộc, nhưng rất phổ biến. Cung cấp các **thông tin bổ sung (metadata)** về Request hoặc Response, hoặc về chính nội dung (Body) sẽ được gửi.
    *   Mỗi Header là một cặp `Tên-Header: Giá-trị` trên một dòng.
    *   Có rất nhiều loại Header được chuẩn hóa (ví dụ: `Host`, `User-Agent`, `Accept`, `Content-Type`, `Content-Length`, `Set-Cookie`, `Cache-Control`...).
    *   Ví dụ Headers trong Request:
        ```
        Host: www.example.com
        User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) ...
        Accept: text/html,application/xhtml+xml,*/*
        Accept-Language: en-US,en;q=0.5
        ```
    *   Ví dụ Headers trong Response:
        ```
        Date: Tue, 15 Nov 2024 10:00:00 GMT
        Server: Apache/2.4.41 (Ubuntu)
        Content-Type: text/html; charset=UTF-8
        Content-Length: 12345
        Connection: close
        ```
*   **c. Empty Line (Dòng trống):** Một dòng chỉ chứa `CRLF`. Dòng này bắt buộc phải có để **ngăn cách** phần Headers và phần Body.
*   **d. Message Body (Phần thân thông điệp):** Không bắt buộc. Chứa dữ liệu thực tế của Request hoặc Response.
    *   **Request Body:** Thường dùng với phương thức `POST` hoặc `PUT` để gửi dữ liệu từ Client lên Server (ví dụ: dữ liệu form đăng nhập, file upload).
    *   **Response Body:** Thường chứa nội dung tài nguyên được yêu cầu (ví dụ: mã HTML của trang web, dữ liệu ảnh).
    *   Sự tồn tại và định dạng của Body thường được chỉ định bởi các Header như `Content-Type` và `Content-Length`.

### 4. Các Phương Thức HTTP Phổ Biến (HTTP Methods/Verbs)

Phương thức HTTP chỉ định hành động mong muốn được thực hiện trên tài nguyên được xác định bởi Request-URI.

*   **GET:** Yêu cầu lấy (retrieve) tài nguyên tại URI đã cho. Đây là phương thức phổ biến nhất. **An toàn** (không làm thay đổi trạng thái Server) và **Idempotent** (gọi nhiều lần có kết quả như gọi 1 lần). Dữ liệu gửi kèm (nếu có) thường nằm trong URI (query string).
*   **POST:** Gửi dữ liệu đến Server để xử lý (ví dụ: tạo một tài nguyên mới, gửi dữ liệu form). Dữ liệu được gửi trong **Request Body**. **Không an toàn** và **không idempotent**.
*   **PUT:** Gửi dữ liệu đến Server để **tạo mới hoặc thay thế toàn bộ** tài nguyên tại URI đã cho. Dữ liệu nằm trong Request Body. **Idempotent** (gọi nhiều lần kết quả như gọi 1 lần) nhưng **không an toàn**.
*   **DELETE:** Yêu cầu Server **xóa** tài nguyên tại URI đã cho. **Idempotent** nhưng **không an toàn**.
*   **HEAD:** Giống hệt `GET`, nhưng Server **chỉ trả về Headers**, không trả về Body. Hữu ích để kiểm tra thông tin metadata (Content-Type, Content-Length, ngày sửa đổi...) mà không cần tải toàn bộ nội dung.
*   **OPTIONS:** Yêu cầu Server cho biết các phương thức HTTP nào được hỗ trợ cho tài nguyên tại URI đã cho.
*   **CONNECT:** Dùng để thiết lập một kết nối tunnel (ví dụ: cho HTTPS).
*   **TRACE:** Yêu cầu Server gửi lại Request mà nó nhận được. Dùng để debug, nhưng có thể bị lạm dụng và thường bị tắt.
*   **PATCH:** Dùng để áp dụng các thay đổi **một phần** cho tài nguyên (khác với PUT thay thế toàn bộ).

### 5. Mã Trạng Thái HTTP Phổ Biến (HTTP Status Codes)

Mã trạng thái trong dòng Status Line của Response cho Client biết kết quả xử lý Request. Chúng được chia thành 5 lớp:

*   **1xx (Informational - Thông tin):** Request đã được nhận, đang tiếp tục xử lý. (Ít gặp).
    *   `100 Continue`
*   **2xx (Successful - Thành công):** Request đã được nhận, hiểu và chấp nhận thành công.
    *   `200 OK`: Thành công chuẩn cho GET, HEAD, PUT, POST.
    *   `201 Created`: Request đã thành công và một tài nguyên mới đã được tạo (thường dùng cho POST, PUT).
    *   `204 No Content`: Server xử lý thành công nhưng không có nội dung để trả về (ví dụ: sau khi DELETE thành công).
*   **3xx (Redirection - Chuyển hướng):** Cần thực hiện thêm hành động để hoàn thành Request. Client thường phải tự động truy cập một URI khác.
    *   `301 Moved Permanently`: Tài nguyên đã chuyển đi vĩnh viễn sang URI mới (trong Header `Location`). Tốt cho SEO.
    *   `302 Found` / `307 Temporary Redirect`: Tài nguyên tạm thời ở URI khác. Client nên tiếp tục dùng URI gốc cho lần sau.
    *   `304 Not Modified`: Tài nguyên không thay đổi kể từ lần truy cập trước (dùng cho caching). Server không gửi lại Body.
*   **4xx (Client Error - Lỗi phía Client):** Request chứa cú pháp sai hoặc không thể hoàn thành.
    *   `400 Bad Request`: Request không hợp lệ.
    *   `401 Unauthorized`: Cần xác thực (chưa đăng nhập).
    *   `403 Forbidden`: Đã xác thực nhưng không có quyền truy cập tài nguyên.
    *   `404 Not Found`: Tài nguyên được yêu cầu không tồn tại trên Server.
    *   `405 Method Not Allowed`: Phương thức HTTP không được phép cho tài nguyên này.
*   **5xx (Server Error - Lỗi phía Server):** Server gặp lỗi khi cố gắng xử lý một Request hợp lệ.
    *   `500 Internal Server Error`: Lỗi chung chung phía Server.
    *   `502 Bad Gateway`: Server hoạt động như gateway/proxy nhận phản hồi không hợp lệ từ server nguồn.
    *   `503 Service Unavailable`: Server tạm thời quá tải hoặc đang bảo trì.
    *   `504 Gateway Timeout`: Server hoạt động như gateway/proxy không nhận được phản hồi kịp thời từ server nguồn.

### 6. HTTP Stateless và Cookies

*   **Stateless (Không trạng thái):** HTTP được thiết kế là giao thức không trạng thái. Nghĩa là **mỗi cặp Request/Response là độc lập**. Server không lưu trữ bất kỳ thông tin nào về các Request trước đó từ cùng một Client.
*   **Vấn đề:** Làm sao để Server nhận ra người dùng quay lại, duy trì trạng thái đăng nhập, giỏ hàng...?
*   **Giải pháp: Cookies!**
    1.  Khi Client đăng nhập hoặc thực hiện hành động cần ghi nhớ, Server có thể gửi một **Cookie** (một mẩu dữ liệu nhỏ) về cho Client thông qua Header `Set-Cookie` trong HTTP Response.
    2.  Trình duyệt Client sẽ **lưu trữ Cookie** này lại (thường gắn với tên miền của Server).
    3.  Trong các **Request tiếp theo** đến cùng Server đó, trình duyệt sẽ **tự động gửi kèm Cookie** đó trong Header `Cookie` của HTTP Request.
    4.  Server đọc Cookie nhận được để **nhận dạng Client** và khôi phục trạng thái (ví dụ: biết người dùng đã đăng nhập, lấy thông tin giỏ hàng).

=> Cookies giúp "tạo" trạng thái trên nền giao thức HTTP vốn không trạng thái.

### 7. HTTPS (HTTP Secure) - Thêm Bảo Mật Cho Web

*   **Vấn đề của HTTP:** Toàn bộ thông tin trong HTTP Request và Response (bao gồm cả Headers và Body, có thể chứa username, password, thông tin nhạy cảm) được truyền đi dưới dạng **văn bản thuần túy (plain text)**, không mã hóa. Kẻ gian ở giữa (Man-in-the-Middle) có thể **dễ dàng đọc trộm hoặc thay đổi** dữ liệu này. Server cũng không được xác thực, Client không chắc mình đang nói chuyện với đúng Server thật.
*   **Giải pháp: HTTPS!** HTTPS không phải là một giao thức riêng biệt, mà là **HTTP chạy trên một lớp bảo mật bổ sung** gọi là **SSL/TLS (Secure Sockets Layer / Transport Layer Security)**.
    *   `HTTP + SSL/TLS = HTTPS`
*   **Cách hoạt động:**
    1.  **Thiết lập kết nối an toàn (SSL/TLS Handshake):** Trước khi bất kỳ dữ liệu HTTP nào được gửi, Client và Server thực hiện một quá trình "bắt tay SSL/TLS" phức tạp trên nền kết nối TCP (Cổng mặc định **Port 443**). Quá trình này bao gồm:
        *   **Xác thực Server:** Server gửi **Chứng chỉ số (SSL/TLS Certificate)** của mình cho Client. Client kiểm tra tính hợp lệ của chứng chỉ (được cấp bởi Tổ chức Chứng thực số - CA đáng tin cậy, chưa hết hạn, đúng tên miền...). Điều này giúp Client **chắc chắn mình đang nói chuyện với Server thật**, không phải kẻ mạo danh.
        *   **Thỏa thuận thuật toán mã hóa:** Client và Server thống nhất các thuật toán mã hóa đối xứng (symmetric encryption - như AES) và khóa bí mật (session key) sẽ dùng để mã hóa dữ liệu HTTP sau này. Khóa bí mật này được trao đổi an toàn nhờ mã hóa bất đối xứng (asymmetric encryption - như RSA) hoặc Diffie-Hellman.
    2.  **Truyền dữ liệu HTTP được mã hóa:** Sau khi handshake thành công, toàn bộ dữ liệu HTTP (Request và Response) sẽ được **mã hóa bằng khóa bí mật đã thỏa thuận** trước khi gửi đi và được giải mã tại đầu nhận.
*   **Lợi ích của HTTPS:**
    *   **Confidentiality (Bảo mật):** Dữ liệu được mã hóa, kẻ gian không đọc được.
    *   **Integrity (Toàn vẹn):** Đảm bảo dữ liệu không bị thay đổi trên đường truyền (thông qua mã MAC - Message Authentication Code).
    *   **Authentication (Xác thực):** Client xác thực được danh tính của Server. (Có thể có cả xác thực Client nếu dùng Client Certificate).
*   **Hiện trạng:** HTTPS ngày nay là **tiêu chuẩn bắt buộc** cho hầu hết các trang web, đặc biệt là những trang yêu cầu đăng nhập, giao dịch tài chính, hoặc xử lý thông tin cá nhân. Các trình duyệt hiện đại cảnh báo người dùng khi truy cập trang HTTP không an toàn.

## Tóm Tắt & Bài Học Tiếp Theo

HTTP là ngôn ngữ giao tiếp cốt lõi của Web, hoạt động theo mô hình Request/Response trên nền TCP. Các phương thức và mã trạng thái định nghĩa hành động và kết quả. Tuy stateless, HTTP dùng Cookies để duy trì trạng thái. HTTPS bổ sung lớp mã hóa SSL/TLS lên trên HTTP, đảm bảo an toàn, toàn vẹn và xác thực cho giao tiếp web, trở thành chuẩn mực hiện nay.

Tiếp theo, chúng ta sẽ khám phá cách thức hoạt động của một dịch vụ quen thuộc khác mà bạn sử dụng hàng ngày: **Email**. Bài học tiếp theo (`BaiHoc_18_Email_SMTP_POP3_IMAP.md`) sẽ đi sâu vào các giao thức đằng sau việc gửi và nhận thư điện tử: SMTP, POP3 và IMAP. Hãy sẵn sàng mở hộp thư kiến thức nhé! ✉️📬
