# Bài Học 05: Địa Chỉ MAC và Giao Thức ARP - "Hỏi Tên, Xin Địa Chỉ Nhà" 🏠❓

## Mục Tiêu Bài Học

*   Ôn tập và hiểu sâu hơn về cấu trúc, ý nghĩa của địa chỉ MAC.
*   Phân biệt rõ ràng giữa địa chỉ MAC (Layer 2) và địa chỉ IP (Layer 3).
*   Hiểu rõ tại sao cần cả hai loại địa chỉ này.
*   Nắm vững nguyên lý hoạt động của **Giao thức Phân giải Địa chỉ ARP (Address Resolution Protocol)**.
*   Phân tích các loại bản tin ARP (ARP Request, ARP Reply).
*   Hiểu khái niệm **ARP Cache (bộ đệm ARP)** và cách xem nó trên máy tính.
*   Nhận biết một số vấn đề liên quan đến ARP (ví dụ: ARP Spoofing - giả mạo ARP).

## Nội Dung Chi Tiết

### 1. Ôn Tập Về Địa Chỉ MAC

Như đã học ở bài trước, địa chỉ MAC (Media Access Control) là:

*   Địa chỉ **vật lý**, **duy nhất** toàn cầu (về lý thuyết), được gán cứng cho card mạng (NIC).
*   Dài **48 bit** (6 byte), biểu diễn dạng Hexadecimal (VD: `0A:1B:2C:3D:4E:5F`).
*   Hoạt động ở **Tầng Liên Kết Dữ Liệu (Layer 2)**.
*   Chỉ có ý nghĩa và được sử dụng để giao tiếp **trong cùng một mạng LAN (broadcast domain)**. Khi dữ liệu đi qua Router sang mạng khác, địa chỉ MAC nguồn/đích trong Frame sẽ thay đổi.

### 2. Phân Biệt Địa Chỉ MAC và Địa Chỉ IP

Đây là điểm cực kỳ quan trọng và thường gây nhầm lẫn:

| Đặc Điểm         | Địa Chỉ MAC (Layer 2)                    | Địa Chỉ IP (Layer 3)                           | Ví Dụ Tương Đồng                     |
| :--------------- | :--------------------------------------- | :--------------------------------------------- | :----------------------------------- |
| **Tầng Hoạt Động**| Data Link (Liên kết dữ liệu)            | Network (Mạng)                                 |                                      |
| **Bản Chất**     | Vật lý, định danh thiết bị phần cứng (NIC)| Logic, định danh vị trí thiết bị trong mạng | Số Seri của máy tính **vs** Địa chỉ nhà |
| **Độ Dài**        | 48 bit (IPv4 & IPv6)                     | 32 bit (IPv4) hoặc 128 bit (IPv6)            |                                      |
| **Ai Gán**        | Nhà sản xuất NIC (thường cố định)       | Quản trị mạng / DHCP Server / ISP (thay đổi) | Nhà sản xuất **vs** Bưu điện/Chủ nhà |
| **Phạm Vi**       | Chỉ trong cùng một mạng LAN             | Toàn cục (có thể định tuyến qua Internet)       | Số Seri duy nhất **vs** Địa chỉ toàn cầu |
| **Thay Đổi**      | **Không đổi** khi thiết bị di chuyển     | **Thay đổi** khi di chuyển sang mạng khác       | Số Seri giữ nguyên **vs** Đổi địa chỉ nhà |
| **Mục Đích Chính** | Gửi Frame đến **chặng kế tiếp** (next hop) trong cùng LAN | Gửi Packet đến **đích cuối cùng** trên toàn mạng | Giao hàng trong khu phố **vs** Gửi thư liên tỉnh |

**Tại sao cần cả hai?**

Hãy tưởng tượng bạn muốn gửi thư cho bạn ở thành phố khác:

1.  **Địa chỉ IP (Giống địa chỉ nhà người nhận trên phong bì):** Giúp bưu điện (Router) biết thư cần đi đến thành phố nào, khu vực nào (định tuyến toàn cầu).
2.  **Địa chỉ MAC (Giống tên người đưa thư và số nhà cụ thể trong khu phố):** Khi thư đến bưu cục thành phố đích (Router cuối cùng kết nối vào LAN của người nhận), người đưa thư (Router) cần biết chính xác "cánh cửa" (NIC) của ngôi nhà (máy tính) để giao thư. Tương tự, khi bạn gửi thư đi, bạn đưa cho người đưa thư tại bưu cục gần nhà bạn (Default Gateway), cần biết MAC của Gateway đó.

=> IP dùng cho định tuyến **giữa các mạng**, MAC dùng cho chuyển giao **trong cùng một mạng**.

### 3. Vấn Đề Cần Giải Quyết: Biết IP, Làm Sao Tìm MAC?

Máy tính A (IP: 192.168.1.10) muốn gửi dữ liệu cho máy tính B (IP: 192.168.1.20) trong **cùng một mạng LAN**.

*   Máy A biết IP đích là `192.168.1.20`.
*   Để tạo được Ethernet Frame (Layer 2), máy A **cần biết địa chỉ MAC** của máy B để điền vào phần "MAC Đích" trong Frame Header.
*   Làm thế nào máy A tìm được MAC của máy B khi chỉ biết IP?

=> **ARP (Address Resolution Protocol)** ra đời để giải quyết chính vấn đề này!

### 4. Giao Thức Phân Giải Địa Chỉ ARP (Address Resolution Protocol)

*   **Chức năng:** Ánh xạ (map) một địa chỉ IP (Layer 3) sang một địa chỉ MAC (Layer 2) tương ứng **trong cùng một mạng LAN**.
*   **Hoạt động:** Khi một thiết bị (ví dụ: Máy A) cần gửi dữ liệu đến một địa chỉ IP (ví dụ: IP của Máy B) trong cùng mạng LAN nhưng chưa biết địa chỉ MAC tương ứng, nó sẽ thực hiện các bước sau:

    1.  **Kiểm tra ARP Cache:** Máy A đầu tiên kiểm tra **bộ đệm ARP (ARP Cache)** của mình xem đã có thông tin ánh xạ cho IP đích (192.168.1.20) chưa.
        *   Nếu có: Lấy địa chỉ MAC từ cache và tạo Frame gửi đi. (Kết thúc quá trình ARP).
        *   Nếu không có: Thực hiện bước 2.

    2.  **Gửi ARP Request (Yêu cầu ARP):** Máy A tạo một bản tin **ARP Request** và gửi nó ra mạng LAN.
        *   **Nội dung chính:** "Hỡi tất cả mọi người trong mạng LAN này! Ai có địa chỉ IP là `192.168.1.20` thì làm ơn cho tôi (Máy A - IP: `192.168.1.10`, MAC: `MAC_A`) biết địa chỉ MAC của bạn là gì?"
        *   **Đặc điểm ARP Request:**
            *   **Gửi dạng Broadcast:** Frame chứa ARP Request có **địa chỉ MAC đích là `FF:FF:FF:FF:FF:FF`**. Điều này đảm bảo tất cả các thiết bị trong mạng LAN đều nhận và xử lý bản tin này.
            *   Địa chỉ MAC nguồn: MAC của máy A (`MAC_A`).
            *   Địa chỉ IP nguồn: IP của máy A (`192.168.1.10`).
            *   Địa chỉ IP đích cần hỏi: IP của máy B (`192.168.1.20`).
            *   Địa chỉ MAC đích cần hỏi: Thường để là `00:00:00:00:00:00`.

    3.  **Xử lý ARP Request tại các máy khác:**
        *   Tất cả các máy trong LAN nhận được ARP Request.
        *   Mỗi máy kiểm tra xem địa chỉ IP đích trong Request có phải là của mình không.
        *   Nếu **không phải:** Hủy bỏ ARP Request.
        *   Nếu **đúng là IP của mình (Máy B):** Thực hiện bước 4. Đồng thời, máy B cũng học được ánh xạ IP-MAC của máy A (`192.168.1.10` -> `MAC_A`) và lưu vào ARP Cache của mình.

    4.  **Gửi ARP Reply (Phản hồi ARP):** Máy B tạo một bản tin **ARP Reply** và gửi **trực tiếp** lại cho Máy A.
        *   **Nội dung chính:** "Chào Máy A (MAC: `MAC_A`), tôi (Máy B - IP: `192.168.1.20`) có địa chỉ MAC là `MAC_B` đây."
        *   **Đặc điểm ARP Reply:**
            *   **Gửi dạng Unicast:** Frame chứa ARP Reply có **địa chỉ MAC đích là `MAC_A`** (địa chỉ MAC của máy A).
            *   Địa chỉ MAC nguồn: MAC của máy B (`MAC_B`).
            *   Địa chỉ IP nguồn: IP của máy B (`192.168.1.20`).
            *   Địa chỉ IP đích: IP của máy A (`192.168.1.10`).
            *   Địa chỉ MAC đích: MAC của máy A (`MAC_A`).

    5.  **Xử lý ARP Reply tại Máy A:**
        *   Máy A nhận được ARP Reply.
        *   Lưu thông tin ánh xạ IP-MAC của máy B (`192.168.1.20` -> `MAC_B`) vào **ARP Cache** của mình.
        *   Bây giờ máy A đã có đủ thông tin (MAC đích) để tạo Frame và gửi dữ liệu ban đầu đến máy B.

### 5. ARP Cache (Bộ Đệm ARP)

*   Là một bảng tạm thời lưu trữ các ánh xạ IP-MAC đã học được trên mỗi thiết bị mạng (máy tính, router, switch Layer 3).
*   Giúp giảm số lượng bản tin ARP Request broadcast trên mạng. Nếu thông tin đã có trong cache, thiết bị sẽ dùng luôn mà không cần hỏi lại.
*   Các mục trong ARP Cache có **thời gian tồn tại (timeout)** nhất định (thường vài phút). Sau thời gian này, nếu không được sử dụng/làm mới, mục đó sẽ bị xóa và thiết bị sẽ phải thực hiện lại quy trình ARP nếu cần.
*   **Cách xem ARP Cache:**
    *   **Windows:** Mở Command Prompt, gõ lệnh `arp -a`
    *   **Linux/macOS:** Mở Terminal, gõ lệnh `arp -n` hoặc `ip neigh`

### 6. Vấn Đề Liên Quan: ARP Spoofing (Giả Mạo ARP)

*   Do ARP hoạt động dựa trên sự tin tưởng và không có cơ chế xác thực mạnh mẽ, kẻ tấn công (Attacker) có thể lợi dụng điều này.
*   **ARP Spoofing (hay ARP Poisoning):** Kẻ tấn công gửi các bản tin ARP Reply giả mạo đến các máy tính trong mạng LAN (ví dụ: Máy A và Default Gateway).
    *   Gửi ARP Reply giả cho Máy A: "Tôi (Attacker) là Default Gateway (IP_GW), MAC của tôi là MAC_Attacker".
    *   Gửi ARP Reply giả cho Default Gateway: "Tôi (Attacker) là Máy A (IP_A), MAC của tôi là MAC_Attacker".
*   **Hậu quả:**
    *   Lưu lượng truy cập từ Máy A ra Internet sẽ đi qua máy của Attacker thay vì Gateway thật.
    *   Lưu lượng từ Internet về Máy A cũng đi qua máy của Attacker.
    *   Attacker có thể **nghe lén (sniffing)**, **sửa đổi (modification)** hoặc **chặn (denial of service)** dữ liệu. Đây là kỹ thuật phổ biến trong tấn công **Man-in-the-Middle (MitM)**.
*   **Phòng chống:** Sử dụng các kỹ thuật như Dynamic ARP Inspection (DAI) trên Switch, các phần mềm phát hiện ARP Spoofing.

## Tóm Tắt & Bài Học Tiếp Theo

Chúng ta đã hiểu rõ sự khác biệt và mối liên hệ mật thiết giữa địa chỉ IP (Layer 3) và địa chỉ MAC (Layer 2). Giao thức ARP chính là "chất keo" kết dính hai thế giới này trong phạm vi mạng LAN, giúp các thiết bị tìm thấy nhau ở tầng vật lý khi biết địa chỉ logic. Nhớ rằng, ARP chỉ hoạt động trong cùng một mạng LAN!

Bài học tiếp theo (`BaiHoc_06_ThietBiMangCoBan.md`) sẽ tập trung vào các "nhân vật" phần cứng quen thuộc: **Hub, Switch, Router**. Chúng ta sẽ phân tích chi tiết cách chúng hoạt động, vai trò của từng thiết bị trong việc xây dựng mạng lưới và chúng thuộc về những tầng nào trong mô hình OSI. Đừng bỏ lỡ nhé! ⚙️🔧
