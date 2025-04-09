# Bài Học 09: Subnetting (Chia Mạng Con) - Nghệ Thuật Phân Chia Địa Chỉ IP ✂️📊

## Mục Tiêu Bài Học

*   Hiểu rõ **tại sao cần phải chia mạng con (Subnetting)**.
*   Nắm vững khái niệm "mượn bit" từ phần Host ID để tạo Subnet ID.
*   Hiểu cách **Subnet Mask tùy chỉnh (Custom Subnet Mask)** hoạt động.
*   Thực hành các bước tính toán khi chia mạng con:
    *   Xác định số lượng Subnet tạo ra.
    *   Xác định số lượng Host/Subnet.
    *   Tìm Network Address, dải địa chỉ Host hợp lệ, và Broadcast Address cho từng Subnet.
*   Làm quen với **ký pháp CIDR (Classless Inter-Domain Routing)** trong Subnetting.
*   Hiểu sơ lược về **VLSM (Variable Length Subnet Mask)** - Mặt nạ mạng con có độ dài thay đổi.

## Nội Dung Chi Tiết

### 1. Tại Sao Cần Chia Mạng Con (Subnetting)?

Hãy tưởng tượng bạn được cấp một dải địa chỉ lớn thuộc Class B, ví dụ: `172.16.0.0 /16`. Dải này cho phép bạn có tới 65,534 thiết bị trong cùng một mạng. Nếu bạn chỉ có vài trăm hoặc vài nghìn thiết bị trong tổ chức của mình, việc sử dụng cả dải địa chỉ lớn này cho một mạng duy nhất sẽ gây ra nhiều vấn đề:

*   **Lãng phí địa chỉ IP:** Rất nhiều địa chỉ không được sử dụng.
*   **Hiệu suất mạng kém:** Tạo ra một **Broadcast Domain (Miền quảng bá)** cực lớn. Bất kỳ một bản tin broadcast nào (ví dụ: ARP Request) cũng sẽ bị gửi đến tất cả 65,534 thiết bị, gây tắc nghẽn và làm chậm mạng.
*   **Khó quản lý:** Quản lý an ninh, phân chia phòng ban, xử lý sự cố trên một mạng lớn duy nhất rất phức tạp.
*   **Kém linh hoạt:** Khó khăn trong việc áp dụng các chính sách bảo mật hoặc QoS khác nhau cho từng nhóm người dùng/thiết bị.

**Giải pháp:** **Subnetting (Chia mạng con)!**

Subnetting là kỹ thuật **chia một dải địa chỉ mạng lớn (Network ID) thành nhiều dải địa chỉ mạng con (Subnet ID) nhỏ hơn**. Mỗi Subnet sẽ là một **Broadcast Domain riêng biệt**, giúp giải quyết các vấn đề trên:

*   **Tiết kiệm địa chỉ IP:** Sử dụng địa chỉ hiệu quả hơn.
*   **Tăng hiệu suất mạng:** Giảm kích thước của Broadcast Domain, hạn chế lưu lượng broadcast không cần thiết.
*   **Dễ quản lý và tăng cường bảo mật:** Có thể nhóm các thiết bị theo phòng ban, chức năng hoặc vị trí địa lý vào các Subnet riêng. Áp dụng các chính sách truy cập (Access Control List - ACL) giữa các Subnet dễ dàng hơn.
*   **Tăng tính linh hoạt:** Tổ chức cấu trúc mạng logic hơn.

### 2. Khái Niệm "Mượn Bit" và Subnet Mask Tùy Chỉnh

Subnetting hoạt động dựa trên nguyên tắc **"mượn" một số bit từ phần Host ID của địa chỉ IP gốc để tạo thành phần Subnet ID mới.**

*   Địa chỉ IP bây giờ được chia thành 3 phần: **Network ID** (giữ nguyên) | **Subnet ID** (các bit mượn) | **Host ID** (các bit còn lại).
*   Để hệ thống (máy tính, router) biết được bao nhiêu bit đã được mượn làm Subnet ID, chúng ta sử dụng một **Subnet Mask tùy chỉnh (Custom Subnet Mask)**. Subnet Mask tùy chỉnh sẽ có nhiều bit `1` hơn so với Subnet Mask mặc định của lớp địa chỉ đó. Các bit `1` bổ sung này chính là các bit đã được mượn.

**Ví dụ:**

*   Địa chỉ mạng gốc: `192.168.1.0 /24` (Class C)
    *   Network ID: `192.168.1` (24 bit)
    *   Host ID: 8 bit cuối (cho phép 2⁸-2 = 254 host)
    *   Subnet Mask mặc định: `255.255.255.0` (Nhị phân: `11111111.11111111.11111111.00000000`)
*   **Quyết định:** Chúng ta muốn chia mạng này thành nhiều Subnet nhỏ hơn. Giả sử chúng ta **mượn 3 bit** từ phần Host ID để làm Subnet ID.
*   **Subnet Mask tùy chỉnh:** Chúng ta "bật" 3 bit đầu tiên của phần Host ID trong Subnet Mask lên thành `1`.
    *   Subnet Mask mới (nhị phân): `11111111.11111111.11111111.11100000`
    *   Subnet Mask mới (thập phân): `255.255.255.224`
    *   Ký pháp CIDR mới: `/27` (vì có 24 + 3 = 27 bit 1)
*   **Cấu trúc mới:**
    *   Network ID: `192.168.1` (24 bit - không đổi)
    *   Subnet ID: 3 bit tiếp theo (các bit mượn)
    *   Host ID: 5 bit cuối (8 - 3 = 5 bit còn lại)

### 3. Các Bước Tính Toán Khi Chia Subnet

Giả sử chúng ta có bài toán: Chia mạng `192.168.1.0 /24` bằng cách mượn 3 bit làm Subnet. (Subnet Mask mới là `255.255.255.224` hay `/27`).

**Bước 1: Xác định số lượng Subnet tạo ra**

*   Số bit mượn (S) = 3
*   Số lượng Subnet = 2ˢ = 2³ = **8 Subnet**

**Bước 2: Xác định số lượng Host/Subnet**

*   Số bit còn lại cho Host ID (H) = 8 (Host ID gốc) - 3 (bit mượn) = 5
*   Số lượng địa chỉ IP mỗi Subnet = 2ᴴ = 2⁵ = 32 địa chỉ (tính cả Network và Broadcast)
*   Số lượng Host hợp lệ mỗi Subnet = 2ᴴ - 2 = 2⁵ - 2 = 30 Host

**Bước 3: Liệt kê các Subnet (Tìm Network Address, Dải Host, Broadcast Address)**

Chúng ta cần tìm Network Address, dải IP Host hợp lệ (First Host - Last Host), và Broadcast Address cho từng Subnet trong số 8 Subnet đã tạo.

*   **Cách tìm Network Address của các Subnet:** Network Address của Subnet đầu tiên chính là Network Address của mạng gốc (`192.168.1.0`). Network Address của các Subnet tiếp theo được tính bằng cách cộng thêm "bước nhảy".
*   **Bước nhảy (Increment/Block Size):** Là giá trị của bit cuối cùng được mượn trong Subnet Mask, tính ở octet mà việc mượn bit xảy ra. Hoặc cách tính đơn giản: `Bước nhảy = 256 - Giá trị octet của Subnet Mask tùy chỉnh` (tại octet có thay đổi).
    *   Trong ví dụ: Mượn bit ở octet thứ 4. Giá trị octet 4 của Mask là 224.
    *   Bước nhảy = 256 - 224 = **32**.
    *   Điều này có nghĩa là Network Address của các Subnet sẽ cách nhau 32 đơn vị ở octet thứ 4.

*   **Liệt kê:**
    *   **Subnet 1:**
        *   Network Address: `192.168.1.0` (Subnet đầu tiên)
        *   First Host: `192.168.1.1` (Network Address + 1)
        *   Last Host: `192.168.1.30` (Broadcast Address - 1)
        *   Broadcast Address: `192.168.1.31` (Network Address tiếp theo - 1)
    *   **Subnet 2:**
        *   Network Address: `192.168.1.32` (`192.168.1.0 + 32`)
        *   First Host: `192.168.1.33`
        *   Last Host: `192.168.1.62`
        *   Broadcast Address: `192.168.1.63`
    *   **Subnet 3:**
        *   Network Address: `192.168.1.64` (`192.168.1.32 + 32`)
        *   First Host: `192.168.1.65`
        *   Last Host: `192.168.1.94`
        *   Broadcast Address: `192.168.1.95`
    *   **Subnet 4:**
        *   Network Address: `192.168.1.96` (`192.168.1.64 + 32`)
        *   First Host: `192.168.1.97`
        *   Last Host: `192.168.1.126`
        *   Broadcast Address: `192.168.1.127`
    *   **Subnet 5:**
        *   Network Address: `192.168.1.128` (`192.168.1.96 + 32`)
        *   First Host: `192.168.1.129`
        *   Last Host: `192.168.1.158`
        *   Broadcast Address: `192.168.1.159`
    *   **Subnet 6:**
        *   Network Address: `192.168.1.160` (`192.168.1.128 + 32`)
        *   First Host: `192.168.1.161`
        *   Last Host: `192.168.1.190`
        *   Broadcast Address: `192.168.1.191`
    *   **Subnet 7:**
        *   Network Address: `192.168.1.192` (`192.168.1.160 + 32`)
        *   First Host: `192.168.1.193`
        *   Last Host: `192.168.1.222`
        *   Broadcast Address: `192.168.1.223`
    *   **Subnet 8:**
        *   Network Address: `192.168.1.224` (`192.168.1.192 + 32`)
        *   First Host: `192.168.1.225`
        *   Last Host: `192.168.1.254`
        *   Broadcast Address: `192.168.1.255`

Như vậy, từ mạng `/24` ban đầu, chúng ta đã tạo ra 8 mạng `/27` nhỏ hơn, mỗi mạng có 30 Host khả dụng.

### 4. Ký Pháp CIDR (Classless Inter-Domain Routing)

Như đã đề cập, CIDR là cách biểu diễn địa chỉ mạng kèm theo độ dài của Subnet Mask bằng dấu `/`. Ví dụ: `192.168.1.64 /27`.

*   CIDR giúp loại bỏ sự phụ thuộc vào các lớp địa chỉ (Classful A, B, C). Bất kỳ dải địa chỉ nào cũng có thể được mô tả bằng tiền tố (prefix) và độ dài mask.
*   Linh hoạt hơn rất nhiều trong việc cấp phát và quản lý địa chỉ IP. Subnetting thực chất là một ứng dụng của CIDR.

### 5. VLSM (Variable Length Subnet Mask) - Mặt nạ mạng con có độ dài thay đổi

Trong ví dụ trên, chúng ta chia mạng gốc thành 8 Subnet có kích thước **bằng nhau** (cùng là /27, 30 Host/Subnet). Tuy nhiên, trong thực tế, các mạng con có thể có nhu cầu số lượng Host khác nhau (ví dụ: phòng Kế toán cần 20 host, phòng Kỹ thuật cần 50 host, kết nối điểm-điểm giữa 2 router chỉ cần 2 host).

**VLSM** là kỹ thuật cho phép **áp dụng các Subnet Mask khác nhau (độ dài khác nhau)** cho các Subnet khác nhau được chia ra từ cùng một mạng gốc. Điều này giúp:

*   **Tiết kiệm địa chỉ IP tối đa:** Cấp phát Subnet có kích thước phù hợp chính xác với nhu cầu của từng mạng con, tránh lãng phí.
*   **Thiết kế mạng hiệu quả hơn.**

**Nguyên tắc cơ bản:** Chia Subnet lớn nhất trước, sau đó lấy một trong các Subnet chưa sử dụng để tiếp tục chia nhỏ hơn nữa với Mask dài hơn.

*Ví dụ (Sơ lược):* Từ mạng `192.168.1.0 /24`:
1. Chia thành `/27` (30 host/subnet) để cấp cho phòng Kỹ thuật (cần 50 - à, ví dụ này không ổn, /27 không đủ 50 host, cần /26 = 62 host. Giả sử chia /26 trước).
   *   Subnet 1: `192.168.1.0 /26` (0-63) -> Dùng cho Kỹ thuật (62 host)
   *   Subnet 2: `192.168.1.64 /26` (64-127)
   *   Subnet 3: `192.168.1.128 /26` (128-191)
   *   Subnet 4: `192.168.1.192 /26` (192-255)
2. Lấy Subnet 2 (`192.168.1.64 /26`) tiếp tục chia thành `/28` (14 host/subnet) để cấp cho phòng Kế toán (cần 20 - vẫn chưa đủ, cần /27. Ví dụ này hơi lủng củng, ý tưởng là lấy 1 subnet đã chia để chia nhỏ tiếp).
   *   Subnet 2.1: `192.168.1.64 /28` (64-79) -> Cấp cho phòng khác cần ít hơn
   *   Subnet 2.2: `192.168.1.80 /28` (80-95) -> Cấp cho Kế toán (14 host - OK nếu nhu cầu là 14)
   *   ...
3. Lấy một Subnet khác (ví dụ Subnet 4) chia thành các `/30` (2 host/subnet) cho các kết nối point-to-point giữa các router.
   *   Subnet 4.1: `192.168.1.192 /30` (192-195) -> Dùng cho kết nối P2P 1
   *   Subnet 4.2: `192.168.1.196 /30` (196-199) -> Dùng cho kết nối P2P 2
   *   ...

VLSM đòi hỏi kỹ năng tính toán và lập kế hoạch cẩn thận hơn.

## Tóm Tắt & Bài Học Tiếp Theo

Subnetting là một kỹ năng thiết yếu cho quản trị viên mạng, giúp tối ưu hóa việc sử dụng địa chỉ IP, cải thiện hiệu suất và tăng cường bảo mật bằng cách chia nhỏ các miền quảng bá. Chúng ta đã học cách "mượn bit", tính toán số Subnet, số Host, và xác định các thông tin quan trọng cho từng Subnet. CIDR và VLSM là những khái niệm nâng cao hơn giúp việc chia Subnet trở nên linh hoạt và hiệu quả.

Sau khi đã thành thạo việc chia địa chỉ, câu hỏi tiếp theo là: Làm thế nào để các Packet biết đường đi giữa các Subnet này và các mạng khác trên thế giới? Bài học tiếp theo (`BaiHoc_10_DinhTuyen_Routing.md`) sẽ đi sâu vào **Quá trình Định tuyến (Routing)** - trái tim của Tầng Mạng. Chúng ta sẽ tìm hiểu cách Router xây dựng bảng định tuyến và đưa ra quyết định chuyển tiếp Packet. Hẹn gặp bạn trên những "ngã rẽ" của mạng! 🛣️🧭
