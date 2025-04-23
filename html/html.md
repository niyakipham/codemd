# KHÓA HỌC TOÀN DIỆN VỀ HTML: Từ Cơ Bản Đến Nâng Cao

Xin chào, người bạn đồng hành trên hành trình kiến tạo Web!

Cảm ơn bạn vì đã tin tưởng giao cho tôi nhiệm vụ này. HTML không chỉ là những dòng ký tự; nó là ngôn ngữ của cấu trúc, là nền tảng vững chắc mà trên đó, những ý tưởng sáng tạo của bạn sẽ được hình thành. Hãy cùng tôi khám phá từng ngóc ngách của ngôn ngữ này nhé!

---

## PHẦN 1: NHỮNG BƯỚC CHÂN ĐẦU TIÊN - LÀM QUEN VỚI HTML (CƠ BẢN)

Mọi công trình vĩ đại đều bắt đầu từ viên gạch đầu tiên. Phần này sẽ giúp bạn đặt nền móng cho trang web của mình.

### Bài 1.1: HTML là gì và Tại sao chúng ta cần nó?

*   **Định nghĩa:** HTML (HyperText Markup Language) không phải là một ngôn ngữ lập trình, mà là một ngôn ngữ đánh dấu. Nó được dùng để cấu trúc nội dung trên web.
*   **Vai trò:** Giống như bộ xương trong cơ thể chúng ta, HTML tạo ra cấu trúc cho trang web: xác định đâu là tiêu đề, đâu là đoạn văn, đâu là hình ảnh, đâu là liên kết...
*   **Lịch sử ngắn gọn:** Từ những ngày đầu đơn giản, HTML đã tiến hóa qua các phiên bản (đặc biệt là HTML5) để trở nên mạnh mẽ và linh hoạt hơn, đáp ứng nhu cầu của một thế giới web ngày càng phức tạp.
*   **Công cụ cần thiết:**
    *   Trình duyệt web (Chrome, Firefox, Edge, Safari...) để xem kết quả.
    *   Trình soạn thảo văn bản (VS Code, Sublime Text, Atom, Notepad++, TextEdit...). Tôi gợi ý dùng VS Code vì tính năng hỗ trợ lập trình rất tốt.

### Bài 1.2: Cấu trúc Tài liệu HTML cơ bản (The Boilerplate)

Mọi trang HTML đều có một bộ khung sườn chuẩn.

*   **`<!DOCTYPE html>`:** Khai báo loại tài liệu, báo cho trình duyệt biết đây là tài liệu HTML5. Luôn đặt nó ở dòng đầu tiên.
*   **`<html></html>`:** Thẻ gốc, chứa toàn bộ nội dung của trang HTML. Thuộc tính `lang="vi"` thường được thêm vào để khai báo ngôn ngữ chính của trang.
*   **`<head></head>`:** Chứa các thông tin *không hiển thị trực tiếp* trên trang web nhưng quan trọng đối với trình duyệt và công cụ tìm kiếm (metadata).
    *   `<meta charset="UTF-8">`: Quan trọng bậc nhất! Khai báo bộ mã ký tự UTF-8 để hỗ trợ hầu hết các ngôn ngữ, tránh lỗi hiển thị tiếng Việt.
    *   `<meta name="viewport" content="width=device-width, initial-scale=1.0">`: Rất cần thiết cho Responsive Web Design (hiển thị tốt trên nhiều thiết bị).
    *   `<title></title>`: Văn bản bên trong thẻ này sẽ hiển thị trên thanh tiêu đề của tab trình duyệt. Quan trọng cho trải nghiệm người dùng và SEO.
    *   `<link rel="stylesheet" href="style.css">`: Liên kết đến tệp CSS để trang trí cho trang web.
    *   `<script src="script.js"></script>`: Liên kết đến tệp JavaScript để thêm tính tương tác.
*   **`<body></body>`:** Chứa toàn bộ nội dung *hiển thị trực tiếp* trên trang web mà người dùng thấy. Đây là nơi chúng ta làm việc chủ yếu.

```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Trang Web Đầu Tiên Của Tôi</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <!-- Nội dung hiển thị trên trang web sẽ nằm ở đây -->
    <h1>Chào mừng bạn đến với thế giới HTML!</h1>
    <p>Chúng ta đang bắt đầu một cuộc hành trình thú vị.</p>

    <script src="script.js"></script>
</body>
</html>
```

### Bài 1.3: Làm việc với Tiêu đề (Headings) và Đoạn văn (Paragraphs)

Đây là những khối văn bản cơ bản nhất.

*   **Tiêu đề (`<h1>` đến `<h6>`):** Dùng để định nghĩa các tiêu đề và tiêu đề con. `<h1>` là quan trọng nhất (thường chỉ dùng một lần cho tiêu đề chính của trang/nội dung), `<h6>` là ít quan trọng nhất. Việc sử dụng đúng cấu trúc heading rất quan trọng cho SEO và khả năng tiếp cận (Accessibility).
*   **Đoạn văn (`<p>`):** Dùng để chứa các đoạn văn bản thông thường.
*   **Xuống dòng (`<br>`):** Chèn một lần ngắt dòng. Nên sử dụng ít, chủ yếu dùng CSS để tạo khoảng cách. `<br>` là thẻ tự đóng.
*   **Đường ngang (`<hr>`):** Chèn một đường phân cách ngang, thường dùng để phân chia nội dung theo chủ đề. `<hr>` cũng là thẻ tự đóng.

```html
<h1>Tiêu đề Cấp 1 - Quan trọng nhất</h1>
<p>Đây là một đoạn văn bản đầu tiên.</p>

<h2>Tiêu đề Cấp 2</h2>
<p>Đây là đoạn văn bản thứ hai, nói chi tiết hơn về tiêu đề cấp 2.</p>
<p>Có thể có nhiều đoạn văn dưới cùng một tiêu đề. <br> Thẻ br dùng để xuống dòng.</p>

<h3>Tiêu đề Cấp 3</h3>
<hr> <!-- Dùng để phân chia -->
<p>Văn bản dưới tiêu đề cấp 3.</p>
```

### Bài 1.4: Định dạng Văn bản cơ bản (Text Formatting)

HTML cung cấp các thẻ để làm nổi bật hoặc thay đổi ý nghĩa của văn bản.

*   **`<strong>` và `<b>`:** `<strong>` đánh dấu văn bản quan trọng (ý nghĩa ngữ nghĩa), `<b>` chỉ làm cho văn bản in đậm (ý nghĩa trình bày). Trong hầu hết các trường hợp, nên dùng `<strong>`.
*   **`<em>` và `<i>`:** `<em>` đánh dấu văn bản nhấn mạnh (ý nghĩa ngữ nghĩa), `<i>` chỉ làm cho văn bản in nghiêng (ý nghĩa trình bày, ví dụ: thuật ngữ kỹ thuật, tên tàu). Nên dùng `<em>` khi muốn nhấn mạnh nội dung.
*   **`<mark>`:** Đánh dấu văn bản như được tô sáng.
*   **`<small>`:** Làm cho văn bản nhỏ hơn.
*   **`<del>`:** Đánh dấu văn bản đã bị xóa (gạch ngang).
*   **`<ins>`:** Đánh dấu văn bản đã được chèn (gạch chân).
*   **`<sub>`:** Văn bản chỉ số dưới (subscript).
*   **`<sup>`:** Văn bản chỉ số trên (superscript).
*   **`<code>`:** Định dạng văn bản như mã nguồn (code).
*   **`<pre>`:** Hiển thị văn bản với khoảng trắng và ngắt dòng giữ nguyên (thường dùng cho các khối code).
*   **`<blockquote>`:** Định nghĩa một khối trích dẫn dài.
*   **`<q>`:** Định nghĩa một trích dẫn ngắn (tự động thêm dấu ngoặc kép).

```html
<p>
    Chúng ta sẽ học về <strong>HTML</strong> và cách định dạng <em>văn bản</em>.
    Từ này là <mark>quan trọng</mark>.
    <small>Đây là văn bản nhỏ.</small>
</p>
<p>Công thức H<sub>2</sub>O, Phương trình E=MC<sup>2</sup>.</p>
<p>Đã <del>hủy bỏ</del> thành <ins>công</ins>.</p>
<p>Khi code bạn có thể dùng thẻ <code>&lt;p&gt;</code>.</p>
<pre>
function xinChao() {
    console.log("Chào bạn!");
}
xinChao();
</pre>
<blockquote>
    Tri thức là sức mạnh.
    <cite>-- Francis Bacon</cite> <!-- Thẻ cite dùng cho tiêu đề của một tác phẩm hoặc tên tác giả -->
</blockquote>
<p>Như Lạc Long Quân đã nói: <q>Ta là giống Rồng, nàng là giống Tiên...</q></p>

```

### Bài 1.5: Liên kết (Links)

Thẻ `<a>` (anchor) là trái tim của web, kết nối các trang lại với nhau.

*   **Cú pháp:** `<a href="url">Văn bản liên kết</a>`
*   **Thuộc tính `href`:** Chỉ định địa chỉ URL mà liên kết sẽ trỏ tới.
    *   **Absolute URLs:** Địa chỉ đầy đủ (ví dụ: `https://www.google.com`).
    *   **Relative URLs:** Địa chỉ tương đối so với vị trí của tệp HTML hiện tại (ví dụ: `about.html`, `images/logo.png`, `../index.html`).
*   **Thuộc tính `target`:** Chỉ định nơi mở liên kết.
    *   `_self`: Mở trong cùng một cửa sổ/tab (mặc định).
    *   `_blank`: Mở trong một cửa sổ/tab mới.
    *   `_parent`: Mở trong khung cha.
    *   `_top`: Mở trong toàn bộ thân cửa sổ trình duyệt.
*   **Liên kết neo (Anchor links):** Liên kết đến một phần cụ thể trong cùng một trang web hoặc trang khác. Sử dụng thuộc tính `id` trên phần tử đích, và trong `href` dùng `#id-của-phần-tử`.
*   **Liên kết email:** `<a href="mailto:email@example.com">Gửi Email</a>` (có thể thêm subject, body: `mailto:email@example.com?subject=Hỏi đáp&body=Xin chào,...`)
*   **Liên kết số điện thoại:** `<a href="tel:+84123456789">Gọi ngay</a>`

```html
<p>Hãy ghé thăm trang <a href="https://freetuts.net/" target="_blank">FreeTuts.net</a> để học lập trình miễn phí.</p>

<p>Hoặc xem <a href="ve-chung-toi.html">trang giới thiệu</a> của chúng tôi (nếu có).</p>

<!-- Liên kết neo -->
<p><a href="#phan-nang-cao">Chuyển đến phần Nâng cao</a></p>

<!-- Somewhere below -->
<h2 id="phan-nang-cao">PHẦN 3: KHÁM PHÁ SÂU HƠN - HTML NÂNG CAO</h2>

<p><a href="mailto:support@example.com">Gửi hỗ trợ qua email</a></p>
<p><a href="tel:+84987654321">Liên hệ qua điện thoại: 0987 654 321</a></p>
```

### Bài 1.6: Chèn Hình ảnh (Images)

Trang web sẽ buồn tẻ nếu không có hình ảnh!

*   **Cú pháp:** `<img src="url-hinh-anh" alt="Văn bản thay thế">` (Thẻ tự đóng)
*   **Thuộc tính `src`:** Chỉ định địa chỉ của tệp hình ảnh. Có thể là absolute URL hoặc relative URL.
*   **Thuộc tính `alt`:** *Quan trọng bậc nhất!* Cung cấp văn bản thay thế nếu hình ảnh không tải được hoặc cho trình đọc màn hình (screen readers) hiểu nội dung hình ảnh (hỗ trợ Accessibility). Mô tả ngắn gọn nội dung hình ảnh.
*   **Thuộc tính `width` và `height`:** Chỉ định kích thước hiển thị của hình ảnh. Nên đặt một trong hai (hoặc cả hai) để trình duyệt tối ưu hóa việc tải trang (mặc dù CSS được ưu tiên dùng để điều khiển kích thước thực tế trên giao diện). Lưu ý: Việc thay đổi kích thước bằng `width`/`height` trong HTML chỉ *co giãn* hình ảnh, không làm thay đổi kích thước tệp gốc.
*   **`<figure>` và `<figcaption>`:** Dùng để nhóm hình ảnh với chú thích của nó, mang ý nghĩa ngữ nghĩa tốt hơn.

```html
<img src="images/logo.png" alt="Logo Công ty Của Tôi" width="100">

<p>Một hình ảnh từ web:</p>
<img src="https://via.placeholder.com/150" alt="Ảnh mẫu 150x150">

<figure>
    <img src="images/my-office.jpg" alt="Văn phòng làm việc của tôi">
    <figcaption>Hình 1: Khung cảnh làm việc lý tưởng.</figcaption>
</figure>
```

### Bài 1.7: Danh sách (Lists)

Sắp xếp thông tin theo dạng danh sách rất phổ biến.

*   **Danh sách không thứ tự (`<ul>`):** Các mục được đánh dấu bằng chấm, tròn, vuông,... (kiểu hiển thị do CSS định nghĩa).
    *   Mỗi mục trong danh sách là một thẻ `<li>` (list item).
*   **Danh sách có thứ tự (`<ol>`):** Các mục được đánh số hoặc chữ cái (kiểu hiển thị do CSS hoặc thuộc tính `type` định nghĩa - A, a, I, i, 1).
    *   Mỗi mục trong danh sách là một thẻ `<li>`.
*   **Danh sách mô tả (`<dl>`):** Thường dùng cho các định nghĩa hoặc các cặp thuật ngữ-giải thích.
    *   `<dt>` (description term): Thuật ngữ.
    *   `<dd>` (description description): Phần mô tả cho thuật ngữ đó.

```html
<h3>Danh sách công việc cần làm:</h3>
<ul>
    <li>Mua cà phê</li>
    <li>Học HTML</li>
    <li>Viết code</li>
</ul>

<h3>Các bước pha cà phê:</h3>
<ol>
    <li>Đun nước sôi</li>
    <li>Cho cà phê vào phin</li>
    <li>Rót nước nóng</li>
    <li>Thưởng thức</li>
</ol>

<h3>Một vài thuật ngữ web:</h3>
<dl>
    <dt>HTML</dt>
    <dd>HyperText Markup Language: Ngôn ngữ đánh dấu cấu trúc nội dung web.</dd>

    <dt>CSS</dt>
    <dd>Cascading Style Sheets: Ngôn ngữ dùng để định kiểu và trình bày bố cục trang web.</dd>

    <dt>JavaScript</dt>
    <dd>Ngôn ngữ lập trình để tạo tương tác cho trang web.</dd>
</dl>
```

---

## PHẦN 2: TẠO NÊN SỰ PHONG PHÚ - HTML TRUNG CẤP

Khi đã nắm vững cơ bản, chúng ta sẽ bắt đầu tạo ra những cấu trúc phức tạp hơn.

### Bài 2.1: Bảng biểu (Tables)

HTML cung cấp cấu trúc để hiển thị dữ liệu dạng bảng. Tuyệt vời cho dữ liệu có cấu trúc, KHÔNG DÙNG ĐỂ TRÌNH BÀY BỐ CỤC trang web (đó là nhiệm vụ của CSS Flexbox/Grid).

*   **`<table>`:** Thẻ gốc của bảng.
*   **`<caption>`:** Chú thích cho bảng (nên dùng).
*   **`<thead>`:** Nhóm các hàng tiêu đề của bảng.
*   **`<tbody>`:** Nhóm các hàng dữ liệu của bảng (phần thân).
*   **`<tfoot>`:** Nhóm các hàng chân bảng (ví dụ: tổng cộng).
*   **`<tr>`:** Table Row - Định nghĩa một hàng trong bảng.
*   **`<th>`:** Table Header - Định nghĩa ô tiêu đề (trong `<thead>`, đôi khi trong `tbody`). Mặc định in đậm và căn giữa. Thuộc tính `scope` (`col` hoặc `row`) quan trọng cho Accessbility.
*   **`<td>`:** Table Data - Định nghĩa ô dữ liệu.
*   **`colspan`:** Gộp nhiều cột thành một ô.
*   **`rowspan`:** Gộp nhiều hàng thành một ô.

```html
<table>
    <caption>Danh Sách Sinh Viên</caption>
    <thead>
        <tr>
            <th>STT</th>
            <th>Họ và Tên</th>
            <th>Điểm Trung Bình</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>1</td>
            <td>Nguyễn Văn A</td>
            <td>8.5</td>
        </tr>
        <tr>
            <td>2</td>
            <td>Trần Thị B</td>
            <td>9.0</td>
        </tr>
        <tr>
            <td>3</td>
            <td>Lê Văn C</td>
            <td>7.8</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td colspan="2">Tổng số sinh viên:</td>
            <td>3</td>
        </tr>
    </tfoot>
</table>
```

### Bài 2.2: Biểu mẫu (Forms) - Thu thập Dữ liệu Người dùng

Biểu mẫu là cách chúng ta tương tác và thu thập thông tin từ người dùng.

*   **`<form>`:** Thẻ gốc của biểu mẫu.
    *   **`action`:** Chỉ định URL nơi dữ liệu biểu mẫu sẽ được gửi đi khi submit.
    *   **`method`:** Chỉ định phương thức HTTP để gửi dữ liệu (`GET` hoặc `POST`). `GET` gửi dữ liệu qua URL (không an toàn cho dữ liệu nhạy cảm, giới hạn ký tự), `POST` gửi dữ liệu trong phần thân của request (an toàn hơn, không giới hạn ký tự).
*   **`<label>`:** Gán nhãn cho các điều khiển form (input, select, textarea). Sử dụng thuộc tính `for` có giá trị *giống hệt* với thuộc tính `id` của điều khiển form. Quan trọng cho Accessibility (khi click vào label, điều khiển tương ứng sẽ được focus) và UX.
*   **`<input>`:** Thẻ rất đa năng, dùng để tạo nhiều loại điều khiển form khác nhau tùy thuộc vào thuộc tính `type`. Thẻ tự đóng.
    *   **Thuộc tính `type`:**
        *   `text`: Nhập văn bản một dòng.
        *   `password`: Nhập mật khẩu (ký tự bị ẩn).
        *   `submit`: Nút gửi form.
        *   `reset`: Nút đặt lại form.
        *   `checkbox`: Hộp kiểm (chọn nhiều).
        *   `radio`: Nút chọn (chỉ chọn một trong nhóm cùng tên).
        *   `file`: Tải tệp lên.
        *   `email`: Nhập địa chỉ email (có kiểm tra định dạng cơ bản).
        *   `number`: Nhập số (có nút tăng/giảm).
        *   `date`, `time`, `color`, `range`, `url`, `search`, `tel`: Các loại input chuyên biệt.
    *   **Thuộc tính `name`:** Tên của input, được dùng để xác định dữ liệu khi gửi form. BẮT BUỘC phải có `name` để gửi dữ liệu.
    *   **Thuộc tính `value`:** Giá trị ban đầu của input hoặc giá trị được gửi đi (đối với radio, checkbox, submit).
    *   **Thuộc tính `placeholder`:** Gợi ý văn bản hiển thị trong input khi rỗng.
    *   **Thuộc tính `required`:** Bắt buộc phải nhập/chọn trước khi gửi form.
    *   **Thuộc tính `disabled`:** Vô hiệu hóa input.
    *   **Thuộc tính `readonly`:** Input chỉ đọc, không sửa được nhưng vẫn gửi dữ liệu.
    *   **Thuộc tính `checked`:** Mặc định được chọn (cho checkbox, radio).
*   **`<textarea>`:** Vùng nhập văn bản nhiều dòng. Thuộc tính `rows` và `cols` định kích thước ban đầu.
*   **`<select>` và `<option>`:** Tạo danh sách thả xuống.
    *   `<select name="ten-select">`: Thẻ gốc.
    *   `<option value="gia-tri-gui">Văn bản hiển thị</option>`: Một lựa chọn trong danh sách. `value` là giá trị được gửi đi.
    *   `selected`: Mặc định được chọn trong `<option>`.
    *   `multiple`: Thêm thuộc tính này vào `<select>` để cho phép chọn nhiều lựa chọn.
*   **`<button>`:** Tạo nút bấm. Có thể dùng thay cho `<input type="submit/reset">`. Thường linh hoạt hơn. Mặc định `type="submit"`.

```html
<form action="/submit-form" method="post">
    <div>
        <label for="ho_ten">Họ và Tên:</label>
        <input type="text" id="ho_ten" name="ho_ten" required placeholder="Nhập họ tên của bạn">
    </div>

    <div>
        <label for="email">Email:</label>
        <input type="email" id="email" name="email" required>
    </div>

    <div>
        <label for="mat_khau">Mật khẩu:</label>
        <input type="password" id="mat_khau" name="mat_khau">
    </div>

    <div>
        Giới tính:
        <input type="radio" id="nam" name="gioi_tinh" value="nam" checked>
        <label for="nam">Nam</label>

        <input type="radio" id="nu" name="gioi_tinh" value="nu">
        <label for="nu">Nữ</label>
    </div>

    <div>
        Sở thích:
        <input type="checkbox" id="doc_sach" name="so_thich[]" value="docsach">
        <label for="doc_sach">Đọc sách</label>

        <input type="checkbox" id="du_lich" name="so_thich[]" value="dulich">
        <label for="du_lich">Du lịch</label>
    </div>

    <div>
        <label for="quoc_gia">Quốc gia:</label>
        <select id="quoc_gia" name="quoc_gia">
            <option value="">--Chọn quốc gia--</option>
            <option value="vn">Việt Nam</option>
            <option value="us">Hoa Kỳ</option>
            <option value="other">Khác</option>
        </select>
    </div>

    <div>
        <label for="noi_dung">Nội dung góp ý:</label><br>
        <textarea id="noi_dung" name="noi_dung" rows="4" cols="50"></textarea>
    </div>

    <div>
        <button type="submit">Gửi Thông Tin</button>
        <button type="reset">Xóa Trắng</button>
        <!-- Hoặc <input type="submit" value="Gửi Thông Tin"> -->
    </div>
</form>
```

### Bài 2.3: Các Thẻ HTML5 Semantic (Ngữ nghĩa)

Đây là một bước tiến lớn của HTML5. Các thẻ semantic không chỉ tạo cấu trúc mà còn mang ý nghĩa về nội dung của chúng, giúp máy móc (trình duyệt, công cụ tìm kiếm, screen readers) hiểu rõ hơn cấu trúc trang.

*   **`(<header>)`:** Phần đầu trang hoặc phần đầu của một phần nội dung (ví dụ: `<article>`, `<section>`). Thường chứa logo, tiêu đề trang, hoặc điều hướng chính.
*   **`<nav>`:** Chứa các liên kết điều hướng chính của trang web (menu).
*   **`<main>`:** Chứa nội dung chính và duy nhất của trang. Chỉ nên có một thẻ `<main>` trên mỗi trang.
*   **`<article>`:** Biểu diễn một mục nội dung độc lập, có thể phân phối lại hoặc tái sử dụng một cách độc lập (ví dụ: một bài blog, một mẩu tin, một diễn đàn).
*   **`<section>`:** Biểu diễn một phần nội dung có chủ đề riêng biệt trong một tài liệu hoặc bài viết. Nên có một tiêu đề (h1-h6) bên trong.
*   **`<aside>`:** Biểu diễn nội dung ít liên quan đến nội dung chính xung quanh, thường được trình bày như một thanh bên (sidebar).
*   **`<footer>`:** Phần chân trang hoặc chân của một phần nội dung. Thường chứa thông tin bản quyền, liên hệ, liên kết phụ.
*   **`<figure>` và `<figcaption>`:** (Đã đề cập ở bài hình ảnh) Dùng cho các khối nội dung độc lập như hình ảnh, biểu đồ, đoạn code có chú thích.
*   **`<mark>`, `<time>`, `<cite>`, `<abbr>`, `<address>`:** Các thẻ semantic cho văn bản.
    *   `<time datetime="2023-10-27T12:00:00Z">27/10/2023</time>`: Đánh dấu thời gian/ngày tháng.
    *   `<cite>`: Tên của tác phẩm sáng tạo (sách, bài hát, phim,...).
    *   `<abbr title="HyperText Markup Language">HTML</abbr>`: Định nghĩa từ viết tắt (hiển thị toàn bộ khi hover).
    *   `<address>`: Thông tin liên hệ của tác giả/chủ sở hữu.

Việc sử dụng các thẻ semantic thay vì chỉ dùng `<div>` cho mọi thứ giúp tăng tính ngữ nghĩa, cải thiện SEO và Accessibility.

```html
<header>
    <img src="logo.png" alt="Logo Công Ty">
    <h1>Tên Trang Web</h1>
    <nav>
        <ul>
            <li><a href="/">Trang chủ</a></li>
            <li><a href="/about">Giới thiệu</a></li>
            <li><a href="/contact">Liên hệ</a></li>
        </ul>
    </nav>
</header>

<main>
    <article>
        <h2>Tiêu đề Bài Viết</h2>
        <p>Ngày đăng: <time datetime="2023-10-26">26/10/2023</time></p>
        <section>
            <h3>Phần Giới Thiệu</h3>
            <p>...</p>
        </section>
        <section>
            <h3>Nội Dung Chi Tiết</h3>
            <p>...</p>
            <figure>
                <img src="image1.jpg" alt="Mô tả hình ảnh">
                <figcaption>Hình ảnh minh họa</figcaption>
            </figure>
        </section>
    </article>

    <aside>
        <h3>Bài Viết Liên Quan</h3>
        <ul>
            <li><a href="#">Bài khác A</a></li>
            <li><a href="#">Bài khác B</a></li>
        </ul>
    </aside>
</main>

<footer>
    <p>&copy; 2023 Tên Công Ty. Tất cả bản quyền được bảo lưu.</p>
    <address>
        Email: <a href="mailto:info@example.com">info@example.com</a><br>
        Địa chỉ: Số 1, Đường A, Quận B, Thành phố C.
    </address>
</footer>
```

### Bài 2.4: Nhúng Nội dung Đa phương tiện (Audio & Video)

HTML5 cung cấp các thẻ riêng để nhúng âm thanh và video mà không cần plugin (như Flash trước đây).

*   **`<audio>`:** Nhúng tệp âm thanh.
    *   `src`: Đường dẫn tệp âm thanh (có thể dùng `<source>` bên trong).
    *   `controls`: Hiển thị bộ điều khiển âm thanh mặc định của trình duyệt (phát, dừng, âm lượng...).
    *   `autoplay`: Tự động phát khi trang tải (thường bị chặn bởi trình duyệt).
    *   `loop`: Lặp lại âm thanh.
    *   `muted`: Tắt tiếng mặc định.
*   **`<video>`:** Nhúng tệp video.
    *   `src`: Đường dẫn tệp video (có thể dùng `<source>` bên trong).
    *   `controls`: Hiển thị bộ điều khiển video mặc định của trình duyệt.
    *   `autoplay`, `loop`, `muted`: Tương tự `<audio>`.
    *   `width`, `height`: Kích thước video.
    *   `poster`: Đường dẫn đến hình ảnh hiển thị khi video chưa sẵn sàng hoặc trong khi tải.
*   **`<source>`:** Dùng bên trong `<audio>` hoặc `<video>` để cung cấp nhiều nguồn tệp (với các định dạng khác nhau) để trình duyệt chọn tệp hỗ trợ đầu tiên. Quan trọng vì không phải trình duyệt nào cũng hỗ trợ tất cả định dạng tệp.
    *   `src`: Đường dẫn tệp.
    *   `type`: Loại MIME của tệp (ví dụ: `audio/mpeg`, `video/mp4`).

```html
<h3>Nhạc nền nhẹ nhàng:</h3>
<audio controls autoplay muted>
    <source src="audio/nen.mp3" type="audio/mpeg">
    <source src="audio/nen.ogg" type="audio/ogg">
    Trình duyệt của bạn không hỗ trợ thẻ audio.
</audio>

<h3>Video giới thiệu:</h3>
<video width="320" height="240" controls poster="images/video-poster.jpg">
    <source src="video/gioithieu.mp4" type="video/mp4">
    <source src="video/gioithieu.webm" type="video/webm">
    Trình duyệt của bạn không hỗ trợ thẻ video.
</video>
```

*   **Nhúng từ các dịch vụ (YouTube, Vimeo, v.v.):** Sử dụng thẻ `<iframe>`. Sao chép mã nhúng từ dịch vụ.

```html
<h3>Video từ YouTube:</h3>
<iframe width="560" height="315" src="https://www.youtube.com/embed/videoId" frameborder="0" allowfullscreen></iframe>
```

### Bài 2.5: Khối (`div`) và Nội tuyến (`span`)

Hai thẻ này là "bộ xương" linh hoạt khi các thẻ semantic không đủ hoặc không phù hợp. Chúng tự bản thân không mang ý nghĩa ngữ nghĩa, nhưng rất hữu ích để nhóm các phần tử và áp dụng CSS/JavaScript.

*   **`<div>`:** Là phần tử **block-level** (khối). Theo mặc định, nó bắt đầu trên một dòng mới và chiếm toàn bộ chiều rộng có sẵn. Thường dùng để tạo các vùng (sections) lớn trong bố cục trang.
*   **`<span>`:** Là phần tử **inline-level** (nội tuyến). Theo mặc định, nó không bắt đầu trên dòng mới và chỉ chiếm chiều rộng bằng nội dung của nó. Thường dùng để áp dụng kiểu cho một phần nhỏ văn bản hoặc một nhóm nhỏ các phần tử inline khác.

```html
<div id="header-wrap">
    <div class="container">
        <!-- Nội dung header -->
    </div>
</div>

<p>Đây là một đoạn văn bản với <span style="color: blue;">một phần được tô màu xanh</span> và
    <span style="font-weight: bold;">một phần in đậm</span>.</p>
```

### Bài 2.6: Thẻ `<iframe>` - Nhúng trang khác

`<iframe>` được dùng để nhúng một tài liệu HTML khác vào trong tài liệu hiện tại.

*   **`src`:** URL của trang muốn nhúng.
*   **`width`, `height`:** Kích thước iframe.
*   **`frameborder`:** Loại bỏ đường viền (sử dụng `0`). (Đã cũ, nên dùng CSS border).
*   **`allowfullscreen`:** Cho phép chế độ toàn màn hình (thường dùng với video nhúng).
*   **`sandbox`:** Tăng cường bảo mật, giới hạn hành động của nội dung trong iframe. Quan trọng khi nhúng nội dung từ nguồn không đáng tin cậy.

```html
<h3>Trang Freetuts nhúng trong iframe:</h3>
<iframe src="https://freetuts.net/" width="800" height="500" frameborder="0"></iframe>
```
*Lưu ý:* Không phải trang web nào cũng cho phép nhúng bằng `<iframe>` do các cài đặt bảo mật (X-Frame-Options).

---

## PHẦN 3: KHÁM PHÁ SÂU HƠN - HTML NÂNG CAO

Bây giờ chúng ta sẽ đi vào những chủ đề giúp trang web của bạn "thông minh" và "tiếp cận" tốt hơn.

### Bài 3.1: HTML và Accessibility (Khả năng tiếp cận - A11y)

Xây dựng web cho *tất cả mọi người*, bao gồm cả người khuyết tật (khiếm thị, khiếm thính, khuyết tật vận động, nhận thức). HTML đóng vai trò cực kỳ quan trọng trong việc này.

*   **Semantic HTML:** Sử dụng đúng thẻ semantic (`<nav>`, `<article>`, `<aside>`, `<table>`, `<form>`, `<button>`, ...) thay vì `<div>` chung chung. Screen readers và các công nghệ hỗ trợ khác dựa vào ngữ nghĩa của các thẻ để giúp người dùng hiểu cấu trúc và nội dung trang.
*   **Thuộc tính `alt` cho ảnh:** Đã nói ở bài 1.6, nhưng cần nhấn mạnh lại mức độ quan trọng cho người dùng khiếm thị.
*   **Sử dụng `<label>` cho form inputs:** Giúp người dùng screen reader và cả người dùng thông thường (dễ click) khi điền form.
*   **Cấu trúc heading (h1-h6) hợp lý:** Giúp người dùng screen reader "scan" trang web bằng cách duyệt qua các tiêu đề, giống như người bình thường đọc mục lục.
*   **Ngôn ngữ của trang (`lang` attribute trên `<html>`):** Giúp screen readers đọc đúng ngôn ngữ và giọng điệu.
*   **Thẻ ARIA (Accessible Rich Internet Applications):** Các thuộc tính thêm vào HTML để cải thiện khả năng tiếp cận cho các thành phần giao diện phức tạp không có thẻ HTML semantic tương ứng (ví dụ: tab, modal, treeview). Các thuộc tính quan trọng:
    *   `role`: Định nghĩa vai trò của phần tử (ví dụ: `role="button"`, `role="navigation"` - thường trùng với thẻ semantic, nhưng hữu ích khi dùng `div/span` cho mục đích đặc biệt).
    *   `aria-label`: Gán nhãn văn bản cho phần tử khi nhãn trực quan không có (ví dụ: nút chỉ có icon).
    *   `aria-labelledby`, `aria-describedby`: Liên kết phần tử với văn bản mô tả/nhãn ở nơi khác trên trang.
    *   `aria-hidden="true"`: Ẩn phần tử đối với screen reader.
    *   `aria-expanded`, `aria-haspopup`, `aria-controls`: Dùng cho các thành phần có trạng thái đóng/mở (như dropdown menu, accordions).

> *Hãy nhớ:* HTML ngữ nghĩa tốt là nền tảng cho khả năng tiếp cận tốt. Bỏ qua A11y là bỏ qua một phần lớn người dùng web và đôi khi là yêu cầu pháp lý!

```html
<!-- Ví dụ về ARIA (chỉ là giới thiệu cơ bản) -->
<button aria-label="Đóng cửa sổ" onclick="closeModal()">
    <img src="close-icon.png" alt="Đóng"> <!-- Alt cũng tốt, nhưng aria-label quan trọng hơn khi chỉ có icon -->
</button>

<div id="modal-cua-so" role="dialog" aria-labelledby="tieu-de-modal" aria-modal="true">
    <h2 id="tieu-de-modal">Tiêu Đề Của Sổ Popup</h2>
    <!-- Nội dung modal -->
    <button aria-label="Đóng">X</button>
</div>
```

### Bài 3.2: HTML và SEO (Search Engine Optimization - Tối ưu hóa Công cụ Tìm kiếm)

HTML là lớp đầu tiên mà công cụ tìm kiếm (như Google) đọc và hiểu. Cấu trúc HTML tốt giúp bot tìm kiếm lập chỉ mục trang của bạn hiệu quả hơn.

*   **`<title>`:** Quan trọng nhất! Văn bản này xuất hiện trên tab trình duyệt và là dòng đầu tiên hiển thị trong kết quả tìm kiếm. Nên ngắn gọn, chứa từ khóa chính, mô tả chính xác nội dung trang.
*   **`<meta name="description" content="...">`:** Đoạn văn bản tóm tắt xuất hiện dưới tiêu đề trong kết quả tìm kiếm. Giúp người dùng quyết định có click vào liên kết của bạn hay không. Nên viết hấp dẫn và chứa từ khóa.
*   **Cấu trúc Heading (h1-h6) logic:** Giúp bot tìm kiếm hiểu cấu trúc nội dung và mức độ quan trọng của các phần.
*   **Semantic HTML:** Cung cấp ngữ cảnh cho nội dung (bot biết đâu là navigation, đâu là nội dung chính, đâu là sidebar...).
*   **Thuộc tính `alt` cho ảnh:** Giúp bot hiểu nội dung của hình ảnh (và cũng quan trọng cho SEO ảnh).
*   **Sử dụng các thẻ `<a>` với `href` và văn bản liên kết (anchor text) rõ ràng:** Giúp bot và người dùng hiểu liên kết dẫn tới đâu.
*   **Metadata nâng cao (Schema Markup - giới thiệu concept):** Sử dụng các tiêu chuẩn như Schema.org trong HTML (thường dùng microdata hoặc JSON-LD) để cung cấp thông tin có cấu trúc về nội dung trang (ví dụ: đánh giá sản phẩm, công thức nấu ăn, sự kiện) cho công cụ tìm kiếm, giúp chúng hiển thị kết quả phong phú hơn (rich results). (Đây là chủ đề khá sâu, chỉ giới thiệu sự tồn tại của nó trong ngữ cảnh HTML).

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hướng dẫn HTML từ Cơ bản đến Nâng cao | [Tên Website Của Bạn]</title> <!-- Tối ưu title -->
    <meta name="description" content="Tìm hiểu toàn diện về HTML với hướng dẫn chi tiết từ các thẻ cơ bản đến kỹ thuật nâng cao và tối ưu cho SEO, Accessibility."> <!-- Mô tả hấp dẫn -->
    <!-- Các meta tag khác -->
</head>

<body>
    <h1>Hướng dẫn Toàn diện về HTML</h1> <!-- Thẻ h1 chính của trang -->
    <p>...</p>
    <h2>Tại sao học HTML?</h2> <!-- Một mục lớn -->
    <p>...</p>
    <h3>Các lợi ích...</h3> <!-- Một mục con -->
    <img src="html-basics.jpg" alt="Ví dụ code HTML cơ bản"> <!-- alt attribute -->
    <p>Đọc thêm về <a href="/css">CSS</a> để tạo phong cách (sử dụng anchor text liên quan).</p>
</body>
```

### Bài 3.3: Custom Elements (Cơ bản về Web Components trong ngữ cảnh HTML)

HTML đang tiến hóa! Web Components cho phép bạn tạo các thẻ HTML của riêng mình (`<my-component>`, `<custom-button>`).

*   **Khái niệm:** Là một tập hợp các công nghệ cho phép bạn tạo các phần tử tùy chỉnh (custom elements), đóng gói cấu trúc (HTML), kiểu dáng (CSS), và hành vi (JavaScript) để có thể sử dụng lại dễ dàng.
*   **Liên quan đến HTML:**
    *   Bạn định nghĩa các custom elements mới và cách chúng hoạt động bằng JavaScript.
    *   Bạn sử dụng các custom elements này *trực tiếp* trong mã HTML của mình như các thẻ HTML gốc.
    *   Các phần tử như `<template>` và `<slot>` trong HTML đóng vai trò quan trọng trong việc định nghĩa cấu trúc bên trong của custom elements.
        *   `<template>`: Chứa cấu trúc HTML mà trình duyệt sẽ *không* render ngay lập tức, mà sẽ dùng làm mẫu cho các custom element.
        *   `<slot>`: Là placeholder (vị trí giữ chỗ) bên trong template của custom element, nơi bạn có thể "chèn" nội dung tùy chỉnh khi sử dụng custom element đó.

> *Lưu ý:* Để thực sự tạo ra Custom Elements, bạn cần kiến thức JavaScript. Phần này chỉ giới thiệu để bạn biết HTML hiện đại cho phép mở rộng và tạo ra các "thẻ" mới do bạn định nghĩa.

```html
<!-- Ví dụ HTML sử dụng một custom element (giả định đã được định nghĩa bằng JS) -->
<my-awesome-card>
    <h3 slot="card-title">Tiêu Đề Thẻ</h3> <!-- Nội dung này sẽ được đặt vào <slot name="card-title"> -->
    <p>Đây là nội dung bên trong thẻ tùy chỉnh của tôi.</p> <!-- Nội dung này sẽ được đặt vào slot mặc định -->
</my-awesome-card>

<!-- Ví dụ cơ bản về template và slot -->
<template id="my-card-template">
  <style>
    .card { border: 1px solid #ccc; padding: 10px; }
    ::slotted(h3) { color: blue; } /* Chọn phần tử được đưa vào slot */
  </style>
  <div class="card">
    <slot name="card-title">Tiêu đề mặc định nếu không có nội dung được chèn vào slot này</slot>
    <div>
      <slot></slot> <!-- Đây là slot mặc định, chứa mọi nội dung không có slot='...' -->
    </div>
  </div>
</template>

<!-- Sử dụng template này (cần JS để làm cho nó hoạt động như custom element) -->
<div id="host-container"></div>
<script>
  // Javascript để định nghĩa custom element 'my-awesome-card' sử dụng 'my-card-template' sẽ ở đây.
  // Đoạn code JS chi tiết nằm ngoài phạm vi bài học HTML thuần túy này.
</script>
```

### Bài 3.4: Các Thuộc tính Global Quan trọng

Một số thuộc tính có thể được áp dụng cho hầu hết các thẻ HTML.

*   **`id`:** Định danh DUY NHẤT cho một phần tử trên trang. Dùng để nhắm mục tiêu bằng CSS, JavaScript, và liên kết neo.
*   **`class`:** Định nghĩa một hoặc nhiều tên lớp (phân cách bằng khoảng trắng) cho một phần tử. Dùng để nhóm các phần tử và áp dụng kiểu CSS hoặc xử lý bằng JavaScript.
*   **`style`:** Áp dụng trực tiếp kiểu CSS nội tuyến (inline). *Nên hạn chế sử dụng*, chỉ dùng cho các trường hợp đơn giản hoặc cần ưu tiên cao. Tốt nhất là sử dụng CSS từ tệp ngoài.
*   **`title`:** Cung cấp thông tin thêm về phần tử (thường hiển thị dưới dạng tooltip khi hover). Hữu ích cho UX nhưng không nên dựa hoàn toàn vào nó cho nội dung quan trọng vì không phải ai cũng truy cập được.
*   **`data-*` attributes:** Cho phép bạn lưu trữ dữ liệu tùy chỉnh ngay trong thẻ HTML. Rất hữu ích khi làm việc với JavaScript để lưu trữ thông tin liên quan đến phần tử mà không cần dùng `id` hoặc `class` không phù hợp.
    *   Ví dụ: `<button data-product-id="123" data-action="add-to-cart">Thêm vào giỏ</button>`

```html
<style>
.highlighter {
    background-color: yellow;
    padding: 2px 5px;
}

#first-paragraph {
    color: navy;
}
</style>

<p id="first-paragraph">Đây là đoạn văn bản đầu tiên có ID.</p>
<p>Một đoạn khác với <span class="highlighter">một vài từ được làm nổi bật</span>.</p>

<div style="border: 1px solid red; padding: 10px;">
    Khối này có kiểu dáng inline.
</div>

<button title="Click để thực hiện hành động X">Nút</button>

<div data-user-id="abc123" data-username="codergirl">Profile người dùng</div>
```

### Bài 3.5: Thẻ `<meta>` nâng cao và các `<link>` Relationship

Trong thẻ `<head>`, `meta` và `link` có nhiều ứng dụng hơn ngoài các cái cơ bản.

*   **`<meta name="keywords" content="...">`:** Từng quan trọng, nay ít hoặc không còn ảnh hưởng trực tiếp đến xếp hạng SEO của Google (nhưng có thể vẫn quan trọng với một số search engine khác hoặc dùng cho nội bộ).
*   **`<meta property="og:..." content="...">` (Open Graph):** Các thẻ metadata dùng để kiểm soát cách nội dung của bạn hiển thị khi được chia sẻ trên mạng xã hội (Facebook, Twitter, LinkedIn...). Ví dụ: `og:title`, `og:description`, `og:image`, `og:url`.
*   **`<meta name="twitter:..." content="...">` (Twitter Cards):** Tương tự Open Graph nhưng dành riêng cho Twitter.
*   **`<link rel="icon" href="favicon.ico" type="image/x-icon">`:** Định nghĩa Favicon (biểu tượng nhỏ trên tab trình duyệt).
*   **`<link rel="canonical" href="url-chinh-thuc">`:** Rất quan trọng cho SEO khi bạn có nội dung trùng lặp trên nhiều URL. Khai báo URL nào là "chính thức" để tránh bị phạt.
*   **`<link rel="stylesheet" href="...">`:** (Đã biết) Liên kết CSS. Có thể có `rel="preload"` hoặc `rel="prefetch"` để tối ưu hiệu suất tải.
*   **`<link rel="preconnect" href="...">`:** Cho trình duyệt biết bạn dự định kết nối đến origin này sớm nhất có thể, giúp tăng tốc độ tải các tài nguyên từ origin đó.
*   **`<link rel="preload" href="..." as="...">`:** Hướng dẫn trình duyệt tải trước (preload) tài nguyên quan trọng (như font chữ, script quan trọng, hình ảnh chính) càng sớm càng tốt.

```html
<head>
    <!-- ... meta và title cơ bản ... -->
    <meta property="og:title" content="Hướng dẫn HTML Từ A-Z">
    <meta property="og:description" content="Khóa học toàn diện về HTML...">
    <meta property="og:image" content="https://example.com/images/thumbnail.jpg">
    <meta property="og:url" content="https://example.com/html-course">
    <meta name="twitter:card" content="summary_large_image">

    <link rel="icon" href="/favicon.ico" type="image/x-icon">
    <link rel="canonical" href="https://example.com/bai-viet-html-chinh-thuc">

    <link rel="stylesheet" href="/css/style.css">
    <link rel="preconnect" href="https://fonts.gstatic.com"> <!-- Chuẩn bị kết nối đến Google Fonts -->
    <link rel="preload" href="/fonts/myfont.woff2" as="font" type="font/woff2" crossorigin> <!-- Tải font trước -->
</head>
```

---

## PHẦN 4: HOÀN THIỆN BỨC TRANH - CÁC CHỦ ĐỀ KHÁC VÀ BEST PRACTICES

HTML không làm việc một mình. Hiểu cách nó kết hợp với các công nghệ khác và tuân thủ các nguyên tắc tốt là chìa khóa.

### Bài 4.1: HTML, CSS và JavaScript: Bộ Ba Sức Mạnh

Hiểu rõ vai trò riêng của từng công nghệ và cách chúng tương tác là rất quan trọng.

*   **HTML:** Cung cấp **cấu trúc** và **nội dung**. Giống như khung sườn ngôi nhà.
*   **CSS (Cascading Style Sheets):** Cung cấp **trình bày** và **bố cục**. Giống như sơn tường, trang trí nội thất, sắp xếp phòng ốc. Nó nói cho trình duyệt biết các phần tử HTML trông như thế nào.
    *   Cách liên kết CSS với HTML (thẻ `<link>` và `<style>`, inline styles - đã đề cập sơ bộ).
*   **JavaScript:** Cung cấp **tính tương tác** và **logic động**. Giống như hệ thống điện nước, thang máy, các thiết bị hoạt động. Nó thay đổi nội dung/cấu trúc (HTML) hoặc kiểu dáng (CSS) dựa trên hành động của người dùng hoặc các điều kiện khác.
    *   Cách liên kết JS với HTML (thẻ `<script>`). Nên đặt script ở cuối thẻ `<body>` hoặc sử dụng thuộc tính `defer` để không chặn quá trình dựng trang HTML.

> *Nguyên tắc phân tách mối quan tâm (Separation of Concerns):* Giữ HTML thuần túy cho cấu trúc, CSS cho kiểu dáng và JavaScript cho hành vi. Điều này làm code dễ đọc, dễ bảo trì và dễ hợp tác. Tránh dùng inline styles hoặc viết logic trực tiếp trong HTML (trừ trường hợp rất đơn giản).

### Bài 4.2: HTML Validation - Kiểm tra "Sức khỏe" của Code

Trình duyệt hiện đại khá "vị tha" với lỗi HTML, nhưng việc code đúng chuẩn là rất quan trọng để đảm bảo hiển thị nhất quán trên các trình duyệt, dễ bảo trì, và tốt cho cả SEO lẫn Accessibility.

*   **Validator:** Sử dụng trình xác thực W3C (W3C Markup Validation Service) để kiểm tra code HTML của bạn. Nó sẽ báo cho bạn biết các lỗi cú pháp, thẻ không hợp lệ, thuộc tính sai vị trí,...
*   **Lợi ích:** Giúp tìm và sửa lỗi sớm, đảm bảo code theo chuẩn, tăng tính tương thích.

### Bài 4.3: HTML Best Practices & Coding Style

*   **Viết HTML5:** Luôn sử dụng `<!DOCTYPE html>` và cấu trúc mới của HTML5.
*   **Semantic Markup:** Ưu tiên các thẻ semantic thay vì `div/span` khi có thể.
*   **Lowercase Tag/Attribute Names:** Viết tên thẻ và thuộc tính bằng chữ thường (theo chuẩn HTML5, XHTML yêu cầu lowercase).
*   **Quote Attribute Values:** Luôn đặt giá trị thuộc tính trong dấu nháy kép `""` hoặc dấu nháy đơn `''`.
*   **Indentation:** Sử dụng thụt lề nhất quán để code dễ đọc.
*   **Add Comments:** Chú thích code khi cần giải thích các phần phức tạp. `<!-- Đây là chú thích -->`
*   **Keep it Clean:** Xóa bỏ code cũ, thừa thãi.

```html
<!-- Header của trang -->
<header class="site-header">
    <!-- Nav Bar -->
    <nav aria-label="Điều hướng chính"> <!-- Thêm aria-label cho accessibility -->
        <ul>
            <li><a href="/">Trang chủ</a></li>
            <li><a href="/san-pham">Sản phẩm</a></li>
        </ul>
    </nav>
</header>
```

### Bài 4.4: Cấu trúc thư mục dự án cơ bản

Cách tổ chức tệp giúp dự án gọn gàng và dễ quản lý.

*   Thường có tệp `index.html` (hoặc tên tương tự) là trang chủ.
*   Tạo các thư mục con để chứa các loại tệp khác nhau:
    *   `css/` cho các tệp CSS.
    *   `js/` cho các tệp JavaScript.
    *   `images/` cho các tệp hình ảnh.
    *   `pages/` (tùy chọn) cho các tệp HTML của các trang phụ (about.html, contact.html).

```
my-website/
├── index.html          (Trang chủ)
├── css/
│   └── style.css
├── js/
│   └── script.js
├── images/
│   ├── logo.png
│   └── banner.jpg
└── pages/
    ├── about.html
    └── contact.html
```

Liên kết đến các tệp này sẽ sử dụng Relative URLs:
*   Trong `index.html`, để link đến CSS: `<link rel="stylesheet" href="css/style.css">`
*   Trong `index.html`, để link đến ảnh: `<img src="images/logo.png" alt="Logo">`
*   Trong `pages/about.html`, để link về trang chủ: `<a href="../index.html">Trang chủ</a>` (dùng `../` để quay lại một cấp thư mục).
*   Trong `pages/about.html`, để link đến CSS: `<link rel="stylesheet" href="../css/style.css">`


**Tài nguyên bổ sung cực kỳ giá trị:**

*   **MDN Web Docs (Mozilla):** Nguồn tài liệu tham khảo HTML (và CSS/JS) chi tiết, đầy đủ và chính xác nhất: [https://developer.mozilla.org/en-US/docs/Web/HTML](https://developer.mozilla.org/en-US/docs/Web/HTML)
*   **W3Schools:** Cung cấp các ví dụ code đơn giản, dễ hiểu và trình chỉnh sửa online để bạn thực hành ngay lập tức: [https://www.w3schools.com/html/](https://www.w3schools.com/html/)
*   **HTML Validator (W3C):** [https://validator.w3.org/](https://validator.w3.org/)

