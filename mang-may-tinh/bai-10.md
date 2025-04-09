# Bài Học 10: Định Tuyến (Routing) - Trái Tim Của Kết Nối Liên Mạng ❤️🌐

## Mục Tiêu Bài Học

*   Ôn tập và hiểu sâu hơn về quá trình định tuyến (Routing) tại Tầng Mạng.
*   Phân biệt rõ ràng giữa **Routing (Định tuyến - Control Plane)** và **Forwarding (Chuyển tiếp - Data Plane)**.
*   Hiểu cách Router sử dụng **Bảng Định Tuyến (Routing Table)** để đưa ra quyết định chuyển tiếp Packet.
*   Nắm vững các loại thông tin chính trong một mục nhập của bảng định tuyến (Route Entry).
*   Tìm hiểu về các **phương pháp xây dựng bảng định tuyến**: Static Routing (Định tuyến tĩnh) và Dynamic Routing (Định tuyến động).
*   Hiểu khái niệm **Metric (Thông số đo lường)** và vai trò của nó trong việc chọn đường đi tốt nhất.
*   Biết về quy tắc **Longest Prefix Match (Khớp tiền tố dài nhất)** khi tra cứu bảng định tuyến.
*   Tìm hiểu về khái niệm **Default Route (Đường đi mặc định)**.

## Nội Dung Chi Tiết

### 1. Ôn Tập: Routing vs. Forwarding

Như đã đề cập ở bài về Tầng Mạng, quá trình hoạt động của Router có thể chia thành hai mặt phẳng chức năng chính:

*   **Routing (Định tuyến - Control Plane):** Là quá trình **xây dựng và duy trì Bảng Định Tuyến**. Router sử dụng các thông tin cấu hình tĩnh hoặc trao đổi thông tin với các Router khác thông qua các **Giao thức định tuyến động (Dynamic Routing Protocols)** để "học" về cấu trúc mạng và tính toán ra đường đi tốt nhất đến các mạng đích khác nhau. Đây là quá trình xử lý thông tin, đưa ra quyết định "trên bản đồ".
*   **Forwarding (Chuyển tiếp - Data Plane):** Là hành động **di chuyển Packet thực tế** từ một cổng vào (Ingress Interface) đến một cổng ra (Egress Interface) dựa trên thông tin đã có sẵn trong Bảng Định Tuyến (và bảng Forwarding Information Base - FIB, thường được tối ưu từ Routing Table). Đây là quá trình xử lý dữ liệu tốc độ cao, giống như việc "lái xe" theo chỉ dẫn đã có.

**Tóm lại:** Routing là tìm đường, Forwarding là đi theo đường đã tìm. Bài này tập trung vào khía cạnh Routing - làm thế nào Router biết được đường đi.

### 2. Bảng Định Tuyến (Routing Table) - Bản Đồ Của Router

Mỗi Router duy trì một Bảng Định Tuyến, chứa thông tin về các đường đi đến các mạng đích khác nhau mà nó biết. Đây là cơ sở để Router đưa ra quyết định Forwarding.

**Các thông tin chính trong một mục nhập (Route Entry) của bảng định tuyến thường bao gồm:**

*   **Destination Network Prefix (Tiền tố mạng đích):** Địa chỉ mạng đích mà đường đi này áp dụng (ví dụ: `10.1.1.0`).
*   **Prefix Length / Subnet Mask (Độ dài tiền tố / Mặt nạ mạng con):** Chỉ định phần Network ID của địa chỉ đích (ví dụ: `/24` hoặc `255.255.255.0`). Router sẽ dùng thông tin này kết hợp với IP đích của Packet để tìm mục nhập phù hợp.
*   **Next Hop IP Address (Địa chỉ IP của chặng kế tiếp):** Địa chỉ IP của Router tiếp theo trên đường đi đến mạng đích. Nếu mạng đích được kết nối trực tiếp với Router này, thông tin Next Hop có thể không cần thiết hoặc chỉ ra chính cổng giao diện của Router.
*   **Outgoing Interface (Cổng giao diện ra):** Cổng vật lý hoặc logic mà Router sẽ đẩy Packet ra để đi đến Next Hop hoặc mạng đích.
*   **Metric (Thông số đo lường):** Một giá trị số thể hiện "độ tốt" hoặc "chi phí" của đường đi này. Các giao thức định tuyến khác nhau sử dụng các metric khác nhau (sẽ nói rõ hơn ở mục 5). Router thường ưu tiên đường đi có Metric thấp nhất.
*   **Route Source / Protocol (Nguồn gốc đường đi / Giao thức):** Cho biết đường đi này được học từ đâu:
    *   `C` hoặc `Connected`: Mạng kết nối trực tiếp với Router.
    *   `S` hoặc `Static`: Đường đi được cấu hình thủ công (Static Route).
    *   `R`, `O`, `E`, `B`, `i`, ...: Ký hiệu cho các Giao thức định tuyến động (RIP, OSPF, EIGRP, BGP...).
*   **Administrative Distance (AD - Khoảng cách quản trị):** Một con số (từ 0 đến 255) thể hiện **độ tin cậy** của nguồn gốc đường đi. Khi có nhiều đường đi đến cùng một mạng đích được học từ các nguồn khác nhau (ví dụ: một Static Route và một OSPF Route), Router sẽ **ưu tiên đường đi có AD thấp hơn**.
    *   Connected: 0 (Tin cậy nhất)
    *   Static: 1
    *   eBGP: 20
    *   EIGRP (Internal): 90
    *   OSPF: 110
    *   RIP: 120
    *   iBGP: 200
    *   *(Giá trị AD có thể thay đổi tùy hãng thiết bị và cấu hình)*

**Cách xem bảng định tuyến:**
*   **Cisco IOS:** `show ip route`
*   **Juniper JunOS:** `show route`
*   **Windows:** `route print` hoặc `Get-NetRoute` (PowerShell)
*   **Linux:** `ip route show` hoặc `netstat -r`

### 3. Phương Pháp Xây Dựng Bảng Định Tuyến

Có hai cách chính để Router "học" các đường đi và đưa vào Bảng Định Tuyến:

*   **Static Routing (Định tuyến tĩnh):**
    *   **Cách hoạt động:** Quản trị viên mạng **cấu hình thủ công** từng đường đi (route) vào Bảng Định Tuyến của Router. Họ phải chỉ rõ mạng đích, subnet mask, next hop IP và/hoặc cổng ra.
    *   **Ưu điểm:**
        *   Đơn giản cho các mạng nhỏ, cấu trúc không thay đổi.
        *   Không tốn tài nguyên CPU/RAM của Router để chạy giao thức định tuyến.
        *   An toàn hơn (không trao đổi thông tin định tuyến với bên ngoài).
        *   Quản trị viên có toàn quyền kiểm soát đường đi.
    *   **Nhược điểm:**
        *   **Không linh hoạt:** Khi cấu trúc mạng thay đổi (thêm mạng mới, hỏng đường link), quản trị viên phải **cập nhật thủ công** trên tất cả các Router liên quan. Rất tốn công và dễ gây lỗi cho mạng lớn.
        *   **Không có khả năng tự động chọn đường đi dự phòng** khi đường chính bị lỗi (trừ khi cấu hình thêm "floating static route" với AD cao hơn).
    *   **Ứng dụng:** Thường dùng ở các mạng biên (stub network) chỉ có một đường ra ngoài, cấu hình Default Route, hoặc trong các tình huống cần kiểm soát đường đi chặt chẽ.

*   **Dynamic Routing (Định tuyến động):**
    *   **Cách hoạt động:** Các Router sử dụng các **Giao thức định tuyến động (Dynamic Routing Protocols)** để **tự động trao đổi thông tin** về các mạng mà chúng kết nối tới với các Router láng giềng. Dựa trên thông tin nhận được, mỗi Router sẽ tự tính toán đường đi tốt nhất đến các mạng đích và cập nhật vào Bảng Định Tuyến.
    *   **Ưu điểm:**
        *   **Tự động thích ứng:** Tự động khám phá mạng mới và cập nhật bảng định tuyến khi cấu trúc mạng thay đổi.
        *   **Tự động chọn đường đi dự phòng:** Khi đường đi tốt nhất bị lỗi, giao thức định tuyến có thể tự động tính toán và chuyển sang sử dụng đường đi dự phòng (nếu có).
        *   **Khả năng mở rộng:** Dễ dàng quản lý các mạng lớn và phức tạp hơn so với định tuyến tĩnh.
    *   **Nhược điểm:**
        *   **Tốn tài nguyên:** Cần CPU, RAM và băng thông mạng để chạy giao thức định tuyến và trao đổi thông tin cập nhật.
        *   **Phức tạp hơn:** Cần hiểu biết về các giao thức định tuyến để cấu hình và xử lý sự cố.
        *   **Vấn đề bảo mật:** Cần cấu hình các biện pháp bảo mật (như authentication) để tránh thông tin định tuyến giả mạo.
    *   **Ứng dụng:** Phổ biến trong hầu hết các mạng doanh nghiệp và nhà cung cấp dịch vụ để đảm bảo tính linh hoạt và khả năng phục hồi. (Các giao thức cụ thể như RIP, OSPF, BGP... sẽ học ở bài sau).

### 4. Metric - Thước Đo Chọn Đường

Khi một giao thức định tuyến động tìm thấy **nhiều đường đi** đến cùng một mạng đích, nó cần một cách để quyết định đường nào là **tốt nhất**. Đó là lúc **Metric** phát huy tác dụng.

*   Metric là một giá trị số được gán cho mỗi đường đi. **Đường đi có Metric thấp hơn thường được coi là tốt hơn.**
*   Các giao thức định tuyến khác nhau sử dụng các Metric khác nhau:
    *   **RIP (Routing Information Protocol):** Sử dụng **Hop Count (Số lượng Router phải đi qua)**. Metric tối đa là 15 hops (16 coi như không tới được). Đơn giản nhưng không tối ưu (không xét đến băng thông, độ trễ).
    *   **OSPF (Open Shortest Path First):** Sử dụng **Cost (Chi phí)**, thường được tính **nghịch đảo với Băng thông (Bandwidth)** của đường link (Link nhanh hơn có Cost thấp hơn). Linh hoạt và chính xác hơn RIP.
    *   **EIGRP (Enhanced Interior Gateway Routing Protocol - Cisco):** Sử dụng một **Metric phức hợp** dựa trên **Bandwidth, Delay (Độ trễ)**, và tùy chọn có thể thêm Load (Tải) và Reliability (Độ tin cậy). Rất linh hoạt nhưng phức tạp.
    *   **BGP (Border Gateway Protocol):** Không dùng Metric đơn giản mà sử dụng một **quy trình chọn đường phức tạp** dựa trên nhiều **thuộc tính (Attributes)** như AS-Path, Local Preference, MED...

### 5. Longest Prefix Match - Quy Tắc Vàng Khi Tra Cứu

Khi một Router nhận Packet và cần tìm đường đi trong Bảng Định Tuyến, có thể có nhiều mục nhập (route entry) cùng "khớp" với địa chỉ IP đích của Packet ở các mức độ khác nhau. Ví dụ, Bảng Định Tuyến có thể chứa:
*   `10.1.0.0 /16`
*   `10.1.1.0 /24`
*   `10.1.1.128 /25`

Nếu Packet có IP đích là `10.1.1.130`, thì cả ba mục nhập trên đều "khớp". Router sẽ chọn đường đi nào?

**Quy tắc:** Router luôn chọn mục nhập có **tiền tố (prefix) khớp với địa chỉ IP đích dài nhất (Most Specific Match)**.

*   `10.1.0.0 /16`: Khớp 16 bit đầu.
*   `10.1.1.0 /24`: Khớp 24 bit đầu.
*   `10.1.1.128 /25`: Khớp 25 bit đầu.

Trong trường hợp này, `/25` là khớp dài nhất. Do đó, Router sẽ sử dụng đường đi tương ứng với `10.1.1.128 /25` để chuyển tiếp Packet. Quy tắc này đảm bảo Packet được gửi đến mạng đích cụ thể nhất có thể.

### 6. Default Route (Đường Đi Mặc Định) - Lối Thoát Cuối Cùng

*   **Khái niệm:** Là một loại Static Route đặc biệt chỉ định đường đi cho tất cả các Packet có địa chỉ IP đích **không khớp với bất kỳ mục nhập nào khác** trong Bảng Định Tuyến.
*   **Biểu diễn:** Thường có địa chỉ mạng đích và subnet mask là `0.0.0.0 /0` (hoặc `0.0.0.0 0.0.0.0`).
*   **Vai trò:** Cực kỳ quan trọng, đặc biệt cho các Router biên kết nối ra Internet. Khi Router nhận Packet đi đến một địa chỉ IP nào đó trên Internet mà nó không có đường đi cụ thể trong bảng, nó sẽ sử dụng Default Route (thường trỏ đến Router của ISP) để đẩy Packet ra ngoài. Nó giống như biển chỉ dẫn "Tất cả các hướng khác" hoặc "Lối ra Internet".
*   Còn được gọi là "Gateway of Last Resort".

## Tóm Tắt & Bài Học Tiếp Theo

Định tuyến là quá trình cốt lõi giúp kết nối các mạng. Router sử dụng Bảng Định Tuyến (xây dựng bằng Static hoặc Dynamic Routing) để quyết định đường đi tốt nhất cho Packet dựa trên Metric và quy tắc Longest Prefix Match. Default Route đóng vai trò lối thoát cuối cùng cho các đích không xác định. Hiểu về Administrative Distance giúp Router chọn đường đi tin cậy nhất khi có nhiều lựa chọn.

Sau khi đã hiểu cơ chế định tuyến nói chung, bài học tiếp theo (`BaiHoc_11_GiaoThucDinhTuyen.md`) sẽ đưa chúng ta vào thế giới của các **Giao thức Định tuyến Động** cụ thể. Chúng ta sẽ phân loại chúng (IGP/EGP, Distance Vector/Link State) và điểm qua các đại diện tiêu biểu như RIP, OSPF, EIGRP, và BGP. Hãy sẵn sàng gặp gỡ những "hoa tiêu" tự động của mạng nhé! 🗺️🤖
