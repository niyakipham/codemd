# Bài Học 03: Tầng Vật Lý (Physical Layer) - Nền Móng Của Kết Nối 🧱⚡

## Mục Tiêu Bài Học

*   Hiểu rõ vai trò và chức năng của Tầng Vật Lý trong mô hình OSI/TCP/IP.
*   Phân biệt các loại môi trường truyền dẫn phổ biến (cáp đồng, cáp quang, không dây).
*   Nắm được các khái niệm cơ bản: Tín hiệu Analog/Digital, Bit Rate, Bandwidth, Latency, Throughput.
*   Tìm hiểu về các kiểu mã hóa đường truyền (Line Coding) cơ bản.
*   Biết về các thiết bị hoạt động chủ yếu ở Tầng Vật Lý.

## Nội Dung Chi Tiết

### 1. Vai Trò và Chức Năng

Tầng Vật Lý (Layer 1) là tầng thấp nhất, làm việc trực tiếp với **tín hiệu (signals)** và **môi trường truyền dẫn (transmission media)**. Nó không quan tâm đến ý nghĩa của dữ liệu (là hình ảnh hay văn bản), mà chỉ tập trung vào việc **truyền các bit (0 và 1)** từ điểm A đến điểm B một cách vật lý.

**Chức năng chính:**

*   **Định nghĩa đặc tính cơ/điện/quang:** Quy định về loại đầu nối (connector), số chân (pinout), kích thước cáp, mức điện áp/cường độ ánh sáng biểu diễn bit 0 và 1.
*   **Mã hóa tín hiệu (Encoding):** Chuyển đổi chuỗi bit (010110...) thành tín hiệu vật lý phù hợp với môi trường truyền (ví dụ: các mức điện áp khác nhau, bật/tắt ánh sáng).
*   **Tốc độ truyền bit (Bit Rate):** Xác định số lượng bit có thể truyền qua môi trường trong một giây (đơn vị: bps, Kbps, Mbps, Gbps...).
*   **Đồng bộ hóa bit (Bit Synchronization):** Đảm bảo bên nhận biết khi nào một bit bắt đầu và kết thúc để đọc chính xác.
*   **Loại môi trường truyền dẫn:** Xác định các đặc tính của cáp đồng, cáp quang hay sóng vô tuyến.
*   **Cấu trúc liên kết vật lý (Physical Topology):** Cách các thiết bị được kết nối vật lý (Bus, Star, Ring, Mesh - sẽ nói kỹ hơn ở bài khác).

### 2. Môi Trường Truyền Dẫn (Transmission Media)

Là con đường vật lý mà tín hiệu đi qua. Có hai loại chính:

*   **Có dây (Guided Media):** Tín hiệu được dẫn theo một đường dẫn vật lý xác định.
    *   **Cáp Xoắn Đôi (Twisted Pair Cable):**
        *   Cấu tạo: Gồm nhiều cặp dây đồng nhỏ xoắn lại với nhau để giảm nhiễu điện từ (EMI) và nhiễu xuyên âm (crosstalk).
        *   Phân loại:
            *   **UTP (Unshielded Twisted Pair):** Không có vỏ bọc chống nhiễu, phổ biến nhất cho mạng LAN (Ethernet), giá rẻ, dễ lắp đặt. Các loại phổ biến: Cat 5e, Cat 6, Cat 6a, Cat 7 (khác nhau về tốc độ và khả năng chống nhiễu).
            *   **STP (Shielded Twisted Pair):** Có lớp vỏ bọc kim loại chống nhiễu tốt hơn UTP, đắt hơn, khó lắp đặt hơn. Dùng trong môi trường nhiễu cao.
        *   Đầu nối: **RJ45**.
    *   **Cáp Đồng Trục (Coaxial Cable):**
        *   Cấu tạo: Lõi đồng ở giữa, lớp cách điện, lớp lưới kim loại chống nhiễu, vỏ nhựa bên ngoài.
        *   Đặc điểm: Chống nhiễu tốt hơn UTP, băng thông lớn hơn (từng dùng cho Ethernet đời đầu, giờ chủ yếu cho truyền hình cáp và Internet cáp quang đến nhà - đoạn cuối).
        *   Đầu nối: BNC, F-type.
    *   **Cáp Quang (Fiber Optic Cable):**
        *   Cấu tạo: Sử dụng các **sợi thủy tinh hoặc nhựa** trong suốt để truyền **tín hiệu ánh sáng**. Gồm lõi (core), lớp phản xạ (cladding), vỏ bảo vệ (buffer), lớp gia cường, vỏ ngoài.
        *   Đặc điểm:
            *   **Băng thông cực lớn.**
            *   **Truyền xa** (hàng chục, hàng trăm km mà không cần bộ khuếch đại).
            *   **Miễn nhiễm hoàn toàn với nhiễu điện từ (EMI).**
            *   **Bảo mật cao hơn** (khó trích tín hiệu).
            *   Đắt tiền và khó lắp đặt/sửa chữa hơn cáp đồng.
        *   Phân loại:
            *   **Single-mode Fiber (SMF):** Lõi rất nhỏ, dùng tia laser, truyền xa, băng thông lớn. Dùng cho đường trục WAN, MAN.
            *   **Multi-mode Fiber (MMF):** Lõi lớn hơn, dùng LED hoặc laser rẻ tiền hơn, khoảng cách ngắn hơn (trong tòa nhà, trung tâm dữ liệu), băng thông thấp hơn SMF nhưng vẫn rất cao so với cáp đồng.
        *   Đầu nối: SC, ST, LC, MTP/MPO...

*   **Không dây (Unguided Media):** Tín hiệu lan truyền trong không gian mở.
    *   **Sóng Radio:** Dùng cho phát thanh AM/FM, mạng di động (cellular), Wi-Fi, Bluetooth, mạng không dây tầm xa. Bị ảnh hưởng bởi vật cản.
    *   **Vi sóng (Microwave):** Truyền thẳng (line-of-sight). Dùng cho kết nối điểm-điểm giữa các tòa nhà, trạm thu phát sóng, vệ tinh.
    *   **Hồng ngoại (Infrared):** Tầm rất ngắn, không xuyên tường. Dùng cho điều khiển từ xa (TV remote), một số kết nối máy tính cũ.

### 3. Các Khái Niệm Cơ Bản

*   **Tín hiệu Analog vs Digital:**
    *   **Analog:** Tín hiệu liên tục, thay đổi mượt mà theo thời gian (giống giọng nói, sóng radio). Dễ bị nhiễu và suy hao.
    *   **Digital:** Tín hiệu rời rạc, chỉ có một số hữu hạn các mức giá trị (thường là 2 mức biểu diễn 0 và 1). Ít bị nhiễu hơn, dễ tái tạo. Máy tính xử lý tín hiệu digital.
*   **Bit Rate (Tốc độ bit):** Số bit truyền/giây (bps). Ví dụ: Mạng Ethernet 1 Gbps = 1 tỷ bit/giây.
*   **Bandwidth (Băng thông):**
    *   Trong tín hiệu analog: Phạm vi tần số mà môi trường truyền dẫn có thể hỗ trợ (Hz).
    *   Trong tín hiệu digital (thường dùng hơn): **Tốc độ truyền dữ liệu tối đa** theo lý thuyết của kênh truyền (cùng đơn vị với Bit Rate).
*   **Throughput (Thông lượng):** Tốc độ truyền dữ liệu **thực tế** đo được qua một kênh truyền. Luôn nhỏ hơn hoặc bằng Bandwidth do các yếu tố như: độ trễ, lỗi, giao thức, tắc nghẽn...
*   **Latency (Độ trễ):** Thời gian để một bit dữ liệu di chuyển từ nguồn đến đích. Bao gồm:
    *   **Propagation delay:** Thời gian tín hiệu lan truyền qua môi trường.
    *   **Transmission delay:** Thời gian để đẩy hết các bit của một gói tin vào đường truyền (Kích thước gói tin / Bandwidth).
    *   **Queuing delay:** Thời gian chờ đợi trong hàng đợi tại các router, switch.
    *   **Processing delay:** Thời gian xử lý gói tin tại router, switch.
*   **Jitter (Độ biến động trễ):** Sự thay đổi về độ trễ của các gói tin liên tiếp. Ảnh hưởng lớn đến ứng dụng thời gian thực như thoại VoIP, video conference.

### 4. Mã Hóa Đường Truyền (Line Coding)

Là cách biểu diễn chuỗi bit (0, 1) thành tín hiệu điện áp hoặc ánh sáng trên đường truyền. Mục tiêu:

*   Truyền hiệu quả.
*   Đảm bảo đồng bộ hóa (bên nhận biết đâu là bit).
*   Phát hiện lỗi cơ bản.
*   Giảm thành phần dòng một chiều (DC component).

Một số kiểu phổ biến:

*   **NRZ (Non-Return-to-Zero):**
    *   NRZ-L (Level): Mức điện áp cao là 1, thấp là 0 (hoặc ngược lại). Đơn giản nhưng khó đồng bộ nếu có chuỗi dài 0 hoặc 1.
    *   NRZ-I (Invert): Chuyển trạng thái (đổi mức điện áp) khi gặp bit 1, giữ nguyên khi gặp bit 0. Tốt hơn cho đồng bộ.
*   **RZ (Return-to-Zero):** Tín hiệu luôn trở về 0 ở giữa mỗi bit. Dễ đồng bộ nhưng tốn băng thông gấp đôi NRZ.
*   **Manchester:** Chuyển trạng thái ở giữa mỗi bit. Chuyển từ cao xuống thấp là 0, từ thấp lên cao là 1 (hoặc ngược lại). Dùng trong Ethernet đời đầu (10 Mbps). Đảm bảo đồng bộ tốt, tự chứa xung clock. Tốn băng thông gấp đôi NRZ.
*   **Differential Manchester:** Luôn có chuyển trạng thái ở giữa bit. Bit 0 có thêm chuyển trạng thái ở đầu bit, bit 1 thì không. Dùng trong Token Ring.
*   **Các mã phức tạp hơn:** 4B/5B, 8B/10B, MLT-3... dùng trong Fast Ethernet, Gigabit Ethernet để tăng hiệu quả băng thông và đảm bảo đồng bộ.

### 5. Thiết Bị Tầng Vật Lý

Các thiết bị này chủ yếu xử lý tín hiệu điện/quang, không hiểu về địa chỉ MAC hay IP.

*   **Hub (Bộ tập trung):**
    *   Kết nối nhiều thiết bị trong mạng LAN (kiểu hình sao - Star).
    *   Khi nhận tín hiệu từ một cổng, nó **khuếch đại và gửi ra tất cả các cổng khác**.
    *   Tạo ra một **miền đụng độ (collision domain)** lớn -> hiệu suất kém khi có nhiều thiết bị.
    *   Ngày nay rất ít được sử dụng, đã bị thay thế bởi Switch.
*   **Repeater (Bộ lặp):**
    *   Nhận tín hiệu yếu hoặc bị suy hao, **khuếch đại và gửi đi** để mở rộng khoảng cách mạng.
    *   Không thay đổi nội dung tín hiệu. Hoạt động trên cáp đồng và cáp quang.
*   **Card Mạng (NIC - Network Interface Card):**
    *   Là phần cứng cắm vào máy tính/thiết bị để kết nối vào mạng.
    *   Chịu trách nhiệm gửi và nhận tín hiệu trên đường truyền vật lý. Nó cũng có chức năng của Tầng 2 (Data Link).
*   **Transceiver (Bộ thu phát):** Thiết bị chuyển đổi tín hiệu giữa các loại môi trường khác nhau (ví dụ: từ điện sang quang) hoặc chuẩn bị tín hiệu để truyền đi (ví dụ: SFP, QSFP trong switch/router).
*   **Media Converter (Bộ chuyển đổi quang điện):** Chuyển đổi tín hiệu giữa cáp đồng (RJ45) và cáp quang.

## Tóm Tắt & Bài Học Tiếp Theo

Tầng Vật Lý là nền tảng, định nghĩa cách bit được biến thành tín hiệu và truyền qua các môi trường vật lý như cáp đồng, cáp quang hay không khí. Hiểu về môi trường truyền, các đặc tính tín hiệu và thiết bị liên quan là bước đầu tiên để xây dựng và khắc phục sự cố mạng.

Trong bài học kế tiếp (`BaiHoc_04_TangLienKetDuLieu.md`), chúng ta sẽ di chuyển lên **Tầng Liên Kết Dữ Liệu (Data Link Layer)**. Tầng này sẽ bổ sung cấu trúc cho luồng bit, xử lý lỗi cơ bản và quan trọng nhất là định danh các thiết bị trong cùng một mạng cục bộ thông qua địa chỉ MAC. Cùng khám phá cách các thiết bị "nói chuyện" trực tiếp với nhau nhé! 🤝
