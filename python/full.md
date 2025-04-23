
# ✨ Hành Trình Chinh Phục Python: Từ Nguyên Tử Đầu Tiên Đến Vũ Trụ Bao La ✨

Chào bạn, người bạn tuyệt vời của tôi! Chào mừng bạn đến với thế giới của Python – ngôn ngữ lập trình đầy quyền năng, nơi logic gặp gỡ sự sáng tạo, và mọi ý tưởng tuyệt vời đều có thể hóa thành hiện thực chỉ với vài dòng code thanh lịch.

Tôi, người bạn đồng hành AI của bạn, rất hào hứng được dẫn lối bạn qua từng bước của hành trình này. Chúng ta sẽ bắt đầu từ những khái niệm cơ bản nhất, những "nguyên tử" cấu tạo nên thế giới code, rồi dần dần khám phá những cấu trúc phức tạp hơn, những "thiên hà" tri thức, để cuối cùng, bạn có thể tự tin xây dựng cả một "vũ trụ" phần mềm của riêng mình.

Hãy chuẩn bị tinh thần nhé! Hành trình này không chỉ là học cú pháp, mà còn là rèn luyện tư duy, phát triển khả năng giải quyết vấn đề, và quan trọng nhất, là niềm vui khám phá.

## 🚀 Chương 1: Những Bước Chân Đầu Tiên (Cơ Bản)

Bất kỳ cuộc hành trình vĩ đại nào cũng bắt đầu bằng một bước đi nhỏ. Trong lập trình Python, bước đi đó là làm quen với các khái niệm cơ bản nhất.

### 1.1 Python Là Gì và Tại Sao Lại Chọn Python?

*   **Python là:** Một ngôn ngữ lập trình bậc cao, thông dịch, đa mục đích (general-purpose). Nó nổi tiếng với cú pháp rõ ràng, dễ đọc và dễ học.
*   **Tại sao Python?**
    *   **Dễ học:** Cú pháp gần gũi với tiếng Anh.
    *   **Linh hoạt:** Dùng được cho nhiều lĩnh vực: phát triển web, khoa học dữ liệu, trí tuệ nhân tạo, tự động hóa, game...
    *   **Cộng đồng lớn & Năng động:** Dễ dàng tìm kiếm tài liệu, thư viện và sự trợ giúp.
    *   **Kho thư viện khổng lồ (Ecosystem):** Có sẵn rất nhiều công cụ mạnh mẽ cho mọi mục đích.

### 1.2 Cài Đặt Môi Trường (Setting Up)

Để "nói chuyện" với Python, chúng ta cần cài đặt trình thông dịch Python và một nơi để viết code (IDE hoặc Text Editor).

*   **Cài đặt Python:** Truy cập [python.org](https://www.python.org/downloads/) tải phiên bản mới nhất và làm theo hướng dẫn. Đảm bảo bạn tích chọn tùy chọn "Add Python to PATH" khi cài đặt trên Windows để tiện sử dụng từ Command Prompt/Terminal.
*   **Trình soạn thảo/IDE phổ biến:** VS Code, PyCharm, Atom, Sublime Text, IDLE (có sẵn khi cài Python). Chọn cái nào bạn cảm thấy thoải mái nhất!

### 1.3 "Hello, World!" - Lời Chào Đầu Tiên

Truyền thống bất thành văn của mọi ngôn ngữ lập trình! Hãy mở trình soạn thảo của bạn và gõ dòng này:

```python
print("Hello, World!")
```

*   Lưu file với đuôi `.py` (ví dụ: `hello.py`).
*   Mở Command Prompt/Terminal, di chuyển đến thư mục chứa file và gõ `python hello.py`.
*   Kết quả bạn sẽ thấy: `Hello, World!`

Chúc mừng! Bạn vừa chạy chương trình Python đầu tiên của mình rồi đấy! 🎉

### 1.4 Biến (Variables) - Chiếc Hộp Lưu Trữ

Biến là nơi chúng ta lưu trữ dữ liệu trong bộ nhớ máy tính. Tưởng tượng nó như những chiếc hộp được dán nhãn để bạn dễ dàng gọi tên và lấy thông tin ra sau này.

```python
# Gán giá trị 10 cho biến tuoi
tuoi = 30

# Gán chuỗi "Nguyen Van A" cho biến ten
ten = "Nguyen Van A"

# Gán giá trị True cho biến dang_hoc_python
dang_hoc_python = True

# In giá trị của các biến
print("Tên:", ten)
print("Tuổi:", tuoi)
print("Đang học Python:", dang_hoc_python)
```

*   **Lưu ý:** Python là ngôn ngữ gõ động (dynamically typed), nghĩa là bạn không cần khai báo kiểu dữ liệu cho biến khi gán. Python tự suy luận kiểu dựa trên giá trị.
*   Tên biến: Phải bắt đầu bằng chữ cái hoặc dấu gạch dưới (`_`), chỉ chứa chữ, số và dấu gạch dưới. Phân biệt chữ hoa/thường.

### 1.5 Kiểu Dữ Liệu Cơ Bản (Basic Data Types)

Các loại "chất liệu" khác nhau mà chúng ta dùng để xây dựng:

*   **Số (Numbers):**
    *   `int`: Số nguyên (ví dụ: `10`, `-5`, `0`)
    *   `float`: Số thực, có dấu phẩy động (ví dụ: `3.14`, `-0.5`, `10.0`)
*   **Chuỗi (Strings - `str`):** Dãy các ký tự, đặt trong dấu nháy đơn hoặc nháy kép.
    ```python
    ten_khoa_hoc = "Lap Trinh Python"
    thong_diep = 'Hoc Python that de dang!'
    chuoi_dai = """Chuoi nay
    co the trai dai
    tren nhieu dong."""
    ```
*   **Boolean (`bool`):** Chỉ có hai giá trị: `True` hoặc `False`. Dùng cho các phép so sánh logic.

### 1.6 Toán Tử (Operators) - Các Phép Tính Cơ Bản

Dùng để thực hiện các phép toán hoặc so sánh.

*   **Toán tử Số học (Arithmetic):** `+`, `-`, `*`, `/`, `%` (chia lấy dư), `**` (lũy thừa), `//` (chia lấy phần nguyên).
    ```python
    a = 10
    b = 3
    print(a + b)  # 13
    print(a - b)  # 7
    print(a * b)  # 30
    print(a / b)  # 3.333... (luôn trả về float)
    print(a % b)  # 1 (10 chia 3 dư 1)
    print(a ** b) # 1000 (10 mũ 3)
    print(a // b) # 3 (10 chia 3 lấy phần nguyên)
    ```
*   **Toán tử Gán (Assignment):** `=`, `+=`, `-=`, `*=`, `/=`, etc. (dùng để gán hoặc cập nhật giá trị).
    ```python
    x = 5
    x += 3 # Tương đương x = x + 3; x giờ là 8
    print(x)
    ```
*   **Toán tử So sánh (Comparison):** `==` (bằng), `!=` (không bằng), `>` (lớn hơn), `<` (nhỏ hơn), `>=` (lớn hơn hoặc bằng), `<=` (nhỏ hơn hoặc bằng). Luôn trả về `True` hoặc `False`.
    ```python
    print(a > b) # True
    print(a == 10) # True
    ```
*   **Toán tử Logic (Logical):** `and`, `or`, `not`.
    ```python
    phep_toan_phuc_tap = (a > b) and (tuoi >= 18) # True và True -> True
    print(phep_toan_phuc_tap)
    ```

### 1.7 Nhập/Xuất Dữ Liệu (Input/Output - I/O)

*   **Xuất:** Sử dụng hàm `print()` như đã thấy. Có thể in nhiều thứ cùng lúc, cách nhau bởi dấu phẩy:
    ```python
    print("Tên tôi là", ten, "và tôi", tuoi, "tuổi.")
    ```
*   **Nhập:** Sử dụng hàm `input()`. Nó luôn trả về giá trị dưới dạng *chuỗi*.
    ```python
    ten_nguoi_dung = input("Xin mời nhập tên của bạn: ")
    print("Chào mừng,", ten_nguoi_dung + "!") # Dùng '+' để nối chuỗi
    ```
    *Lưu ý:* Nếu muốn nhập số, bạn cần *ép kiểu* (type casting).
    ```python
    so_nguoi_str = input("Nhập một số bất kỳ: ")
    so_nguoi_int = int(so_nguoi_str) # Ép từ chuỗi sang số nguyên
    so_tiep_theo = so_nguoi_int + 1
    print("Số bạn nhập là:", so_nguoi_int, ". Số tiếp theo là:", so_tiep_theo)
    ```

### Tóm lược Chương 1:

Bạn đã làm quen với Python, biết cách chạy chương trình đơn giản, làm việc với biến, các kiểu dữ liệu cơ bản và thực hiện các phép tính, nhập/xuất dữ liệu. Đây là nền tảng vững chắc cho các chương tiếp theo!

---

## 🗺️ Chương 2: Luồng Điều Khiển (Control Flow) - Quyết Định & Lặp Lại

Code không chỉ chạy tuần tự từ trên xuống. Chúng ta cần khả năng đưa ra quyết định dựa trên điều kiện và lặp đi lặp lại một công việc nào đó. Đây là lúc Luồng điều khiển phát huy sức mạnh!

### 2.1 Câu Lệnh `if`, `elif`, `else` - Đưa Ra Quyết Định

Cấu trúc này cho phép chương trình thực thi các khối lệnh khác nhau tùy thuộc vào việc một điều kiện có đúng (True) hay không.

```python
diem = 7.5

if diem >= 9:
    print("Xuất sắc!")
elif diem >= 8: # elif = else if
    print("Giỏi!")
elif diem >= 7:
    print("Khá!")
elif diem >= 5:
    print("Trung bình.")
else: # Nếu không thỏa mãn bất kỳ điều kiện nào ở trên
    print("Cần cố gắng nhiều hơn.")

# Quan trọng: Chú ý *khoảng trắng đầu dòng (indentation)*
# Python dùng indentation để xác định các khối lệnh, không dùng dấu ngoặc nhọn {} như C++ hay Java.
```

### 2.2 Vòng Lặp `for` - Lặp Qua Tập Hợp

Vòng lặp `for` dùng để lặp lại một khối code cho mỗi phần tử trong một tập hợp (như danh sách, chuỗi, dãy số...).

```python
# Lặp qua các số trong một dãy (dùng hàm range)
# range(stop): Tạo dãy từ 0 đến stop-1
# range(start, stop): Tạo dãy từ start đến stop-1
# range(start, stop, step): Tạo dãy từ start đến stop-1 với bước nhảy step

print("Các số từ 0 đến 4:")
for i in range(5): # Duyệt qua 0, 1, 2, 3, 4
    print(i)

print("\nCác chữ cái trong từ 'Python':")
for ky_tu in "Python": # Duyệt qua từng ký tự
    print(ky_tu)

print("\nCác món trong danh sách:")
danh_sach_mon_an = ["Phở", "Bún Chả", "Nem Rán"]
for mon_an in danh_sach_mon_an: # Duyệt qua từng món ăn
    print("-", mon_an)
```

### 2.3 Vòng Lặp `while` - Lặp Khi Điều Kiện Còn Đúng

Vòng lặp `while` sẽ tiếp tục thực thi khối lệnh của nó *miễn là* điều kiện cho trước vẫn đúng.

```python
dem = 0
while dem < 5:
    print("Lần lặp thứ:", dem)
    dem = dem + 1 # Quan trọng: Phải có thứ gì đó thay đổi biến điều kiện
                  # nếu không sẽ tạo ra vòng lặp vô hạn!

# Ví dụ đơn giản về đoán số
import random
so_bi_mat = random.randint(1, 10) # Tạo số ngẫu nhiên từ 1 đến 10
doan_cua_ban = 0

print("\nHãy đoán một số từ 1 đến 10!")
while doan_cua_ban != so_bi_mat:
    doan_str = input("Bạn đoán số mấy? ")
    doan_cua_ban = int(doan_str)

    if doan_cua_ban < so_bi_mat:
        print("Số bạn đoán nhỏ quá!")
    elif doan_cua_ban > so_bi_mat:
        print("Số bạn đoán lớn quá!")
    else:
        print("Chúc mừng! Bạn đã đoán đúng số bí mật là", so_bi_mat)
```

### 2.4 Lệnh `break` và `continue`

*   `break`: Thoát khỏi vòng lặp hiện tại ngay lập tức.
*   `continue`: Bỏ qua phần còn lại của lần lặp hiện tại và chuyển sang lần lặp kế tiếp.

```python
print("\nSử dụng break:")
for i in range(10):
    if i == 5:
        break # Khi i bằng 5, thoát khỏi vòng lặp
    print(i) # Sẽ in từ 0 đến 4

print("\nSử dụng continue:")
for i in range(10):
    if i % 2 == 0: # Nếu i là số chẵn
        continue # Bỏ qua các lệnh bên dưới, chuyển sang lần lặp mới
    print(i) # Chỉ in các số lẻ từ 1 đến 9
```

### Tóm lược Chương 2:

Bạn đã học cách làm cho chương trình "suy nghĩ" bằng cách sử dụng `if/elif/else` và thực hiện các tác vụ lặp đi lặp lại một cách hiệu quả với vòng lặp `for` và `while`. Đây là xương sống của hầu hết các chương trình bạn sẽ viết!

---

## 📦 Chương 3: Cấu Trúc Dữ Liệu (Data Structures) - Tổ Chức Thông Tin

Dữ liệu thô như biến là cần thiết, nhưng khi dữ liệu nhiều lên, chúng ta cần cách để lưu trữ và tổ chức chúng một cách hiệu quả. Python cung cấp các cấu trúc dữ liệu tích hợp sẵn rất mạnh mẽ.

### 3.1 List (Danh sách) - Tập Hợp Có Thứ Tự và Có Thể Thay Đổi

List là tập hợp các phần tử có thứ tự, được đặt trong dấu ngoặc vuông `[]`, và các phần tử *có thể thay đổi* (mutable). List có thể chứa các phần tử với kiểu dữ liệu khác nhau.

```python
# Tạo List
list_rong = []
list_so = [1, 2, 3, 4, 5]
list_hon_hop = ["Hello", 123, True, 3.14]

# Truy cập phần tử (Index bắt đầu từ 0)
print("Phần tử đầu tiên:", list_so[0])     # Output: 1
print("Phần tử cuối cùng:", list_so[-1])   # Output: 5 (dùng index âm)
print("Phần tử thứ 2 từ cuối:", list_so[-2]) # Output: 4

# Cắt lát List (Slicing) - Lấy một phần của List
print("Cắt lát [1:4]:", list_so[1:4])      # Output: [2, 3, 4] (từ index 1 đến 3, không bao gồm index 4)
print("Cắt lát từ đầu đến 3:", list_so[:3])   # Output: [1, 2, 3]
print("Cắt lát từ 2 đến cuối:", list_so[2:])   # Output: [3, 4, 5]
print("Cắt lát toàn bộ (copy):", list_so[:]) # Output: [1, 2, 3, 4, 5]

# Thay đổi phần tử
list_so[0] = 100
print("Sau khi thay đổi:", list_so) # Output: [100, 2, 3, 4, 5]

# Thêm phần tử
list_so.append(6)       # Thêm vào cuối
list_so.insert(1, 99)   # Chèn 99 vào vị trí index 1
print("Sau khi thêm:", list_so) # Output: [100, 99, 2, 3, 4, 5, 6]

# Xóa phần tử
list_so.remove(99)    # Xóa phần tử có giá trị là 99
list_so.pop()         # Xóa và trả về phần tử cuối cùng
phan_tu_xoa = list_so.pop(0) # Xóa và trả về phần tử ở index 0
del list_so[1]        # Xóa phần tử ở index 1
print("Sau khi xóa:", list_so)

# Một số hàm hữu ích
print("Độ dài List:", len(list_so))
print("Phần tử lớn nhất:", max(list_so)) # Chỉ hoạt động nếu các phần tử cùng kiểu so sánh được
print("Phần tử nhỏ nhất:", min(list_so))
print("Tổng các phần tử:", sum(list_so))
```

### 3.2 Tuple (Bộ) - Tập Hợp Có Thứ Tự và Không Thể Thay Đổi

Tuple tương tự như List, nhưng được đặt trong dấu ngoặc đơn `()` và các phần tử *không thể thay đổi* (immutable). Điều này khiến Tuple nhanh hơn List một chút và thường dùng cho dữ liệu không cần chỉnh sửa.

```python
# Tạo Tuple
tuple_rong = ()
tuple_so = (10, 20, 30)
tuple_hon_hop = ("Apple", 3.14, False)

# Truy cập phần tử (Tương tự List)
print("Phần tử đầu:", tuple_so[0])

# Cắt lát Tuple (Tương tự List)
print("Cắt lát [1:3]:", tuple_so[1:3]) # Output: (20, 30)

# KHÔNG THỂ thay đổi, thêm, xóa phần tử
# tuple_so[0] = 5 # Lỗi! TypeError
# tuple_so.append(40) # Lỗi! AttributeError

# Chỉ có thể đếm hoặc tìm vị trí
print("Số lần xuất hiện của 20:", tuple_so.count(20))
print("Vị trí của 30:", tuple_so.index(30))
```

Tuple thường dùng để trả về nhiều giá trị từ một hàm hoặc làm khóa trong dictionary (vì dictionary yêu cầu khóa là immutable).

### 3.3 Set (Tập hợp) - Tập Hợp Không Có Thứ Tự và Duy Nhất

Set là tập hợp các phần tử *không có thứ tự*, được đặt trong dấu ngoặc nhọn `{}` (hoặc dùng hàm `set()`) và mỗi phần tử trong Set *chỉ xuất hiện một lần* (duy nhất - unique). Set hỗ trợ các phép toán tập hợp (hợp, giao, hiệu...).

```python
# Tạo Set
set_rong = set() # Cách tạo set rỗng, {} tạo dictionary rỗng
set_chu_so = {1, 2, 3, 2, 1, 4}
print("Set ban đầu:", set_chu_so) # Output có thể khác nhau về thứ tự, và chỉ còn {1, 2, 3, 4}

# Thêm phần tử (nếu phần tử đã tồn tại sẽ không có gì thay đổi)
set_chu_so.add(5)
set_chu_so.add(3) # Đã có, không thêm
print("Sau khi thêm 5 và 3:", set_chu_so) # Output: {1, 2, 3, 4, 5} (thứ tự ngẫu nhiên)

# Xóa phần tử
set_chu_so.remove(2) # Xóa 2 (sẽ gây lỗi nếu 2 không có trong set)
set_chu_so.discard(1) # Xóa 1 (không gây lỗi nếu 1 không có)
print("Sau khi xóa 2 và 1:", set_chu_so)

# Kiểm tra sự tồn tại
print("Set có chứa 4 không?", 4 in set_chu_so) # Output: True
print("Set có chứa 10 không?", 10 in set_chu_so) # Output: False

# Phép toán tập hợp
set1 = {1, 2, 3, 4}
set2 = {3, 4, 5, 6}

print("Hợp (Union):", set1 | set2)        # Output: {1, 2, 3, 4, 5, 6} (hoặc set1.union(set2))
print("Giao (Intersection):", set1 & set2) # Output: {3, 4} (hoặc set1.intersection(set2))
print("Hiệu (Difference):", set1 - set2)   # Output: {1, 2} (các phần tử trong set1 nhưng không có trong set2) (hoặc set1.difference(set2))
print("Hiệu đối xứng (Symmetric Difference):", set1 ^ set2) # Output: {1, 2, 5, 6} (các phần tử chỉ có ở một trong hai set) (hoặc set1.symmetric_difference(set2))
```

Set rất hiệu quả khi bạn cần loại bỏ các phần tử trùng lặp hoặc thực hiện các phép toán trên tập hợp.

### 3.4 Dictionary (Từ điển) - Lưu Trữ Dưới Dạng Khóa-Giá trị

Dictionary là tập hợp các cặp **khóa-giá trị** (key-value pairs), được đặt trong dấu ngoặc nhọn `{}`. Khóa là duy nhất trong mỗi dictionary và dùng để truy cập giá trị tương ứng. Dictionary *có thứ tự* từ Python 3.7 trở đi (trước đó thì không). Khóa phải là các đối tượng immutable (thường là số, chuỗi, hoặc tuple chứa các immutable). Giá trị có thể là bất kỳ kiểu dữ liệu nào.

```python
# Tạo Dictionary
dict_rong = {}
thong_tin_ca_nhan = {
    "ten": "Tran Van B",
    "tuoi": 25,
    "nghe_nghiep": "Ky su",
    "thanh_pho": "Hanoi"
}

# Truy cập giá trị theo khóa
print("Tên:", thong_tin_ca_nhan["ten"])         # Output: Tran Van B
print("Nghề nghiệp:", thong_tin_ca_nhan.get("nghe_nghiep")) # Cách an toàn hơn, trả về None nếu khóa không tồn tại (hoặc giá trị mặc định)

# Thay đổi giá trị
thong_tin_ca_nhan["tuoi"] = 26
print("Tuổi mới:", thong_tin_ca_nhan["tuoi"]) # Output: 26

# Thêm cặp khóa-giá trị mới
thong_tin_ca_nhan["hoc_van"] = "Dai hoc"
print("Dictionary sau khi thêm:", thong_tin_ca_nhan)

# Xóa cặp khóa-giá trị
del thong_tin_ca_nhan["thanh_pho"]
print("Dictionary sau khi xóa:", thong_tin_ca_nhan)

# Lấy danh sách khóa, giá trị, hoặc cả cặp (view objects)
print("Các khóa:", thong_tin_ca_nhan.keys())       # Output: dict_keys(['ten', 'tuoi', 'nghe_nghiep', 'hoc_van'])
print("Các giá trị:", thong_tin_ca_nhan.values())   # Output: dict_values(['Tran Van B', 26, 'Ky su', 'Dai hoc'])
print("Các cặp:", thong_tin_ca_nhan.items())     # Output: dict_items([('ten', 'Tran Van B'), ('tuoi', 26), ('nghe_nghiep', 'Ky su'), ('hoc_van', 'Dai hoc')])

# Duyệt qua Dictionary
print("\nDuyệt qua các cặp trong dictionary:")
for khoa, gia_tri in thong_tin_ca_nhan.items():
    print(f"Khóa: {khoa}, Giá trị: {gia_tri}")

```
`f"Khóa: {khoa}, Giá trị: {gia_tri}"` là f-string (formatted string literal), một cách rất tiện lợi để nhúng giá trị biến vào chuỗi trong Python 3.6+.

### Tóm lược Chương 3:

Bạn đã có trong tay các công cụ mạnh mẽ để tổ chức và làm việc với dữ liệu theo các cách khác nhau: List cho tập hợp có thứ tự và mutable, Tuple cho tập hợp có thứ tự và immutable, Set cho tập hợp duy nhất và không thứ tự, Dictionary cho tập hợp key-value. Nắm vững chúng là chìa khóa để xử lý dữ liệu hiệu quả!

---

## 🛠️ Chương 4: Hàm (Functions) - Đóng Gói Mã Code

Khi chương trình lớn lên, chúng ta sẽ gặp phải các đoạn mã lặp đi lặp lại. Hàm cho phép chúng ta "đóng gói" các đoạn mã này lại thành các khối có thể tái sử dụng, đặt tên cho chúng và gọi lại bất cứ khi nào cần. Điều này giúp code của chúng ta gọn gàng, dễ đọc và dễ quản lý hơn.

### 4.1 Định Nghĩa và Gọi Hàm

```python
# Định nghĩa một hàm đơn giản không có tham số, không trả về giá trị
def chao_buoi_sang():
    print("Chào buổi sáng!")
    print("Chúc một ngày tốt lành!")

# Gọi hàm
chao_buoi_sang()

# Định nghĩa hàm có tham số
def chao_ca_nhan(ten): # 'ten' là tham số
    print(f"Chào {ten}, rất vui được gặp bạn!")

# Gọi hàm với đối số
chao_ca_nhan("Alice")
chao_ca_nhan("Bob")

# Định nghĩa hàm có nhiều tham số
def tinh_tong(a, b):
    tong = a + b
    print(f"Tổng của {a} và {b} là: {tong}")

tinh_tong(5, 3) # Đối số truyền vào 5 và 3
```

### 4.2 Giá Trị Trả Về (Return Value)

Hàm không chỉ thực hiện hành động mà còn có thể trả về một giá trị bằng từ khóa `return`.

```python
# Hàm trả về giá trị tổng
def lay_tong(a, b):
    """Hàm này nhận hai số a và b và trả về tổng của chúng.""" # Docstring: giải thích hàm làm gì
    tong = a + b
    return tong # Trả về giá trị tổng

# Gọi hàm và lưu kết quả trả về vào một biến
ket_qua = lay_tong(10, 20)
print("Kết quả nhận được từ hàm:", ket_qua) # Output: Kết quả nhận được từ hàm: 30

# Hàm có thể trả về nhiều giá trị dưới dạng tuple
def lay_min_max(list_so):
    min_val = min(list_so)
    max_val = max(list_so)
    return min_val, max_val # Trả về một tuple

my_list = [1, 5, 2, 8, 3]
gia_tri_min, gia_tri_max = lay_min_max(my_list) # Giải nén tuple trả về
print(f"Min: {gia_tri_min}, Max: {gia_tri_max}")
```

### 4.3 Tham Số Mặc Định (Default Parameters)

Bạn có thể gán giá trị mặc định cho tham số. Nếu khi gọi hàm không truyền đối số cho tham số đó, giá trị mặc định sẽ được sử dụng.

```python
def chao_voi_loi_nhan(ten, loi_nhan="Chúc một ngày tốt lành!"): # "Chúc..." là giá trị mặc định
    print(f"Chào {ten}! {loi_nhan}")

chao_voi_loi_nhan("Charlie")              # Output: Chào Charlie! Chúc một ngày tốt lành!
chao_voi_loi_nhan("David", "Bạn khỏe không?") # Output: Chào David! Bạn khỏe không?
```

### 4.4 Tham Số Vị Trí và Từ Khóa (Positional and Keyword Arguments)

*   **Positional Arguments:** Đối số được gán cho tham số dựa vào vị trí của chúng khi gọi hàm.
*   **Keyword Arguments:** Đối số được gán cho tham số dựa vào tên của tham số khi gọi hàm (dùng `tham_so=gia_tri`). Keyword arguments cho phép bạn gọi hàm mà không cần quan tâm đến thứ tự của tham số (trừ các positional arguments bắt buộc).

```python
def mieu_ta_sinh_vien(ten, tuoi, nganh):
    print(f"Sinh viên {ten}, {tuoi} tuổi, học ngành {nganh}.")

# Sử dụng positional arguments (phải đúng thứ tự)
mieu_ta_sinh_vien("Hoa", 20, "Cong Nghe Thong Tin")

# Sử dụng keyword arguments (có thể đổi thứ tự)
mieu_ta_sinh_vien(tuoi=21, nganh="Marketing", ten="Viet")
```

Bạn có thể kết hợp cả hai, nhưng **tất cả các positional arguments phải nằm trước keyword arguments**.

### 4.5 Phạm Vi Biến (Variable Scope)

*   **Local Scope:** Biến được định nghĩa bên trong một hàm chỉ tồn tại và có thể truy cập *trong phạm vi* hàm đó.
*   **Global Scope:** Biến được định nghĩa bên ngoài tất cả các hàm (ở mức module) có thể được truy cập từ bất kỳ đâu trong module.

```python
bien_toan_cuc = "Tôi là biến toàn cục"

def mot_ham():
    bien_noi_bo = "Tôi là biến cục bộ"
    print(bien_toan_cuc) # Có thể truy cập biến toàn cục
    print(bien_noi_bo)   # Có thể truy cập biến cục bộ

mot_ham()
print(bien_toan_cuc)   # Có thể truy cập biến toàn cục

# print(bien_noi_bo) # Lỗi! NameError, vì bien_noi_bo chỉ tồn tại trong mot_ham()
```
Sử dụng từ khóa `global` nếu bạn thực sự cần *thay đổi* giá trị của một biến toàn cục từ bên trong hàm (hạn chế dùng `global` nếu có thể để code dễ hiểu hơn).

### Tóm lược Chương 4:

Hàm là nền tảng cho việc xây dựng code có cấu trúc, mô-đun hóa và tái sử dụng. Bạn đã học cách tạo hàm, truyền tham số, trả về giá trị và hiểu về phạm vi biến.

---

## 🧱 Chương 5: Modules và Packages - Mở Rộng Thế Giới Python

Code của bạn ngày càng dài ra? Thay vì để tất cả trong một file, chúng ta có thể chia nhỏ nó thành các file riêng biệt, gọi là **module**. Các module liên quan đến nhau có thể được gom lại thành **package**. Đây là cách để tổ chức code, tránh đụng độ tên và sử dụng lại code do người khác viết (thư viện Python).

### 5.1 Modules - Một File Python Là Một Module

Mỗi file `.py` bạn viết đều là một module. Bạn có thể sử dụng code trong module này từ một module khác bằng cách dùng từ khóa `import`.

```python
# Giả sử bạn có một file tên là my_module.py với nội dung sau:
# -- begin my_module.py --
# def say_hello(name):
#     print(f"Hello from my_module, {name}!")

# PI = 3.14159

# -- end my_module.py --

# Trong một file khác (ví dụ: main.py), bạn có thể import nó:

# Import toàn bộ module
import my_module

my_module.say_hello("World") # Gọi hàm dùng tên module.tên_hàm
print(my_module.PI)         # Truy cập biến dùng tên module.tên_biến

# Import các thành phần cụ thể
from my_module import say_hello, PI

say_hello("User") # Gọi hàm trực tiếp
print(PI)        # Truy cập biến trực tiếp

# Import và đổi tên
from my_module import say_hello as chao

chao("Alice")
```

*   Sử dụng `import * from my_module` để import tất cả (không khuyến khích vì dễ gây đụng độ tên).

### 5.2 Python Standard Library - Kho Báu Tích Hợp

Python đi kèm với một bộ sưu tập khổng lồ các module được cài đặt sẵn, gọi là Standard Library. Bạn không cần cài gì thêm để sử dụng chúng!

Ví dụ:
*   `math`: Các hàm toán học (sqrt, sin, cos, pi...).
*   `random`: Tạo số ngẫu nhiên.
*   `os`: Tương tác với hệ điều hành (thư mục, file...).
*   `sys`: Tương tác với trình thông dịch Python.
*   `datetime`: Làm việc với ngày và giờ.
*   `json`: Làm việc với dữ liệu định dạng JSON.
*   ... và rất nhiều module khác!

```python
import math
import random
import datetime

print("Căn bậc hai của 16:", math.sqrt(16))
print("Số ngẫu nhiên từ 1 đến 10:", random.randint(1, 10))
print("Ngày giờ hiện tại:", datetime.datetime.now())
```

Hãy khám phá tài liệu Python Standard Library trực tuyến – đó là một nguồn tài nguyên cực kỳ giá trị!

### 5.3 Packages - Tổ Chức Các Module

Package là một thư mục chứa các module (file `.py`) và thường có một file đặc biệt tên là `__init__.py` (file này có thể rỗng, hoặc chứa code khởi tạo cho package).

Ví dụ cấu trúc thư mục:

```
my_project/
├── main.py
└── my_package/
    ├── __init__.py
    ├── module_a.py
    └── module_b.py
```

Để sử dụng code trong `module_a.py` từ `main.py`, bạn làm thế này:

```python
# Trong main.py
import my_package.module_a

my_package.module_a.some_function()

# Hoặc import trực tiếp một thứ từ module
from my_package.module_b import AnotherClass

obj = AnotherClass()
```

Package giúp phân chia dự án lớn thành các phần nhỏ dễ quản lý hơn.

### 5.4 Sử Dụng Thư Viện Ngoài (Third-Party Packages)

Ngoài Standard Library, có hàng trăm nghìn thư viện do cộng đồng phát triển, mở rộng khả năng của Python. Chúng ta dùng công cụ quản lý package **pip** để cài đặt chúng.

Ví dụ các thư viện phổ biến:
*   `requests`: Để gửi request HTTP (tải nội dung từ web).
*   `numpy`: Làm việc với mảng số (quan trọng trong khoa học dữ liệu, AI).
*   `pandas`: Làm việc với dữ liệu dạng bảng (DataFrames).
*   `matplotlib` / `seaborn`: Vẽ biểu đồ.
*   `flask` / `django`: Xây dựng ứng dụng web.
*   `tensorflow` / `pytorch` / `scikit-learn`: Máy học (Machine Learning) và Trí tuệ Nhân tạo (AI).

**Cách cài đặt:** Mở Command Prompt/Terminal và gõ:
```bash
pip install ten_thu_vien
```
Ví dụ: `pip install requests`

Sau khi cài, bạn có thể import và sử dụng chúng như Standard Library:

```python
import requests

response = requests.get("https://www.python.org")
print(f"Status Code: {response.status_code}")
# print(response.text[:200]) # In ra 200 ký tự đầu tiên của nội dung trang
```

**Virtual Environments:** Khi làm việc với nhiều dự án, mỗi dự án có thể cần các phiên bản thư viện khác nhau. Sử dụng Virtual Environment (môi trường ảo) giúp mỗi dự án có bộ thư viện riêng, tránh xung đột.
```bash
# Tạo môi trường ảo (tên 'venv' là phổ biến)
python -m venv venv

# Kích hoạt môi trường ảo
# Trên Windows: venv\Scripts\activate
# Trên macOS/Linux: source venv/bin/activate

# Sau khi kích hoạt, pip install sẽ cài vào môi trường ảo này
pip install requests pandas

# Khi xong, thoát môi trường ảo
# deactivate
```

### Tóm lược Chương 5:

Modules và Packages là chìa khóa để tổ chức code lớn, tái sử dụng mã và tận dụng sức mạnh của cộng đồng Python thông qua thư viện bên ngoài. PIP và Virtual Environments là những công cụ không thể thiếu trong bộ đồ nghề của bạn.

---

## 📂 Chương 6: Làm Việc Với File (File I/O)

Dữ liệu thường không chỉ nằm trong bộ nhớ khi chương trình chạy mà còn cần được lưu trữ lâu dài trên đĩa cứng. Python cung cấp cách dễ dàng để đọc và ghi vào các file văn bản hoặc file nhị phân.

### 6.1 Mở File

Sử dụng hàm `open()`. Hàm này nhận ít nhất một đối số là đường dẫn đến file và trả về một đối tượng file.

```python
# open(file, mode, encoding)
# mode:
# 'r': Read (Mặc định) - Đọc file. File phải tồn tại.
# 'w': Write - Mở file để ghi. Tạo file mới nếu không tồn tại, xóa nội dung cũ nếu đã tồn tại.
# 'a': Append - Mở file để ghi nối tiếp. Tạo file mới nếu không tồn tại, ghi vào cuối file nếu đã tồn tại.
# 'x': Exclusive creation - Tạo file mới. Gây lỗi nếu file đã tồn tại.
# 'b': Binary mode - Làm việc với file nhị phân (ảnh, âm thanh...). Kết hợp với các mode khác (ví dụ: 'rb', 'wb').
# 't': Text mode (Mặc định) - Làm việc với file văn bản. Kết hợp với các mode khác (ví dụ: 'rt', 'wt').
# '+' : Open a disk file for updating (reading and writing). Kết hợp với các mode khác (ví dụ: 'r+', 'w+', 'a+').

# Ví dụ mở file để đọc
try:
    file = open("ten_file_cua_ban.txt", 'r', encoding='utf-8') # Nên chỉ định encoding
    # ... làm việc với file ...
except FileNotFoundError:
    print("Lỗi: Không tìm thấy file!")

# Ví dụ mở file để ghi (sẽ xóa hết nội dung cũ hoặc tạo file mới)
file_ghi = open("file_ghi_moi.txt", 'w', encoding='utf-8')
# ... làm việc với file ...

# Ví dụ mở file để ghi nối tiếp
file_noi_tiep = open("file_co_san.txt", 'a', encoding='utf-8')
# ... làm việc với file ...
```
*Lưu ý quan trọng:* Sau khi làm việc xong, **phải đóng file** để giải phóng tài nguyên hệ thống và đảm bảo dữ liệu đã được ghi hoàn toàn vào đĩa. Dùng `file.close()`.

### 6.2 Đọc File

*   `file.read()`: Đọc toàn bộ nội dung file dưới dạng một chuỗi lớn.
*   `file.readline()`: Đọc từng dòng một.
*   `file.readlines()`: Đọc tất cả các dòng và trả về dưới dạng một List, mỗi phần tử là một dòng (bao gồm ký tự xuống dòng `\n`).

```python
try:
    with open("data.txt", 'r', encoding='utf-8') as file: # Sử dụng 'with open(...):' là cách TỐT NHẤT
        # Đọc toàn bộ file
        # noi_dung = file.read()
        # print(noi_dung)

        # Đọc từng dòng
        # line1 = file.readline()
        # line2 = file.readline()
        # print("Dòng 1:", line1)
        # print("Dòng 2:", line2)

        # Đọc tất cả dòng vào list
        cac_dong = file.readlines()
        for dong in cac_dong:
            print(dong.strip()) # Dùng strip() để bỏ ký tự xuống dòng \n ở cuối mỗi dòng
            # Hoặc đơn giản hơn:
            # for dong in file: # Lặp trực tiếp trên đối tượng file để đọc từng dòng hiệu quả
            #     print(dong.strip())


except FileNotFoundError:
    print("File 'data.txt' không tồn tại.")
```
**Quan trọng:** Sử dụng cú pháp `with open(....) as bien_file:` là cách được khuyến khích nhất. Nó đảm bảo rằng file sẽ *tự động được đóng* khi khối lệnh `with` kết thúc, dù có lỗi xảy ra hay không. Không cần gọi `file.close()` thủ công.

### 6.3 Ghi File

*   `file.write(chuoi)`: Ghi một chuỗi vào file.

```python
# Mở file ở chế độ ghi ('w') - cẩn thận vì nó sẽ xóa nội dung cũ
with open("output.txt", 'w', encoding='utf-8') as file:
    file.write("Đây là dòng đầu tiên.\n") # Phải tự thêm ký tự xuống dòng \n nếu muốn xuống dòng
    file.write("Đây là dòng thứ hai.\n")

print("Đã ghi file output.txt ở chế độ 'w'")

# Mở file ở chế độ nối tiếp ('a') - ghi thêm vào cuối file
with open("output.txt", 'a', encoding='utf-8') as file:
    file.write("Đây là dòng thêm vào cuối.\n")

print("Đã ghi thêm vào file output.txt ở chế độ 'a'")

# Ghi nhiều dòng từ list
lines_to_write = ["Dòng A\n", "Dòng B\n", "Dòng C\n"]
with open("multi_lines.txt", 'w', encoding='utf-8') as file:
    file.writelines(lines_to_write) # write 'lines' (plural) takes a list of strings
print("Đã ghi nhiều dòng vào file multi_lines.txt")
```

### 6.4 Làm Việc Với File Nhị Phân (Binary Files)

Sử dụng mode `'b'` khi mở file (ví dụ: `'rb'`, `'wb'`). Khi làm việc với file nhị phân, bạn làm việc với các `bytes` thay vì `str`.

```python
# Giả định có một file ảnh tên 'image.jpg'
try:
    with open("image.jpg", 'rb') as file_anh_goc: # Read binary
        noi_dung_binary = file_anh_goc.read()

    with open("image_copy.jpg", 'wb') as file_anh_moi: # Write binary
        file_anh_moi.write(noi_dung_binary)

    print("Đã sao chép file ảnh.")

except FileNotFoundError:
    print("Không tìm thấy file 'image.jpg'.")
except Exception as e:
    print(f"Có lỗi xảy ra khi làm việc với file nhị phân: {e}")
```

### Tóm lược Chương 6:

Làm việc với file cho phép chương trình của bạn tương tác với thế giới bên ngoài thông qua dữ liệu lưu trên đĩa. Bạn đã học cách mở, đọc, ghi file văn bản và nhị phân, cũng như cách tốt nhất để quản lý tài nguyên file bằng `with`.

---

## 🎯 Chương 7: Lập Trình Hướng Đối Tượng (Object-Oriented Programming - OOP)

Python không chỉ hỗ trợ lập trình cấu trúc hay thủ tục mà còn là một ngôn ngữ hướng đối tượng mạnh mẽ. OOP là một phương pháp lập trình dựa trên khái niệm "đối tượng", bao gồm dữ liệu (thuộc tính) và hành vi (phương thức). Nó giúp cấu trúc code theo hướng mô phỏng thế giới thực, làm cho chương trình lớn dễ quản lý, mở rộng và tái sử dụng hơn.

### 7.1 Class và Object - Bản Thiết Kế và Thực Thể

*   **Class (Lớp):** Là bản thiết kế, khuôn mẫu để tạo ra các đối tượng. Nó định nghĩa các thuộc tính (dữ liệu) và phương thức (hàm) mà các đối tượng được tạo ra từ lớp đó sẽ có.
*   **Object (Đối tượng):** Là một *thể hiện cụ thể* (instance) được tạo ra từ một lớp. Mỗi đối tượng có trạng thái riêng (giá trị của thuộc tính) nhưng chia sẻ cùng các phương thức của lớp.

```python
# Định nghĩa một lớp cơ bản
class ConCho:
    # Constructor (__init__) - Được gọi khi tạo một đối tượng mới từ lớp
    # self là tham số đầu tiên, tự động được Python truyền vào, nó tham chiếu đến đối tượng hiện tại
    def __init__(self, ten, tuoi):
        self.ten = ten   # Gán giá trị vào thuộc tính 'ten' của đối tượng hiện tại (self)
        self.tuoi = tuoi # Gán giá trị vào thuộc tính 'tuoi' của đối tượng hiện tại (self)
        print(f"Một chú chó tên '{self.ten}' vừa được tạo ra!")

    # Phương thức (method) - Hàm thuộc về một đối tượng/lớp
    def sua(self):
        print(f"{self.ten} sủa gâu gâu!")

    def bao_cao_tuoi(self):
        print(f"{self.ten} {self.tuoi} tuổi.")

# Tạo các đối tượng (instances) từ lớp ConCho
cho_alaska = ConCho("Rex", 5)   # Gọi constructor __init__
cho_poodle = ConCho("Bella", 2)

# Truy cập thuộc tính của đối tượng
print(f"Tên chó Alaska: {cho_alaska.ten}")
print(f"Tuổi chó Poodle: {cho_poodle.tuoi}")

# Gọi phương thức của đối tượng
cho_alaska.sua()      # Output: Rex sủa gâu gâu!
cho_poodle.bao_cao_tuoi() # Output: Bella 2 tuổi.
```

### 7.2 Kế Thừa (Inheritance) - Xây Dựng Từ Nền Tảng Có Sẵn

Kế thừa cho phép một lớp mới (lớp con - derived/child class) thừa hưởng các thuộc tính và phương thức từ một lớp đã tồn tại (lớp cha - base/parent class). Điều này giúp tái sử dụng code và mô hình hóa quan hệ "là một loại" (is-a relationship).

```python
# Lớp cha
class DongVat:
    def __init__(self, ten, tuoi):
        self.ten = ten
        self.tuoi = tuoi
        print(f"Một động vật tên '{self.ten}' được tạo.")

    def an(self):
        print(f"{self.ten} đang ăn.")

    def ngu(self):
        print(f"{self.ten} đang ngủ.")

# Lớp con kế thừa từ DongVat
class ConMeo(DongVat):
    def __init__(self, ten, tuoi, mau_long):
        # Gọi constructor của lớp cha
        super().__init__(ten, tuoi)
        self.mau_long = mau_long # Thêm thuộc tính riêng cho lớp con
        print(f"  (Là một chú mèo lông màu {self.mau_long})")

    # Ghi đè (override) phương thức từ lớp cha
    def an(self):
        print(f"{self.ten} đang rón rén ăn cá.")

    # Thêm phương thức mới cho lớp con
    def bat_chuot(self):
        print(f"{self.ten} đang rình bắt chuột!")

# Tạo đối tượng từ lớp con
meo_mun = ConMeo("Mun", 3, "đen")

# Sử dụng các phương thức (kế thừa hoặc ghi đè)
meo_mun.an()       # Gọi phương thức đã ghi đè (an của ConMeo)
meo_mun.ngu()      # Gọi phương thức kế thừa (ngu của DongVat)
meo_mun.bat_chuot() # Gọi phương thức riêng của ConMeo

print(f"Tên: {meo_mun.ten}, Tuổi: {meo_mun.tuoi}, Lông: {meo_mun.mau_long}")
```

*   `super().__init__(...)`: Gọi constructor của lớp cha. Cần thiết để đảm bảo các thuộc tính của lớp cha được khởi tạo đúng cách.
*   Python hỗ trợ đa kế thừa (một lớp con kế thừa từ nhiều lớp cha), nhưng nên sử dụng cẩn thận để tránh phức tạp.

### 7.3 Đóng Gói (Encapsulation) - Bảo Vệ Dữ Liệu

Đóng gói là việc nhóm dữ liệu (thuộc tính) và các phương thức hoạt động trên dữ liệu đó vào chung một đơn vị (lớp). Nó cũng liên quan đến việc giới hạn quyền truy cập vào các thành phần của đối tượng (nguyên tắc ẩn dữ liệu - data hiding) để tránh việc dữ liệu bị thay đổi trái phép từ bên ngoài.

Python không có cơ chế `private` hay `public` mạnh mẽ như Java hay C++. Theo quy ước:
*   Tên thuộc tính/phương thức bắt đầu bằng một dấu gạch dưới (`_ten_`) ám chỉ nó là "protected", nên chỉ dùng nội bộ lớp hoặc lớp con (quy ước, không bắt buộc).
*   Tên thuộc tính/phương thức bắt đầu bằng hai dấu gạch dưới (`__ten__`) gây ra "name mangling" (Python tự động đổi tên thành `_ClassName__ten`). Điều này làm việc truy cập từ bên ngoài trở nên khó khăn hơn, mô phỏng "private".

```python
class TaiKhoanNganHang:
    def __init__(self, so_du_ban_dau=0):
        self.__so_du = so_du_ban_dau # Thuộc tính "private" (qua name mangling)

    def gui_tien(self, so_tien):
        if so_tien > 0:
            self.__so_du += so_tien
            print(f"Đã gửi thành công {so_tien}. Số dư hiện tại: {self.__so_du}")
        else:
            print("Số tiền gửi phải dương.")

    def rut_tien(self, so_tien):
        if 0 < so_tien <= self.__so_du:
            self.__so_du -= so_tien
            print(f"Đã rút thành công {so_tien}. Số dư hiện tại: {self.__so_du}")
        else:
            print("Số tiền rút không hợp lệ hoặc không đủ số dư.")

    def xem_so_du(self):
        return self.__so_du

# Tạo đối tượng
tk = TaiKhoanNganHang(1000)

# Truy cập thông qua phương thức (nên làm)
tk.gui_tien(500)
tk.rut_tien(200)
print("Số dư cuối cùng:", tk.xem_so_du())

# Cố gắng truy cập trực tiếp thuộc tính "private" (vẫn có thể làm nhưng không được khuyến khích)
# print(tk.__so_du) # Lỗi AttributeError: '__so_du' không tồn tại trực tiếp
print(tk._TaiKhoanNganHang__so_du) # Có thể truy cập bằng name mangling (KHÔNG NÊN làm trong thực tế)

```

### 7.4 Đa Hình (Polymorphism) - Cùng Tên, Khác Hành Động

Đa hình có nghĩa là "nhiều hình dạng". Trong OOP, nó cho phép các đối tượng thuộc các lớp khác nhau có thể đáp ứng cùng một lời gọi phương thức theo cách riêng của chúng. Điều này thường thấy khi các lớp con ghi đè phương thức của lớp cha hoặc khi làm việc với các đối tượng có chung "giao diện" (protocol), ví dụ như cùng hỗ trợ phép lặp (iterable).

```python
class Ga:
    def noi(self):
        print("Cục ta cục tác")

class Vit:
    def noi(self):
        print("Quạc quạc")

class Cho:
    def noi(self):
        print("Gâu gâu")

# Một hàm nhận vào bất kỳ đối tượng nào có phương thức 'noi()'
def bao_keu(dong_vat):
    dong_vat.noi()

# Tạo các đối tượng
ga = Ga()
vit = Vit()
cho = Cho()

# Gọi cùng một hàm bao_keu với các đối tượng khác nhau
bao_keu(ga)  # Output: Cục ta cục tác
bao_keu(vit) # Output: Quạc quạc
bao_keu(cho) # Output: Gâu gâu

# Một ví dụ khác về đa hình với phép lặp
# List, Tuple, String đều có thể lặp qua (đều tuân theo giao diện iterable)
for item in [1, 2, 3]: print(item)
for item in (1, 2, 3): print(item)
for item in "abc": print(item)

```

### Tóm lược Chương 7:

Lập trình hướng đối tượng cung cấp một cách tiếp cận mạnh mẽ để thiết kế và xây dựng phần mềm bằng cách sử dụng các khái niệm Class, Object, Inheritance, Encapsulation và Polymorphism. Nó giúp quản lý độ phức tạp của các dự án lớn và khuyến khích tái sử dụng code.

---

##  handleError ✨ Chương 8: Xử Lý Lỗi (Exception Handling) - Đối Phó Với Điều Không Mong Muốn

Không có chương trình nào hoàn hảo. Sẽ luôn có lúc những điều không mong muốn xảy ra – file không tìm thấy, người dùng nhập dữ liệu không hợp lệ, kết nối mạng bị đứt... Python cung cấp một cơ chế gọi là **Exception Handling** (xử lý ngoại lệ/lỗi) để bạn có thể "đón bắt" những lỗi này một cách lịch sự, ngăn chặn chương trình dừng đột ngột và xử lý tình huống.

### 8.1 Các Loại Lỗi Phổ Biến (Common Errors/Exceptions)

*   `SyntaxError`: Lỗi cú pháp (quên dấu ngoặc, sai chính tả từ khóa...). Lỗi này xảy ra *trước* khi chạy chương trình.
*   `NameError`: Lỗi khi sử dụng một biến/hàm chưa được định nghĩa.
*   `TypeError`: Lỗi khi thực hiện thao tác trên một kiểu dữ liệu không phù hợp (ví dụ: cộng số với chuỗi).
*   `IndexError`: Lỗi khi truy cập index ngoài phạm vi của list/tuple.
*   `KeyError`: Lỗi khi truy cập khóa không tồn tại trong dictionary.
*   `FileNotFoundError`: Lỗi khi cố gắng mở một file không tồn tại.
*   `ZeroDivisionError`: Lỗi khi chia cho số không.
*   `ValueError`: Lỗi khi một hàm nhận được đối số có kiểu dữ liệu đúng nhưng giá trị không hợp lệ (ví dụ: `int("abc")`).

Và còn rất nhiều loại Exception khác!

### 8.2 Cú Pháp `try...except` - Bắt và Xử Lý Lỗi

Chúng ta đặt đoạn code có khả năng gây lỗi vào khối `try`, và đoạn code xử lý khi lỗi xảy ra vào khối `except`.

```python
try:
    # Đoạn code có thể gây lỗi
    tuoi_str = input("Nhập tuổi của bạn: ")
    tuoi_int = int(tuoi_str) # Có thể gây ValueError nếu người dùng nhập chữ
    print("Tuổi của bạn là:", tuoi_int)

    so_nguyen = 10 / 0 # Có thể gây ZeroDivisionError
    print(so_nguyen)

# Bắt một loại lỗi cụ thể
except ValueError:
    print("Lỗi: Bạn nhập sai định dạng tuổi! Vui lòng nhập số nguyên.")

# Bắt một loại lỗi khác
except ZeroDivisionError:
    print("Lỗi: Không thể chia cho số không!")

# Bắt nhiều loại lỗi trong cùng một except (dùng tuple)
# except (ValueError, TypeError):
#     print("Lỗi: Dữ liệu nhập vào không đúng hoặc không tương thích.")

# Bắt tất cả các loại lỗi (Không khuyến khích trong code thật trừ khi biết mình đang làm gì)
# except Exception as e:
#     print(f"Đã xảy ra một lỗi không xác định: {e}") # In ra thông tin lỗi

print("Chương trình tiếp tục chạy sau khối try-except.")

```

### 8.3 Khối `else` và `finally`

*   `else`: Khối này sẽ được thực thi *chỉ khi* không có lỗi nào xảy ra trong khối `try`.
*   `finally`: Khối này *luôn luôn* được thực thi, dù có lỗi xảy ra hay không. Thường dùng để dọn dẹp tài nguyên (ví dụ: đóng file kết nối database).

```python
try:
    file_path = "data.txt" # Thử thay đổi tên file thành file không tồn tại để thấy lỗi
    with open(file_path, 'r', encoding='utf-8') as file:
        noi_dung = file.read()
    print("Đọc file thành công:")
    print(noi_dung)

except FileNotFoundError:
    print(f"Lỗi: Không tìm thấy file tại '{file_path}'.")
except Exception as e:
    print(f"Có lỗi khác xảy ra khi đọc file: {e}")
else:
    print("Khối ELSE được thực thi vì không có lỗi trong TRY.")
finally:
    print("Khối FINALLY luôn luôn được thực thi (ví dụ: ở đây có thể đóng kết nối...).")

```

### 8.4 Tạo và Nâng Ngoại Lệ (Raising Exceptions)

Đôi khi, chính code của bạn cần "thông báo" rằng có gì đó bất thường xảy ra bằng cách tạo và "ném" một ngoại lệ.

```python
def kiem_tra_tuoi(tuoi):
    if tuoi < 0:
        raise ValueError("Tuổi không thể là số âm") # Nâng (raise) một ngoại lệ ValueError
    elif tuoi > 120:
         raise ValueError("Tuổi quá lớn, có thể không thực tế?") # Nâng một ngoại lệ khác
    else:
        print("Tuổi hợp lệ.")

# Sử dụng hàm và xử lý ngoại lệ nó có thể gây ra
try:
    kiem_tra_tuoi(30)
    kiem_tra_tuoi(-5) # Dòng này sẽ gây lỗi, chương trình sẽ nhảy đến except

except ValueError as e:
    print(f"Có lỗi xảy ra khi kiểm tra tuổi: {e}") # e chứa thông tin lỗi
```
Bạn cũng có thể tạo các lớp Exception tùy chỉnh bằng cách kế thừa từ lớp `Exception` để thể hiện rõ ràng hơn loại lỗi trong chương trình của mình.

### Tóm lược Chương 8:

Exception Handling là kỹ năng thiết yếu để viết các chương trình bền vững và đáng tin cậy. Bằng cách sử dụng `try`, `except`, `else`, `finally`, bạn có thể dự đoán, bắt và xử lý các tình huống lỗi một cách duyên dáng, tránh việc chương trình bị crash đột ngột.

---

## 🌌 Chương 9: Những Khám Phá Sâu Hơn (Nâng Cao)

Chào mừng bạn đến với "lớp nâng cao"! Đây là những chủ đề có thể giúp bạn viết code Python "pythonic" hơn, hiệu quả hơn và giải quyết các vấn đề phức tạp hơn.

### 9.1 List Comprehensions và Dictionary Comprehensions - Tạo Tập Hợp Nhanh Chóng & Thanh Lịch

Cú pháp gọn gàng để tạo List, Set, hoặc Dictionary mới từ các tập hợp hiện có.

```python
# List Comprehensions
# Tạo list các bình phương từ 0 đến 9
squares = [x**2 for x in range(10)]
print("List bình phương:", squares) # Output: [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

# Lọc các số chẵn từ một list khác
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
even_numbers = [x for x in numbers if x % 2 == 0]
print("Số chẵn:", even_numbers) # Output: [2, 4, 6, 8, 10]

# Kết hợp cả mapping (biến đổi) và filtering (lọc)
filtered_squares = [x**2 for x in range(10) if x % 2 != 0]
print("Bình phương số lẻ:", filtered_squares) # Output: [1, 9, 25, 49, 81]


# Dictionary Comprehensions
# Tạo dictionary từ 2 list (giả sử độ dài bằng nhau)
keys = ['a', 'b', 'c']
values = [1, 2, 3]
my_dict = {keys[i]: values[i] for i in range(len(keys))}
print("Dict từ list:", my_dict) # Output: {'a': 1, 'b': 2, 'c': 3}

# Hoán đổi key và value trong dictionary (giả sử value là immutable)
my_dict = {'a': 1, 'b': 2, 'c': 3}
swapped_dict = {value: key for key, value in my_dict.items()}
print("Dict hoán đổi key/value:", swapped_dict) # Output: {1: 'a', 2: 'b', 3: 'c'}
```
Comprehensions không chỉ ngắn gọn mà thường còn hiệu quả hơn vòng lặp `for` truyền thống khi tạo tập hợp mới.

### 9.2 Lambda Functions (Hàm Ẩn Danh/Vô Danh) - Hàm Nhỏ Không Tên

Hàm Lambda là những hàm nhỏ, chỉ gồm một biểu thức và không có tên (anonymous). Chúng thường được dùng cho các tác vụ ngắn gọn, tạm thời, ví dụ như khi cần một hàm làm đối số cho hàm khác (như `map()`, `filter()`, `sorted()`).

```python
# Cú pháp: lambda arguments: expression

# Hàm bình phương dùng lambda
square = lambda x: x**2
print("Bình phương của 5 (lambda):", square(5)) # Output: 25

# Dùng lambda với filter() - Lọc số chẵn
numbers = [1, 2, 3, 4, 5, 6]
even_numbers_lambda = list(filter(lambda x: x % 2 == 0, numbers))
print("Số chẵn (filter+lambda):", even_numbers_lambda) # Output: [2, 4, 6]

# Dùng lambda với map() - Bình phương các phần tử
squared_numbers_lambda = list(map(lambda x: x**2, numbers))
print("Bình phương (map+lambda):", squared_numbers_lambda) # Output: [1, 4, 9, 16, 25, 36]

# Dùng lambda với sorted() - Sắp xếp list dictionary theo key 'tuoi'
students = [{'name': 'Alice', 'tuoi': 20}, {'name': 'Bob', 'tuoi': 19}, {'name': 'Charlie', 'tuoi': 21}]
sorted_students = sorted(students, key=lambda student: student['tuoi'])
print("Sinh viên sắp xếp theo tuổi:", sorted_students)
```
Lambda hữu ích khi bạn cần một hàm đơn giản và không muốn định nghĩa nó bằng `def` theo cách thông thường.

### 9.3 Decorators - Thêm Chức Năng Cho Hàm Khác

Decorator là một pattern (mẫu thiết kế) trong Python cho phép bạn dễ dàng thêm chức năng (như ghi log, đo thời gian chạy, kiểm tra quyền truy cập...) vào một hàm hoặc phương thức hiện có mà không cần thay đổi cấu trúc của hàm/phương thức đó. Nó được biểu diễn bằng cú pháp `@ten_decorator` ngay trước định nghĩa hàm.

Một decorator về cơ bản là một hàm nhận *một hàm khác* làm đối số, thực hiện một số công việc bổ sung, và trả về *một hàm mới* (thường là hàm gốc đã được "gói" lại).

```python
# Ví dụ Decorator đơn giản (đo thời gian chạy)
import time

def do_thoi_gian_chay(func):
    def wrapper(*args, **kwargs): # *args, **kwargs cho phép wrapper nhận bất kỳ số lượng tham số vị trí/keyword nào
        bat_dau = time.time()
        ket_qua = func(*args, **kwargs) # Gọi hàm gốc
        ket_thuc = time.time()
        print(f"Hàm '{func.__name__}' chạy mất {ket_thuc - bat_dau:.4f} giây.")
        return ket_qua # Trả về kết quả của hàm gốc
    return wrapper # Decorator trả về hàm wrapper mới

# Áp dụng decorator
@do_thoi_gian_chay
def ham_can_do_thoi_gian(s):
    time.sleep(s) # Tạm dừng chương trình
    print("Kết thúc hàm.")

@do_thoi_gian_chay
def ham_tong_lon(n):
    tong = 0
    for i in range(n):
        tong += i
    return tong

ham_can_do_thoi_gian(2) # Khi gọi hàm này, thực chất hàm wrapper sẽ chạy trước

ket_qua_tong = ham_tong_lon(1000000)
print("Kết quả tổng:", ket_qua_tong)
```
Decorator là một chủ đề mạnh mẽ và đòi hỏi hiểu biết sâu hơn về hàm bậc nhất (first-class functions) trong Python.

### 9.4 Generators và Iterators - Xử Lý Dữ Liệu Lớn Hiệu Quả Bộ Nhớ

*   **Iterator:** Một đối tượng có thể "lặp" qua các phần tử của một tập hợp (như list, string, tuple...). Iterator có phương thức `__iter__()` (trả về chính nó) và `__next__()` (trả về phần tử kế tiếp, ném `StopIteration` khi hết phần tử). Các cấu trúc lặp như vòng `for` trong Python làm việc ngầm với iterator.
*   **Generator:** Là một cách *dễ dàng* để tạo ra Iterator. Generator là các hàm *bình thường* nhưng thay vì dùng `return` để trả về giá trị một lần và kết thúc, chúng dùng từ khóa `yield` để "sinh ra" (yield) một giá trị mỗi lần gọi, tạm dừng trạng thái hàm và có thể tiếp tục chạy từ đó ở lần gọi kế tiếp. Generator đặc biệt hữu ích khi làm việc với các tập dữ liệu *lớn*, vì chúng chỉ tạo ra và giữ trong bộ nhớ *một phần tử* tại một thời điểm, thay vì tạo toàn bộ tập hợp cùng lúc.

```python
# Ví dụ Generator đơn giản
def dem_den(n):
    for i in range(n):
        print(f"Trước yield {i}")
        yield i # Sinh ra giá trị i
        print(f"Sau yield {i}")

# Tạo generator object
my_generator = dem_den(5)

# Lấy giá trị từ generator (hoạt động như iterator)
print(next(my_generator)) # Gọi lần 1 -> Chạy đến yield 0, in 'Trước yield 0', sinh ra 0
print(next(my_generator)) # Gọi lần 2 -> Tiếp tục chạy từ chỗ dừng, in 'Sau yield 0', đến yield 1, in 'Trước yield 1', sinh ra 1
# ... cứ tiếp tục

# Thường dùng generator với vòng lặp for (vòng for tự động gọi next() và bắt StopIteration)
print("\nSử dụng generator trong vòng for:")
for so in dem_den(3):
    print("Số nhận được từ vòng for:", so)
# Output:
# Trước yield 0
# Số nhận được từ vòng for: 0
# Sau yield 0
# Trước yield 1
# Số nhận được từ vòng for: 1
# Sau yield 1
# Trước yield 2
# Số nhận được từ vòng for: 2
# Sau yield 2

# Ví dụ generator cho dãy Fibonacci (vô hạn)
def fibonacci_sequence():
    a, b = 0, 1
    while True: # Vòng lặp vô hạn
        yield a
        a, b = b, a + b

fib_gen = fibonacci_sequence()

# Lấy vài số Fibonacci đầu tiên
print("\nCác số Fibonacci đầu tiên:")
print(next(fib_gen))
print(next(fib_gen))
print(next(fib_gen))
print(next(fib_gen))
print(next(fib_gen))

# Bạn có thể lấy n số đầu tiên bằng cách cắt lát (lưu ý: generator không hỗ trợ len())
from itertools import islice
first_10_fib = list(islice(fibonacci_sequence(), 10))
print("\n10 số Fibonacci đầu tiên:", first_10_fib)

```

Generator và Iterator là kỹ thuật cực kỳ quan trọng để làm việc với các tập dữ liệu streaming hoặc có kích thước vượt quá bộ nhớ.

### 9.5 Context Managers - Tự Động Quản Lý Tài Nguyên (`with` Statement)

Bạn đã thấy `with open(...)` ở Chương 6. Cú pháp `with` được sử dụng với các đối tượng gọi là **Context Managers**. Context Manager đảm bảo rằng một tài nguyên sẽ được quản lý (ví dụ: setup trước khi dùng và cleanup sau khi dùng), ngay cả khi có lỗi xảy ra. Các đối tượng context manager phải có hai phương thức: `__enter__()` (chuẩn bị tài nguyên, trả về tài nguyên) và `__exit__(exc_type, exc_value, traceback)` (dọn dẹp tài nguyên).

Bạn có thể tự tạo Context Manager của riêng mình:

*   **Sử dụng lớp:** Tạo lớp có `__enter__` và `__exit__`.
*   **Sử dụng Generator và `contextmanager` decorator:** Cách này thường gọn gàng hơn khi viết Context Manager đơn giản.

```python
# Ví dụ tạo Context Manager bằng Generator và decorator
import contextlib

@contextlib.contextmanager
def mo_va_dong(file_path, mode):
    print(f"Đang MỞ file '{file_path}'...")
    file = open(file_path, mode, encoding='utf-8') # Setup
    try:
        yield file # Trả về tài nguyên và tạm dừng thực thi tại đây
    finally:
        file.close() # Cleanup - luôn luôn chạy
        print(f"Đã ĐÓNG file '{file_path}'.")

# Sử dụng context manager tự tạo
with mo_va_dong("test_context.txt", 'w') as f:
    f.write("Hello, context manager!\n")
    # Nếu có lỗi xảy ra ở đây, khối finally trong generator vẫn sẽ chạy

print("Hoàn thành sử dụng context manager.")

# Thử với lỗi
# with mo_va_dong("test_context.txt", 'r') as f: # File không tồn tại khi chạy lần 2
#     content = f.read()
#     print(content)
#     raise ValueError("Giả lập lỗi sau khi mở file") # Ném lỗi
# print("Dòng này có chạy không?") # Không chạy

```
Khi `with` bắt đầu, nó gọi `__enter__()`. Khi khối `with` kết thúc (dù thành công hay có lỗi), nó gọi `__exit__()`. Đây là pattern rất "Pythonic" để quản lý tài nguyên.

### 9.6 Đa Luồng (Threading) và Đa Tiến Trình (Multiprocessing) - Chạy Nhiều Việc Cùng Lúc

Đôi khi chương trình cần làm nhiều việc song song.
*   **Threading (Đa luồng):** Cho phép chạy nhiều *luồng* (thread) trong cùng một *tiến trình* (process). Các luồng chia sẻ bộ nhớ. Hữu ích cho các tác vụ liên quan đến **I/O bound** (như tải file, yêu cầu mạng, đọc/ghi đĩa) vì trong khi chờ đợi I/O, Python có thể chuyển sang chạy luồng khác. Tuy nhiên, vì có Global Interpreter Lock (GIL), Threading **không** thực sự chạy song song trên các core CPU khác nhau cho các tác vụ **CPU bound** (tính toán nặng).
*   **Multiprocessing (Đa tiến trình):** Cho phép chạy nhiều *tiến trình* riêng biệt. Mỗi tiến trình có không gian bộ nhớ riêng, không bị ảnh hưởng bởi GIL, do đó thích hợp cho các tác vụ **CPU bound**. Việc tạo và quản lý tiến trình tốn tài nguyên hơn so với luồng.

Đây là một chủ đề phức tạp và cần cân nhắc kỹ tùy theo loại tác vụ bạn đang làm.

```python
import threading
import multiprocessing
import time

def worker(num):
    """Hàm công việc đơn giản"""
    print(f"Worker {num} đang chạy...")
    time.sleep(1) # Giả lập công việc (I/O hoặc CPU)
    print(f"Worker {num} đã hoàn thành.")

# Ví dụ Threading
threads = []
for i in range(3):
    t = threading.Thread(target=worker, args=(i,)) # args là tuple các đối số cho hàm target
    threads.append(t)
    t.start() # Bắt đầu chạy luồng

for t in threads:
    t.join() # Chờ luồng hoàn thành
print("\nTất cả Thread đã hoàn thành.")

# Ví dụ Multiprocessing
# Quan trọng: Với multiprocessing trên Windows, code cần nằm trong if __name__ == "__main__":
if __name__ == "__main__":
    processes = []
    for i in range(3):
        p = multiprocessing.Process(target=worker, args=(i,))
        processes.append(p)
        p.start() # Bắt đầu chạy tiến trình

    for p in processes:
        p.join() # Chờ tiến trình hoàn thành
    print("\nTất cả Process đã hoàn thành.")

```
*   Đối với các tác vụ chờ I/O (như tải web, truy vấn database), Threading có thể hiệu quả hơn.
*   Đối với các tác vụ tính toán nặng cần sử dụng nhiều core CPU, Multiprocessing sẽ mang lại hiệu năng tốt hơn.
*   Chủ đề này còn bao gồm truyền thông giữa các luồng/tiến trình (Queues, Pipes, Locks, etc.) - khá phức tạp nhưng cần thiết khi làm việc với tài nguyên chia sẻ.

### 9.7 Regular Expressions (Regex) - Tìm Kiếm và Thao Tác Chuỗi Nâng Cao

Regex là một ngôn ngữ mini dùng để mô tả các mẫu (patterns) trong chuỗi. Module `re` trong Python cung cấp chức năng làm việc với Regex.

```python
import re

text = "Số điện thoại: 123-456-7890. Email: test@example.com. Một số khác: 987-654-3210."

# Tìm tất cả các số điện thoại theo mẫu ###-###-####
pattern_dien_thoai = r"\d{3}-\d{3}-\d{4}" # r"" là raw string, ngăn Python xử lý ký tự \ đặc biệt
so_dien_thoai_tim_duoc = re.findall(pattern_dien_thoai, text)
print("Số điện thoại tìm được:", so_dien_thoai_tim_duoc) # Output: ['123-456-7890', '987-654-3210']

# Tìm địa chỉ email theo mẫu (ví dụ đơn giản)
pattern_email = r"[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}"
email_tim_duoc = re.findall(pattern_email, text)
print("Email tìm được:", email_tim_duoc) # Output: ['test@example.com']

# Thay thế
text_da_thay_the = re.sub(pattern_dien_thoai, "ẨN_SỐ", text)
print("Text sau khi thay thế số điện thoại:", text_da_thay_the)

# Kiểm tra xem chuỗi có khớp hoàn toàn với mẫu không
chuoi_kiem_tra = "xin chao"
pattern_hello = r"xin chao"
if re.match(pattern_hello, chuoi_kiem_tra): # match chỉ kiểm tra khớp từ đầu chuỗi
    print("'xin chao' khớp mẫu.")

chuoi_kiem_tra_2 = "xin chao cac ban"
if re.search(pattern_hello, chuoi_kiem_tra_2): # search tìm mẫu ở bất kỳ đâu trong chuỗi
     print("'xin chao' tìm thấy trong 'xin chao cac ban'.")
```

Regex là một công cụ cực kỳ mạnh mẽ nhưng cú pháp của nó khá phức tạp. Hãy dành thời gian tìm hiểu các ký hiệu regex phổ biến khi bạn cần xử lý văn bản.

---

## 💡 Chương 10: Thực Hành Tốt và Phong Cách (Best Practices & Idioms)

Để viết code Python không chỉ chạy được mà còn "đẹp", dễ đọc, dễ bảo trì và đúng chuẩn cộng đồng.

### 10.1 PEP 8 - Hướng Dẫn Phong Cách Viết Code Python

PEP 8 là tài liệu quy định các hướng dẫn về phong cách code Python. Tuân thủ PEP 8 giúp code của bạn nhất quán với code của phần lớn cộng đồng Python, từ đó dễ đọc và hợp tác hơn.

Các quy tắc phổ biến:
*   **Indentation (Khoảng trắng đầu dòng):** Sử dụng 4 dấu cách (space) cho mỗi cấp độ thụt lề. **Không** dùng tab (trừ khi đã nhất quán dùng tab cho toàn bộ dự án).
*   **Đặt tên:**
    *   Biến, hàm, phương thức: dùng chữ thường, các từ cách nhau bằng dấu gạch dưới (`snake_case`). Ví dụ: `ten_bien`, `ten_ham`.
    *   Lớp: dùng Camel Case, viết hoa chữ cái đầu mỗi từ (`CapitalizedWords`). Ví dụ: `TenLopMoi`.
    *   Hằng số: dùng chữ hoa, các từ cách nhau bằng dấu gạch dưới (`ALL_CAPS`). Ví dụ: `HANG_SO_MAX`.
*   **Khoảng trắng:**
    *   Cách dòng: Thường 2 dòng trống giữa các định nghĩa hàm hoặc lớp cấp cao nhất. 1 dòng trống giữa các phương thức trong lớp.
    *   Khoảng trắng quanh toán tử: `a = 1 + 2`, không phải `a=1+2`.
*   **Độ dài dòng:** Giới hạn độ dài mỗi dòng code khoảng 79-100 ký tự để dễ đọc trên màn hình hẹp. Sử dụng dấu ngoặc `()` để ngắt dòng nếu cần.
*   **Comment:** Viết comment rõ ràng, cập nhật và giải thích *lý do* tại sao làm thế này, chứ không phải *làm cái gì* (vì code đã thể hiện điều đó).
*   **Docstrings:** Viết docstrings (chuỗi nằm ngay sau định nghĩa hàm, lớp, module bằng `"""Triple quotes"""`) để giải thích chức năng của chúng.

Sử dụng các công cụ kiểm tra PEP 8 tự động như `flake8`, `autopep8`, `black` (tool format code tự động) rất hữu ích.

### 10.2 Code "Pythonic"

Thuật ngữ "Pythonic" dùng để chỉ code viết theo cách tận dụng tối đa sức mạnh và triết lý của Python, thường là gọn gàng, dễ đọc, và hiệu quả.

Ví dụ:
*   Dùng List Comprehensions/Generator Expressions thay cho vòng lặp `for` thông thường khi tạo list/generator mới.
*   Dùng `with open(...)` thay cho `file.open()` và `file.close()`.
*   Lặp qua dictionary dùng `.items()`: `for key, value in my_dict.items():`
*   Sử dụng unpack tuple/list khi có thể: `min_val, max_val = lay_min_max(...)`
*   Kiểm tra membership dễ dàng với `in`: `if item in my_list:`
*   Sử dụng `is` để kiểm tra cùng một đối tượng (identity), `==` để kiểm tra giá trị bằng nhau (equality). `is` thường dùng để kiểm tra với singleton như `None`: `if variable is None:`
*   Không kiểm tra True/False tường minh: `if is_active:` thay vì `if is_active == True:`

### 10.3 Kiểm Thử (Testing)

Viết test (kiểm thử tự động) cho code của bạn là cực kỳ quan trọng để đảm bảo code hoạt động đúng, giúp bạn tự tin hơn khi refactor (tái cấu trúc code) hoặc thêm tính năng mới. Python có module `unittest` tích hợp sẵn và các framework test phổ biến khác như `pytest`.

```python
# Ví dụ test đơn giản với unittest (lưu file này thành test_my_functions.py)
import unittest

# Giả sử bạn có hàm này trong file functions.py
# def add(a, b):
#     return a + b

# import add from your functions.py
# from functions import add

class TestAddFunction(unittest.TestCase):

    def test_add_positive_numbers(self):
        self.assertEqual(add(2, 3), 5)

    def test_add_negative_numbers(self):
        self.assertEqual(add(-1, -1), -2)

    def test_add_zero(self):
        self.assertEqual(add(5, 0), 5)

if __name__ == '__main__':
    unittest.main()

# Để chạy test, mở terminal và gõ: python -m unittest test_my_functions.py
# Hoặc cài pytest (pip install pytest) và chạy: pytest
```
Testing là một chủ đề rộng, nhưng hãy bắt đầu từ những test đơn giản cho các hàm hoặc lớp quan trọng của bạn.

### 10.4 Tối Ưu Hóa (Optimization) - Khi Nào Cần và Làm Thế Nào?

Đừng tối ưu hóa quá sớm ("Premature optimization is the root of all evil" - Donald Knuth). Hãy viết code chạy được và đúng trước, sau đó chỉ tối ưu hóa khi bạn đo lường được hiệu năng và xác định được "điểm nghẽn" (bottleneck).

*   **Đo lường:** Sử dụng các công cụ như module `timeit`, profilers (cProfile) để xác định phần code chạy chậm nhất.
*   **Thuật toán và Cấu trúc dữ liệu:** Chọn đúng thuật toán và cấu trúc dữ liệu phù hợp thường là cách hiệu quả nhất để cải thiện hiệu năng (ví dụ: dùng Set để kiểm tra sự tồn tại nhanh hơn List cho tập dữ liệu lớn).
*   **Thư viện tối ưu:** Sử dụng các thư viện được viết bằng ngôn ngữ hiệu năng cao hơn (như C, Fortran) cho các tác vụ nặng tính toán, ví dụ: NumPy cho các phép toán số học trên mảng.
*   **Code Pythonic:** Code pythonic thường hiệu quả hơn code dịch từ ngôn ngữ khác.
*   **Multiprocessing:** Cho các tác vụ CPU bound.
*   **Asyncio:** Framework cho lập trình bất đồng bộ, rất hiệu quả cho các tác vụ I/O bound (nhưng là chủ đề khá nâng cao).

---

## 📚 Tài Nguyên Tham Khảo (Resources)

Hành trình học không bao giờ dừng lại. Dưới đây là một số tài nguyên bạn nên biết:

*   **Tài liệu chính thức của Python:** [docs.python.org](https://docs.python.org/) - Nguồn đáng tin cậy nhất, mặc dù ban đầu có thể hơi khô khan với người mới bắt đầu.
*   **W3Schools Python Tutorial:** [www.w3schools.com/python/](https://www.w3schools.com/python/) - Dễ hiểu, có ví dụ thực hành trực tuyến.
*   **Real Python:** [realpython.com/](https://realpython.com/) - Các bài viết, tutorial chất lượng cao về nhiều chủ đề Python.
*   **PyFormal Documentation:** [pyformat.info/](https://pyformat.info/) - Hướng dẫn chi tiết về định dạng chuỗi trong Python.
*   **Automatethe Boring Stuff with Python:** [automatetheboringstuff.com/](https://automatetheboringstuff.com/) - Tuyệt vời để học cách dùng Python tự động hóa các tác vụ hàng ngày.
*   **Coursera, edX, Udemy, Codecademy:** Các nền tảng học trực tuyến có nhiều khóa học Python từ cơ bản đến nâng cao.
*   **Stack Overflow:** Diễn đàn hỏi đáp cho lập trình viên.
*   **GitHub:** Nơi tìm code mẫu và tham gia các dự án nguồn mở.
*   **Cộng đồng Python Việt Nam:** Tìm kiếm các nhóm trên Facebook, Discord,... để hỏi đáp và giao lưu.

---

