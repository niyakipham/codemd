# Bài Học 04: Tầng Liên Kết Dữ Liệu (Data Link Layer) - Giao Tiếp Hàng Xóm Láng Giềng 🏘️

## Mục Tiêu Bài Học

*   Hiểu rõ vai trò và chức năng của Tầng Liên Kết Dữ Liệu (Layer 2) trong mô hình OSI/TCP/IP.
*   Phân biệt hai tầng con: LLC (Logical Link Control) và MAC (Media Access Control).
*   Nắm được khái niệm về **địa chỉ MAC** (địa chỉ vật lý).
*   Hiểu cách Layer 2 đóng gói dữ liệu thành **Frame (khung tin)**.
*   Tìm hiểu về cơ chế **phát hiện lỗi** (Error Detection) cơ bản (ví dụ: CRC).
*   Biết về các phương pháp **điều khiển truy cập đường truyền** (Media Access Control).
*   Làm quen với các giao thức phổ biến ở Layer 2 (Ethernet, Wi-Fi, PPP).

## Nội Dung Chi Tiết

### 1. Vai Trò và Chức Năng

Sau khi Tầng Vật Lý (Layer 1) biến đổi dữ liệu thành các bit và truyền đi trên đường truyền, Tầng Liên Kết Dữ Liệu (Layer 2) đảm nhận nhiệm vụ quan trọng: **Cung cấp phương thức truyền dữ liệu tin cậy giữa hai thiết bị kết nối trực tiếp trong cùng một đoạn mạng (segment) hoặc mạng cục bộ (LAN).**

Nó giống như việc gửi thư trong cùng một khu phố: Bạn cần biết địa chỉ nhà (MAC) của người nhận trong khu phố đó và đảm bảo lá thư (frame) không bị rách nát khi đến nơi.

**Chức năng chính:**

*   **Framing (Đóng khung):** Nhận các gói tin (packets) từ Tầng Mạng (Layer 3), đóng gói chúng thành các **Frame (khung tin)** bằng cách thêm Header và Trailer. Header chứa địa chỉ nguồn và đích (MAC), còn Trailer thường chứa thông tin kiểm tra lỗi.
*   **Addressing (Địa chỉ vật lý):** Sử dụng **địa chỉ MAC (Media Access Control)** để xác định duy nhất thiết bị nguồn và thiết bị đích trong cùng một mạng LAN.
*   **Error Detection (Phát hiện lỗi):** Tính toán và thêm một giá trị kiểm tra lỗi (như CRC - Cyclic Redundancy Check) vào Trailer của Frame. Bên nhận sẽ tính toán lại và so sánh để phát hiện xem Frame có bị lỗi trong quá trình truyền hay không. (Lưu ý: Layer 2 thường chỉ *phát hiện* lỗi, việc *sửa lỗi* hoặc yêu cầu gửi lại thường do các tầng cao hơn đảm nhiệm).
*   **Flow Control (Điều khiển luồng - ít phổ biến hơn ở Layer 2 hiện đại):** Cơ chế để bên gửi không làm "ngập" dữ liệu cho bên nhận nếu bên nhận xử lý chậm.
*   **Media Access Control (Điều khiển truy cập đường truyền):** Rất quan trọng! Xác định **ai được phép gửi dữ liệu vào đường truyền tại một thời điểm**, đặc biệt khi môi trường truyền là dùng chung (shared media) như trong mạng không dây hoặc mạng Ethernet dùng Hub (cũ).

### 2. Hai Tầng Con: LLC và MAC

IEEE đã chia Layer 2 thành hai tầng con để rõ ràng hơn về chức năng:

*   **LLC (Logical Link Control) - Điều khiển liên kết logic (IEEE 802.2):**
    *   Nằm ở phía trên, giao tiếp với Tầng Mạng (Layer 3).
    *   Chức năng: Đóng gói dữ liệu từ Layer 3, xác định giao thức Layer 3 nào đang được sử dụng (ví dụ: IP, IPX - cũ). Có thể cung cấp dịch vụ kết nối (connection-oriented) hoặc không kết nối (connectionless). Trong mạng TCP/IP hiện đại, vai trò LLC không quá nổi bật vì TCP/UDP ở Layer 4 đã đảm nhiệm tốt việc kiểm soát luồng và độ tin cậy.
*   **MAC (Media Access Control) - Điều khiển truy cập đường truyền:**
    *   Nằm ở phía dưới, giao tiếp với Tầng Vật Lý (Layer 1).
    *   Chức năng chính:
        *   **Định địa chỉ MAC:** Gán địa chỉ vật lý duy nhất cho card mạng.
        *   **Framing:** Tạo cấu trúc Frame, thêm địa chỉ MAC nguồn/đích.
        *   **Điều khiển truy cập đường truyền:** Quyết định khi nào thiết bị được phép gửi Frame (sẽ nói kỹ ở mục 4).

### 3. Địa Chỉ MAC (Media Access Control Address)

*   Còn gọi là: **Địa chỉ vật lý (physical address), địa chỉ Ethernet, địa chỉ phần cứng (hardware address).**
*   Là một địa chỉ **duy nhất** được "ghi chết" (burned-in) vào card mạng (NIC) bởi nhà sản xuất.
*   Độ dài: **48 bit** (6 byte).
*   Biểu diễn: Thường viết dưới dạng 12 ký tự **thập lục phân (hexadecimal)**, chia thành 6 cặp, ngăn cách bởi dấu hai chấm (:) hoặc gạch ngang (-).
    *   Ví dụ: `00:1A:2B:3C:4D:5E` hoặc `00-1A-2B-3C-4D-5E`
*   Cấu trúc:
    *   **24 bit đầu (3 byte):** OUI (Organizationally Unique Identifier) - Mã định danh nhà sản xuất, do IEEE cấp.
    *   **24 bit sau (3 byte):** Mã định danh duy nhất cho card mạng đó, do nhà sản xuất tự quản lý.
*   **Phạm vi hoạt động:** Địa chỉ MAC chỉ có ý nghĩa trong **cùng một mạng LAN (broadcast domain)**. Khi gói tin đi qua Router để sang mạng khác, địa chỉ MAC nguồn/đích sẽ bị thay đổi.
*   **Địa chỉ MAC đặc biệt:**
    *   **Broadcast MAC:** `FF:FF:FF:FF:FF:FF` - Frame gửi đến địa chỉ này sẽ được tất cả thiết bị trong mạng LAN nhận.
    *   **Multicast MAC:** Bắt đầu bằng `01:00:5E...` (cho IPv4 multicast) hoặc `33:33...` (cho IPv6 multicast) - Frame gửi đến một nhóm thiết bị cụ thể đã đăng ký nhận.

### 4. Điều Khiển Truy Cập Đường Truyền (Media Access Control - MAC)

Giải quyết vấn đề: Khi nào một thiết bị có thể gửi dữ liệu lên môi trường truyền dùng chung để tránh **đụng độ (collision)** - tức là hai hoặc nhiều thiết bị gửi cùng lúc làm hỏng tín hiệu của nhau.

Có hai phương pháp chính:

*   **Phương pháp cạnh tranh (Contention-based):** Các thiết bị "tranh giành" quyền sử dụng đường truyền.
    *   **CSMA/CD (Carrier Sense Multiple Access with Collision Detection):** Dùng trong mạng **Ethernet có dây (dùng Hub hoặc cáp đồng trục)**.
        1.  **Carrier Sense (CS):** Nghe xem đường truyền có rảnh không. Nếu rảnh mới gửi.
        2.  **Multiple Access (MA):** Nhiều thiết bị cùng truy cập đường truyền.
        3.  **Collision Detection (CD):** Vừa gửi vừa nghe. Nếu phát hiện đụng độ (tín hiệu nhận được khác tín hiệu gửi đi), lập tức:
            *   Ngừng gửi.
            *   Gửi một tín hiệu Jam để báo cho các máy khác biết có đụng độ.
            *   Chờ một khoảng thời gian **ngẫu nhiên** (Backoff Algorithm) rồi thử gửi lại từ bước 1.
        *   Lưu ý: Mạng Ethernet hiện đại dùng **Switch** hoạt động ở chế độ **Full-duplex** (gửi và nhận đồng thời trên các đôi dây riêng) nên **không còn xảy ra đụng độ** và cơ chế CD thường bị tắt đi.
    *   **CSMA/CA (Carrier Sense Multiple Access with Collision Avoidance):** Dùng trong mạng **không dây (Wi-Fi - IEEE 802.11)**.
        1.  **Carrier Sense (CS):** Nghe kênh sóng xem có rảnh không (cả vật lý và ảo - NAV).
        2.  **Multiple Access (MA):** Nhiều thiết bị cùng truy cập.
        3.  **Collision Avoidance (CA):** **Cố gắng tránh đụng độ** thay vì phát hiện sau khi xảy ra (vì trong không dây, việc phát hiện đụng độ rất khó khăn do "hidden station problem" - trạm bị che khuất).
            *   Sử dụng cơ chế chờ một khoảng thời gian ngẫu nhiên (backoff) ngay cả khi kênh rảnh.
            *   Có thể dùng tín hiệu **RTS (Request to Send)** và **CTS (Clear to Send)** để "đặt chỗ" kênh truyền trước khi gửi dữ liệu lớn, giúp giảm thiểu đụng độ (đặc biệt hữu ích khi có hidden station).

*   **Phương pháp có kiểm soát (Controlled Access / Deterministic):** Mỗi thiết bị được cấp một lượt (turn) để gửi dữ liệu.
    *   **Token Passing:** Một "thẻ bài" (token) đặc biệt được lưu chuyển vòng quanh mạng (ví dụ: Token Ring, FDDI - đã lỗi thời). Chỉ thiết bị nào giữ token mới được phép gửi dữ liệu. Đảm bảo không có đụng độ, hiệu suất dự đoán được nhưng phức tạp và có độ trễ khi chờ token.

### 5. Giao Thức Layer 2 Phổ Biến

*   **Ethernet (IEEE 802.3):** Giao thức **thống trị** trong mạng LAN có dây. Có nhiều tốc độ khác nhau (10 Mbps, 100 Mbps - Fast Ethernet, 1 Gbps - Gigabit Ethernet, 10 Gbps, 40 Gbps, 100 Gbps và hơn nữa). Sử dụng địa chỉ MAC và cơ chế CSMA/CD (cho Half-duplex) hoặc không cần (cho Full-duplex).
*   **Wi-Fi (Wireless Fidelity - IEEE 802.11):** Tiêu chuẩn cho mạng LAN không dây (WLAN). Sử dụng địa chỉ MAC và cơ chế CSMA/CA. Có nhiều phiên bản (802.11a/b/g/n/ac/ax - Wi-Fi 6) với tốc độ và kỹ thuật khác nhau.
*   **PPP (Point-to-Point Protocol):** Dùng để thiết lập kết nối trực tiếp giữa hai điểm (nodes), thường qua đường truyền nối tiếp hoặc quay số (dial-up) - ít dùng cho LAN, phổ biến hơn cho kết nối WAN hoặc truy cập từ xa.
*   **HDLC (High-Level Data Link Control):** Giao thức cũ hơn PPP, dùng cho kết nối điểm-điểm hoặc điểm-đa điểm.
*   **Frame Relay & ATM (Asynchronous Transfer Mode):** Các công nghệ WAN Layer 2 cũ hơn (đã phần lớn bị thay thế bởi MPLS và Ethernet WAN).

## Tóm Tắt & Bài Học Tiếp Theo

Tầng Liên Kết Dữ Liệu (Layer 2) xây dựng cầu nối tin cậy giữa các thiết bị "hàng xóm" trong cùng mạng LAN. Nó định danh thiết bị bằng địa chỉ MAC, đóng gói dữ liệu thành Frame, kiểm tra lỗi cơ bản và quan trọng là điều phối quyền truy cập đường truyền dùng chung.

Trong bài học tới (`BaiHoc_05_DiaChiMAC_Va_ARP.md`), chúng ta sẽ đào sâu hơn vào **Địa chỉ MAC** và khám phá một giao thức cực kỳ quan trọng ở ranh giới Layer 2 và Layer 3 là **ARP (Address Resolution Protocol)** - Giao thức giúp tìm ra địa chỉ MAC khi biết địa chỉ IP. Hẹn gặp lại! 🤔💡
