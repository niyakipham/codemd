# Bài Học 02: Mô Hình Tham Chiếu OSI và TCP/IP - Bản Thiết Kế Của Mạng 🏗️

## Mục Tiêu Bài Học

*   Hiểu tại sao cần có các mô hình tham chiếu trong mạng máy tính.
*   Nắm vững cấu trúc, chức năng của 7 tầng trong mô hình OSI.
*   Nắm vững cấu trúc, chức năng của 4 (hoặc 5) tầng trong mô hình TCP/IP.
*   So sánh được sự giống và khác nhau giữa hai mô hình OSI và TCP/IP.
*   Hiểu khái niệm "đóng gói dữ liệu" (Encapsulation) và "mở gói dữ liệu" (Decapsulation).

## Nội Dung Chi Tiết

### 1. Tại Sao Cần Mô Hình Tham Chiếu?

Hãy tưởng tượng việc xây dựng một tòa nhà chọc trời. Bạn không thể cứ thế đổ bê tông và xếp gạch. Cần có bản thiết kế chi tiết, chia thành các hạng mục: móng, khung, điện, nước, nội thất...

Mạng máy tính cũng phức tạp như vậy. Mô hình tham chiếu giúp:

*   **Chia nhỏ sự phức tạp:** Phân tách các chức năng mạng thành các **tầng (layers)** độc lập, dễ quản lý và phát triển hơn.
*   **Tiêu chuẩn hóa:** Các nhà sản xuất khác nhau có thể tạo ra thiết bị và phần mềm tương thích với nhau nếu cùng tuân theo một mô hình.
*   **Dễ học và nghiên cứu:** Cung cấp một khuôn khổ để hiểu cách dữ liệu di chuyển qua mạng.
*   **Khắc phục sự cố:** Giúp cô lập vấn đề xảy ra ở tầng nào.

Có hai mô hình tham chiếu chính: OSI và TCP/IP.

### 2. Mô Hình OSI (Open Systems Interconnection)

Do Tổ chức Tiêu chuẩn hóa Quốc tế (ISO) phát triển, gồm 7 tầng. Đây là mô hình lý thuyết, chuẩn mực, giúp hiểu rõ chức năng từng lớp.

+---------------------+ +---------------------+
| 7. Application | ----> | Dữ liệu người dùng|
+---------------------+ +---------------------+ ⬆️ Encapsulation
| 6. Presentation | ----> | Dữ liệu định dạng| ⬇️ Decapsulation
+---------------------+ +---------------------+
| 5. Session | ----> | Dữ liệu phiên |
+---------------------+ +---------------------+
| 4. Transport | ----> | Segment/Datagram| (+ TCP/UDP Header)
+---------------------+ +---------------------+
| 3. Network | ----> | Packet | (+ IP Header)
+---------------------+ +---------------------+
| 2. Data Link | ----> | Frame | (+ MAC Header/Trailer)
+---------------------+ +---------------------+
| 1. Physical | ----> | Bits | (Tín hiệu điện/quang...)
+---------------------+ +---------------------+
Mô hình OSI Đơn vị dữ liệu (PDU)

*   **Tầng 7: Application (Ứng dụng):** Cung cấp giao diện cho người dùng và các ứng dụng truy cập vào mạng (HTTP, FTP, SMTP, DNS...). *"Cánh cửa" vào mạng.*
*   **Tầng 6: Presentation (Trình diễn):** Đảm bảo dữ liệu từ tầng Ứng dụng của máy gửi có thể được hiểu bởi tầng Ứng dụng của máy nhận. Chịu trách nhiệm **định dạng dữ liệu, mã hóa/giải mã, nén/giải nén.** *"Người phiên dịch" của mạng.*
*   **Tầng 5: Session (Phiên):** Thiết lập, quản lý và kết thúc các **phiên (session)** giao tiếp giữa hai máy. Đảm bảo dữ liệu của các ứng dụng khác nhau không bị lẫn lộn. *"Người quản lý cuộc hội thoại."*
*   **Tầng 4: Transport (Giao vận):** Cung cấp dịch vụ vận chuyển dữ liệu **đầu cuối (end-to-end)** giữa các **tiến trình (processes)** đang chạy trên hai máy. Có hai kiểu chính:
    *   **TCP (Transmission Control Protocol):** Hướng kết nối, đảm bảo tin cậy, kiểm soát luồng, kiểm soát tắc nghẽn.
    *   **UDP (User Datagram Protocol):** Không kết nối, không đảm bảo tin cậy, nhanh và đơn giản.
    *   Sử dụng **số hiệu cổng (port number)** để phân biệt các ứng dụng.
    *   Đơn vị dữ liệu: **Segment (TCP)** hoặc **Datagram (UDP)**. *"Người vận chuyển hàng hóa tin cậy hoặc siêu tốc."*
*   **Tầng 3: Network (Mạng):** Chịu trách nhiệm **định địa chỉ logic (IP address)** và **chọn đường (routing)** tốt nhất cho dữ liệu đi qua các mạng khác nhau để đến đích.
    *   Thiết bị chính: **Router**.
    *   Đơn vị dữ liệu: **Packet (gói tin)**. *"Người chỉ đường thông minh."*
*   **Tầng 2: Data Link (Liên kết dữ liệu):** Cung cấp phương tiện truyền dữ liệu **tin cậy** giữa hai thiết bị **kết nối trực tiếp** trong cùng một mạng cục bộ (LAN).
    *   **Định địa chỉ vật lý (MAC address)**.
    *   **Phát hiện lỗi** (nhưng thường không sửa lỗi).
    *   Điều khiển truy cập đường truyền (MAC - Media Access Control).
    *   Thiết bị chính: **Switch, Bridge**.
    *   Đơn vị dữ liệu: **Frame (khung tin)**. *"Người kiểm soát giao thông trên một đoạn đường."*
*   **Tầng 1: Physical (Vật lý):** Định nghĩa các đặc tính **vật lý và điện/quang** của việc truyền **bits** qua đường truyền.
    *   Loại cáp, đầu nối, mức điện áp, tốc độ truyền bit, kiểu mã hóa tín hiệu...
    *   Thiết bị chính: **Hub, Repeater, Card mạng (NIC), cáp mạng, sóng vô tuyến...**
    *   Đơn vị dữ liệu: **Bit**. *"Con đường và phương tiện vận chuyển tín hiệu."*

### 3. Mô Hình TCP/IP

Là mô hình được sử dụng thực tế trong mạng Internet. Có thể được mô tả với 4 hoặc 5 tầng, tùy tài liệu.

**Cách mô tả 4 tầng (phổ biến):**
Use code with caution.
+-------------------------+ <---- Tầng Application (OSI 5-7)
| Application |
+-------------------------+ <---- Tầng Transport (OSI 4)
| Transport |
+-------------------------+ <---- Tầng Internet (OSI 3)
| Internet (hoặc Network)|
+-------------------------+ <---- Tầng Network Access (OSI 1-2)
| Network Access |
| (hoặc Link) |
+-------------------------+
Mô hình TCP/IP (4 tầng)


*   **Tầng 7: Application (Ứng dụng):** Cung cấp giao diện cho người dùng và các ứng dụng truy cập vào mạng (HTTP, FTP, SMTP, DNS...). *"Cánh cửa" vào mạng.*
*   **Tầng 6: Presentation (Trình diễn):** Đảm bảo dữ liệu từ tầng Ứng dụng của máy gửi có thể được hiểu bởi tầng Ứng dụng của máy nhận. Chịu trách nhiệm **định dạng dữ liệu, mã hóa/giải mã, nén/giải nén.** *"Người phiên dịch" của mạng.*
*   **Tầng 5: Session (Phiên):** Thiết lập, quản lý và kết thúc các **phiên (session)** giao tiếp giữa hai máy. Đảm bảo dữ liệu của các ứng dụng khác nhau không bị lẫn lộn. *"Người quản lý cuộc hội thoại."*
*   **Tầng 4: Transport (Giao vận):** Cung cấp dịch vụ vận chuyển dữ liệu **đầu cuối (end-to-end)** giữa các **tiến trình (processes)** đang chạy trên hai máy. Có hai kiểu chính:
    *   **TCP (Transmission Control Protocol):** Hướng kết nối, đảm bảo tin cậy, kiểm soát luồng, kiểm soát tắc nghẽn.
    *   **UDP (User Datagram Protocol):** Không kết nối, không đảm bảo tin cậy, nhanh và đơn giản.
    *   Sử dụng **số hiệu cổng (port number)** để phân biệt các ứng dụng.
    *   Đơn vị dữ liệu: **Segment (TCP)** hoặc **Datagram (UDP)**. *"Người vận chuyển hàng hóa tin cậy hoặc siêu tốc."*
*   **Tầng 3: Network (Mạng):** Chịu trách nhiệm **định địa chỉ logic (IP address)** và **chọn đường (routing)** tốt nhất cho dữ liệu đi qua các mạng khác nhau để đến đích.
    *   Thiết bị chính: **Router**.
    *   Đơn vị dữ liệu: **Packet (gói tin)**. *"Người chỉ đường thông minh."*
*   **Tầng 2: Data Link (Liên kết dữ liệu):** Cung cấp phương tiện truyền dữ liệu **tin cậy** giữa hai thiết bị **kết nối trực tiếp** trong cùng một mạng cục bộ (LAN).
    *   **Định địa chỉ vật lý (MAC address)**.
    *   **Phát hiện lỗi** (nhưng thường không sửa lỗi).
    *   Điều khiển truy cập đường truyền (MAC - Media Access Control).
    *   Thiết bị chính: **Switch, Bridge**.
    *   Đơn vị dữ liệu: **Frame (khung tin)**. *"Người kiểm soát giao thông trên một đoạn đường."*
*   **Tầng 1: Physical (Vật lý):** Định nghĩa các đặc tính **vật lý và điện/quang** của việc truyền **bits** qua đường truyền.
    *   Loại cáp, đầu nối, mức điện áp, tốc độ truyền bit, kiểu mã hóa tín hiệu...
    *   Thiết bị chính: **Hub, Repeater, Card mạng (NIC), cáp mạng, sóng vô tuyến...**
    *   Đơn vị dữ liệu: **Bit**. *"Con đường và phương tiện vận chuyển tín hiệu."*

### 3. Mô Hình TCP/IP

Là mô hình được sử dụng thực tế trong mạng Internet. Có thể được mô tả với 4 hoặc 5 tầng, tùy tài liệu.

**Cách mô tả 4 tầng (phổ biến):**

+-------------------------+ <---- Tầng Application (OSI 5-7)
| Application |
+-------------------------+ <---- Tầng Transport (OSI 4)
| Transport |
+-------------------------+ <---- Tầng Internet (OSI 3)
| Internet (hoặc Network)|
+-------------------------+ <---- Tầng Network Access (OSI 1-2)
| Network Access |
| (hoặc Link) |
+-------------------------+
Mô hình TCP/IP (4 tầng)


*   **Tầng Application:** Gộp chức năng của 3 tầng trên cùng OSI (Application, Presentation, Session). Các giao thức như HTTP, SMTP, DNS hoạt động ở đây.
*   **Tầng Transport:** Tương đương tầng Transport của OSI. Chịu trách nhiệm vận chuyển đầu cuối với TCP và UDP.
*   **Tầng Internet (hoặc Network):** Tương đương tầng Network của OSI. Chịu trách nhiệm định địa chỉ IP và định tuyến (IP, ICMP, ARP - mặc dù ARP đôi khi xếp vào Link).
*   **Tầng Network Access (hoặc Link):** Gộp chức năng của 2 tầng dưới cùng OSI (Data Link, Physical). Bao gồm các công nghệ LAN/WAN như Ethernet, Wi-Fi, PPP...

**Cách mô tả 5 tầng (chi tiết hơn):** Tách tầng Network Access thành Data Link và Physical, giống OSI hơn.

### 4. So Sánh OSI và TCP/IP

| Đặc Điểm          | Mô Hình OSI                     | Mô Hình TCP/IP                 |
| :---------------- | :------------------------------ | :----------------------------- |
| **Số Tầng**       | 7                               | 4 (hoặc 5)                     |
| **Phát Triển**    | Lý thuyết, bởi ISO              | Thực tế, đi cùng Internet     |
| **Tính Phổ Biến** | Dùng làm chuẩn để tham chiếu   | Được sử dụng rộng rãi        |
| **Mức Độ Chi Tiết**| Rất chi tiết, phân tách rõ ràng | Gộp một số tầng của OSI       |
| **Giao Thức**     | Mô hình độc lập với giao thức   | Gắn liền với bộ giao thức TCP/IP |
| **Ưu Tiên**       | Xây dựng mô hình trước, rồi tới giao thức | Phát triển giao thức trước, mô hình theo sau |

**Điểm chung:** Cả hai đều là mô hình phân tầng, sử dụng kiến trúc lớp để đơn giản hóa thiết kế mạng. Các tầng dưới cung cấp dịch vụ cho tầng trên.

### 5. Quá Trình Đóng Gói (Encapsulation) và Mở Gói (Decapsulation)

Đây là quá trình **then chốt** để hiểu dữ liệu di chuyển qua các tầng như thế nào.

*   **Encapsulation (Phía máy gửi):**
    1.  Dữ liệu người dùng ở tầng **Application**.
    2.  Xuống **Transport**: Thêm TCP/UDP header (thông tin cổng...) -> **Segment/Datagram**.
    3.  Xuống **Network**: Thêm IP header (địa chỉ IP nguồn/đích...) -> **Packet**.
    4.  Xuống **Data Link**: Thêm MAC header & trailer (địa chỉ MAC nguồn/đích, kiểm tra lỗi...) -> **Frame**.
    5.  Xuống **Physical**: Chuyển Frame thành **Bits** để truyền đi.
    *   *Mỗi tầng thêm thông tin điều khiển của mình (header/trailer) vào dữ liệu nhận từ tầng trên.*

*   **Decapsulation (Phía máy nhận):** Quá trình ngược lại.
    1.  **Physical**: Nhận **Bits**, chuyển thành **Frame**.
    2.  Lên **Data Link**: Đọc và gỡ bỏ MAC header/trailer, kiểm tra lỗi. Đẩy Packet lên trên.
    3.  Lên **Network**: Đọc và gỡ bỏ IP header, kiểm tra IP đích. Đẩy Segment/Datagram lên trên.
    4.  Lên **Transport**: Đọc và gỡ bỏ TCP/UDP header, xác định ứng dụng đích qua cổng. Đẩy dữ liệu lên trên.
    5.  Lên **Application**: Dữ liệu gốc được trao cho ứng dụng phù hợp.
    *   *Mỗi tầng xử lý và loại bỏ thông tin điều khiển tương ứng trước khi chuyển dữ liệu lên tầng trên.*

## Tóm Tắt & Bài Học Tiếp Theo

Hiểu về mô hình OSI và TCP/IP cùng quá trình đóng/mở gói là cực kỳ quan trọng. Nó giống như hiểu được "bộ xương" và "luật lệ giao thông" của mạng máy tính vậy.

Trong bài học tiếp theo (`BaiHoc_03_TangVatLy.md`), chúng ta sẽ "zoom" vào tầng thấp nhất nhưng không kém phần quan trọng: **Tầng Vật Lý**. Chúng ta sẽ xem xét các loại cáp mạng, tín hiệu và cách bit được truyền đi thực sự. Hẹn gặp bạn ở thế giới của tín hiệu và dây dẫn! 💡🔌
