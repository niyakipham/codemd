# Bài Học 06: Các Thiết Bị Mạng Cơ Bản - Hub, Switch, Router: Bộ Ba Quyền Lực 💪🔌

## Mục Tiêu Bài Học

*   Phân biệt rõ ràng chức năng và cách hoạt động của Hub, Switch và Router.
*   Xác định Tầng (Layer) hoạt động chính của từng thiết bị trong mô hình OSI.
*   Hiểu các khái niệm **Collision Domain (Miền đụng độ)** và **Broadcast Domain (Miền quảng bá)**.
*   Nắm được cách Hub, Switch, Router xử lý lưu lượng dữ liệu (Frames và Packets).
*   Biết được ưu nhược điểm và vai trò của từng thiết bị trong thiết kế mạng.

## Nội Dung Chi Tiết

Trong các bài trước, chúng ta đã nhắc đến Hub, Switch, Router. Bây giờ là lúc "mổ xẻ" chúng thật kỹ lưỡng! Đây là những thành phần cốt lõi tạo nên mạng máy tính.

### 1. Hub (Bộ Tập Trung)

*   **Tầng hoạt động:** **Tầng 1 - Physical Layer (Vật lý)**.
*   **Chức năng:** Kết nối nhiều thiết bị trong cùng một mạng LAN vật lý theo mô hình hình sao (Star Topology).
*   **Cách hoạt động (Rất đơn giản):**
    *   Khi Hub nhận được tín hiệu điện (biểu diễn các bit) từ một cổng (port), nó **tái tạo (regenerate)** tín hiệu đó (khuếch đại) và **gửi ra tất cả các cổng còn lại**, trừ cổng gốc đã gửi tín hiệu vào.
    *   Hub **không đọc/hiểu** địa chỉ MAC hay địa chỉ IP. Nó chỉ đơn thuần là một thiết bị lặp tín hiệu đa cổng (multi-port repeater).
*   **Collision Domain (Miền đụng độ):**
    *   **Tất cả các cổng trên Hub thuộc về CÙNG MỘT Miền Đụng Độ.**
    *   Điều này có nghĩa là nếu hai thiết bị kết nối vào Hub cùng gửi dữ liệu một lúc, tín hiệu sẽ bị **đụng độ (collision)** và dữ liệu bị hỏng.
    *   Mạng phải sử dụng cơ chế **CSMA/CD** để xử lý đụng độ.
    *   Càng nhiều thiết bị nối vào Hub, khả năng xảy ra đụng độ càng cao, hiệu suất mạng càng giảm.
    *   Hub hoạt động ở chế độ **Half-duplex** (tại một thời điểm chỉ có thể gửi hoặc nhận, không thể làm cả hai).
*   **Broadcast Domain (Miền quảng bá):**
    *   Tất cả các cổng trên Hub cũng thuộc về **CÙNG MỘT Miền Quảng Bá.**
    *   Một bản tin broadcast (ví dụ: ARP Request có MAC đích là FF:FF:FF:FF:FF:FF) gửi vào một cổng sẽ được Hub đẩy ra tất cả các cổng khác.
*   **Ưu điểm:** Rẻ tiền (ngày xưa). Đơn giản.
*   **Nhược điểm:** Hiệu suất rất kém do miền đụng độ lớn, lãng phí băng thông, không thông minh, bảo mật kém.
*   **Hiện trạng:** **Rất hiếm khi được sử dụng** trong mạng hiện đại, đã hoàn toàn bị thay thế bởi Switch.

### 2. Switch (Bộ Chuyển Mạch)

*   **Tầng hoạt động:** **Tầng 2 - Data Link Layer (Liên kết dữ liệu)**. (Một số Switch cao cấp có thể có chức năng Layer 3).
*   **Chức năng:** Kết nối nhiều thiết bị trong cùng một mạng LAN, nhưng **thông minh hơn Hub rất nhiều**. Mục tiêu là chuyển Frame dữ liệu **chỉ đến cổng đích** cần thiết, thay vì gửi đi khắp nơi.
*   **Cách hoạt động:**
    1.  **Học địa chỉ MAC (Learning):** Switch xây dựng một bảng gọi là **MAC Address Table** (hay CAM Table). Khi một Frame đi vào một cổng, Switch sẽ đọc **địa chỉ MAC nguồn** của Frame đó và ghi nhớ: "Địa chỉ MAC nguồn này được tìm thấy ở cổng số X".
    2.  **Chuyển tiếp Frame (Forwarding/Filtering):** Khi Switch nhận một Frame:
        *   Nó đọc **địa chỉ MAC đích** trong Frame Header.
        *   Tra cứu địa chỉ MAC đích này trong bảng MAC Address Table.
        *   **Nếu tìm thấy:** Switch sẽ chỉ chuyển tiếp (forward) Frame đó ra **đúng cổng** tương ứng với MAC đích trong bảng. Các cổng khác sẽ không nhận được Frame này (Filtering).
        *   **Nếu không tìm thấy (MAC đích chưa có trong bảng) hoặc MAC đích là địa chỉ Broadcast (FF:FF..):** Switch sẽ **làm ngập (flood)** Frame đó ra tất cả các cổng khác, trừ cổng gốc nhận vào (Giống Hub trong trường hợp này).
*   **Collision Domain (Miền đụng độ):**
    *   **MỖI CỔNG trên Switch là MỘT Miền Đụng Độ RIÊNG BIỆT.**
    *   Điều này có nghĩa là nếu bạn cắm một thiết bị vào mỗi cổng Switch, **không bao giờ xảy ra đụng độ** giữa các cổng đó.
    *   Switch cho phép các cổng hoạt động ở chế độ **Full-duplex** (gửi và nhận dữ liệu đồng thời), giúp tăng gấp đôi băng thông hiệu dụng của kết nối (ví dụ: cổng 1Gbps có thể gửi 1Gbps và nhận 1Gbps cùng lúc).
    *   => Đây là cải tiến **vượt trội** so với Hub, mang lại hiệu suất mạng cao hơn hẳn.
*   **Broadcast Domain (Miền quảng bá):**
    *   **Mặc định, TẤT CẢ các cổng trên một Switch thuộc về CÙNG MỘT Miền Quảng Bá.**
    *   Giống như Hub, một bản tin broadcast gửi vào một cổng sẽ được Switch làm ngập (flood) ra tất cả các cổng khác.
    *   Broadcast quá nhiều có thể làm giảm hiệu suất mạng (Broadcast Storm). Có thể chia nhỏ miền quảng bá bằng cách sử dụng **VLAN (Virtual LAN)** - sẽ học ở bài sau.
*   **Ưu điểm:** Hiệu suất cao (do phân chia miền đụng độ, full-duplex), thông minh (chuyển mạch dựa trên MAC), tăng băng thông, bảo mật tốt hơn Hub.
*   **Nhược điểm:** Đắt hơn Hub (nhưng giờ giá rất phải chăng), không thể ngăn chặn broadcast storm (trừ khi dùng VLAN).
*   **Hiện trạng:** Là thiết bị **cực kỳ phổ biến** để xây dựng mạng LAN trong gia đình, văn phòng, doanh nghiệp.

### 3. Router (Bộ Định Tuyến)

*   **Tầng hoạt động:** **Tầng 3 - Network Layer (Mạng)**.
*   **Chức năng:**
    *   **Kết nối các mạng khác nhau** lại với nhau (ví dụ: kết nối mạng LAN nhà bạn với mạng Internet của nhà cung cấp dịch vụ - ISP).
    *   **Chọn đường đi (Routing):** Xác định đường đi tốt nhất để gửi các **gói tin (Packet)** từ mạng nguồn đến mạng đích dựa trên **địa chỉ IP đích**.
*   **Cách hoạt động:**
    1.  Router duy trì một **Bảng Định Tuyến (Routing Table)** chứa thông tin về các mạng mà nó biết và cách để đi đến các mạng đó (qua cổng nào, địa chỉ IP của router kế tiếp - next hop).
    2.  Khi Router nhận một Packet trên một cổng giao diện (interface):
        *   Nó đọc **địa chỉ IP đích** trong IP Header của Packet.
        *   Tra cứu địa chỉ IP đích này trong Bảng Định Tuyến để tìm **lối ra (outgoing interface)** và **next-hop router** (nếu cần) phù hợp nhất.
        *   **Trước khi gửi Packet đi:** Router sẽ **thay đổi địa chỉ MAC nguồn và đích** của Frame (Layer 2) bao bọc Packet đó.
            *   MAC nguồn mới: MAC của cổng giao diện Router sẽ gửi Packet ra.
            *   MAC đích mới: MAC của thiết bị kế tiếp (next-hop router hoặc máy đích cuối cùng nếu nằm cùng mạng với cổng ra của Router). Router sẽ dùng ARP để tìm MAC của next-hop nếu chưa biết.
        *   Router chuyển tiếp Packet ra cổng giao diện tương ứng.
        *   **Quan trọng:** Router **không** chuyển tiếp các bản tin broadcast của Layer 2 (ví dụ ARP Request có MAC đích FF:FF...) từ mạng này sang mạng khác.
*   **Collision Domain (Miền đụng độ):**
    *   **MỖI CỔNG trên Router là MỘT Miền Đụng Độ RIÊNG BIỆT** (Giống Switch). Router thường kết nối với Switch hoặc các thiết bị đầu cuối, nên nó cũng được hưởng lợi từ việc không có đụng độ trên từng cổng.
*   **Broadcast Domain (Miền quảng bá):**
    *   **MỖI CỔNG trên Router là MỘT Miền Quảng Bá RIÊNG BIỆT.**
    *   Đây là điểm khác biệt lớn nhất so với Switch! Router **chặn đứng** các bản tin broadcast. Broadcast từ mạng A sẽ không đi qua Router để sang mạng B.
    *   => Router giúp **phân chia các Miền Quảng Bá**, ngăn chặn broadcast storm và giới hạn phạm vi của các bản tin broadcast.
*   **Ưu điểm:** Kết nối các mạng khác nhau, chọn đường đi thông minh dựa trên IP, phân chia miền quảng bá, tăng cường bảo mật (có thể lọc traffic giữa các mạng).
*   **Nhược điểm:** Thường chậm hơn Switch (do phải xử lý ở Layer 3 phức tạp hơn), đắt hơn Switch.
*   **Hiện trạng:** Là thiết bị **thiết yếu** để kết nối Internet, liên kết các chi nhánh văn phòng, phân đoạn mạng lớn. Router Wi-Fi gia đình thực chất là thiết bị tích hợp nhiều chức năng: Router, Switch 4 cổng, Access Point Wi-Fi, Firewall...

### 4. Tóm Tắt So Sánh

| Đặc Điểm           | Hub                                    | Switch                                       | Router                                              |
| :----------------- | :------------------------------------- | :------------------------------------------- | :-------------------------------------------------- |
| **Tầng OSI**       | Layer 1 (Physical)                     | Layer 2 (Data Link)                          | Layer 3 (Network)                                   |
| **Đơn vị xử lý**   | Bits (Tín hiệu)                       | Frames (Dựa vào MAC Address)                 | Packets (Dựa vào IP Address)                        |
| **Chức năng chính**| Kết nối vật lý, lặp tín hiệu           | Kết nối thiết bị trong LAN, chuyển mạch Frame | Kết nối các mạng khác nhau, định tuyến Packet      |
| **Collision Domain**| 1 miền lớn cho tất cả cổng             | Mỗi cổng là 1 miền riêng                     | Mỗi cổng là 1 miền riêng                           |
| **Broadcast Domain**| 1 miền lớn cho tất cả cổng             | Mặc định 1 miền lớn (trừ khi dùng VLAN)      | Mỗi cổng là 1 miền riêng                           |
| **Bảng sử dụng**   | Không có                               | Bảng địa chỉ MAC (MAC Address Table)         | Bảng định tuyến (Routing Table)                      |
| **Tốc độ**         | Chậm (Half-duplex, chia sẻ băng thông) | Nhanh (Full-duplex, băng thông riêng)         | Chậm hơn Switch (xử lý phức tạp hơn)               |
| **Số lượng cổng**  | Thường ít (4-24)                       | Nhiều (4-48+)                               | Thường ít hơn Switch (2-5 cho router nhỏ, nhiều hơn cho router lớn) |
| **Sử dụng chính**  | Lỗi thời                               | Xây dựng mạng LAN                            | Kết nối các mạng LAN, kết nối Internet               |

## Tóm Tắt & Bài Học Tiếp Theo

Hub, Switch và Router là những "viên gạch" nền tảng xây dựng nên hệ thống mạng. Hub hoạt động ở Layer 1, tạo ra miền đụng độ và quảng bá lớn. Switch thông minh hơn ở Layer 2, chia nhỏ miền đụng độ và chuyển Frame dựa trên MAC. Router ở Layer 3 kết nối các mạng, định tuyến Packet dựa trên IP và quan trọng nhất là chia nhỏ các miền quảng bá.

Sau khi đã nắm vững các thiết bị cơ bản và cách chúng chuyển tiếp dữ liệu trong LAN (Switch) và giữa các mạng (Router), bài học tiếp theo (`BaiHoc_07_TangMang.md`) sẽ đưa chúng ta đi sâu vào **Tầng Mạng (Network Layer)**. Chúng ta sẽ khám phá chi tiết hơn về vai trò của tầng này, đặc biệt là về địa chỉ IP và quá trình định tuyến. Hẹn gặp bạn ở tầng cao hơn nhé! 🌐⬆️
