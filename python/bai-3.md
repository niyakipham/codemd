## ⚙️ Bài 03: Các Loại Toán Tử (Operators) ➕➖✖️➗

Yo! Chào mừng trở lại võ đài Python! 😉 Bài trước chúng ta đã biết cách lưu trữ dữ liệu vào biến. Bây giờ là lúc học cách "thao tác" trên dữ liệu đó bằng các *Toán tử* (Operators).

**🎯 Mục tiêu:**

*   Hiểu và sử dụng các toán tử số học.
*   Hiểu và sử dụng các toán tử so sánh.
*   Hiểu và sử dụng các toán tử logic.
*   Biết về toán tử gán.

**1. Toán Tử Số Học (Arithmetic Operators):**

Đây là những toán tử dùng để thực hiện các phép tính toán học cơ bản.

| Toán tử | Ý nghĩa                   | Ví dụ (`a=10`, `b=3`) | Kết quả |
| :------ | :------------------------ | :------------------- | :------ |
| `+`     | Cộng                      | `a + b`              | `13`    |
| `-`     | Trừ                       | `a - b`              | `7`     |
| `*`     | Nhân                      | `a * b`              | `30`    |
| `/`     | Chia (luôn ra số thực)    | `a / b`              | `3.333` |
| `//`    | Chia lấy phần nguyên       | `a // b`             | `3`     |
| `%`     | Chia lấy phần dư (modulo) | `a % b`              | `1`     |
| `**`    | Lũy thừa                  | `a ** b`             | `1000`  |

```python
x = 15
y = 4

print(f"{x} + {y} =", x + y)
print(f"{x} / {y} =", x / y)       # Phép chia thông thường
print(f"{x} // {y} =", x // y)     # Chia lấy nguyên
print(f"{x} % {y} =", x % y)       # Chia lấy dư
print(f"2 ** 5 =", 2 ** 5)       # 2 mũ 5
```
*Lưu ý: `f"{biến}"` là một cách định dạng chuỗi gọi là f-string, rất tiện lợi!*

**2. Toán Tử So Sánh (Comparison Operators):**

Dùng để so sánh hai giá trị, kết quả luôn là `True` (Đúng) hoặc `False` (Sai). Đây là nền tảng của việc ra quyết định trong lập trình.

| Toán tử | Ý nghĩa            | Ví dụ (`a=10`, `b=3`) | Kết quả |
| :------ | :----------------- | :------------------- | :------ |
| `==`    | Bằng              | `a == b`             | `False` |
| `!=`    | Không bằng        | `a != b`             | `True`  |
| `>`     | Lớn hơn           | `a > b`              | `True`  |
| `<`     | Nhỏ hơn           | `a < b`              | `False` |
| `>=`    | Lớn hơn hoặc bằng | `a >= 10`            | `True`  |
| `<=`    | Nhỏ hơn hoặc bằng | `b <= 3`             | `True`  |

```python
diem_thi = 7.5
diem_dau = 5.0

print(f"Điểm thi có lớn hơn điểm đậu không? {diem_thi > diem_dau}")
print(f"Điểm thi có bằng 10 không? {diem_thi == 10.0}")
```

**3. Toán Tử Logic (Logical Operators):**

Dùng để kết hợp các biểu thức điều kiện (thường là kết quả của toán tử so sánh).

| Toán tử | Ý nghĩa                                               | Ví dụ (`x=True`, `y=False`) | Kết quả |
| :------ | :---------------------------------------------------- | :-------------------------- | :------ |
| `and`   | Trả về `True` nếu CẢ HAI vế đều `True`                 | `x and y`                   | `False` |
| `or`    | Trả về `True` nếu ÍT NHẤT MỘT vế là `True`             | `x or y`                    | `True`  |
| `not`   | Đảo ngược giá trị logic (True thành False, vv.)        | `not x`                     | `False` |

```python
tuoi = 20
co_giay_phep = True

du_dieu_kien_lai_xe = (tuoi >= 18) and co_giay_phep
print(f"Đủ điều kiện lái xe? {du_dieu_kien_lai_xe}")

troi_dep = True
cuoi_tuan = False
di_choi = troi_dep or cuoi_tuan
print(f"Đi chơi không? {di_choi}")

ban_ron = True
print(f"Có rảnh không? {not ban_ron}")
```

**4. Toán Tử Gán (Assignment Operators):**

Toán tử cơ bản nhất là dấu bằng (`=`). Ngoài ra còn có các toán tử gán kết hợp để viết code ngắn gọn hơn.

| Toán tử | Tương đương với | Ví dụ (`c = 5`) | Sau phép gán, `c` bằng |
| :------ | :------------- | :-------------- | :---------------------- |
| `+=`    | `c = c + 2`    | `c += 2`        | `7`                     |
| `-=`    | `c = c - 1`    | `c -= 1`        | `4`                     |
| `*=`    | `c = c * 3`    | `c *= 3`        | `15`                    |
| `/=`    | `c = c / 2`    | `c /= 2`        | `2.5`                   |
| `//=`   | `c = c // 2`   | `c //= 2`       | `2`                     |
| `%=`    | `c = c % 3`    | `c %= 3`        | `2`                     |
| `**=`   | `c = c ** 2`   | `c **= 2`       | `25`                    |

**💡 Đi sâu hơn một chút:**

*   **Độ ưu tiên của toán tử:** Giống như trong toán học, Python có quy tắc về thứ tự thực hiện các phép toán (ví dụ: nhân/chia trước cộng/trừ, `not` trước `and` rồi đến `or`). Bạn có thể dùng dấu ngoặc đơn `()` để thay đổi hoặc làm rõ thứ tự ưu tiên.
*   **Short-Circuiting:** Với `and`, nếu vế trái là `False`, Python sẽ không cần kiểm tra vế phải nữa (vì kết quả chắc chắn là `False`). Với `or`, nếu vế trái là `True`, Python không cần kiểm tra vế phải (vì kết quả chắc chắn là `True`). Điều này đôi khi hữu ích để tránh lỗi hoặc tối ưu hiệu năng.

**✍️ Bài tập thực hành:**

1.  Tính diện tích hình chữ nhật có chiều dài 10, chiều rộng 5.
2.  Kiểm tra xem số 20 có chia hết cho 3 hay không (dùng toán tử modulo `%`).
3.  Một học sinh có điểm Toán là 8, điểm Văn là 7. Kiểm tra xem học sinh đó có đủ điều kiện là học sinh giỏi không (điểm trung bình >= 8 HOẶC cả hai môn >= 6.5 VÀ không có môn nào dưới 5). Bạn thử kết hợp các toán tử xem sao nhé!
4.  Sử dụng toán tử gán kết hợp `+=` để cộng thêm 10 vào một biến có giá trị ban đầu là 5.

**✨ Tổng kết:**

Các toán tử là công cụ thiết yếu để thực hiện tính toán, so sánh và kết hợp các điều kiện logic. Nắm vững chúng là bạn đã có trong tay sức mạnh để "ra lệnh" cho máy tính thực hiện nhiều tác vụ phức tạp hơn rồi đấy!

**🧭 Bài tiếp theo:** Chúng ta sẽ tìm hiểu về kiểu dữ liệu `Boolean` (chính là `True`/`False` mà chúng ta vừa thấy) và cách sử dụng câu lệnh `if` để máy tính đưa ra quyết định dựa trên các điều kiện. Logic sắp bắt đầu! 🤔
