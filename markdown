# Khóa Học Markdown Toàn Diện: Từ Cơ Bản Đến Nâng Cao

*Chào mừng bạn đến với hành trình khám phá vẻ đẹp và sự tiện lợi của Markdown!* 👋

Markdown không phải là một ngôn ngữ lập trình phức tạp, mà là một ngôn ngữ đánh dấu văn bản rất nhẹ nhàng và dễ đọc. Mục tiêu của nó là cho phép mọi người viết nội dung dễ dàng bằng định dạng văn bản thuần túy, sau đó có thể chuyển đổi nó thành HTML (hoặc các định dạng khác) một cách nhanh chóng.

Nó được sử dụng rộng rãi trong:
*   **Github và các nền tảng quản lý mã nguồn:** Để viết file README, bình luận code.
*   **Blog và hệ thống quản lý nội dung (CMS):** Nhiều nền tảng hỗ trợ viết bài bằng Markdown.
*   **Ghi chú:** Các ứng dụng ghi chú hiện đại như Obsidian, Notion, Typora... sử dụng Markdown làm cốt lõi.
*   **Tài liệu:** Viết tài liệu kỹ thuật, sách, bài báo...

Hãy cùng đi sâu vào từng phần nhé!

## Phần 1: Kiến Thức Cơ Bản Về Markdown

Phần này bao gồm những cú pháp Markdown "xương sống", mà bạn sẽ gặp hàng ngày. Nắm vững chúng là bạn đã có thể định dạng được hầu hết các loại văn bản cơ bản rồi đấy!

---

### 1.1. Tiêu Đề (Headings)

Tiêu đề giúp cấu trúc văn bản và phân chia nội dung. Markdown sử dụng dấu thăng (`#`) để tạo tiêu đề.

*   **Cách dùng:** Số lượng dấu `#` từ 1 đến 6 tương ứng với các cấp độ tiêu đề `<h1>` đến `<h6>` trong HTML.
*   **Lưu ý:** Luôn có khoảng trắng sau dấu `#`.

```markdown
# Đây là Tiêu Đề Cấp 1 (<h1>)
## Đây là Tiêu Đề Cấp 2 (<h2>)
### Đây là Tiêu Đề Cấp 3 (<h3>)
#### Đây là Tiêu Đề Cấp 4 (<h4>)
##### Đây là Tiêu Đề Cấp 5 (<h5>)
###### Đây là Tiêu Đề Cấp 6 (<h6>)
```

*   **Kết quả (khi render):**
    # Đây là Tiêu Đề Cấp 1 (<h1>)
    ## Đây là Tiêu Đề Cấp 2 (<h2>)
    ### Đây là Tiêu Đề Cấp 3 (<h3>)
    #### Đây là Tiêu Đề Cấp 4 (<h4>)
    ##### Đây là Tiêu Đề Cấp 5 (<h5>)
    ###### Đây là Tiêu Đề Cấp 6 (<h6>)

---

### 1.2. Đoạn Văn (Paragraphs) và Ngắt Dòng (Line Breaks)

*   **Đoạn Văn:** Để tạo một đoạn văn mới, bạn chỉ cần để lại một dòng trống giữa hai đoạn văn bản. Markdown coi hai dòng văn bản được phân tách bằng một dòng trống là hai đoạn văn khác nhau.
*   **Ngắt Dòng (mềm):** Để ngắt dòng nhưng vẫn thuộc cùng một đoạn văn (tương đương `<br>` trong HTML), bạn có thể thêm hai hoặc nhiều khoảng trắng vào cuối dòng, sau đó nhấn Enter.

```markdown
Đây là đoạn văn thứ nhất.
Nó bao gồm một số câu.

Đây là đoạn văn thứ hai.
Đây là dòng đầu tiên.
Đây là dòng thứ hai trong cùng một đoạn,
nhờ có hai khoảng trắng ở cuối dòng trên.
```

*   **Kết quả:**
    Đây là đoạn văn thứ nhất.
    Nó bao gồm một số câu.

    Đây là đoạn văn thứ hai.
    Đây là dòng đầu tiên.
    Đây là dòng thứ hai trong cùng một đoạn,
    nhờ có hai khoảng trắng ở cuối dòng trên.

---

### 1.3. Nhấn Mạnh (Emphasis)

Markdown cho phép bạn làm chữ in nghiêng hoặc in đậm để nhấn mạnh nội dung.

*   **In nghiêng (Italic):** Dùng dấu sao (`*`) hoặc dấu gạch dưới (`_`) bao quanh văn bản.
*   **In đậm (Bold):** Dùng hai dấu sao (`**`) hoặc hai dấu gạch dưới (`__`) bao quanh văn bản.
*   **In đậm và In nghiêng:** Kết hợp cả hai, dùng ba dấu sao (`***`) hoặc ba dấu gạch dưới (`___`) bao quanh.

```markdown
*Văn bản này sẽ in nghiêng*
_Văn bản này cũng in nghiêng_

**Văn bản này sẽ in đậm**
__Văn bản này cũng in đậm__

***Văn bản này vừa in đậm vừa in nghiêng***
___Văn bản này cũng vậy___
```

*   **Kết quả:**
    *Văn bản này sẽ in nghiêng*
    _Văn bản này cũng in nghiêng_

    **Văn bản này sẽ in đậm**
    __Văn bản này cũng in đậm__

    ***Văn bản này vừa in đậm vừa in nghiêng***
    ___Văn bản này cũng vậy___

---

### 1.4. Danh Sách (Lists)

Markdown hỗ trợ danh sách không thứ tự và danh sách có thứ tự.

*   **Danh Sách Không Thứ Tự (Unordered List):** Dùng dấu gạch ngang (`-`), dấu sao (`*`) hoặc dấu cộng (`+`) ở đầu mỗi mục.
*   **Danh Sách Có Thứ Tự (Ordered List):** Dùng số theo sau là dấu chấm (`.`) ở đầu mỗi mục. Bạn có thể dùng cùng một số (ví dụ: `1.`) cho tất cả các mục, trình render Markdown sẽ tự động tăng số thứ tự đúng.
*   **Danh sách lồng nhau:** Thêm 2 hoặc 4 khoảng trắng (hoặc 1 tab) trước các mục con.

```markdown
**Danh Sách Không Thứ Tự:**
*   Mục A
*   Mục B
    -   Mục con B.1
    -   Mục con B.2
*   Mục C

**Danh Sách Có Thứ Tự:**
1.  Mục 1
2.  Mục 2
3.  Mục 3
    1.  Mục con 3.1
    2.  Mục con 3.2
        -   Một mục nhỏ hơn nữa

```

*   **Kết quả:**
    **Danh Sách Không Thứ Tự:**
    *   Mục A
    *   Mục B
        -   Mục con B.1
        -   Mục con B.2
    *   Mục C

    **Danh Sách Có Thứ Tự:**
    1.  Mục 1
    2.  Mục 2
    3.  Mục 3
        1.  Mục con 3.1
        2.  Mục con 3.2
            -   Một mục nhỏ hơn nữa

---

### 1.5. Liên Kết (Links)

Có hai cách phổ biến để tạo liên kết: inline và reference.

*   **Liên Kết Inline:** Đặt văn bản hiển thị liên kết trong dấu ngoặc vuông `[]` và URL trong dấu ngoặc đơn `()` ngay sau đó. Có thể thêm tooltip bằng cách đặt nó trong dấu nháy kép `""` sau URL (có khoảng cách).

    ```markdown
    Truy cập [Trang chủ Google](https://www.google.com)
    Hoặc truy cập [Website của tôi](https://tenduanai.com "Đây là trang web tuyệt vời")
    ```

    *   **Kết quả:**
        Truy cập [Trang chủ Google](https://www.google.com)
        Hoặc truy cập [Website của tôi](https://tenduanai.com "Đây là trang web tuyệt vời")

*   **Liên Kết Reference (tham chiếu):** Rất hữu ích khi bạn dùng một URL nhiều lần hoặc muốn giữ văn bản dễ đọc hơn.

    ```markdown
    Truy cập [Trang chủ Google][google_link]
    Hoặc xem [Bài viết thú vị][bai_viet_so_1]

    <!-- Định nghĩa liên kết (thường đặt ở cuối file) -->
    [google_link]: https://www.google.com
    [bai_viet_so_1]: https://example.com/bai-viet-thu-vi "Tiêu đề Bài viết"
    ```

    *   **Kết quả:** (Render tương tự inline, nhưng cú pháp viết dễ quản lý hơn)
        Truy cập [Trang chủ Google][google_link]
        Hoặc xem [Bài viết thú vị][bai_viet_so_1]

        [google_link]: https://www.google.com
        [bai_viet_so_1]: https://example.com/bai-viet-thu-vi "Tiêu đề Bài viết"

---

### 1.6. Hình Ảnh (Images)

Cú pháp hình ảnh rất giống với liên kết, chỉ thêm dấu chấm than (`!`) ở phía trước.

```markdown
![Văn bản thay thế cho ảnh](url/den/anh.jpg "Tiêu đề (tooltip) của ảnh")

<!-- Ví dụ cụ thể: -->
![Logo Markdown](https://markdown.org/assets/img/touchicon-180.png "Đây là logo của Markdown")
```

*   **Kết quả:**
    ![Văn bản thay thế cho ảnh](url/den/anh.jpg "Tiêu đề (tooltip) của ảnh")

    ![Logo Markdown](https://markdown.org/assets/img/touchicon-180.png "Đây là logo của Markdown")

*   **Lưu ý:** Markdown cơ bản không hỗ trợ tùy chỉnh kích thước ảnh. Bạn có thể cần dùng cú pháp HTML hoặc các tiện ích mở rộng của trình render Markdown.

---

### 1.7. Khối Trích Dẫn (Blockquotes)

Để định dạng văn bản như một khối trích dẫn (giống `<blockquot>e` trong HTML), sử dụng dấu mũi tên phải (`>`) ở đầu mỗi dòng hoặc chỉ ở đầu dòng đầu tiên của đoạn trích.

```markdown
> Đây là một câu trích dẫn.
> Nó có thể kéo dài nhiều dòng.

> Đây là một đoạn trích dẫn khác, chỉ cần dấu '>' ở đầu dòng đầu tiên.
Văn bản này vẫn thuộc khối trích dẫn cho đến khi gặp dòng trống.

```

*   **Kết quả:**
    > Đây là một câu trích dẫn.
    > Nó có thể kéo dài nhiều dòng.

    > Đây là một đoạn trích dẫn khác, chỉ cần dấu '>' ở đầu dòng đầu tiên.
    Văn bản này vẫn thuộc khối trích dẫn cho đến khi gặp dòng trống.

*   **Lưu ý:** Có thể lồng ghép khối trích dẫn (`>>`) và các định dạng Markdown khác bên trong blockquote.

    ```markdown
    > Đây là khối trích dẫn cấp 1.
    >
    >> Đây là khối trích dẫn lồng nhau cấp 2.
    >>
    > *   Một mục danh sách bên trong trích dẫn.
    ```

    *   **Kết quả:**
        > Đây là khối trích dẫn cấp 1.
        >
        >> Đây là khối trích dẫn lồng nhau cấp 2.
        >>
        > *   Một mục danh sách bên trong trích dẫn.

---

### 1.8. Dòng Ngang (Horizontal Rules)

Dòng ngang (hoặc đường phân cách chủ đề) được tạo bằng cách đặt ba hoặc nhiều hơn các dấu gạch ngang (`---`), dấu sao (`***`) hoặc dấu gạch dưới (`___`) trên một dòng riêng biệt.

```markdown
Nội dung phía trên đường phân cách

---

Nội dung phía dưới đường phân cách

***

Nội dung tiếp theo

___

Và nội dung cuối cùng.
```

*   **Kết quả:**
    Nội dung phía trên đường phân cách

    ---

    Nội dung phía dưới đường phân cách

    ***

    Nội dung tiếp theo

    ___

    Và nội dung cuối cùng.

---

## Phần 2: Kiến Thức Trung Cấp & Các Phần Mở Rộng Phổ Biến

Phần này sẽ giới thiệu một số cú pháp Markdown nâng cao hơn một chút, bao gồm cách xử lý code và tạo bảng, cùng với một số cú pháp mở rộng thường thấy.

---

### 2.1. Code (Inline & Blocks)

Markdown sinh ra từ cộng đồng kỹ thuật, nên việc định dạng code là rất quan trọng.

*   **Inline Code:** Dùng dấu huyền (` `) bao quanh một đoạn code ngắn trong dòng văn bản.

    ```markdown
    Sử dụng hàm `print()` trong Python.
    Hoặc biến `$myVariable` trong PHP.
    ```

    *   **Kết quả:**
        Sử dụng hàm `print()` trong Python.
        Hoặc biến `$myVariable` trong PHP.

*   **Code Blocks (Khối Code):** Dùng bốn khoảng trắng hoặc một tab thụt đầu dòng cho mỗi dòng code, hoặc sử dụng "Fenced Code Blocks" bằng cách đặt ba dấu huyền (```) hoặc ba dấu ngã (~~~) ở đầu và cuối khối code. Cách Fenced phổ biến hơn vì bạn có thể chỉ định ngôn ngữ lập trình để hightlight cú pháp (syntax highlighting).

    **Sử dụng thụt lề:**

    ```markdown
        def say_hello():
            print("Hello, world!")
    ```

    **Sử dụng Fenced Code Blocks (khuyên dùng):**

    ```markdown
    ```python
    def say_hello():
        print("Hello from Python!")

    say_hello()
    ```

    ```javascript
    function greet(name) {
        console.log(`Hello, ${name}!`);
    }
    greet("Markdown User");
    ```
    ```

    *   **Kết quả:**
        ```python
        def say_hello():
            print("Hello from Python!")

        say_hello()
        ```

        ```javascript
        function greet(name) {
            console.log(`Hello, ${name}!`);
        }
        greet("Markdown User");
        ```
    *   **Lưu ý:** Việc highlight cú pháp phụ thuộc vào trình render Markdown bạn đang sử dụng.

---

### 2.2. Bảng (Tables)

Markdown gốc không có cú pháp cho bảng, nhưng hầu hết các phiên bản Markdown hiện đại (như GitHub Flavored Markdown - GFM) đều hỗ trợ. Bạn dùng dấu gạch ngang (`-`) và dấu gạch đứng (`|`) để tạo bảng.

*   **Cú pháp:**
    *   Dòng đầu tiên là tiêu đề cột, dùng dấu `|` để phân cách.
    *   Dòng thứ hai dùng dấu `|`, dấu `-` và dấu hai chấm (`:`) để phân cách các cột và định nghĩa căn chỉnh văn bản.
    *   Các dòng tiếp theo là dữ liệu bảng.

    ```markdown
    | Tiêu Đề Cột 1 | Tiêu Đề Cột 2 | Tiêu Đề Cột 3 |
    |---------------|:-------------:|--------------:|
    | Dữ liệu hàng 1, cột 1 | Căn giữa | Căn phải    |
    | Dữ liệu hàng 2, cột 1 | abc         | 123         |
    ```

*   **Định nghĩa căn chỉnh:**
    *   `:---` hoặc `---:` : Căn trái (mặc định).
    *   `:---:` : Căn giữa.
    *   `---:` : Căn phải.

*   **Kết quả:**
    | Tiêu Đề Cột 1 | Tiêu Đề Cột 2 | Tiêu Đề Cột 3 |
    |---------------|:-------------:|--------------:|
    | Dữ liệu hàng 1, cột 1 | Căn giữa | Căn phải    |
    | Dữ liệu hàng 2, cột 1 | abc         | 123         |

---

### 2.3. Danh Sách Nhiệm Vụ (Task Lists)

Một tính năng hữu ích trong GFM (và nhiều trình render khác) là danh sách các công việc có thể tick (checkboxes).

*   **Cú pháp:** Bắt đầu một mục danh sách bằng `-` hoặc `*`, theo sau là khoảng trắng, dấu ngoặc vuông `[]` hoặc `[x]` (có khoảng trắng giữa ngoặc vuông và mục).

    ```markdown
    - [x] Hoàn thành bài học cơ bản Markdown
    - [ ] Bắt đầu phần trung cấp
    - [ ] Luyện tập cú pháp Bảng
    *   [x] Mua cà phê
    *   [ ] Gửi email cho đồng nghiệp
    ```

*   **Kết quả:**
    - [x] Hoàn thành bài học cơ bản Markdown
    - [ ] Bắt đầu phần trung cấp
    - [ ] Luyện tập cú pháp Bảng
    *   [x] Mua cà phê
    *   [ ] Gửi email cho đồng nghiệp

*   **Lưu ý:** Checkbox này chỉ hiển thị trạng thái (`[ ]` hoặc `[x]`), việc *thực sự* tick vào ô để thay đổi trạng thái phụ thuộc vào nền tảng bạn đang xem file `.md` đó (ví dụ: GitHub hỗ trợ điều này).

---

### 2.4. Gạch Ngang Chữ (Strikethrough)

Đây cũng là một tính năng mở rộng phổ biến (GFM). Sử dụng hai dấu ngã (`~~`) bao quanh văn bản.

```markdown
Đây là văn bản ~~cần bỏ đi~~.
```

*   **Kết quả:**
    Đây là văn bản ~~cần bỏ đi~~.

---

### 2.5. Emoji (Biểu Tượng Cảm Xúc)

Nhiều trình render Markdown, bao gồm GFM, hỗ trợ chuyển đổi các mã ngắn (shortcode) thành emoji.

```markdown
Tôi thấy bài học này rất tuyệt! :tada: :+1: :heart:
Cần tập trung hơn: :focus: :nerd_face:
```

*   **Kết quả:** (Hiển thị tùy thuộc vào trình render và font chữ)
    Tôi thấy bài học này rất tuyệt! 🎉 👍 ❤️
    Cần tập trung hơn: फोकस 🤓

*   **Lưu ý:** Danh sách các mã ngắn emoji có thể khác nhau giữa các nền tảng. Bạn có thể tìm kiếm "emoji shortcode list" để xem danh sách đầy đủ.

---

### 2.6. Liên Kết URL Tự Động (Automatic URL Linking)

Nhiều trình render tự động biến các URL và địa chỉ email trong văn bản thành liên kết có thể click. Bạn cũng có thể dùng dấu ngoặc nhọn `< >` để đảm bảo chúng được xử lý như liên kết.

```markdown
Trang web của tôi là https://tenduanai.com
Địa chỉ email liên hệ: support@tenduanai.com

Sử dụng ngoặc nhọn:
<https://tenduanai.com>
<support@tenduanai.com>
```

*   **Kết quả:**
    Trang web của tôi là https://tenduanai.com
    Địa chỉ email liên hệ: support@tenduanai.com

    Sử dụng ngoặc nhọn:
    <https://tenduanai.com>
    <support@tenduanai.com>

---

### 2.7. HTML Embedding (Chèn HTML thô)

Một trong những quy tắc của Markdown là nó được thiết kế để dễ dàng đọc và viết. Khi cần định dạng phức tạp hơn mà Markdown không hỗ trợ, bạn có thể sử dụng trực tiếp HTML trong file Markdown. Markdown sẽ *không* xử lý các khối HTML này (trừ một vài thẻ đơn giản), nó chỉ "để yên" cho trình duyệt xử lý.

```markdown
Markdown bình thường ở đây.

<div style="background-color: #f0f0f0; padding: 10px;">
  <h4>Đây là HTML bên trong Markdown</h4>
  <p>Bạn có thể dùng các thẻ HTML phức tạp hơn khi cần thiết.</p>
</div>

Một đoạn Markdown tiếp theo.
```

*   **Kết quả:** (Khi được render thành HTML và xem trong trình duyệt)
    Markdown bình thường ở đây.

    <div style="background-color: #f0f0f0; padding: 10px;">
      <h4>Đây là HTML bên trong Markdown</h4>
      <p>Bạn có thể dùng các thẻ HTML phức tạp hơn khi cần thiết.</p>
    </div>

    Một đoạn Markdown tiếp theo.

*   **Lưu ý:** Việc chèn HTML có thể làm giảm khả năng đọc của file Markdown thô và đôi khi bị giới hạn bởi trình render Markdown.

---

### 2.8. Ký Tự Thoát (Escaping Characters)

Nếu bạn muốn hiển thị các ký tự Markdown theo nghĩa đen thay vì định dạng chúng, bạn dùng dấu gạch ngược (`\`) phía trước ký tự đó.

```markdown
Tôi muốn hiển thị *dấu sao* này theo đúng nghĩa đen: \*Dấu sao\*
Và cả `_gạch dưới_`: \_Gạch dưới\_
Một URL mà không biến thành link: `\`https://example.com\`
```

*   **Kết quả:**
    Tôi muốn hiển thị *dấu sao* này theo đúng nghĩa đen: \*Dấu sao\*
    Và cả `_gạch dưới_`: \_Gạch dưới\_
    Một URL mà không biến thành link: `\`https://example.com\`

---

## Phần 3: Mẹo và Thực Hành Tốt (Tips & Best Practices)

Để viết Markdown hiệu quả và dễ bảo trì, hãy xem xét một số mẹo nhỏ sau:

1.  **Độ Thống Nhất (Consistency):** Dù có nhiều cách để đạt được cùng một định dạng (ví dụ: dùng `*` hoặc `-` cho danh sách, dùng `*` hoặc `_` cho in nghiêng), hãy chọn một kiểu và gắn bó với nó trong toàn bộ tài liệu của bạn.
2.  **Khoảng Cách:** Sử dụng khoảng cách một cách hợp lý (như sau dấu `#`, sau `-` trong danh sách, quanh `**` hoặc `__`) giúp file `.md` gốc dễ đọc hơn rất nhiều.
3.  **Tên File:** Lưu file Markdown với đuôi `.md` hoặc `.markdown`.
4.  **Sử Dụng Trình Biên Tập (Editor):** Có rất nhiều trình biên tập Markdown tuyệt vời (VS Code với các extension, Typora, Obsidian, iA Writer, StackEdit online...) hỗ trợ xem trước (preview) trực tiếp hoặc side-by-side khi bạn gõ, giúp bạn dễ dàng thấy kết quả render.
5.  **Bắt Đầu Đơn Giản:** Đừng cố gắng định dạng quá phức tạp ngay từ đầu. Bắt đầu với các cú pháp cơ bản. Markdown phát huy tốt nhất sức mạnh của nó khi giữ mọi thứ đơn giản và tập trung vào nội dung.
6.  **Định dạng Bảng Phức Tạp:** Đối với các bảng phức tạp hoặc yêu cầu nhiều định dạng, đôi khi sử dụng HTML trực tiếp sẽ dễ quản lý hơn.

