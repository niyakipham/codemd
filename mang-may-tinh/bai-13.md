# Bài Học 13: TCP vs. UDP - "Xe Tải Chắc Chắn" Hay "Xe Đua Tốc Độ"? 🚚💨🏎️

## Mục Tiêu Bài Học

*   Phân tích sâu hơn về cách thức hoạt động của TCP, bao gồm:
    *   Quá trình bắt tay ba bước (Three-way Handshake) để thiết lập kết nối.
    *   Cơ chế đảm bảo độ tin cậy và thứ tự (Sequence Numbers, Acknowledgements, Retransmission).
    *   Kiểm soát luồng bằng cửa sổ trượt (Sliding Window).
    *   Khái niệm kiểm soát tắc nghẽn.
    *   Quá trình kết thúc kết nối.
    *   Cấu trúc TCP Header.
*   Phân tích sâu hơn về sự đơn giản và tốc độ của UDP:
    *   Thiếu vắng các cơ chế phức tạp của TCP.
    *   Cấu trúc UDP Header.
*   So sánh trực tiếp TCP và UDP qua các tiêu chí quan trọng.
*   Xác định khi nào nên lựa chọn sử dụng TCP và khi nào nên sử dụng UDP cho ứng dụng.

## Nội Dung Chi Tiết

Như đã giới thiệu ở bài trước, Tầng Giao Vận cung cấp hai lựa chọn chính để vận chuyển dữ liệu giữa các ứng dụng: TCP và UDP. Chúng phục vụ những mục đích rất khác nhau và có cách hoạt động hoàn toàn khác biệt.

### 1. TCP (Transmission Control Protocol) - Người Vận Chuyển Cẩn Trọng

TCP được ví như một dịch vụ chuyển phát nhanh **cao cấp**, đảm bảo hàng hóa (dữ liệu) đến nơi **nguyên vẹn, đúng thứ tự, và có xác nhận**.

*   **Đặc điểm cốt lõi:** Hướng kết nối (Connection-oriented), Đáng tin cậy (Reliable), Đảm bảo thứ tự (Ordered), Kiểm soát luồng (Flow Control), Kiểm soát tắc nghẽn (Congestion Control).

*   **a. Thiết lập Kết nối (Three-way Handshake):** Trước khi gửi bất kỳ dữ liệu nào, Client và Server phải "bắt tay" để thiết lập một kết nối ảo. Quá trình này sử dụng các cờ (flags) đặc biệt trong TCP Header: SYN (Synchronize) và ACK (Acknowledgement).
    1.  **Client -> Server: SYN**
        *   Client gửi một Segment với cờ `SYN=1` và một số thứ tự (Sequence Number - SEQ) ngẫu nhiên `x`. Ý nghĩa: "Tôi muốn kết nối, số thứ tự đầu tiên của tôi là x."
    2.  **Server -> Client: SYN-ACK**
        *   Server nhận được SYN, nếu chấp nhận kết nối, nó gửi lại một Segment với:
            *   Cờ `SYN=1` và `ACK=1`.
            *   Số thứ tự (SEQ) ngẫu nhiên của riêng Server `y`.
            *   Số báo nhận (Acknowledgement Number - ACK) là `x + 1`. Ý nghĩa: "Tôi đồng ý kết nối. Số thứ tự của tôi là y. Tôi đã nhận được số thứ tự x của bạn, tôi mong đợi nhận byte tiếp theo có số thứ tự là x+1."
    3.  **Client -> Server: ACK**
        *   Client nhận được SYN-ACK. Nó gửi lại một Segment với:
            *   Cờ `ACK=1`.
            *   Số thứ tự (SEQ) là `x + 1`.
            *   Số báo nhận (ACK) là `y + 1`. Ý nghĩa: "Tôi đã nhận được sự đồng ý và số thứ tự y của bạn. Tôi sẵn sàng gửi/nhận dữ liệu. Tôi mong đợi nhận byte tiếp theo có số thứ tự y+1."
    *   Sau bước 3, kết nối được thiết lập, hai bên có thể bắt đầu trao đổi dữ liệu.

*   **b. Truyền Dữ Liệu & Đảm Bảo Tin Cậy:**
    *   **Sequence Numbers (SEQ):** Mỗi byte dữ liệu gửi đi được gán một số thứ tự duy nhất. Header của mỗi Segment chứa SEQ của byte dữ liệu đầu tiên trong Segment đó.
    *   **Acknowledgement Numbers (ACK):** Bên nhận sử dụng số ACK trong Segment gửi về để báo cho bên gửi biết byte dữ liệu tiếp theo mà nó **mong đợi** nhận được. Ví dụ: ACK = 1001 nghĩa là "Tôi đã nhận thành công tất cả dữ liệu đến byte 1000, làm ơn gửi tiếp từ byte 1001."
    *   **Retransmission (Gửi lại):** Nếu bên gửi không nhận được ACK cho một Segment nào đó trong một khoảng thời gian chờ (timeout), nó sẽ coi như Segment đó bị mất và **tự động gửi lại** Segment đó. TCP cũng có thể phát hiện mất gói tin thông qua việc nhận các ACK trùng lặp (Duplicate ACKs).
    *   **Ordering (Sắp xếp thứ tự):** Bên nhận sử dụng SEQ để sắp xếp lại các Segment có thể đến không đúng thứ tự do đường truyền mạng, đảm bảo dữ liệu được chuyển lên tầng ứng dụng một cách liền mạch.

*   **c. Kiểm Soát Luồng (Flow Control - Sliding Window):**
    *   Bên nhận có một bộ đệm (buffer) với kích thước giới hạn để chứa dữ liệu đến.
    *   Trong TCP Header, có trường **Window Size (Kích thước cửa sổ)**. Bên nhận sử dụng trường này để "quảng bá" cho bên gửi biết còn bao nhiêu dung lượng trống trong bộ đệm của mình.
    *   Bên gửi sẽ điều chỉnh tốc độ gửi sao cho lượng dữ liệu đang "trên đường đi" (chưa được ACK) không vượt quá Window Size mà bên nhận quảng bá. => Tránh làm tràn bộ đệm bên nhận.

*   **d. Kiểm Soát Tắc Nghẽn (Congestion Control):**
    *   Khác với Flow Control (quan tâm đến khả năng của *máy nhận*), Congestion Control quan tâm đến tình trạng của *mạng lưới trung gian*.
    *   TCP có các thuật toán phức tạp (như Slow Start, Congestion Avoidance, Fast Retransmit, Fast Recovery) để dò tìm và phản ứng với tắc nghẽn mạng (phát hiện qua mất gói tin hoặc tăng độ trễ). Khi phát hiện tắc nghẽn, TCP sẽ chủ động giảm tốc độ gửi của mình để giảm tải cho mạng.

*   **e. Kết Thúc Kết Nối (Four-way Handshake):** Khi một bên muốn đóng kết nối, cần có một quy trình "chia tay" lịch sự sử dụng cờ FIN (Finish).
    1.  **Bên A -> Bên B: FIN** (Gửi Segment với cờ `FIN=1`). Ý nghĩa: "Tôi đã gửi xong dữ liệu, tôi muốn đóng kết nối."
    2.  **Bên B -> Bên A: ACK** (Gửi Segment báo nhận FIN). Ý nghĩa: "Tôi đã nhận yêu cầu đóng của bạn." (Lúc này Bên B vẫn có thể gửi nốt dữ liệu nếu còn).
    3.  **Bên B -> Bên A: FIN** (Khi Bên B cũng hết dữ liệu cần gửi, nó gửi Segment với cờ `FIN=1`). Ý nghĩa: "Tôi cũng đã gửi xong, tôi đồng ý đóng."
    4.  **Bên A -> Bên B: ACK** (Gửi Segment báo nhận FIN của Bên B). Ý nghĩa: "Tôi đã nhận yêu cầu đóng của bạn."
    *   Sau bước 4, kết nối chính thức đóng lại.

*   **f. TCP Header:**
    *   Phức tạp, chứa nhiều trường để hỗ trợ các chức năng trên.
    *   Các trường chính: Source Port (16 bit), Destination Port (16 bit), Sequence Number (32 bit), Acknowledgment Number (32 bit), Header Length, Flags (URG, ACK, PSH, RST, SYN, FIN), Window Size (16 bit), Checksum (16 bit), Urgent Pointer, Options...
    *   Kích thước tối thiểu: **20 bytes** (không có Options).

*   **g. Use Cases:** Khi độ tin cậy và thứ tự là tối quan trọng: Duyệt Web (HTTP/HTTPS), Gửi/nhận Email (SMTP, POP3, IMAP), Truyền file (FTP, SCP), Kết nối đầu cuối an toàn (SSH, Telnet)...

### 2. UDP (User Datagram Protocol) - Người Giao Hàng Siêu Tốc

UDP giống như gửi một tấm bưu thiếp: **nhanh, đơn giản, không cần xác nhận, không đảm bảo đến nơi, không quan tâm thứ tự.**

*   **Đặc điểm cốt lõi:** Không kết nối (Connectionless), Không đáng tin cậy (Unreliable), Không đảm bảo thứ tự (Unordered), Không kiểm soát luồng, Không kiểm soát tắc nghẽn. Chỉ cung cấp chức năng **Multiplexing/Demultiplexing** cơ bản và **kiểm tra lỗi (checksum) tùy chọn**.

*   **a. Hoạt động:**
    *   **Không bắt tay:** Không có three-way handshake. Ứng dụng có dữ liệu là UDP đóng gói (thêm UDP header) và gửi xuống IP ngay lập tức.
    *   **Không SEQ/ACK:** Không đánh số thứ tự byte, không có cơ chế báo nhận. Gói tin bị mất là mất luôn, không gửi lại.
    *   **Không sắp xếp:** Gói tin đến đích có thể sai thứ tự so với lúc gửi đi. UDP không tự sắp xếp lại.
    *   **"Gửi và Quên" (Fire and Forget):** UDP chỉ cố gắng hết sức (best-effort) để gửi Datagram đi, phó mặc cho IP và mạng lưới lo phần còn lại.

*   **b. UDP Header:**
    *   Cực kỳ đơn giản.
    *   Chỉ có 4 trường: Source Port (16 bit), Destination Port (16 bit), Length (16 bit - tổng độ dài header + data), Checksum (16 bit - kiểm tra lỗi cho header và data, có thể không dùng).
    *   Kích thước cố định: **8 bytes**.

*   **c. Ưu điểm:**
    *   **Nhanh:** Không tốn thời gian cho kết nối, không có độ trễ do chờ ACK hay gửi lại.
    *   **Overhead thấp:** Header nhỏ (8 bytes vs 20+ bytes của TCP), tiết kiệm băng thông.
    *   **Đơn giản:** Ít trạng thái cần duy trì, ít tốn tài nguyên hệ thống.
    *   **Hỗ trợ Broadcast/Multicast:** TCP là giao thức điểm-điểm (unicast), UDP có thể dùng cho gửi broadcast và multicast dễ dàng hơn.

*   **d. Handling Reliability:** Nếu ứng dụng dùng UDP mà vẫn cần độ tin cậy (ví dụ: đảm bảo file cấu hình TFTP đến đủ), thì logic kiểm tra lỗi, yêu cầu gửi lại phải được **tự xây dựng ở Tầng Ứng Dụng**.

*   **e. Use Cases:** Khi tốc độ và độ trễ thấp là quan trọng hơn độ tin cậy tuyệt đối, hoặc khi mất một vài gói tin không ảnh hưởng nghiêm trọng, hoặc khi ứng dụng tự xử lý lỗi:
    *   Tra cứu tên miền (DNS - thường chỉ cần 1 request, 1 reply, nhanh là ưu tiên).
    *   Cấp phát IP động (DHCP).
    *   Quản lý mạng (SNMP).
    *   Truyền thanh/Truyền hình trực tuyến (Streaming video/audio - mất vài khung hình/âm thanh có thể chấp nhận được).
    *   Thoại qua IP (VoIP - ưu tiên độ trễ thấp, nói lại còn hơn là nghe bị ngắt quãng).
    *   Game online thời gian thực (cập nhật vị trí/hành động cần nhanh nhất có thể).

### 3. TCP vs. UDP: So Sánh Trực Tiếp

| Tiêu Chí             | TCP (Transmission Control Protocol) | UDP (User Datagram Protocol)       |
| :------------------- | :---------------------------------- | :--------------------------------- |
| **Thiết lập Kết nối** | Có (Three-way Handshake)            | Không (Connectionless)            |
| **Độ tin cậy**       | Cao (ACK, Retransmission)           | Thấp (Không đảm bảo)               |
| **Thứ tự gói tin**   | Đảm bảo (Sequence Numbers)          | Không đảm bảo                     |
| **Kiểm soát luồng**  | Có (Sliding Window)                 | Không                              |
| **Kiểm soát tắc nghẽn**| Có                                  | Không                              |
| **Tốc độ**           | Chậm hơn                             | Nhanh hơn                           |
| **Overhead (Header)**| Cao (Tối thiểu 20 bytes)            | Thấp (Cố định 8 bytes)            |
| **Truyền dữ liệu**   | Dạng luồng (Stream-oriented)         | Dạng thông điệp (Message-oriented) |
| **State**            | Stateful (Duy trì trạng thái K/N)    | Stateless                          |
| **Use Cases**        | Web, Email, FTP, SSH...             | DNS, DHCP, VoIP, Streaming, Games...|

### 4. Lựa Chọn Nào Cho Ứng Dụng Của Bạn?

*   **Chọn TCP khi:**
    *   Độ tin cậy 100% là yêu cầu bắt buộc (không được mất dữ liệu).
    *   Dữ liệu phải được nhận đúng thứ tự.
    *   Ứng dụng không quá nhạy cảm với độ trễ (có thể chấp nhận trễ do handshake, retransmission).
    *   Truyền các file lớn, nội dung web, email.

*   **Chọn UDP khi:**
    *   Tốc độ và độ trễ thấp là ưu tiên hàng đầu.
    *   Mất một vài gói tin có thể chấp nhận được hoặc ứng dụng có cơ chế tự phục hồi/bù đắp.
    *   Thứ tự gói tin không quá quan trọng hoặc ứng dụng tự xử lý.
    *   Cần gửi dữ liệu đến nhiều người nhận cùng lúc (Multicast/Broadcast).
    *   Truyền audio/video thời gian thực, game online, các truy vấn nhanh (DNS).

## Tóm Tắt & Bài Học Tiếp Theo

TCP và UDP là hai trụ cột của Tầng Giao Vận, cung cấp những dịch vụ vận chuyển hoàn toàn khác biệt. TCP mang lại sự tin cậy, thứ tự và kiểm soát với chi phí là độ phức tạp và tốc độ chậm hơn. UDP cung cấp tốc độ và sự đơn giản bằng cách hy sinh độ tin cậy và các cơ chế kiểm soát. Hiểu rõ sự khác biệt này là chìa khóa để lựa chọn giao thức phù hợp cho từng ứng dụng mạng.

Sau khi hiểu rõ về TCP và UDP, chúng ta cần hiểu thêm về cách các ứng dụng "cắm" vào tầng giao vận để gửi và nhận dữ liệu thông qua các Port Number. Bài học tiếp theo (`BaiHoc_14_Ports_Va_Sockets.md`) sẽ làm rõ khái niệm **Ports (Cổng)** và **Sockets (Ổ cắm mạng)** - giao diện lập trình giữa tầng ứng dụng và tầng giao vận. Hẹn gặp bạn ở cổng kết nối nhé!🚪🔌
