# Bài Học 12: Tầng Giao Vận (Transport Layer) - Người Đưa Thư Tận Tay Ứng Dụng 📦📫

## Mục Tiêu Bài Học

*   Hiểu rõ vai trò và chức năng chính của Tầng Giao Vận (Layer 4) trong mô hình OSI và TCP/IP.
*   Nắm vững khái niệm **truyền thông đầu cuối (End-to-End Communication)** và **truyền thông tiến trình-đến-tiến trình (Process-to-Process Communication)**.
*   Hiểu cơ chế **ghép kênh (Multiplexing)** và **phân kênh (Demultiplexing)** sử dụng số hiệu cổng (Port Numbers).
*   Tìm hiểu chức năng **phân đoạn dữ liệu (Segmentation)** và **tái hợp (Reassembly)**.
*   Biết về hai giao thức cốt lõi của Tầng Giao Vận: **TCP (Transmission Control Protocol)** và **UDP (User Datagram Protocol)** (sẽ tìm hiểu kỹ hơn ở bài sau).
*   Hiểu các chức năng tùy chọn mà Tầng Giao Vận có thể cung cấp (thông qua TCP): **Kiểm soát luồng (Flow Control)** và **Đảm bảo độ tin cậy (Reliability)**.

## Nội Dung Chi Tiết

### 1. Vai Trò và Chức Năng

Tầng Giao Vận (Layer 4) nằm giữa Tầng Mạng (Layer 3) và Tầng Ứng Dụng (Layer 5+). Nếu Tầng Mạng lo việc chuyển gói tin (Packet) **giữa các máy tính (host-to-host)** khác nhau dựa trên địa chỉ IP, thì Tầng Giao Vận có trách nhiệm tinh tế hơn: **Cung cấp dịch vụ vận chuyển dữ liệu logic giữa các ứng dụng (process-to-process) đang chạy trên các máy tính đầu cuối đó.**

Hãy tưởng tượng Tầng Mạng như dịch vụ bưu chính chuyển thư đến đúng địa chỉ nhà (IP Address). Tầng Giao Vận giống như người đưa thư bên trong tòa nhà đó, đảm bảo lá thư đến đúng căn hộ (ứng dụng cụ thể) của người nhận thông qua số phòng (Port Number).

**Chức năng chính:**

*   **Process-to-Process Communication (Truyền thông tiến trình-đến-tiến trình):** Đảm bảo dữ liệu từ một ứng dụng trên máy gửi được chuyển đến đúng ứng dụng trên máy nhận. Điều này được thực hiện thông qua việc sử dụng **số hiệu cổng (Port Numbers)**.
*   **Multiplexing & Demultiplexing (Ghép kênh & Phân kênh):**
    *   **Multiplexing (Tại máy gửi):** Gom dữ liệu từ nhiều ứng dụng (tiến trình) khác nhau, đóng gói chúng (thêm Header của Layer 4) và chuyển xuống Tầng Mạng để gửi đi trên cùng một đường truyền mạng.
    *   **Demultiplexing (Tại máy nhận):** Nhận các Segment/Datagram từ Tầng Mạng, đọc thông tin Port trong Header, và phân phối dữ liệu đến đúng ứng dụng (tiến trình) đang chờ ở Port đó.
*   **Segmentation & Reassembly (Phân đoạn & Tái hợp):**
    *   **Segmentation:** Chia luồng dữ liệu lớn từ Tầng Ứng Dụng thành các **đơn vị nhỏ hơn** gọi là **Segment (cho TCP)** hoặc **Datagram (cho UDP)**. Việc này giúp truyền dữ liệu hiệu quả hơn và phù hợp với giới hạn kích thước của Tầng Mạng (MTU).
    *   **Reassembly:** Tại máy nhận, tập hợp các Segment/Datagram lại theo đúng thứ tự (nếu cần, như TCP làm) để khôi phục luồng dữ liệu gốc cho Tầng Ứng Dụng.
*   **Connection Management (Quản lý kết nối - Chủ yếu TCP):** Thiết lập, duy trì và kết thúc các kết nối ảo giữa hai ứng dụng trước khi truyền dữ liệu (Connection-oriented).
*   **Reliability (Đảm bảo độ tin cậy - Chủ yếu TCP):** Cung cấp cơ chế để đảm bảo dữ liệu đến đích một cách đáng tin cậy, không lỗi, đúng thứ tự. Bao gồm:
    *   **Error Control (Kiểm soát lỗi):** Sử dụng Checksum để phát hiện lỗi trong dữ liệu. Sử dụng cơ chế báo nhận (Acknowledgement - ACK) và đánh số thứ tự (Sequence Number) để phát hiện mất mát hoặc trùng lặp Segment, và yêu cầu gửi lại (Retransmission).
    *   **Sequencing (Sắp xếp thứ tự):** Đảm bảo các Segment được tái hợp đúng thứ tự tại bên nhận.
*   **Flow Control (Kiểm soát luồng - Chủ yếu TCP):** Ngăn chặn việc máy gửi gửi dữ liệu quá nhanh làm "ngập" bộ đệm của máy nhận. Sử dụng cơ chế cửa sổ trượt (Sliding Window).
*   **Congestion Control (Kiểm soát tắc nghẽn - Chủ yếu TCP):** Giúp điều chỉnh tốc độ gửi dữ liệu để tránh làm tắc nghẽn mạng lưới trung gian (các Router).

### 2. Truyền Thông Tiến Trình-đến-Tiến Trình & Số Hiệu Cổng (Port Numbers)

Một máy tính có thể chạy nhiều ứng dụng mạng cùng lúc (trình duyệt web, email client, game online...). Làm thế nào Tầng Giao Vận biết được dữ liệu nhận về từ Tầng Mạng là dành cho ứng dụng nào?

**Giải pháp:** Sử dụng **Số Hiệu Cổng (Port Numbers)**.

*   Port Number là một con số **16 bit** (từ 0 đến 65535) được gán cho mỗi tiến trình (ứng dụng) cần giao tiếp qua mạng tại Tầng Giao Vận.
*   **Header của Segment (TCP) hoặc Datagram (UDP)** sẽ chứa cả **Source Port (Cổng nguồn)** và **Destination Port (Cổng đích)**.
*   **Source Port:** Số hiệu cổng của ứng dụng gửi dữ liệu trên máy nguồn. Thường là một số được hệ điều hành chọn ngẫu nhiên từ một dải cổng động (Ephemeral Ports).
*   **Destination Port:** Số hiệu cổng của ứng dụng nhận dữ liệu trên máy đích. Đối với các dịch vụ mạng phổ biến (web, email), đây thường là các cổng được chuẩn hóa (Well-known Ports).

**Ví dụ:** Bạn dùng trình duyệt (Process A, được gán Source Port 51000) để truy cập trang web `google.com` (Process B - Web Server, lắng nghe ở Destination Port 80 - cổng chuẩn của HTTP).
*   Khi gửi yêu cầu: Packet sẽ có IP_Nguồn = IP_CủaBạn, IP_Đích = IP_Google, Port_Nguồn = 51000, Port_Đích = 80.
*   Khi Google trả lời: Packet sẽ có IP_Nguồn = IP_Google, IP_Đích = IP_CủaBạn, Port_Nguồn = 80, Port_Đích = 51000.

Tầng Giao Vận tại máy bạn nhận Packet này, đọc Port_Đích là 51000, và biết phải chuyển dữ liệu lên cho Process A (trình duyệt) đang lắng nghe ở cổng đó.

### 3. Ghép Kênh (Multiplexing) và Phân Kênh (Demultiplexing)

*   **Multiplexing:** Tại máy gửi, Tầng Giao Vận nhận dữ liệu từ nhiều socket (mỗi socket ứng với một ứng dụng và một cặp địa chỉ/cổng). Nó tạo các Segment/Datagram, gắn đúng Source/Destination Port cho từng cái, rồi đẩy xuống Tầng Mạng. Giống như việc nhiều người cùng bỏ thư vào một thùng thư chung.
*   **Demultiplexing:** Tại máy nhận, Tầng Giao Vận nhận các Segment/Datagram từ Tầng Mạng. Dựa vào thông tin **Source IP, Destination IP, Source Port, Destination Port, và Protocol Type (TCP hay UDP)** trong Header, nó xác định chính xác Socket (ứng dụng) nào cần nhận dữ liệu này và chuyển lên. Giống như người đưa thư nhìn địa chỉ và số phòng để phát thư đúng người.

### 4. Phân Đoạn (Segmentation) và Tái Hợp (Reassembly)

*   Ứng dụng ở Tầng trên (Application Layer) thường xử lý các luồng dữ liệu lớn (ví dụ: tải một file, xem video).
*   Tầng Mạng (Layer 3) lại có giới hạn về kích thước tối đa của một Packet (MTU - Maximum Transmission Unit, thường khoảng 1500 bytes cho Ethernet).
*   **Segmentation:** Tầng Giao Vận (đặc biệt là TCP) chia nhỏ luồng dữ liệu lớn thành các **Segment**, mỗi Segment có kích thước phù hợp để có thể đóng gói thành Packet ở Layer 3 mà không vượt quá MTU. Mỗi Segment được gắn thêm Header của Layer 4 (chứa Port, Sequence Number...).
*   **Reassembly:** Tại máy nhận, Tầng Giao Vận (TCP) sử dụng **Sequence Number** trong Header để sắp xếp lại các Segment theo đúng thứ tự ban đầu và ghép chúng lại thành luồng dữ liệu hoàn chỉnh trước khi chuyển lên cho ứng dụng.

### 5. Hai Giao Thức Chính: TCP và UDP

Tầng Giao Vận cung cấp hai lựa chọn giao thức chính với các đặc tính dịch vụ khác nhau:

*   **TCP (Transmission Control Protocol):**
    *   **Hướng kết nối (Connection-oriented):** Thiết lập một kết nối ảo (bắt tay ba bước - three-way handshake) trước khi truyền dữ liệu và giải phóng kết nối khi hoàn tất.
    *   **Đáng tin cậy (Reliable):** Đảm bảo dữ liệu đến đúng thứ tự, không mất mát, không lỗi thông qua cơ chế đánh số thứ tự (Sequence Numbers), báo nhận (Acknowledgements - ACKs), và gửi lại (Retransmissions).
    *   **Kiểm soát luồng (Flow Control):** Điều chỉnh tốc độ gửi để không làm tràn bộ đệm bên nhận.
    *   **Kiểm soát tắc nghẽn (Congestion Control):** Giảm tốc độ gửi khi phát hiện tắc nghẽn trên mạng.
    *   **Đơn vị dữ liệu:** Segment.
    *   **Overhead cao hơn:** Header lớn hơn (tối thiểu 20 bytes), cần duy trì trạng thái kết nối, tốn thêm băng thông cho ACK.
    *   **Ứng dụng:** HTTP/HTTPS (Web), FTP (Truyền file), SMTP/POP3/IMAP (Email), SSH... những ứng dụng yêu cầu độ tin cậy cao.

*   **UDP (User Datagram Protocol):**
    *   **Không kết nối (Connectionless):** Gửi dữ liệu đi ngay mà không cần thiết lập kết nối trước.
    *   **Không đáng tin cậy (Unreliable):** Không đảm bảo dữ liệu sẽ đến đích, không đảm bảo đúng thứ tự, không gửi lại nếu mất. Chỉ có cơ chế kiểm tra lỗi cơ bản bằng Checksum (tùy chọn).
    *   **Không kiểm soát luồng, không kiểm soát tắc nghẽn.**
    *   **Đơn vị dữ liệu:** Datagram.
    *   **Overhead thấp:** Header nhỏ (8 bytes), không cần duy trì trạng thái, gửi nhanh.
    *   **Ứng dụng:** DNS, DHCP, SNMP, VoIP (Thoại qua IP), Streaming video/audio, Game online... những ứng dụng ưu tiên **tốc độ**, chấp nhận mất mát một ít dữ liệu, hoặc có cơ chế kiểm soát lỗi riêng ở tầng ứng dụng.

=> Việc lựa chọn giữa TCP và UDP phụ thuộc vào yêu cầu cụ thể của ứng dụng.

## Tóm Tắt & Bài Học Tiếp Theo

Tầng Giao Vận (Layer 4) là cầu nối quan trọng giữa Tầng Mạng và các ứng dụng. Nó sử dụng Port Numbers để phân biệt và chuyển giao dữ liệu đến đúng tiến trình (Multiplexing/Demultiplexing). Nó cũng chia nhỏ dữ liệu thành Segment/Datagram để truyền đi hiệu quả. Quan trọng nhất, nó cung cấp hai lựa chọn dịch vụ chính: TCP (tin cậy, hướng kết nối) và UDP (nhanh, không tin cậy, không kết nối).

Trong bài học tiếp theo (`BaiHoc_13_TCP_vs_UDP.md`), chúng ta sẽ "soi" kỹ hơn vào **sự khác biệt và cách hoạt động chi tiết** của hai "gã khổng lồ" ở Tầng Giao Vận này: **TCP và UDP**. Hãy chuẩn bị để hiểu rõ khi nào nên dùng "xe tải chắc chắn" TCP và khi nào nên dùng "xe đua tốc độ" UDP nhé! 🚚💨🏎️
