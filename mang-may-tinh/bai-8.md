# Bài Học 07: Tầng Mạng (Network Layer) - Chỉ Đường Trên Xa Lộ Thông Tin 🗺️🚦

## Mục Tiêu Bài Học

*   Hiểu rõ vai trò và chức năng chính của Tầng Mạng (Layer 3) trong mô hình OSI và TCP/IP.
*   Nắm vững khái niệm **định địa chỉ logic (Logical Addressing)** sử dụng địa chỉ IP.
*   Hiểu khái niệm **định tuyến (Routing)** và vai trò của Router trong việc chọn đường đi tốt nhất.
*   Phân biệt giữa **mặt phẳng điều khiển (Control Plane)** và **mặt phẳng dữ liệu (Data Plane)** trong định tuyến.
*   Tìm hiểu về đơn vị dữ liệu của Tầng Mạng: **Packet (Gói tin)**.
*   Biết về các giao thức quan trọng hoạt động ở Tầng Mạng (IP, ICMP, một phần của ARP/RARP - mặc dù ARP hoạt động ở ranh giới L2/L3).

## Nội Dung Chi Tiết

### 1. Vai Trò và Chức Năng

Tầng Mạng (Layer 3) nằm phía trên Tầng Liên kết Dữ liệu (Layer 2). Nếu Layer 2 tập trung vào việc di chuyển dữ liệu (Frames) **trong cùng một mạng cục bộ (LAN)**, thì Layer 3 có nhiệm vụ lớn lao hơn: **Chuyển giao dữ liệu (Packets) giữa các mạng khác nhau từ nguồn đến đích cuối cùng (end-to-end delivery across multiple networks).**

Hãy tưởng tượng mạng Internet là một hệ thống đường cao tốc khổng lồ nối các thành phố (mạng LAN). Tầng Mạng chính là hệ thống bản đồ, biển chỉ dẫn và các giao lộ (Router) giúp chiếc xe chở hàng (Packet) của bạn tìm được đường đi tốt nhất từ thành phố này sang thành phố khác để đến đúng địa chỉ người nhận.

**Chức năng chính:**

*   **Logical Addressing (Định địa chỉ logic):** Cung cấp một hệ thống địa chỉ **duy nhất trên toàn mạng** (không chỉ trong LAN) để xác định thiết bị nguồn và đích. Địa chỉ này chính là **địa chỉ IP (Internet Protocol)**. Địa chỉ IP là địa chỉ *logic*, có thể thay đổi tùy thuộc vào mạng mà thiết bị đang kết nối, khác với địa chỉ MAC là địa chỉ *vật lý*, cố định.
*   **Routing (Định tuyến):** Đây là chức năng cốt lõi. Tầng Mạng (thông qua các Router) chịu trách nhiệm **xác định đường đi tối ưu** cho các Packet di chuyển qua các mạng trung gian (interconnected networks) để đến được mạng đích. Router sử dụng các **thuật toán định tuyến (routing algorithms)** và **bảng định tuyến (routing table)** để đưa ra quyết định này.
*   **Packetizing/Encapsulation (Đóng gói):** Nhận dữ liệu (Segments/Datagrams) từ Tầng Giao vận (Layer 4), đóng gói chúng thành các **Packet (gói tin)** bằng cách thêm **IP Header**. IP Header chứa thông tin quan trọng như địa chỉ IP nguồn, địa chỉ IP đích, thời gian sống của gói tin (TTL), và thông tin về giao thức tầng trên (TCP hay UDP).
*   **Fragmentation & Reassembly (Phân mảnh & Tái hợp - chủ yếu với IPv4):** Nếu một Packet quá lớn so với kích thước tối đa mà một mạng trung gian có thể xử lý (MTU - Maximum Transmission Unit), Tầng Mạng có thể **phân mảnh (fragment)** Packet đó thành các mảnh nhỏ hơn. Các mảnh này sẽ được **tái hợp (reassemble)** tại thiết bị đích cuối cùng. (IPv6 xử lý việc này khác đi).
*   **Error Handling & Diagnostics (Xử lý lỗi & Chẩn đoán):** Sử dụng các giao thức như **ICMP (Internet Control Message Protocol)** để gửi các thông báo lỗi (ví dụ: "Đích không tới được" - Destination Unreachable) hoặc các thông điệp chẩn đoán (ví dụ: lệnh `ping` dùng ICMP Echo Request/Reply).

### 2. Định Địa Chỉ Logic (Logical Addressing - IP Address)

*   **Tại sao cần địa chỉ logic?** Địa chỉ MAC (Layer 2) chỉ có ý nghĩa trong cùng một mạng LAN. Để gửi dữ liệu đi xa hơn, qua nhiều mạng khác nhau, chúng ta cần một hệ thống địa chỉ có phạm vi toàn cầu và có cấu trúc phân cấp giúp cho việc định tuyến trở nên khả thi. Đó chính là địa chỉ IP.
*   **Cấu trúc phân cấp:** Địa chỉ IP thường bao gồm hai phần:
    *   **Network ID (Địa chỉ mạng):** Xác định mạng mà thiết bị đó thuộc về. Tất cả các thiết bị trong cùng một mạng LAN sẽ có cùng Network ID. Router sử dụng Network ID để quyết định chuyển Packet đến mạng nào.
    *   **Host ID (Địa chỉ máy chủ/thiết bị):** Xác định duy nhất một thiết bị cụ thể trong mạng đó.
*   **Phiên bản:** Có hai phiên bản chính:
    *   **IPv4 (Internet Protocol version 4):** 32 bit, là phiên bản đang được sử dụng phổ biến nhất hiện nay (ví dụ: `192.168.1.10`). Chúng ta sẽ tìm hiểu kỹ về IPv4 ở bài sau.
    *   **IPv6 (Internet Protocol version 6):** 128 bit, được phát triển để giải quyết tình trạng cạn kiệt địa chỉ IPv4 và cung cấp nhiều cải tiến khác (ví dụ: `2001:0db8:85a3:0000:0000:8a2e:0370:7334`). Sẽ có bài riêng về IPv6.

### 3. Định Tuyến (Routing)

Đây là quá trình **chọn đường đi (path selection)** cho các Packet từ nguồn đến đích qua một hoặc nhiều Router.

*   **Router:** Thiết bị chính thực hiện chức năng định tuyến. Mỗi Router duy trì một **Bảng Định Tuyến (Routing Table)**.
*   **Bảng Định Tuyến:** Chứa các mục (entries), mỗi mục thường bao gồm:
    *   **Destination Network (Mạng đích):** Địa chỉ mạng mà Router biết cách đi đến.
    *   **Subnet Mask (Mặt nạ mạng con):** Giúp Router xác định phần Network ID và Host ID của địa chỉ IP.
    *   **Next Hop IP Address (Địa chỉ IP của Router kế tiếp):** Địa chỉ IP của Router tiếp theo trên đường đi đến mạng đích. Nếu mạng đích kết nối trực tiếp với Router, mục này có thể không cần.
    *   **Outgoing Interface (Cổng giao diện ra):** Cổng mà Router sẽ gửi Packet ra để đi đến Next Hop hoặc mạng đích.
    *   **Metric (Thông số đo lường):** Một giá trị thể hiện "chi phí" hoặc "độ tốt" của đường đi đó (ví dụ: số lượng hop, băng thông, độ trễ...). Router sẽ ưu tiên đường đi có metric thấp nhất.
*   **Quá trình định tuyến Packet tại Router:**
    1.  Nhận Packet vào một Interface.
    2.  Kiểm tra lỗi Header (Checksum).
    3.  Giảm giá trị TTL (Time To Live) đi 1. Nếu TTL = 0, hủy Packet và gửi ICMP "Time Exceeded" về nguồn (tránh Packet chạy vòng lặp vô hạn).
    4.  Đọc **địa chỉ IP đích** trong IP Header.
    5.  **Tìm đường đi phù hợp nhất (Best Path Match)** trong Bảng Định Tuyến dựa trên địa chỉ IP đích và Subnet Mask (thường là tìm mục có tiền tố (prefix) khớp dài nhất - longest prefix match).
    6.  Xác định được Outgoing Interface và Next Hop IP Address.
    7.  **Chuẩn bị Frame Layer 2 mới:**
        *   Dùng ARP để tìm MAC của Next Hop (nếu chưa có trong ARP Cache).
        *   Tạo Frame mới với: MAC nguồn = MAC của Outgoing Interface, MAC đích = MAC của Next Hop/Máy đích cuối.
    8.  Gửi Frame chứa Packet ra Outgoing Interface.
*   **Mặt phẳng điều khiển (Control Plane) và Mặt phẳng dữ liệu (Data Plane):**
    *   **Control Plane:** Liên quan đến việc **xây dựng và duy trì Bảng Định Tuyến**. Bao gồm việc chạy các giao thức định tuyến (như OSPF, BGP), trao đổi thông tin định tuyến với các Router khác, tính toán đường đi tốt nhất. Hoạt động này tương đối "chậm" và tốn CPU.
    *   **Data Plane (Forwarding Plane):** Liên quan đến việc **xử lý và chuyển tiếp Packet thực tế** dựa trên Bảng Định Tuyến đã có. Quá trình này cần diễn ra **cực kỳ nhanh** và thường được tối ưu bằng phần cứng chuyên dụng (ASICs) trong các Router hiện đại.

### 4. Đơn Vị Dữ Liệu: Packet (Gói tin)

*   Khi dữ liệu từ Layer 4 (Segment/Datagram) đi xuống Layer 3, nó được đóng gói thêm **IP Header** để trở thành một **Packet**.
*   IP Header chứa các thông tin quan trọng cho việc định tuyến và chuyển giao, bao gồm:
    *   Version (Phiên bản IP - 4 hoặc 6)
    *   IHL (Internet Header Length - Độ dài IP Header, chỉ có ở IPv4)
    *   Type of Service (ToS)/Differentiated Services (DS) (Chất lượng dịch vụ)
    *   Total Length (Tổng độ dài Packet)
    *   Identification, Flags, Fragment Offset (Liên quan đến phân mảnh IPv4)
    *   **Time To Live (TTL)** (Giới hạn số hop tối đa)
    *   **Protocol** (Giao thức tầng trên - ví dụ: 6 cho TCP, 17 cho UDP, 1 cho ICMP)
    *   Header Checksum (Kiểm tra lỗi Header - chỉ có ở IPv4)
    *   **Source IP Address (Địa chỉ IP nguồn)**
    *   **Destination IP Address (Địa chỉ IP đích)**
    *   Options (Tùy chọn - ít dùng, chỉ có ở IPv4)

### 5. Các Giao Thức Quan Trọng ở Layer 3

*   **IP (Internet Protocol):** Giao thức cốt lõi, định nghĩa cấu trúc địa chỉ IP và định dạng Packet. Cung cấp dịch vụ chuyển phát "nỗ lực tốt nhất" (best-effort), **không hướng kết nối (connectionless)** và **không đáng tin cậy (unreliable)** - tức là IP không đảm bảo Packet sẽ đến đích, không đảm bảo đúng thứ tự, và không kiểm tra/sửa lỗi dữ liệu bên trong (chỉ kiểm tra lỗi Header ở IPv4). Độ tin cậy sẽ do các tầng cao hơn (như TCP ở Layer 4) đảm nhiệm.
*   **ICMP (Internet Control Message Protocol):** Hoạt động song song với IP, dùng để gửi các **thông báo lỗi** và **thông tin điều khiển** giữa các thiết bị mạng (Router, Host). Lệnh `ping` và `traceroute` là những ứng dụng phổ biến của ICMP.
*   **ARP (Address Resolution Protocol):** Như đã học, ARP giúp tìm MAC Address từ IP Address trong cùng mạng LAN. Nó hoạt động ở ranh giới Layer 2 và Layer 3.
*   **RARP (Reverse Address Resolution Protocol):** Ngược lại với ARP, giúp thiết bị tìm IP Address của mình khi chỉ biết MAC Address (ít dùng ngày nay, chủ yếu thay bằng BOOTP/DHCP).
*   **Giao thức định tuyến (Routing Protocols):** Như RIP, EIGRP, OSPF, BGP. Các giao thức này không trực tiếp mang dữ liệu người dùng, mà dùng để các Router trao đổi thông tin và xây dựng Bảng Định Tuyến (thuộc về Control Plane). Chúng ta sẽ có bài riêng về các giao thức này.

## Tóm Tắt & Bài Học Tiếp Theo

Tầng Mạng (Layer 3) đóng vai trò như người chỉ đường thông thái, sử dụng địa chỉ IP logic để xác định nguồn và đích, đồng thời dùng các Router và thuật toán định tuyến để tìm ra con đường tốt nhất cho Packet vượt qua các mạng khác nhau. Nó đóng gói dữ liệu thành Packet và sử dụng các giao thức như IP và ICMP để thực hiện nhiệm vụ của mình.

Trong bài học tiếp theo (`BaiHoc_08_DiaChiIP_IPv4.md`), chúng ta sẽ "zoom" vào loại địa chỉ phổ biến nhất hiện nay: **Địa chỉ IPv4**. Chúng ta sẽ tìm hiểu chi tiết cấu trúc, các lớp địa chỉ (classful), khái niệm subnet mask và các loại địa chỉ đặc biệt. Hãy sẵn sàng làm quen với "chứng minh nhân dân" của các thiết bị trên Internet nhé! 🆔💻
