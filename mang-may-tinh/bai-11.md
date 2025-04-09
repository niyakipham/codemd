  +-------------------+          +-------------------+
  |       AS 100      |          |       AS 200      |
  |   (e.g., Your ISP)|          |   (e.g., Another ISP)|
  |  +--+ OSPF +--+   |  BGP Peering  |   +--+ OSPF +--+   |
  |  |R1|------|R2|----------//----------|R3|------|R4|   |
  |  +--+      +--+   | Link       |   +--+      +--+   |
  |   | \      / |    |          |    | \      / |    |
  | OSPF \    / EIGRP |          |    | OSPF\    / RIP |    |
  |   |   +--+   |    |          |    |   +--+   |    |
  |   `---|R5|---'    |          |    |   |R6|---'    |
  |       +--+        |          |    |   +--+        |
  |    IGP Protocols  |          |    |  IGP Protocols  |
  +-------------------+          +-------------------+
        <-------------- EGP (BGP) -------------->

  
### 3. Phân Loại Thuật Toán trong IGP: Distance Vector vs. Link-State

Các giao thức IGP phổ biến có thể được chia thành hai nhóm chính dựa trên thuật toán chúng sử dụng để tính toán đường đi:

*   **Distance Vector (Vector Khoảng cách):**
    *   **Nguyên lý hoạt động:**
        *   Router chỉ biết thông tin về các Router **kết nối trực tiếp** với nó (láng giềng).
        *   Router định kỳ gửi **toàn bộ hoặc một phần bảng định tuyến** của mình cho các láng giềng.
        *   Router cập nhật bảng định tuyến của mình dựa trên thông tin nhận được từ láng giềng. Chúng tin tưởng vào thông tin "khoảng cách" (Metric) mà láng giềng cung cấp.
        *   Hoạt động theo kiểu "tin đồn" (Routing by Rumor): "Tôi biết cách đến mạng X qua anh A với chi phí là 5. Anh B nói anh ấy đến mạng X chỉ mất 3. Vậy tôi sẽ đi qua anh B."
    *   **Thuật toán:** Thường dựa trên Bellman-Ford hoặc DUAL (cho EIGRP).
    *   **Ví dụ:**
        *   **RIP (Routing Information Protocol):** Giao thức lâu đời, đơn giản.
            *   Metric: Hop Count (tối đa 15).
            *   Cập nhật: Gửi toàn bộ bảng định tuyến mỗi 30 giây (RIPv1 - broadcast, RIPv2 - multicast).
            *   Hội tụ chậm. Dễ bị **Routing Loops (vòng lặp định tuyến)** - vấn đề Packet bị chạy vòng quanh không đến được đích. Sử dụng các cơ chế chống loop như Split Horizon, Route Poisoning, Holddown Timers.
            *   Phiên bản: RIPv1 (classful), RIPv2 (classless, hỗ trợ VLSM, có authentication), RIPng (cho IPv6).
            *   Hiện nay ít dùng trong mạng lớn do hạn chế về metric và hội tụ chậm.
        *   **EIGRP (Enhanced Interior Gateway Routing Protocol):** Giao thức độc quyền của Cisco (sau này có mở một phần). Được coi là "Advanced Distance Vector" hoặc "Hybrid".
            *   Metric: Sử dụng Metric phức hợp (Bandwidth, Delay, Load, Reliability), linh hoạt hơn RIP.
            *   Thuật toán DUAL (Diffusing Update Algorithm): Cho phép **hội tụ cực nhanh** và **không tạo routing loop** (guaranteed loop-free). Tính toán sẵn đường đi dự phòng (Feasible Successor) nếu có.
            *   Cập nhật: Chỉ gửi cập nhật **một phần (partial)** và **khi có thay đổi (triggered)**, không gửi định kỳ toàn bộ bảng => Tiết kiệm băng thông. Sử dụng Reliable Transport Protocol (RTP) riêng để đảm bảo việc gửi nhận cập nhật.
            *   Hỗ trợ VLSM, CIDR, IP, IPv6, và các giao thức khác (IPX, AppleTalk - cũ).
            *   Phức tạp hơn RIP nhưng hiệu quả hơn nhiều.
    *   **Ưu điểm (chung của Distance Vector):** Đơn giản hơn Link-State, dễ cấu hình, ít tốn CPU/RAM hơn (đặc biệt là RIP).
    *   **Nhược điểm (chung của Distance Vector):** Hội tụ có thể chậm (nhất là RIP), dễ bị loop (nhất là RIP), Router không có cái nhìn toàn cục về mạng (chỉ biết thông tin từ hàng xóm).

*   **Link-State (Trạng thái Đường liên kết):**
    *   **Nguyên lý hoạt động:**
        *   Mỗi Router xây dựng một "bản đồ" chi tiết về **toàn bộ cấu trúc mạng (topology)** bên trong khu vực (area) của nó.
        *   Router gửi thông tin về **trạng thái các đường liên kết (links)** của chính nó (link đang up/down, chi phí của link...) cho tất cả các Router khác trong cùng khu vực thông qua các bản tin **LSA (Link-State Advertisement)**.
        *   Tất cả Router trong khu vực thu thập LSA và xây dựng một **Cơ sở dữ liệu Trạng thái Liên kết (LSDB - Link-State Database)** giống hệt nhau.
        *   Mỗi Router tự chạy thuật toán **SPF (Shortest Path First - thường là Dijkstra)** trên LSDB của mình để tính toán ra **cây đường đi ngắn nhất (shortest-path tree)** từ nó đến tất cả các mạng đích khác.
        *   Hoạt động theo kiểu "mọi người đều có cùng bản đồ và tự tìm đường".
    *   **Thuật toán:** Dijkstra (SPF).
    *   **Ví dụ:**
        *   **OSPF (Open Shortest Path First):** Giao thức **chuẩn mở (open standard)**, rất phổ biến và mạnh mẽ.
            *   Metric: **Cost** (thường dựa trên bandwidth).
            *   **Kiến trúc phân cấp (Hierarchical):** Chia AS thành các **Area (Khu vực)**. Area 0 (Backbone Area) là trung tâm, các Area khác kết nối vào Area 0. Giúp giảm kích thước LSDB, hạn chế LSA flooding, tăng khả năng mở rộng.
            *   Cập nhật: Gửi LSA khi có thay đổi (triggered flooding). Có các bản tin Hello để duy trì quan hệ láng giềng.
            *   **Hội tụ nhanh**, **không bị routing loop** (do có bản đồ đầy đủ).
            *   Hỗ trợ VLSM, CIDR, Authentication.
            *   Phiên bản: OSPFv2 (cho IPv4), OSPFv3 (cho IPv6 và có thể cả IPv4).
            *   Phức tạp hơn Distance Vector, đòi hỏi cấu hình và quản lý cẩn thận hơn, tốn nhiều CPU/RAM hơn khi tính toán SPF.
        *   **IS-IS (Intermediate System to Intermediate System):** Một giao thức Link-State khác, cũng là chuẩn mở.
            *   Tương tự OSPF về nhiều mặt (dùng SPF, gửi thông tin link-state).
            *   Ít phổ biến hơn OSPF trong mạng doanh nghiệp nhưng lại khá **phổ biến trong mạng lõi của các ISP lớn** do khả năng mở rộng tốt và hỗ trợ tốt các giao thức khác ngoài IP (như CLNS - Connectionless Network Service, mặc dù hiện nay chủ yếu chạy cho IP).
            *   Có thể coi là đối thủ cạnh tranh trực tiếp với OSPF.
    *   **Ưu điểm (chung của Link-State):** Hội tụ nhanh, không bị loop, mỗi Router có cái nhìn toàn cục về topology (trong Area), dễ dàng khắc phục sự cố hơn.
    *   **Nhược điểm (chung của Link-State):** Phức tạp hơn Distance Vector, tốn nhiều tài nguyên CPU/RAM hơn (đặc biệt khi topology lớn/thay đổi thường xuyên), yêu cầu thiết kế mạng phân cấp (Area) cẩn thận.

### 4. BGP (Border Gateway Protocol) - "Chúa Tể" Của Định Tuyến Internet

*   **Loại giao thức:** **EGP (Exterior Gateway Protocol)** duy nhất được sử dụng rộng rãi hiện nay.
*   **Mục đích:** Trao đổi thông tin về **khả năng tiếp cận (reachability)** các dải địa chỉ IP (gọi là các **Prefix**) giữa các **Hệ thống Tự trị (AS)**.
*   **Không phải là Distance Vector hay Link-State thuần túy:** BGP thường được gọi là giao thức **Path Vector (Vector Đường đi)**.
    *   Khi quảng bá một Prefix, BGP mang theo danh sách các AS (AS-Path) mà Prefix đó đã đi qua.
    *   AS-Path giúp **phát hiện và tránh routing loop** một cách hiệu quả (Router sẽ không chấp nhận route có AS của chính mình trong AS-Path).
    *   Quan trọng hơn, AS-Path và các **thuộc tính (Attributes)** khác của BGP được sử dụng để **áp dụng các Chính sách Định tuyến (Routing Policies)**.
*   **Tập trung vào Chính sách, không chỉ là Tốc độ:** Khác với IGP (ưu tiên đường nhanh nhất), BGP cho phép các nhà quản trị AS (ví dụ: ISP) điều khiển luồng traffic dựa trên các yếu tố kinh doanh, thỏa thuận peering, chi phí...
*   **Hoạt động dựa trên TCP:** BGP sử dụng **TCP port 179** để thiết lập kết nối (phiên BGP - BGP session) tin cậy giữa các Router ngang hàng (peers) trước khi trao đổi thông tin định tuyến.
*   **Phân loại Phiên BGP:**
    *   **iBGP (Internal BGP):** Phiên BGP giữa các Router **trong cùng một AS**. Cần cơ chế full-mesh hoặc dùng Route Reflector/Confederation để tránh loop.
    *   **eBGP (External BGP):** Phiên BGP giữa các Router thuộc **hai AS khác nhau**. Đây là cách các AS kết nối với nhau trên Internet.
*   **Rất phức tạp:** BGP có nhiều thuộc tính, quy trình chọn đường phức tạp và yêu cầu cấu hình cẩn thận. Thường chỉ được quản lý bởi các kỹ sư mạng có kinh nghiệm tại các ISP hoặc doanh nghiệp lớn có nhiều kết nối Internet.

## Tóm Tắt & Bài Học Tiếp Theo

Các giao thức định tuyến động là xương sống cho hoạt động tự động và linh hoạt của mạng. IGP (như RIP, EIGRP, OSPF, IS-IS) đảm nhiệm việc tìm đường tối ưu bên trong một AS, với hai trường phái chính là Distance Vector và Link-State. EGP (chủ yếu là BGP) quản lý việc kết nối và áp dụng chính sách giữa các AS, tạo nên Internet toàn cầu. Mỗi giao thức có ưu, nhược điểm và trường hợp sử dụng riêng.

Chúng ta đã khám phá xong Tầng Mạng (Layer 3) với địa chỉ IP, Subnetting và Routing. Giờ là lúc tiến lên một tầng cao hơn, nơi đảm bảo dữ liệu không chỉ đến đúng máy mà còn đến đúng ứng dụng! Bài học tiếp theo (`BaiHoc_12_TangGiaoVan.md`) sẽ giới thiệu về **Tầng Giao Vận (Transport Layer)** - người vận chuyển cần mẫn của mạng. Hẹn gặp bạn ở Layer 4! 🚚📦
