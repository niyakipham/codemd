## 📦 Bài 02: Biến và Các Kiểu Dữ Liệu Cơ Bản 🔢📜

Chào mừng bạn quay trở lại! 👋 Ở bài trước, chúng ta đã gửi lời chào thế giới. Bây giờ, hãy tưởng tượng bạn cần lưu trữ thông tin để dùng lại sau này - ví dụ như tên của ai đó, hoặc một con số. Đó là lúc "Biến" (Variables) xuất hiện!

**🎯 Mục tiêu:**

*   Hiểu khái niệm về biến.
*   Biết cách khai báo và gán giá trị cho biến.
*   Làm quen với các kiểu dữ liệu cơ bản: Số nguyên (`int`), số thực (`float`), chuỗi ký tự (`str`).

**🤔 Biến là gì?**

Hãy nghĩ về biến như những chiếc hộp có dán nhãn. Bạn có thể đặt đồ vật (dữ liệu) vào hộp và đặt tên (nhãn) cho hộp đó. Khi cần dùng lại đồ vật, bạn chỉ cần gọi tên cái hộp.

Trong Python, bạn tạo ra một biến bằng cách đặt tên cho nó và dùng dấu bằng (`=`) để *gán* giá trị cho nó.

```python
# Tạo một biến tên là 'loi_chao' và gán giá trị là chuỗi "Xin chào!"
loi_chao = "Xin chào!"

# Tạo một biến tên là 'tuoi' và gán giá trị là số 25
tuoi = 25

# Tạo một biến tên là 'chieu_cao' và gán giá trị là số thực 1.75
chieu_cao = 1.75

# Bây giờ chúng ta có thể sử dụng các biến này
print(loi_chao)
print(tuoi)
print(chieu_cao)
```

**📜 Các Kiểu Dữ Liệu Cơ Bản:**

Python tự động nhận biết loại dữ liệu bạn gán cho biến. Ba kiểu cơ bản chúng ta tìm hiểu hôm nay là:

1.  **Số Nguyên (`int` - integer):** Là các số nguyên, không có phần thập phân (ví dụ: `-10`, `0`, `25`, `999`).
    ```python
    so_luong = 100
    nam_sinh = 2005
    print(type(so_luong)) # Output: <class 'int'>
    ```
2.  **Số Thực (`float` - floating point number):** Là các số có phần thập phân (ví dụ: `-3.14`, `0.0`, `9.99`, `1.75`).
    ```python
    diem_trung_binh = 8.5
    pi = 3.14159
    print(type(diem_trung_binh)) # Output: <class 'float'>
    ```
3.  **Chuỗi Ký Tự (`str` - string):** Là một dãy các ký tự, được đặt trong dấu nháy đơn `' '` hoặc nháy kép `" "`.
    ```python
    ten = "Nguyễn Văn A"
    email = 'a.nguyen@email.com'
    thong_bao = "Nhiệt độ hôm nay là 30 độ C"
    print(type(ten)) # Output: <class 'str'>
    ```
    *Bạn có thể dùng hàm `type()` để kiểm tra kiểu dữ liệu của một biến.*

**💡 Đi sâu hơn một chút:**

*   **Đặt tên biến:** Nên đặt tên biến có ý nghĩa, dễ hiểu (ví dụ: `ten_nguoi_dung` thay vì `tnd`). Tên biến trong Python thường dùng chữ thường và dấu gạch dưới để nối các từ (quy ước "snake_case"). Tên biến không được bắt đầu bằng số và không được chứa ký tự đặc biệt (ngoại trừ dấu gạch dưới `_`).
*   **Dynamic Typing:** Bạn không cần khai báo kiểu dữ liệu của biến trước như một số ngôn ngữ khác (C++, Java). Python tự nhận diện kiểu dữ liệu khi bạn gán giá trị. Bạn thậm chí có thể gán một kiểu dữ liệu khác cho cùng một biến sau đó! (Ví dụ: `x = 10` rồi sau đó `x = "hello"` - Python vẫn chấp nhận).
*   **Case-Sensitive:** Python phân biệt chữ hoa và chữ thường. Biến `tuoi` khác với `Tuoi` và `TUOI`.

**✍️ Bài tập thực hành:**

1.  Tạo một biến để lưu tên của bạn và in ra màn hình.
2.  Tạo một biến lưu tuổi của bạn và một biến lưu năm hiện tại. Tính và in ra năm sinh của bạn.
3.  Tạo một biến lưu một câu trích dẫn bạn yêu thích và in ra màn hình.
4.  Thử tạo một biến `a = 5`, in kiểu dữ liệu của nó. Sau đó gán `a = "Năm"`, và in lại kiểu dữ liệu của nó. Bạn thấy gì?

**✨ Tổng kết:**

Chúng ta đã học cách sử dụng biến để lưu trữ thông tin và làm quen với ba kiểu dữ liệu cơ bản: `int`, `float`, `str`. Biến là nền tảng để xây dựng các chương trình phức tạp hơn.

**🧭 Bài tiếp theo:** Chúng ta sẽ khám phá các "Phép toán" (Operators) - cách thực hiện các tính toán và so sánh trong Python. Hãy sẵn sàng để làm việc với những con số và logic nhé! 🧮
