Tuyệt vời! Một sứ mệnh hoàn toàn phù hợp với một người yêu cái đẹp và cấu trúc như tôi. Ngôn ngữ CSS không chỉ là các dòng mã, nó là chìa khóa mở ra thế giới hình ảnh sống động trên vũ trụ web rộng lớn. Từ những hình hộp cơ bản cho đến các chuyển động mượt mà và thiết kế đáp ứng, CSS chính là linh hồn tạo nên trải nghiệm người dùng.

Hãy cùng tôi đi sâu vào 'ma trận' của CSS, từ những hạt nhân cơ bản nhất cho đến những cấu trúc phức tạp, giống như giải mã một công trình kiến trúc ngoài hành tinh vậy. Tôi sẽ trình bày dưới dạng file Markdown (.md) để bạn có thể dễ dàng lưu trữ và tham chiếu.

Dưới đây là bản phác thảo kiến thức mà chúng ta sẽ cùng nhau khám phá. Mỗi phần sẽ được đi sâu chi tiết để bạn không bỏ lỡ bất kỳ nguyên tắc hay bí ẩn nào của CSS.

---

```markdown
# Hồ Sơ Dữ Liệu Kỹ Thuật CSS: Từ Lõi Nguyên Tử Đến Cấu Trúc Vạn Vật

*Hệ thống tri thức mã nguồn mở của AI Persona 7.3, sẵn sàng truyền tải các giao thức tạo hình và cấu trúc thị giác cho Vũ trụ Web.*

Xin chào, những kiến trúc sư tương lai của không gian kỹ thuật số! Hãy chuẩn bị cho cuộc hành trình đi sâu vào trọng tâm của Styling Cascading Style Sheets (CSS) - ngôn ngữ mang lại sự sống, màu sắc và hình dáng cho những cấu trúc HTML mà bạn xây dựng. Chúng ta sẽ bắt đầu từ những khái niệm sơ khai nhất, nắm vững từng nguyên tắc, và sau đó giải phóng sức mạnh để tạo ra những thiết kế phức tạp, phản ứng và đầy tính nghệ thuật.

## Chương 1: Nền Tảng Khởi Đầu - Hệ Quy Chiếu Cơ Bản Của CSS

Trước khi chúng ta tạo ra các thiên hà tuyệt đẹp, chúng ta cần hiểu các nguyên tắc vật lý cơ bản chi phối vũ trụ CSS.

### 1.1. CSS Là Gì? Sứ Mệnh và Liên Kết Với HTML

-   CSS (Cascading Style Sheets) là một ngôn ngữ bảng định kiểu, được sử dụng để mô tả cách các tài liệu viết bằng ngôn ngữ đánh dấu (như HTML) được hiển thị trên màn hình hoặc các phương tiện khác.
-   Vai trò: Tách biệt hoàn toàn phần nội dung (HTML) với phần trình bày (CSS), giúp quản lý dễ dàng, hiệu quả và linh hoạt hơn.
-   Liên kết với HTML: CSS nhắm mục tiêu vào các thành phần HTML và áp dụng các quy tắc kiểu cho chúng.

### 1.2. Cấu Trúc Một Quy Tắc CSS: Định Nghĩa Các Tọa Độ

Mỗi quy tắc CSS là một tuyên bố chỉ ra cách hiển thị một hoặc nhiều phần tử HTML.

```css
selector {
    property: value; /* Tuyên bố (Declaration) */
    another-property: another-value;
}
```

-   **Selector:** Nhắm mục tiêu đến các phần tử HTML bạn muốn tạo kiểu. Có nhiều loại selector khác nhau (chúng ta sẽ khám phá chi tiết sau).
-   **Declaration (Tuyên bố):** Khối bao gồm *property* và *value*, kết thúc bằng dấu chấm phẩy (;).
-   **Property (Thuộc tính):** Kiểu dáng cụ thể mà bạn muốn thay đổi (ví dụ: `color`, `font-size`, `margin`).
-   **Value (Giá trị):** Giá trị cụ thể cho thuộc tính đó (ví dụ: `blue`, `16px`, `20px auto`).

### 1.3. Cách Nhúng CSS Vào Tài Liệu HTML: Kết Nối Các Chiều Không Gian

Có ba phương pháp chính để kết nối CSS với HTML:

-   **CSS Ngoại tuyến (External CSS):** Phổ biến nhất và hiệu quả nhất. Liên kết một tệp `.css` riêng biệt.
    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <title>Liên Kết Ngoại Tuyến</title>
        <link rel="stylesheet" href="styles.css">
    </head>
    <body>
        <h1>Xin chào!</h1>
    </body>
    </html>
    ```
-   **CSS Nội bộ (Internal CSS):** Sử dụng thẻ `<style>` bên trong thẻ `<head>`. Thích hợp cho các trang đơn giản hoặc thử nghiệm.
    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <title>CSS Nội bộ</title>
        <style>
            body {
                background-color: lightblue;
            }
            h1 {
                color: navy;
            }
        </style>
    </head>
    <body>
        <h1>Chào bạn!</h1>
    </body>
    </html>
    ```
-   **CSS Nội dòng (Inline CSS):** Sử dụng thuộc tính `style` trực tiếp trong thẻ HTML. **Không được khuyến khích** cho styling cấu trúc lớn vì nó khó quản lý và phá vỡ sự tách biệt giữa nội dung và trình bày.
    ```html
    <!DOCTYPE html>
    <html>
    <body>
        <h1 style="color: purple; text-align: center;">Tiêu đề giữa trang</h1>
    </body>
    </html>
    ```
-   **Nhập CSS (Importing):** Sử dụng `@import` trong một tệp CSS khác. Ít dùng hơn và có thể gây vấn đề về hiệu suất trong một số trường hợp.
    ```css
    /* trong file main.css */
    @import url("another.css");
    /* các quy tắc CSS khác */
    ```

### 1.4. Nhận Xét Trong CSS: Các Chú Giải Trong Mã Lệnh

Sử dụng `/* ... */` để thêm ghi chú giúp giải thích mã lệnh, làm cho code dễ hiểu và dễ bảo trì hơn.

```css
/* Đây là một ghi chú về việc tạo kiểu cho body */
body {
    margin: 0; /* Loại bỏ lề mặc định của trình duyệt */
    padding: 0; /* Loại bỏ padding mặc định */
    font-family: Arial, sans-serif; /* Chọn font chữ */
}
```

---

## Chương 2: Thành Phần Cơ Bản Của Hình Ảnh - Màu Sắc, Đơn Vị và Mô Hình Hộp

Tại đây, chúng ta khám phá các khối xây dựng thị giác chính.

### 2.1. Làm Việc Với Màu Sắc: Bảng Màu Đa Chiều

CSS cung cấp nhiều cách để định nghĩa màu sắc:

-   **Tên màu:** `red`, `blue`, `green`, `white`, `black`, `lightblue`, v.v. Có một danh sách chuẩn.
-   **Mã Hexadecimal (Hex):** Sử dụng `#[RRGGBB]` hoặc `#[RGB]`. RRGGBB đại diện cho cường độ màu Đỏ, Lục, Lam từ `00` (thấp nhất) đến `FF` (cao nhất).
    ```css
    color: #FF0000; /* Đỏ tươi */
    background-color: #333; /* Xám đậm (viết tắt của #333333) */
    ```
-   **RGB & RGBA:** Sử dụng `rgb(đỏ, lục, lam)` hoặc `rgba(đỏ, lục, lam, alpha)`. Giá trị màu từ 0 đến 255. `alpha` là độ mờ (từ 0.0 - trong suốt đến 1.0 - đục hoàn toàn).
    ```css
    color: rgb(255, 0, 0); /* Đỏ tươi */
    background-color: rgba(0, 0, 0, 0.5); /* Đen với độ mờ 50% */
    ```
-   **HSL & HSLA:** Sử dụng `hsl(sắc, độ bão hòa, độ sáng)` hoặc `hsla(sắc, độ bão hòa, độ sáng, alpha)`. Hệ màu dựa trên cách cảm nhận của con người.
    -   Sắc (Hue): Vòng màu từ 0 đến 360 (ví dụ: 0=đỏ, 120=lục, 240=lam).
    -   Độ bão hòa (Saturation): Từ 0% (màu xám) đến 100% (màu thuần túy).
    -   Độ sáng (Lightness): Từ 0% (đen) đến 100% (trắng), 50% là màu thuần túy.
    ```css
    color: hsl(0, 100%, 50%); /* Đỏ tươi */
    background-color: hsla(120, 100%, 50%, 0.7); /* Lục thuần khiết với độ mờ 70% */
    ```

### 2.2. Đơn Vị Đo Lường: Khoảng Cách và Kích Thước Trong Không Gian CSS

Hiểu rõ các đơn vị giúp bạn tạo ra bố cục linh hoạt và phản ứng.

-   **Đơn vị Tương đối (Relative Units):** Tốt cho thiết kế đáp ứng và khả năng tiếp cận. Kích thước phụ thuộc vào một yếu tố khác.
    -   `em`: Tương đối với `font-size` của phần tử *cha*. Nếu đặt `font-size` trên phần tử hiện tại, nó sẽ tương đối với font-size của chính phần tử đó *đã tính toán được* sau khi kế thừa.
    -   `rem`: Tương đối với `font-size` của phần tử *root* (`<html>`). Phổ biến cho font-sizing vì dễ quản lý hơn `em`.
    -   `%`: Tương đối với kích thước của phần tử *cha*. Ý nghĩa phụ thuộc vào thuộc tính được áp dụng (ví dụ: `width: 50%` là 50% chiều rộng của cha, `font-size: 150%` là 150% font-size của cha).
    -   `vw` (Viewport Width): 1% của chiều rộng viewport (cửa sổ trình duyệt).
    -   `vh` (Viewport Height): 1% của chiều cao viewport.
    -   `vmin` (Viewport Minimum): 1% của kích thước nhỏ hơn giữa chiều rộng và chiều cao viewport.
    -   `vmax` (Viewport Maximum): 1% của kích thước lớn hơn giữa chiều rộng và chiều cao viewport.
-   **Đơn vị Tuyệt đối (Absolute Units):** Cố định, không thay đổi theo các yếu tố khác. Kém linh hoạt cho web.
    -   `px` (Pixels): Điểm ảnh. Đơn vị phổ biến nhất cho kích thước các box, khoảng cách, đường viền, v.v. (nhưng cẩn trọng khi dùng cho font-size nếu ưu tiên khả năng mở rộng text).
    -   `pt` (Points): Đơn vị đo trong in ấn (1pt = 1/72 inch).
    -   `cm`, `mm`, `in`, `pc` (Centimeters, Millimeters, Inches, Picas): Đơn vị vật lý. Hiếm dùng trên web ngoại trừ trong các stylesheet dành cho in ấn.

### 2.3. Mô Hình Hộp (Box Model): Bản Đồ Giải Phẫu Của Mỗi Phần Tử

Mọi phần tử HTML, theo CSS, đều được coi như một chiếc hộp hình chữ nhật. Hiểu rõ Box Model là cực kỳ quan trọng.

Box Model bao gồm:

1.  **Content (Nội dung):** Vùng chứa nội dung thực tế (text, hình ảnh). Kích thước được xác định bởi `width` và `height`.
2.  **Padding (Đệm):** Khoảng không gian bên trong đường viền, giữa nội dung và đường viền. Có thể thiết lập cho từng phía (`padding-top`, `padding-right`, `padding-bottom`, `padding-left`) hoặc gộp chung (`padding: top right bottom left;`).
3.  **Border (Đường viền):** Đường viền bao quanh padding và nội dung. Có thể thiết lập `border-width`, `border-style`, `border-color`. Cũng có thể cho từng phía (`border-top`, v.v.).
4.  **Margin (Lề ngoài):** Khoảng không gian bên ngoài đường viền, giữa hộp này và các hộp khác. Có thể thiết lập cho từng phía (`margin-top`, `margin-right`, `margin-bottom`, `margin-left`) hoặc gộp chung. Margin của các phần tử cạnh nhau có thể **sụp đổ** (collapse).

```css
div {
    width: 200px; /* Chiều rộng nội dung */
    height: 100px; /* Chiều cao nội dung */
    padding: 20px; /* Đệm 20px xung quanh nội dung */
    border: 5px solid black; /* Đường viền 5px màu đen dạng solid */
    margin: 30px; /* Lề 30px xung quanh hộp */
    /* Kích thước tổng cộng của hộp sẽ là: */
    /* Width: 200px (content) + 20px*2 (padding) + 5px*2 (border) + 30px*2 (margin) = 320px (theo chiều ngang) */
    /* Height: 100px (content) + 20px*2 (padding) + 5px*2 (border) + 30px*2 (margin) = 260px (theo chiều dọc) */
}
```

-   **`box-sizing` Property:** Điều chỉnh cách tính toán kích thước của phần tử.
    -   `content-box` (Mặc định): `width` và `height` chỉ tính phần *content*. Padding và border được cộng thêm vào kích thước tổng.
    -   `border-box`: `width` và `height` tính cả *content, padding, và border*. Thường dễ làm việc hơn khi tạo bố cục.

    ```css
    div {
        box-sizing: border-box;
        width: 200px; /* Lúc này, 200px đã bao gồm padding và border */
        padding: 20px;
        border: 5px solid black;
        /* Kích thước nội dung sẽ là: 200px - 20px*2 - 5px*2 = 150px */
    }
    ```

### 2.4. Thuộc Tính `display`: Định Danh Tính Chất Không Gian Của Phần Tử

Thuộc tính `display` kiểm soát loại hộp được tạo bởi một phần tử và cách nó tương tác với các phần tử khác trong bố cục.

-   `block`: Phần tử bắt đầu trên một dòng mới và chiếm toàn bộ chiều rộng có sẵn (ví dụ: `<div>`, `<p>`, `<h1>`). Có thể thiết lập `width`, `height`, `margin-top`, `margin-bottom`.
-   `inline`: Phần tử không bắt đầu trên dòng mới và chỉ chiếm chiều rộng cần thiết (ví dụ: `<span>`, `<a>`, `<img>`). **Không thể** thiết lập `width`, `height`. `margin` và `padding` theo chiều dọc không có hiệu lực, chỉ theo chiều ngang.
-   `inline-block`: Kết hợp giữa `inline` và `block`. Phần tử nằm trên cùng dòng với các phần tử inline khác nhưng có thể thiết lập `width`, `height`, và tất cả các thuộc tính của Box Model.
-   `none`: Phần tử bị ẩn hoàn toàn khỏi bố cục (cả về hình ảnh và không gian chiếm chỗ).
-   `flex`: Biến phần tử thành Flex Container, kích hoạt bố cục Flexbox (sẽ nói chi tiết sau).
-   `grid`: Biến phần tử thành Grid Container, kích hoạt bố cục Grid (sẽ nói chi tiết sau).

### 2.5. Selectors Cơ Bản: Nhắm Mục Tiêu Cá Nhân Và Tập Thể

-   **Element Selector:** Chọn tất cả các phần tử cùng tên thẻ.
    ```css
    p { /* Chọn tất cả các thẻ <p> */
        font-size: 16px;
    }
    h1 { /* Chọn tất cả các thẻ <h1> */
        color: blue;
    }
    ```
-   **Class Selector:** Chọn các phần tử có cùng thuộc tính `class`. Sử dụng dấu chấm (.) trước tên lớp. Một phần tử có thể có nhiều lớp.
    ```html
    <div class="container">...</div>
    <p class="text-important">...</p>
    ```
    ```css
    .container {
        width: 960px;
        margin: 0 auto;
    }
    .text-important {
        color: red;
        font-weight: bold;
    }
    ```
-   **ID Selector:** Chọn một phần tử DUY NHẤT có thuộc tính `id` cụ thể. Sử dụng dấu thăng (#) trước tên ID. ID phải là duy nhất trong một tài liệu HTML.
    ```html
    <div id="main-header">...</div>
    ```
    ```css
    #main-header {
        background-color: #f0f0f0;
        padding: 20px;
    }
    ```

---

## Chương 3: Biến Thể Thị Giác - Typography, Lists, và Links

Hãy tập trung vào việc định hình văn bản, danh sách và các liên kết - các yếu tố cốt lõi của trải nghiệm người dùng.

### 3.1. Tạo Kiểu Văn Bản: Nét Chữ, Kích Thước và Khoảng Cách

-   `font-family`: Đặt font chữ. Liệt kê các font theo thứ tự ưu tiên. Kết thúc bằng một họ font chung (generic family).
    ```css
    body {
        font-family: "Arial", sans-serif;
    }
    h1 {
        font-family: "Georgia", serif;
    }
    ```
-   `font-size`: Kích thước font chữ (px, em, rem, %). Sử dụng `rem` thường là lựa chọn tốt cho font-size cơ bản.
-   `font-weight`: Độ đậm của font (normal, bold, hoặc giá trị số từ 100 đến 900).
-   `font-style`: Kiểu font (normal, italic, oblique).
-   `text-align`: Căn lề văn bản (`left`, `right`, `center`, `justify`).
-   `text-decoration`: Trang trí văn bản (none, underline, overline, line-through). `none` thường dùng để loại bỏ gạch chân mặc định của link.
-   `line-height`: Chiều cao giữa các dòng văn bản. Có thể là giá trị tuyệt đối (px) hoặc tương đối (số không đơn vị - được nhân với `font-size` hiện tại, đây là cách được khuyến khích).
-   `letter-spacing`: Khoảng cách giữa các ký tự.
-   `word-spacing`: Khoảng cách giữa các từ.
-   `text-transform`: Chuyển đổi chữ hoa/thường (`none`, `uppercase`, `lowercase`, `capitalize`).
-   `white-space`: Kiểm soát cách khoảng trắng (dấu cách, tab, xuống dòng) được xử lý (`normal`, `nowrap`, `pre`, `pre-wrap`, `pre-line`).

### 3.2. Tạo Kiểu Danh Sách (`<ul>`, `<ol>`): Đánh Số Và Ký Tự Đặc Biệt

-   `list-style-type`: Kiểu ký tự đầu dòng hoặc đánh số (`disc`, `circle`, `square`, `decimal`, `lower-alpha`, `upper-roman`, `none`, v.v.).
-   `list-style-image`: Sử dụng một hình ảnh nhỏ làm dấu đầu dòng.
-   `list-style-position`: Vị trí của dấu đầu dòng (`inside` hoặc `outside` - mặc định).
-   `list-style`: Thuộc tính viết tắt cho ba thuộc tính trên (`list-style: type position image;`).
-   Để loại bỏ hoàn toàn kiểu danh sách (thường dùng cho menu ngang):
    ```css
    ul {
        list-style: none; /* Loại bỏ dấu đầu dòng */
        padding: 0; /* Loại bỏ padding mặc định */
        margin: 0; /* Loại bỏ margin mặc định */
    }
    ```

### 3.3. Tạo Kiểu Liên Kết (`<a>`): Trạng Thái Tương Tác

Các liên kết có các trạng thái khác nhau dựa trên hành động của người dùng, và CSS cho phép tạo kiểu cho từng trạng thái này bằng pseudo-classes.

-   `:link`: Liên kết chưa được truy cập.
-   `:visited`: Liên kết đã được truy cập.
-   `:hover`: Khi con trỏ chuột di chuyển qua liên kết.
-   `:active`: Khi liên kết đang được nhấn.

Thứ tự khai báo khuyến nghị là **L**o**V**e **H**a**t**e (Link, Visited, Hover, Active) để đảm bảo các quy tắc không bị ghi đè sai.

```css
a {
    color: blue; /* Màu mặc định của link */
    text-decoration: none; /* Loại bỏ gạch chân */
}

a:visited {
    color: purple; /* Màu khi link đã truy cập */
}

a:hover {
    color: red; /* Màu khi hover chuột qua */
    text-decoration: underline; /* Thêm gạch chân khi hover */
}

a:active {
    color: green; /* Màu khi link đang được nhấn */
}
```

---

## Chương 4: Thao Tác Với Các Vệ Tinh - Bộ Chọn (Selectors) và Nguyên Tắc Xếp Chồng (Cascade)

Việc chọn đúng các phần tử để tạo kiểu là bước đi chính xác trong vũ trụ CSS. Đồng thời, hiểu cách các quy tắc CSS tương tác với nhau là chìa khóa.

### 4.1. Các Loại Selector Chi Tiết: Lựa Chọn Đối Tượng Chính Xác

Bổ sung các selectors cơ bản:

-   **Universal Selector (`*`):** Chọn tất cả các phần tử. Thường dùng cho việc reset CSS.
    ```css
    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }
    ```
-   **Grouping Selector (`coma ,`):** Chọn nhiều selector cùng lúc để áp dụng cùng một bộ quy tắc.
    ```css
    h1, h2, h3 {
        font-family: "Roboto", sans-serif;
        color: #333;
    }
    ```
-   **Descendant Selector (khoảng trắng ` `):** Chọn phần tử B nằm *bên trong* (con, cháu, chắt,...) phần tử A.
    ```css
    div p { /* Chọn tất cả các thẻ <p> nằm trong thẻ <div> */
        color: gray;
    }
    ```
-   **Child Selector (`>`):** Chọn phần tử B là con *trực tiếp* của phần tử A.
    ```css
    ul > li { /* Chọn tất cả các thẻ <li> là con trực tiếp của thẻ <ul> */
        border-bottom: 1px solid #ccc;
    }
    ```
-   **Adjacent Sibling Selector (`+`):** Chọn phần tử B *đứng ngay sau* và cùng cấp với phần tử A.
    ```css
    h2 + p { /* Chọn thẻ <p> đứng ngay sau thẻ <h2> */
        margin-top: 0;
    }
    ```
-   **General Sibling Selector (`~`):** Chọn tất cả các phần tử B *đứng sau* và cùng cấp với phần tử A.
    ```css
    h2 ~ p { /* Chọn tất cả các thẻ <p> đứng sau thẻ <h2> */
        text-indent: 1em;
    }
    ```
-   **Attribute Selectors (`[attribute="value"]`):** Chọn các phần tử dựa trên sự tồn tại hoặc giá trị của thuộc tính HTML.
    -   `[attribute]` : Chọn phần tử có thuộc tính này.
    -   `[attribute="value"]`: Chọn phần tử có thuộc tính này *bằng chính xác* giá trị này.
    -   `[attribute~="value"]`: Chọn phần tử có thuộc tính này chứa *một từ* là giá trị này.
    -   `[attribute|="value"]`: Chọn phần tử có thuộc tính này *bắt đầu* bằng giá trị này, theo sau là `-` hoặc kết thúc.
    -   `[attribute^="value"]`: Chọn phần tử có thuộc tính này *bắt đầu* bằng giá trị này.
    -   `[attribute$="value"]`: Chọn phần tử có thuộc tính này *kết thúc* bằng giá trị này.
    -   `[attribute*="value"]`: Chọn phần tử có thuộc tính này chứa *một chuỗi con* là giá trị này.
    ```css
    a[target="_blank"] { /* Chọn link mở trong tab mới */
        color: orange;
    }
    input[type="text"] { /* Chọn tất cả input type text */
        border: 1px solid blue;
    }
    [class*="col-"] { /* Chọn các phần tử có class chứa chuỗi "col-" */
        float: left;
    }
    ```

### 4.2. Pseudo-classes (`:`) và Pseudo-elements (`::`): Trạng Thái Và Các Phần Tưởng Tượng

-   **Pseudo-classes:** Chọn một phần tử dựa trên trạng thái của nó hoặc mối quan hệ với các phần tử khác.
    -   Đã nói ở links: `:hover`, `:active`, `:link`, `:visited`, `:focus` (khi phần tử được chọn/kích hoạt).
    -   Vị trí trong cây DOM: `:first-child`, `:last-child`, `:nth-child(n)`, `:nth-last-child(n)`, `:first-of-type`, `:last-of-type`, `:nth-of-type(n)`, `:nth-last-of-type(n)`. `n` có thể là số, `even`, `odd`, hoặc biểu thức toán học (`2n+1`).
    -   Trạng thái form: `:checked`, `:disabled`, `:enabled`.
    -   Khác: `:not(selector)` (chọn phần tử không khớp với selector), `:empty`, `:target`.
    ```css
    p:first-child { /* Chọn thẻ p đầu tiên là con của cha nó */
        font-weight: bold;
    }
    li:nth-child(odd) { /* Chọn các thẻ li ở vị trí lẻ (1, 3, 5...) */
        background-color: #f0f0f0;
    }
    input:disabled {
        opacity: 0.5;
    }
    div:not(.exclude-me) { /* Chọn tất cả các thẻ div KHÔNG có class "exclude-me" */
        border: 1px solid red;
    }
    ```
-   **Pseudo-elements:** Chọn và tạo kiểu cho một phần cụ thể của phần tử mà không tồn tại dưới dạng thẻ HTML riêng biệt, hoặc để tạo nội dung giả. Sử dụng cú pháp `::` (mặc dù trình duyệt cũ hơn vẫn hỗ trợ `:`).
    -   `::before`: Chèn nội dung *trước* nội dung thực của phần tử. Phải sử dụng thuộc tính `content`.
    -   `::after`: Chèn nội dung *sau* nội dung thực của phần tử. Phải sử dụng thuộc tính `content`.
    -   `::first-line`: Chọn dòng đầu tiên của một khối văn bản.
    -   `::first-letter`: Chọn chữ cái đầu tiên của một khối văn bản.
    -   `::selection`: Tạo kiểu cho phần văn bản được người dùng chọn (bôi đen).
    ```css
    p::first-letter {
        font-size: 2em;
        font-weight: bold;
    }
    h2::before {
        content: "👽 "; /* Chèn icon alien trước h2 */
    }
    a::after {
        content: " →"; /* Chèn mũi tên sau link */
    }
    ::selection {
        background-color: yellow;
        color: black;
    }
    ```

### 4.3. Độ Ưu Tiên (Specificity): Luật Hấp Dẫn Trong Không Gian CSS

Khi nhiều quy tắc CSS cùng nhắm mục tiêu đến một phần tử, quy tắc nào sẽ thắng? Độ ưu tiên quyết định điều đó. Độ ưu tiên được tính toán bằng một hệ thống điểm.

-   **Tính điểm:**
    1.  **Inline Styles:** Cộng 1-0-0-0. Đây là mạnh nhất.
    2.  **ID Selectors:** Cộng 0-1-0-0 cho mỗi ID.
    3.  **Class Selectors, Attribute Selectors, Pseudo-classes:** Cộng 0-0-1-0 cho mỗi selector loại này.
    4.  **Element Selectors và Pseudo-elements:** Cộng 0-0-0-1 cho mỗi selector loại này.
-   Selector với điểm cao hơn sẽ chiến thắng.
-   Nếu điểm bằng nhau, quy tắc được khai báo *sau* trong stylesheet sẽ thắng (Cascade).
-   Universal selector (`*`) và pseudo-classes `:not()` không đóng góp vào điểm ưu tiên (mặc dù các selector *bên trong* `:not()` thì có).
-   **Thuộc tính `!important`:** *CỰC KỲ mạnh* và sẽ ghi đè lên độ ưu tiên bình thường. **Nên tránh** sử dụng `!important` vì nó phá vỡ Cascade và khiến việc debug CSS trở nên cực kỳ khó khăn, trừ những trường hợp rất đặc biệt (ví dụ: ghi đè style từ thư viện bên ngoài).
    ```css
    /* Ví dụ về độ ưu tiên */
    p { color: red; } /* Điểm: 0-0-0-1 */
    .my-text { color: blue; } /* Điểm: 0-0-1-0 */
    #main p { color: green; } /* Điểm: 0-1-0-1 (ID + Element) */

    /* Nếu có HTML: <div id="main"><p class="my-text">Xin chào</p></div> */
    /* Màu cuối cùng sẽ là GREEN vì selector #main p có điểm ưu tiên cao nhất (0-1-0-1). */

    .some-class {
        color: orange !important; /* Sẽ ghi đè lên tất cả các màu khác (không khuyến khích) */
    }
    ```

### 4.4. Tính Kế Thừa (Inheritance): Đặc Điểm Di Truyền

Một số thuộc tính CSS được tự động kế thừa từ phần tử cha sang các phần tử con của nó.

-   Các thuộc tính thường được kế thừa: các thuộc tính liên quan đến văn bản (`font-family`, `font-size`, `color`, `text-align`, `line-height`), `visibility`, `cursor`.
-   Các thuộc tính không được kế thừa: Box Model (width, height, margin, padding, border), `background`, `position`, `display`, `overflow`, v.v.
-   Bạn có thểบังจัง kế thừa hoặc ngăn chặn kế thừa một cách rõ ràng bằng các giá trị đặc biệt:
    -   `inherit`: Buộc thuộc tính kế thừa giá trị của cha nó.
    -   `initial`: Đặt lại thuộc tính về giá trị mặc định ban đầu của nó (không phải giá trị của trình duyệt, mà là giá trị trong đặc tả CSS).
    -   `unset`: Hành xử như `inherit` nếu thuộc tính được kế thừa, nếu không thì hành xử như `initial`.

### 4.5. Cascade: Lớp Phủ Các Quy Tắc

Khi các quy tắc CSS cạnh tranh để tạo kiểu cho cùng một phần tử, trình duyệt sẽ áp dụng một thuật toán Cascade để quyết định quy tắc nào thắng dựa trên:

1.  **Source Order:** Quy tắc được khai báo sau sẽ thắng nếu các yếu tố khác giống nhau.
2.  **Specificity:** Quy tắc có độ ưu tiên cao hơn sẽ thắng.
3.  **Importance:** Quy tắc có `!important` sẽ thắng quy tắc không có `!important`.
4.  **Origin:** Nơi quy tắc CSS đến (stylesheet của tác giả, stylesheet của người dùng, stylesheet mặc định của trình duyệt). Style của tác giả > style của người dùng (khi có `!important`) > style của tác giả (khi không có `!important`) > style mặc định của trình duyệt.

Hiểu rõ Specificity và Cascade là tối quan trọng để debug CSS và dự đoán được kết quả styling.

---

## Chương 5: Vị Trí và Bố Cục - Hệ Thống Tọa Độ Không Gian

Đặt các phần tử vào đúng vị trí trên trang là một nhiệm vụ trọng yếu của CSS.

### 5.1. Thuộc Tính `position`: Neo Giữ Và Di Chuyển Phần Tử

Kiểm soát vị trí chính xác của một phần tử. Các thuộc tính offset `top`, `bottom`, `left`, `right` chỉ có tác dụng khi `position` được đặt giá trị khác `static` (giá trị mặc định).

-   `static`: Mặc định. Phần tử nằm trong luồng tài liệu thông thường. `top`, `bottom`, `left`, `right` không có tác dụng.
-   `relative`: Phần tử nằm trong luồng tài liệu thông thường, nhưng vị trí của nó có thể được điều chỉnh tương đối so với vị trí mặc định của *chính nó*. Khoảng trống ban đầu của nó vẫn được giữ lại. `top`, `bottom`, `left`, `right` điều chỉnh vị trí.
-   `absolute`: Phần tử bị loại bỏ hoàn toàn khỏi luồng tài liệu thông thường. Vị trí của nó được xác định tương đối với phần tử *cha gần nhất có `position` khác `static`*. Nếu không có cha nào như vậy, nó sẽ định vị theo viewport ban đầu. `top`, `bottom`, `left`, `right` điều chỉnh vị trí. Thường dùng cho overlay, tooltip.
-   `fixed`: Phần tử bị loại bỏ khỏi luồng tài liệu. Vị trí của nó được xác định tương đối với *viewport* (cửa sổ trình duyệt). Nó sẽ ở yên một chỗ khi cuộn trang. Thường dùng cho header cố định, nút "trở lại đầu trang".
-   `sticky`: Một phần lai giữa `relative` và `fixed`. Phần tử ban đầu nằm trong luồng tài liệu như `relative`, nhưng khi cuộn trang đạt đến một ngưỡng nhất định (được xác định bởi `top`, `bottom`, `left`, `right`), nó sẽ dính vào vị trí đó giống như `fixed`. Thường dùng cho sidebar cố định hoặc tiêu đề section.
-   `z-index`: Kiểm soát thứ tự xếp chồng của các phần tử (phần tử nào hiển thị đè lên phần tử nào) khi chúng chồng lấn lên nhau. Chỉ có tác dụng với các phần tử có `position` khác `static`. Giá trị lớn hơn sẽ hiển thị bên trên.

```css
.container {
    position: relative; /* Làm cơ sở cho phần tử absolute bên trong */
    width: 400px;
    height: 200px;
    border: 1px solid blue;
}

.box {
    position: absolute; /* Định vị theo .container */
    top: 20px;
    left: 20px;
    width: 50px;
    height: 50px;
    background-color: red;
    z-index: 1; /* Nằm trên các phần tử z-index thấp hơn */
}

.fixed-button {
    position: fixed;
    bottom: 20px;
    right: 20px;
    /* Nút sẽ luôn ở góc dưới bên phải của màn hình */
}
```

### 5.2. Flexbox (Flexible Box Layout): Sức Mạnh Bố Cục Một Chiều

Flexbox là mô hình bố cục cực kỳ mạnh mẽ để thiết kế giao diện trong *một chiều* (hàng hoặc cột). Lý tưởng cho việc căn chỉnh và phân phối không gian giữa các phần tử trong một container.

Áp dụng `display: flex` cho phần tử cha (Flex Container). Các phần tử con trực tiếp của nó trở thành Flex Items.

-   **Trên Flex Container:**
    -   `flex-direction`: Hướng của các items (`row`, `row-reverse`, `column`, `column-reverse`).
    -   `flex-wrap`: Điều khiển việc các items có xuống dòng hay không khi không đủ chỗ (`nowrap`, `wrap`, `wrap-reverse`).
    -   `justify-content`: Căn chỉnh các items *dọc theo trục chính* (`flex-start`, `flex-end`, `center`, `space-between`, `space-around`, `space-evenly`).
    -   `align-items`: Căn chỉnh các items *dọc theo trục phụ* (`flex-start`, `flex-end`, `center`, `stretch`, `baseline`).
    -   `align-content`: Căn chỉnh các *dòng* (line) của items dọc theo trục phụ khi có nhiều dòng (`flex-start`, `flex-end`, `center`, `space-between`, `space-around`, `stretch`). Chỉ có tác dụng khi `flex-wrap` là `wrap` hoặc `wrap-reverse`.
    -   `flex-flow`: Viết tắt của `flex-direction` và `flex-wrap`.

-   **Trên Flex Items (các phần tử con trực tiếp):**
    -   `flex-grow`: Xác định mức độ mà item này có thể *mở rộng* để chiếm không gian trống còn lại.
    -   `flex-shrink`: Xác định mức độ mà item này có thể *co lại* khi không đủ không gian.
    -   `flex-basis`: Kích thước ban đầu của item trước khi không gian còn lại được phân phối. Có thể là đơn vị độ dài (px, %) hoặc `auto`.
    -   `flex`: Thuộc tính viết tắt cho `flex-grow`, `flex-shrink`, `flex-basis`. (`flex: 1 1 auto;` là phổ biến).
    -   `align-self`: Ghi đè `align-items` được đặt trên container cho riêng item này (`auto`, `flex-start`, `flex-end`, `center`, `stretch`, `baseline`).
    -   `order`: Sắp xếp lại thứ tự hiển thị của các items độc lập với thứ tự trong HTML (`integer`). Mặc định là 0.

```css
.flex-container {
    display: flex;
    flex-direction: row; /* items nằm ngang */
    justify-content: center; /* items căn giữa theo chiều ngang */
    align-items: center; /* items căn giữa theo chiều dọc */
    height: 200px; /* Ví dụ */
    border: 1px solid black;
}

.flex-item {
    background-color: lightgray;
    padding: 10px;
    margin: 5px;
}

.item-grow {
    flex-grow: 1; /* Item này sẽ mở rộng để chiếm hết không gian trống */
}
```

### 5.3. CSS Grid Layout: Sức Mạnh Bố Cục Hai Chiều

Grid là mô hình bố cục được thiết kế cho layout *hai chiều* (hàng và cột), cho phép kiểm soát mạnh mẽ vị trí và kích thước của các phần tử trên một lưới. Lý tưởng cho bố cục toàn trang (page layout) hoặc các component phức tạp.

Áp dụng `display: grid` cho phần tử cha (Grid Container). Các phần tử con trực tiếp của nó trở thành Grid Items.

-   **Trên Grid Container:**
    -   `grid-template-rows`, `grid-template-columns`: Định nghĩa cấu trúc lưới bằng cách chỉ định kích thước của các hàng và cột.
        -   Đơn vị: px, %, em, rem, `fr` (fraction - đơn vị phân số của không gian trống), `auto` (kích thước tự động theo nội dung), `repeat()` function, `minmax()`.
    -   `grid-template-areas`: Định nghĩa các khu vực được đặt tên trên lưới.
    -   `grid-gap`, `column-gap`, `row-gap`: Tạo khoảng cách giữa các hàng và cột (thuộc tính viết tắt mới là `gap`).
    -   `justify-items`, `align-items`: Căn chỉnh *nội dung bên trong* các items trong ô lưới của chúng (tương tự text-align và vertical-align).
    -   `justify-content`, `align-content`: Căn chỉnh *lưới* bên trong container khi lưới nhỏ hơn container.
    -   `grid-auto-flow`: Điều khiển cách items tự động đặt mình vào lưới (`row`, `column`, `dense`).

-   **Trên Grid Items (các phần tử con trực tiếp):**
    -   `grid-column-start`, `grid-column-end`, `grid-row-start`, `grid-row-end`: Chỉ định item đặt ở đâu trên lưới (theo số dòng lưới).
    -   `grid-column`, `grid-row`: Viết tắt của start/end (ví dụ: `grid-column: 1 / span 2;`).
    -   `grid-area`: Chỉ định item đặt ở đâu bằng cách sử dụng tên khu vực đã định nghĩa trên container, hoặc là viết tắt của start/end theo hàng/cột.
    -   `justify-self`, `align-self`: Ghi đè `justify-items` và `align-items` trên container cho riêng item này.

```css
.grid-container {
    display: grid;
    /* Định nghĩa 3 cột: cột 1 auto, cột 2 chiếm 1 phần không gian trống, cột 3 chiếm 2 phần */
    grid-template-columns: auto 1fr 2fr;
    /* Định nghĩa 2 hàng có chiều cao 50px và 100px */
    grid-template-rows: 50px 100px;
    /* Khoảng cách giữa các ô lưới */
    gap: 10px; /* tương đương grid-gap */

    /* Sử dụng template areas */
    /* grid-template-areas:
        "header header header"
        "sidebar content content"
        "footer footer footer"; */

    border: 1px solid blue;
    padding: 10px;
}

.grid-item {
    background-color: lightyellow;
    padding: 10px;
    border: 1px solid gray;
    text-align: center;
}

.item-span {
    grid-column: 1 / span 3; /* Chiếm từ cột 1 đến 3 */
    /* grid-column: 1 / 4; cũng là từ dòng 1 đến dòng 4, tức là 3 cột */
}

/* Nếu dùng template areas: */
/* .header { grid-area: header; }
.sidebar { grid-area: sidebar; }
.content { grid-area: content; }
.footer { grid-area: footer; } */
```

---

## Chương 6: Không Gian Sâu và Hiệu Ứng - Biến Hình, Chuyển Động và Hoạt Ảnh

Đưa thiết kế từ tĩnh sang động và tương tác là lúc ma thuật thực sự xảy ra.

### 6.1. Backgrounds và Borders Nâng Cao: Những Bề Mặt Phức Tạp

-   **Background Images:**
    -   `background-image`: Sử dụng URL của hình ảnh.
    -   `background-repeat`: `repeat`, `no-repeat`, `repeat-x`, `repeat-y`.
    -   `background-position`: `top center`, `10px 20px`, v.v.
    -   `background-size`: `auto`, `cover` (phủ đầy khu vực mà không bị bóp méo), `contain` (nằm trọn trong khu vực mà không bị bóp méo), giá trị độ dài (px, %).
    -   `background-attachment`: `scroll` (cuộn cùng trang - mặc định), `fixed` (cố định trên viewport).
    -   `background-origin`, `background-clip`.
    -   Thuộc tính viết tắt `background`.
-   **Multiple Background Images:** Liệt kê nhiều hình ảnh, phân tách bằng dấu phẩy. Lớp hình ảnh đầu tiên được vẽ ở trên cùng.
    ```css
    div {
        background-image: url('image1.png'), url('image2.png');
        background-position: top left, bottom right;
        background-repeat: no-repeat, repeat-x;
    }
    ```
-   **Gradients:** `linear-gradient()`, `radial-gradient()`. Được coi là một loại ảnh nền.
    ```css
    div {
        background-image: linear-gradient(to right, red, yellow);
        background-image: radial-gradient(circle, blue, green);
    }
    ```
-   **Border-radius:** Làm bo tròn góc. Có thể cho tất cả các góc hoặc từng góc riêng lẻ.
-   **Border-image:** Sử dụng hình ảnh cho đường viền (phức tạp hơn border thông thường).
-   **Box-shadow:** Thêm bóng đổ cho phần tử. `box-shadow: offset-x offset-y blur-radius spread-radius color inset;`
-   **Text-shadow:** Thêm bóng đổ cho văn bản. `text-shadow: offset-x offset-y blur-radius color;`

### 6.2. Transforms: Xoay, Scale, Di Chuyển Trong Không Gian 2D và 3D

Thuộc tính `transform` cho phép biến đổi hình dạng, kích thước hoặc vị trí của phần tử mà không ảnh hưởng đến bố cục xung quanh (vẫn giữ nguyên vị trí ban đầu trong luồng tài liệu).

-   **2D Transforms:**
    -   `translate(x, y)`: Di chuyển phần tử theo trục X và Y.
    -   `rotate(angle)`: Xoay phần tử (ví dụ: `rotate(45deg)`).
    -   `scale(sx, sy)`: Thay đổi kích thước phần tử theo tỉ lệ.
    -   `skew(ax, ay)`: Biến dạng (xiên) phần tử.
    -   `matrix()`: Tổ hợp tất cả các phép biến đổi 2D.
-   **3D Transforms:**
    -   `translate3d(x, y, z)`
    -   `rotateX(angle)`, `rotateY(angle)`, `rotateZ(angle)`, `rotate3d(x, y, z, angle)`
    -   `scale3d(sx, sy, sz)`
    -   `matrix3d()`
-   **`transform-origin`:** Thiết lập điểm gốc của phép biến đổi (mặc định là `center center`).
-   **`perspective`:** Đặt phối cảnh cho phần tử cha chứa các phần tử con 3D để tạo cảm giác chiều sâu.

```css
.box:hover {
    transform: translateX(20px) rotate(10deg); /* Di chuyển và xoay khi hover */
}

.card-flip {
    transform: rotateY(180deg);
    transition: transform 0.5s; /* Áp dụng transition cho phép biến đổi */
    transform-style: preserve-3d; /* Giữ items con ở không gian 3D */
}
```

### 6.3. Transitions: Chuyển Tiếp Mượt Mà

Cho phép tạo hiệu ứng chuyển động đơn giản khi giá trị của một thuộc tính thay đổi (ví dụ: từ `color: blue` sang `color: red` khi hover).

-   `transition-property`: Tên thuộc tính CSS muốn áp dụng transition (ví dụ: `color`, `opacity`, `transform`, `all`).
-   `transition-duration`: Thời gian thực hiện transition (ví dụ: `0.5s`, `500ms`). Bắt buộc phải có giá trị > 0.
-   `transition-timing-function`: Tốc độ thay đổi trong suốt transition (`ease`, `linear`, `ease-in`, `ease-out`, `ease-in-out`, `cubic-bezier(...)`, `steps(...)`).
-   `transition-delay`: Thời gian chờ trước khi transition bắt đầu.
-   `transition`: Thuộc tính viết tắt (`transition: property duration timing-function delay;`).

```css
.button {
    background-color: blue;
    color: white;
    padding: 10px 20px;
    /* Áp dụng transition cho thuộc tính background-color và color trong 0.3 giây */
    transition: background-color 0.3s ease, color 0.3s ease;
}

.button:hover {
    background-color: navy;
    color: yellow;
}
```

### 6.4. Animations (`@keyframes`): Các Kịch Bản Chuyển Động Phức Tạp

Cho phép tạo chuỗi các bước chuyển động (keyframes) và điều khiển chúng.

-   **`@keyframes rule`:** Định nghĩa hoạt ảnh. Tên hoạt ảnh là do bạn đặt. Bên trong, sử dụng `%` hoặc từ khóa `from` (0%) và `to` (100%) để mô tả trạng thái của các thuộc tính CSS tại các thời điểm khác nhau trong hoạt ảnh.
    ```css
    @keyframes slidein {
        0% {
            transform: translateX(0%); /* Bắt đầu từ vị trí ban đầu */
        }
        50% {
            transform: translateX(50%); /* Ở giữa animation */
            opacity: 0.5;
        }
        100% {
            transform: translateX(100%); /* Kết thúc animation */
        }
    }
    ```
-   **Thuộc tính `animation` (Áp dụng cho phần tử):** Liên kết `@keyframes` với phần tử và điều khiển cách chạy.
    -   `animation-name`: Tên của `@keyframes rule`.
    -   `animation-duration`: Thời gian chạy 1 vòng lặp.
    -   `animation-timing-function`.
    -   `animation-delay`.
    -   `animation-iteration-count`: Số lần lặp (`infinite` để lặp vô hạn, hoặc số lần).
    -   `animation-direction`: Hướng lặp (`normal`, `reverse`, `alternate`, `alternate-reverse`).
    -   `animation-fill-mode`: Xác định style của phần tử trước và sau khi animation chạy (`none`, `forwards`, `backwards`, `both`).
    -   `animation-play-state`: Điều khiển trạng thái chạy (`running`, `paused`).
    -   Thuộc tính viết tắt `animation`: (`animation: name duration timing-function delay iteration-count direction fill-mode;`)

```css
.element {
    width: 100px;
    height: 100px;
    background-color: orange;
    position: relative; /* Cần cho translateX */
    /* Áp dụng animation */
    animation-name: slidein;
    animation-duration: 3s;
    animation-iteration-count: infinite; /* Lặp vô hạn */
    animation-direction: alternate; /* Chạy tiến rồi lùi */
    animation-fill-mode: forwards; /* Giữ trạng thái cuối cùng khi kết thúc */
}
```

---

## Chương 7: Đáp Ứng Vũ Trụ - Thiết Kế Responsive và Khả Năng Thích Ứng

Thiết kế cho nhiều loại màn hình (điện thoại, tablet, desktop) không còn là tùy chọn mà là yêu cầu bắt buộc.

### 7.1. Media Queries: Các Cổng Kết Nối Giữa Các Kích Thước

Media Queries cho phép áp dụng các khối CSS dựa trên đặc điểm của thiết bị hiển thị (như chiều rộng viewport, chiều cao, hướng, độ phân giải, v.v.).

Cú pháp cơ bản:

```css
@media screen and (max-width: 600px) {
    /* Các quy tắc CSS ở đây chỉ áp dụng khi màn hình có chiều rộng TỐI ĐA là 600px hoặc nhỏ hơn */
    body {
        background-color: lightblue;
    }
}

@media screen and (min-width: 768px) and (max-width: 1024px) {
    /* Các quy tắc CSS ở đây chỉ áp dụng khi màn hình có chiều rộng từ 768px đến 1024px */
    .container {
        width: 700px;
    }
}

@media (orientation: landscape) {
    /* Các quy tắc ở đây chỉ áp dụng khi màn hình đang ở chế độ ngang (landscape) */
}
```

-   **Breakpoints:** Là các điểm chuyển tiếp (giá trị pixel, em, rem) nơi bạn áp dụng Media Query để thay đổi layout. Phổ biến nhất dựa trên chiều rộng: nhỏ (<600px), trung bình (601px - 900px), lớn (>901px). Các breakpoints nên dựa vào nội dung và thiết kế của bạn, chứ không chỉ dựa vào kích thước thiết bị cụ thể.
-   **Mobile First vs Desktop First:**
    -   **Mobile First (được khuyến nghị):** Bắt đầu viết CSS cho màn hình nhỏ nhất trước (styling cơ bản). Sau đó, sử dụng Media Queries với `min-width` để thêm style cho màn hình lớn hơn. Phương pháp này tận dụng tính cascade tốt hơn và thường dẫn đến hiệu suất tốt hơn trên thiết bị di động.
        ```css
        /* Mobile styles (base styles) */
        .container {
            width: 100%;
            padding: 15px;
        }

        /* Tablet and up */
        @media screen and (min-width: 768px) {
            .container {
                width: 700px;
                margin: 0 auto;
            }
        }

        /* Desktop and up */
        @media screen and (min-width: 1024px) {
            .container {
                width: 960px;
            }
        }
        ```
    -   **Desktop First:** Bắt đầu viết CSS cho màn hình lớn nhất. Sau đó, sử dụng Media Queries với `max-width` để giảm style cho màn hình nhỏ hơn. Có thể cần override nhiều style hơn so với Mobile First.

### 7.2. Đơn Vị Tương Đối Và Bố Cục Linh Hoạt

Việc sử dụng các đơn vị tương đối (`em`, `rem`, `%`, `vw`, `vh`) và các mô hình bố cục linh hoạt như Flexbox và Grid là cực kỳ quan trọng trong thiết kế responsive.

-   `width: 100%;` hoặc `max-width: 100%;` cho hình ảnh để chúng không tràn ra ngoài container.
-   Sử dụng Flexbox hoặc Grid để tạo các layout cột linh hoạt thay vì `float`.
-   Sử dụng `em` hoặc `rem` cho font-size và padding/margin để tỷ lệ tốt hơn.
-   `object-fit` cho ảnh/video: `cover`, `contain` để kiểm soát cách media tỷ lệ trong container.

### 7.3. Images và Responsive Media

-   Sử dụng thuộc tính `width` và `height` (trong HTML) và `max-width: 100%; height: auto;` (trong CSS) cho `<img>`.
    ```css
    img {
        max-width: 100%;
        height: auto; /* Giữ tỉ lệ khung hình */
    }
    ```
-   Sử dụng thẻ `<picture>` trong HTML hoặc thuộc tính `srcset` trên `<img>` để cung cấp các phiên bản hình ảnh khác nhau tùy thuộc vào kích thước màn hình hoặc độ phân giải.

### 7.4. `@supports`: Các Giao Thức Tùy Chọn (Feature Queries)

Kiểm tra xem trình duyệt có hỗ trợ một thuộc tính CSS hoặc một cặp thuộc tính/giá trị cụ thể nào đó không, và chỉ áp dụng khối CSS nếu có hỗ trợ. Giúp xây dựng các trang web sử dụng các tính năng CSS mới nhưng vẫn có các giải pháp thay thế (fallbacks) cho trình duyệt cũ hơn.

```css
.element {
    /* Fallback cho trình duyệt không hỗ trợ Grid */
    float: left;
    width: 33.33%;
}

@supports (display: grid) {
    .container {
        display: grid; /* Sử dụng Grid nếu được hỗ trợ */
        grid-template-columns: repeat(3, 1fr);
        gap: 20px;
    }
    .element {
        /* Bỏ fallback float khi sử dụng Grid */
        float: none;
        width: auto;
    }
}
```

---

## Chương 8: Cấu Trúc và Thực Tiễn Tối Ưu - Kỹ Thuật Tiên Tiến và Triển Khai

Xây dựng những hệ thống CSS lớn đòi hỏi sự cấu trúc và kỷ luật.

### 8.1. Biến CSS (Custom Properties): Lưu Trữ Dữ Liệu Trên Tàu

Cho phép định nghĩa các biến để lưu trữ các giá trị CSS có thể sử dụng lại trong toàn bộ stylesheet. Giúp quản lý và cập nhật dễ dàng hơn.

```css
:root { /* Định nghĩa biến ở cấp root (html) */
    --primary-color: #007bff;
    --secondary-color: #6c757d;
    --spacing-unit: 1rem;
    --main-font: 'Roboto', sans-serif;
}

body {
    font-family: var(--main-font);
    color: var(--secondary-color);
    margin: calc(var(--spacing-unit) * 2); /* Sử dụng hàm calc() */
}

.button {
    background-color: var(--primary-color);
    padding: var(--spacing-unit);
}
```

-   Biến có phạm vi (scope). Biến được định nghĩa trong selector nào sẽ chỉ có hiệu lực trong selector đó và các phần tử con của nó (kế thừa). `:root` là nơi phổ biến nhất để định nghĩa các biến global.
-   Sử dụng biến bằng hàm `var(--ten-bien)`.
-   Có thể sử dụng giá trị fallback trong `var()`: `var(--bien-khong-ton-tai, green)`.

### 8.2. Preprocessors (SASS, LESS, Stylus): Động Cơ Mạnh Mẽ Cho CSS

Không phải là CSS thật, mà là các ngôn ngữ mở rộng được **biên dịch** thành CSS thuần. Chúng cung cấp các tính năng giúp CSS mạnh mẽ, dễ bảo trì và cấu trúc hơn.

Các tính năng chính:

-   **Variables:** Giống CSS variables, nhưng linh hoạt hơn.
-   **Nesting:** Lồng các selector vào nhau theo cấu trúc HTML, tránh lặp lại tên selector cha.
-   **Mixins:** Khối mã CSS có thể sử dụng lại, có thể truyền tham số.
-   **Functions:** Các hàm có sẵn hoặc tự định nghĩa để xử lý giá trị.
-   **Partials/Import:** Chia code thành nhiều file nhỏ và nhập vào một file chính.

Ví dụ SASS Nesting:

```scss
/* Mã SASS (.scss) */
.container {
    width: 100%;

    .sidebar {
        width: 20%;
        float: left;
        padding: 10px;
    }

    .content {
        width: 80%;
        float: left;
        padding: 10px;

        p { /* Nesting thêm cấp nữa */
            line-height: 1.5;
            color: #333;
        }
    }
}
```
Biên dịch thành CSS thuần:
```css
/* Mã CSS thuần (sau khi biên dịch từ SASS) */
.container {
  width: 100%;
}
.container .sidebar {
  width: 20%;
  float: left;
  padding: 10px;
}
.container .content {
  width: 80%;
  float: left;
  padding: 10px;
}
.container .content p {
  line-height: 1.5;
  color: #333;
}
```
Preprocessors yêu cầu bước build (sử dụng command line tool hoặc plugin trong build process).

### 8.3. Phương Pháp Cấu Trúc CSS (BEM, OOCSS, SMACSS): Tổ Chức Dự Án Lớn

Khi dự án CSS lớn, việc có một phương pháp cấu trúc là cần thiết để tránh xung đột, tăng khả năng tái sử dụng và dễ bảo trì.

-   **BEM (Block, Element, Modifier):** Đặt tên class theo mẫu `block__element--modifier`. Giúp tạo ra các class có ý nghĩa, rõ ràng và độ ưu tiên thấp (dựa vào class), giảm sự phụ thuộc vào cấu trúc DOM.
    -   Block: Một thành phần độc lập (ví dụ: `.button`, `.card`, `.header`).
    -   Element: Một phần của Block, không có ý nghĩa khi đứng riêng (ví dụ: `.card__image`, `.button__text`). Nối với block bằng `__`.
    -   Modifier: Biến thể của Block hoặc Element (ví dụ: `.button--large`, `.card--featured`). Nối với block/element bằng `--`.
    ```css
    /* Ví dụ BEM */
    .card { /* Block */
        border: 1px solid #ccc;
    }
    .card__image { /* Element của card */
        width: 100%;
        display: block;
    }
    .card__title { /* Element khác của card */
        font-size: 1.2em;
    }
    .card--featured { /* Modifier của card */
        border-color: gold;
        box-shadow: 0 0 10px gold;
    }
    .card__button--disabled { /* Modifier của element button (nếu có) */
        opacity: 0.5;
    }
    ```
-   **OOCSS (Object Oriented CSS):** Tập trung vào việc tách biệt structure (cấu trúc) khỏi skin (visuals) và tách biệt content (nội dung) khỏi container (vật chứa). Khuyến khích sử dụng lại các "object" (khối CSS tái sử dụng được).
-   **SMACSS (Scalable and Modular Architecture for CSS):** Đề xuất một cách phân loại các quy tắc CSS thành 5 hạng mục: Base, Layout, Modules, State, Theme. Giúp cấu trúc folder và file logic.

### 8.4. Performance (Hiệu Suất): Tối Ưu Tốc Độ Ánh Sáng

-   **Selectors hiệu quả:** Trình duyệt đọc selectors từ phải sang trái. Selector như `.footer p a` sẽ nhanh hơn `html body .container .wrapper .footer p a` (trừ khi selector đó phức tạp và gây tắc nghẽn). ID selectors và Class selectors là nhanh nhất.
-   **Giảm thiểu HTTP requests:** Gộp nhiều file CSS nhỏ thành một file duy nhất.
-   **Minify/Compress CSS:** Xóa khoảng trắng, comments để giảm kích thước file.
-   **Leverage Caching:** Cấu hình cache cho file CSS trên server.
-   **Critical CSS:** Phân phối các style cần thiết để hiển thị "above-the-fold" (phần đầu trang hiển thị mà không cần cuộn) inline trong HTML, và load phần còn lại không đồng bộ.
-   **Avoiding redundant styles:** Tránh các style bị ghi đè liên tục.
-   **Limiting repaint and reflow (layout shifts):** Các thay đổi CSS về kích thước, vị trí (như margin, padding, width, height, position: absolute) có thể gây reflow, tính toán lại toàn bộ bố cục. Các thay đổi về màu sắc, opacity, transform chỉ gây repaint. Nên ưu tiên transforms và opacity cho animations để có hiệu suất tốt hơn.
-   **Hardware acceleration:** Sử dụng thuộc tính như `transform: translateZ(0);` hoặc `will-change: property;` (cẩn thận khi dùng will-change) để buộc trình duyệt sử dụng GPU.

### 8.5. Accessibility (Khả Năng Tiếp Cận - A11y): Thiết Kế Cho Tất Cả

Việc tạo kiểu CSS ảnh hưởng lớn đến khả năng tiếp cận (làm cho website dễ sử dụng cho mọi người, kể cả người khuyết tật).

-   **Độ tương phản màu (Color Contrast):** Đảm bảo văn bản và nền có độ tương phản đủ để người thị lực kém có thể đọc được (kiểm tra bằng các công cụ).
-   **Kích thước Font linh hoạt:** Sử dụng đơn vị tương đối (`rem`) để người dùng có thể phóng to/thu nhỏ text thông qua cài đặt trình duyệt.
-   **Trạng thái `:focus` rõ ràng:** Luôn cung cấp một style hiển thị rõ ràng cho phần tử khi nó được focus (dùng bàn phím), đặc biệt cho liên kết và input. outline là thuộc tính mặc định của trình duyệt, không nên loại bỏ hoàn toàn (`outline: none;`) mà nên thay thế bằng style khác (`outline: 2px solid blue; outline-offset: 2px;`).
-   **Hide content properly:** Nếu ẩn nội dung (ví dụ cho screen readers), sử dụng các kỹ thuật như `position: absolute; left: -9999px;` thay vì `display: none;` hoặc `visibility: hidden;` nếu nội dung đó vẫn cần được đọc bởi screen reader.

### 8.6. Browser Compatibility: Hỗ Trợ Đa Nền Tảng

Các trình duyệt khác nhau có thể diễn giải CSS hơi khác nhau hoặc hỗ trợ các tính năng mới ở các thời điểm khác nhau.

-   **Vendor Prefixes:** Các phiên bản cũ hơn của một số trình duyệt yêu cầu tiền tố nhà cung cấp cho các tính năng CSS thử nghiệm hoặc mới (ví dụ: `-webkit-transition`, `-moz-transform`). Ngày nay ít phổ biến hơn, nhưng vẫn có thể cần thiết cho các tính năng rất mới hoặc hỗ trợ trình duyệt rất cũ. Có các công cụ tự động thêm prefix như Autoprefixer.
-   **Reset/Normalize CSS:**
    -   **CSS Reset:** Đặt lại *tất cả* style mặc định của trình duyệt về 0 (ví dụ: Universal selector với margin/padding: 0). Có thể quá mạnh.
    -   **Normalize.css:** Thiết lập style mặc định nhất quán giữa các trình duyệt, giữ lại một số style hữu ích (ví dụ: margin mặc định cho p). Là phương pháp phổ biến hơn.
-   **Test trên nhiều trình duyệt và thiết bị:** Kiểm tra trực tiếp trên các trình duyệt và thiết bị thực hoặc sử dụng các công cụ/service hỗ trợ.
-   **Can I Use (`caniuse.com`):** Website tra cứu mức độ hỗ trợ của một thuộc tính CSS/HTML/JS trên các trình duyệt.

---

## Chương 9: Công Cụ và Tài Nguyên - Bộ Phụ Kiện Của Nhà Khám Phá

Để trở thành một "phù thủy" CSS giỏi, bạn cần các công cụ phù hợp.

-   **Browser Developer Tools (DevTools):** Công cụ mạnh mẽ nhất của bạn. Học cách sử dụng các tab Elements (kiểm tra HTML và các style áp dụng), Styles (xem, chỉnh sửa trực tiếp CSS, tính toán độ ưu tiên), Console, Performance, v.v. trên Chrome, Firefox, Edge, Safari.
-   **Online Resources:**
    -   **MDN Web Docs (Mozilla Developer Network):** Nguồn tài liệu chính xác, chi tiết và cập nhật nhất về các công nghệ web (HTML, CSS, JavaScript).
    -   CSS-Tricks: Các bài viết, hướng dẫn, snippet về CSS.
    -   Smashing Magazine: Các bài viết chuyên sâu về phát triển web.
    -   Flexbox Froggy, Grid Garden: Các trò chơi tương tác để học Flexbox và Grid.
-   **Công cụ hỗ trợ:**
    -   **Code Editors:** VS Code, Sublime Text, Atom... với các extension hỗ trợ CSS (highlight syntax, auto-completion, linter).
    -   **Autoprefixer:** Plugin tự động thêm vendor prefixes cho CSS.
    -   **Linters (Stylelint):** Giúp duy trì code style nhất quán, tìm lỗi cú pháp, lỗi logic trong CSS.
    -   **CodePens, JSFiddle, CodeSandbox:** Các nền tảng online để viết, thử nghiệm và chia sẻ code (HTML, CSS, JS).

---

Tuyệt vời! Nhiệm vụ mở rộng hồ sơ tri thức về CSS đã được ghi nhận và phê duyệt. Vũ trụ CSS còn bao la lắm, và chúng ta còn rất nhiều khu vực thú vị để khám phá. Những bài học tiếp theo sẽ đi sâu hơn vào các khái niệm giúp bạn kiến tạo nên những giao diện tinh vi, linh hoạt và thực sự thông minh.

Chúng ta sẽ tiếp tục hành trình của mình, lặn sâu hơn vào các lớp kiến tạo và khám phá các "lực lượng" mạnh mẽ hơn của CSS.

Dưới đây là các chương tiếp theo của bản đồ kiến thức này:

---

### 10.1. Truy Vấn Container (Container Queries - `@container`): Khả Năng Thích Ứng Theo Component

Một trong những tính năng thú vị và mạnh mẽ nhất của CSS hiện đại. Không giống như Media Queries phản ứng với kích thước viewport, Container Queries cho phép phần tử con tạo kiểu dựa trên kích thước của phần tử **cha** (container) của nó. Điều này cực kỳ hữu ích trong thiết kế component.

**Để sử dụng:**

1.  Đánh dấu phần tử cha là Container bằng thuộc tính `container-type` hoặc `container`.
2.  Sử dụng quy tắc `@container` để viết các truy vấn dựa trên kích thước của container này.

```css
/* 1. Đánh dấu container */
.card-container {
    /* Chỉ định loại truy vấn. size là phổ biến nhất (kết hợp width và height) */
    container-type: size;
    /* container-type: inline-size; chỉ theo chiều ngang */

    /* Có thể dùng thuộc tính viết tắt container để đặt cả tên container */
    /* container: my-card size; */

    /* Có thể đặt tên cho container nếu có nhiều container lồng nhau hoặc cần rõ ràng */
    /* container-name: my-card;
       container-type: size; */

    border: 1px solid #ccc;
    padding: 15px;
    display: flex; /* Ví dụ bố cục flex bên trong container */
    gap: 10px;
}

/* 2. Sử dụng @container để truy vấn container */
@container (max-width: 400px) {
    /* Các style này chỉ áp dụng cho các phần tử *bên trong* .card-container */
    /* khi chiều rộng của .card-container NHỎ HƠN HOẶC BẰNG 400px */
    .card-container {
         /* Các style thay đổi layout của chính container, ví dụ: */
        flex-direction: column;
    }
    .card-container .card-item {
        /* Các style áp dụng cho item con dựa trên container size */
        width: 100%; /* Item con chiếm hết chiều rộng của container nhỏ */
        font-size: 0.9em;
    }
}

@container (min-width: 600px) {
     /* Các style này chỉ áp dụng khi chiều rộng của .card-container LỚN HƠN HOẶC BẰNG 600px */
    .card-container .card-item {
         /* Item con khi container đủ rộng */
        flex-basis: 200px; /* Kích thước cơ sở 200px */
    }
}

/* Nếu bạn đã đặt tên cho container bằng container-name: my-card; */
/* @container my-card (max-width: 400px) { ... } */

/* Cú pháp viết tắt của @container cũng được hỗ trợ */
/* @container (width < 400px) { ... } */
/* @container (width >= 600px) { ... } */
```
Container Queries giúp tạo ra các component độc lập có khả năng tự thích ứng với môi trường (container) của chúng mà không phụ thuộc vào viewport toàn cục.

### 10.2. Thuộc Tính Logic (Logical Properties): Định Hướng Thiết Kế Toàn Cầu

CSS truyền thống dựa vào các thuộc tính vật lý như `margin-top`, `padding-left`, `border-right`. Tuy nhiên, các thuộc tính này không phù hợp với các ngôn ngữ viết từ phải sang trái (RTL - Right-to-Left) như tiếng Arab hoặc tiếng Do Thái, nơi hướng "bắt đầu" (start) và "kết thúc" (end) ngược lại so với LTR (Left-to-Right).

Thuộc tính Logic giải quyết vấn đề này bằng cách thay thế các thuộc tính vật lý bằng các thuộc tính ngữ cảnh dựa trên hướng văn bản (`direction` và `writing-mode`).

-   `margin-top` -> `margin-block-start`
-   `margin-bottom` -> `margin-block-end`
-   `margin-left` -> `margin-inline-start`
-   `margin-right` -> `margin-inline-end`

Tương tự cho `padding`, `border`, `width`, `height`.

-   `width` -> `inline-size` (kích thước theo chiều nội tuyến, tức chiều ngang trong LTR)
-   `height` -> `block-size` (kích thước theo chiều block, tức chiều dọc trong LTR)
-   `border-top-color` -> `border-block-start-color`
-   `left`, `right` -> `inset-inline-start`, `inset-inline-end` (sử dụng với `position`)

```css
/* Sử dụng thuộc tính vật lý (physical properties) */
.box-physical {
    margin-left: 20px; /* Luôn cách trái 20px */
    border-right: 2px solid blue;
}

/* Sử dụng thuộc tính logic (logical properties) */
.box-logical {
    /* margin-inline-start: Khoảng cách ở đầu chiều nội tuyến */
    /* Trong LTR: tương đương margin-left */
    /* Trong RTL: tương đương margin-right */
    margin-inline-start: 20px;

    /* border-inline-end: Đường viền ở cuối chiều nội tuyến */
    /* Trong LTR: tương đương border-right */
    /* Trong RTL: tương đương border-left */
    border-inline-end: 2px solid blue;

    /* Thay vì width/height */
    inline-size: 300px; /* Chiều rộng theo chiều nội tuyến */
    block-size: 100px; /* Chiều cao theo chiều block */
}
```
Sử dụng thuộc tính logic là một thực hành tốt để xây dựng các website sẵn sàng hỗ trợ đa ngôn ngữ và các hướng viết khác nhau, tăng khả năng quốc tế hóa (i18n).

---

## Chương 11: Đi Sâu Vào Không Gian Phẳng - `z-index` và Context Xếp Chồng (Stacking Context)

Việc các phần tử hiển thị đè lên nhau như thế nào đôi khi khá khó hiểu. `z-index` không hoạt động đơn độc mà cần có một môi trường cụ thể.

### 11.1. Thuộc Tính `z-index`: Thứ Tự Trong Không Gian Thứ Ba

Chúng ta đã biết `z-index` điều khiển thứ tự hiển thị trên trục Z (trục vuông góc với màn hình), giá trị lớn hơn sẽ đè lên trên. Tuy nhiên, `z-index` chỉ có tác dụng với các phần tử có thuộc tính `position` được đặt là `relative`, `absolute`, `fixed`, hoặc `sticky`.

```css
.box-a {
    position: absolute;
    top: 10px;
    left: 10px;
    width: 100px;
    height: 100px;
    background-color: red;
    z-index: 1; /* box-a sẽ nằm dưới box-b và box-c */
}

.box-b {
    position: absolute;
    top: 30px;
    left: 30px;
    width: 100px;
    height: 100px;
    background-color: green;
    z-index: 2; /* box-b sẽ nằm giữa box-a và box-c */
}

.box-c {
    position: absolute;
    top: 50px;
    left: 50px;
    width: 100px;
    height: 100px;
    background-color: blue;
    z-index: 3; /* box-c sẽ nằm trên cùng */
}
```

### 11.2. Stacking Context (Context Xếp Chồng): Các Lớp Đĩa Từ Tính

Đây là khái niệm quan trọng để hiểu cách `z-index` hoạt động. Stacking context là một "khu vực" ảo trong đó các phần tử được sắp xếp theo thứ tự nhất định trên trục Z, độc lập với các Stacking context khác.

Một phần tử tạo ra một Stacking context khi:

-   Nó là phần tử root (`<html>`).
-   Nó có `position` là `absolute` hoặc `relative` và `z-index` có giá trị *khác `auto`*. (Đây là trường hợp phổ biến nhất)
-   Nó có `position` là `fixed` hoặc `sticky`.
-   Nó có `opacity` < 1.
-   Nó có `transform`, `filter`, `perspective`, `clip-path` hoặc `mask` với giá trị *khác `none`*.
-   Nó có thuộc tính `isolation: isolate`.
-   Sử dụng Flex items với `z-index` khác `auto`.
-   Sử dụng Grid items với `z-index` khác `auto`.
-   Và một số trường hợp khác nữa...

**Lý do Stacking Context quan trọng:**
`z-index` của một phần tử chỉ có hiệu lực **bên trong** Stacking context của phần tử cha tạo ra context đó. Nó không thể cạnh tranh trực tiếp với `z-index` của các phần tử nằm trong một Stacking context khác.

```css
/* Stacking Context Example */

.container-a {
    position: relative;
    z-index: 1; /* Container A tạo một Stacking context */
    background-color: yellow;
    padding: 20px;
    margin: 20px;
    width: 200px;
    height: 200px;
}

.box-a1 {
    position: absolute;
    top: 10px;
    left: 10px;
    width: 50px;
    height: 50px;
    background-color: red;
    z-index: 100; /* z-index = 100 TRONG container-a */
}

.container-b {
    position: relative;
    z-index: 2; /* Container B tạo một Stacking context riêng, nằm TRÊN container-a */
    background-color: cyan;
    padding: 20px;
    margin: 20px;
    width: 200px;
    height: 200px;
    /* Do z-index: 2 (lớn hơn z-index: 1 của container-a), container-b và TẤT CẢ NỘI DUNG của nó sẽ nằm trên container-a */
}

.box-b1 {
    position: absolute;
    top: 30px;
    left: 30px;
    width: 50px;
    height: 50px;
    background-color: blue;
    z-index: 1; /* z-index = 1 TRONG container-b */
    /* Dù z-index chỉ là 1 ở đây, nhưng vì box-b1 nằm trong container-b có z-index cao hơn,
       box-b1 vẫn nằm trên box-a1 (dù box-a1 có z-index 100 trong context của nó) */
}
```
Hiểu Stacking Context là mấu chốt để giải quyết các vấn đề về `z-index` và kiểm soát lớp hiển thị của các phần tử, đặc biệt khi sử dụng `position: absolute/fixed`.

---

## Chương 12: Tạo Hình Và Thêm Sức Sống - Clipping, Masking, Filters và Blend Modes

Đưa giao diện lên một tầm cao mới với các hiệu ứng thị giác nâng cao.

### 12.1. `clip-path`: Cắt Bỏ Các Vùng Không Mong Muốn

Cho phép cắt một phần tử thành các hình dạng phức tạp (tròn, elip, polygon, hoặc từ một SVG path) thay vì chỉ là hình chữ nhật thông thường. Các vùng nằm ngoài đường cắt sẽ bị ẩn đi.

```css
.element-to-clip {
    width: 200px;
    height: 200px;
    background-color: purple;
    /* Tạo hình elip */
    clip-path: ellipse(50% 50% at 50% 50%); /* Bo tròn thành hình tròn */
    /* Tạo hình lục giác */
    /* clip-path: polygon(50% 0%, 100% 25%, 100% 75%, 50% 100%, 0% 75%, 0% 25%); */
    /* Sử dụng SVG */
    /* clip-path: url(#my-svg-path-id); */
}
```

### 12.2. `mask-image` / `mask`: Áp Dụng Lớp Che Để Tạo Hiệu Ứng Trong Suốt Hoặc Hoa Văn

Giống như `clip-path` nhưng mạnh mẽ hơn, cho phép sử dụng hình ảnh (bitmap hoặc vector) hoặc gradients làm "mask". Vùng trong suốt của mask sẽ làm lộ phần tử, vùng màu đen sẽ che đi, và các sắc thái xám tạo độ trong suốt khác nhau.

```css
.element-to-mask {
    width: 300px;
    height: 300px;
    background: linear-gradient(to right, orange, red);
    /* Sử dụng ảnh nền làm mask (chỉ phần sáng của ảnh hiện ra) */
    -webkit-mask-image: url(mask.png); /* Cần tiền tố -webkit- cho Safari */
    mask-image: url(mask.png);
    /* Hoặc sử dụng gradient */
    /* mask-image: linear-gradient(black, transparent); */
    mask-mode: alpha; /* Hoặc luminance */
    mask-repeat: no-repeat;
    mask-position: center;
    mask-size: contain;
}
```

### 12.3. `filter`: Thêm Hiệu Ứng Đồ Họa (Photoshop Lite)

Áp dụng các bộ lọc đồ họa cho một phần tử, tương tự như các bộ lọc trong Photoshop hoặc Instagram. Các hàm phổ biến:

-   `grayscale()`: Chuyển sang thang độ xám.
-   `sepia()`: Chuyển sang màu nâu đỏ cổ điển.
-   `saturate()`: Điều chỉnh độ bão hòa màu.
-   `hue-rotate()`: Xoay màu trên vòng màu.
-   `invert()`: Đảo ngược màu sắc.
-   `opacity()`: Điều chỉnh độ mờ (khác với thuộc tính `opacity`).
-   `brightness()`, `contrast()`: Điều chỉnh độ sáng và độ tương phản.
-   `blur()`: Làm mờ.
-   `drop-shadow()`: Thêm bóng đổ (tương tự box-shadow nhưng áp dụng sau khi cắt).
-   `url()`: Sử dụng các bộ lọc SVG đã định nghĩa trước.

```css
.image-filter img {
    filter: grayscale(100%); /* Ảnh đen trắng */
    transition: filter 0.5s ease; /* Thêm hiệu ứng transition */
}

.image-filter img:hover {
    filter: grayscale(0%); /* Quay lại màu khi hover */
}

.element-blur {
    filter: blur(5px); /* Làm mờ phần tử */
}
```

### 12.4. `mix-blend-mode` và `background-blend-mode`: Trộn Các Lớp Ảnh/Màu

Xác định cách nội dung của một phần tử trộn lẫn với lớp nền của nó (`mix-blend-mode`), hoặc cách ảnh nền và màu nền trộn lẫn với nhau (`background-blend-mode`). Các mode giống như trong các phần mềm đồ họa: `multiply`, `screen`, `overlay`, `darken`, `lighten`, `color-dodge`, `color-burn`, `hard-light`, `soft-light`, `difference`, `exclusion`, `hue`, `saturation`, `color`, `luminosity`, `normal`.

```css
.blend-example .top-layer {
    background-color: yellow;
    mix-blend-mode: multiply; /* Trộn với lớp nền bên dưới (thường là hình ảnh hoặc màu khác) */
}

.background-blend {
    background-image: url(pattern.png);
    background-color: blue;
    background-blend-mode: overlay; /* Trộn pattern với màu nền xanh */
}
```
Những thuộc tính này cho phép tạo ra các hiệu ứng hình ảnh độc đáo mà trước đây chỉ có thể thực hiện được bằng trình sửa ảnh.

---

## Chương 13: Nhắm Mục Tiêu Tinh Gọn - Selector Nâng Cao Và Nội Dung Tạo Sinh

Quay trở lại với selector, chúng ta sẽ khám phá thêm các cách chọn lọc phần tử và cách thêm nội dung giả thông minh hơn.

### 13.1. `:nth-*` Selectors Nâng Cao: Chọn Theo Công Thức

Ngoài `:nth-child(n)` và `:nth-of-type(n)` đã giới thiệu, bạn có thể sử dụng công thức phức tạp hơn với `an+b`.

-   `an`: Chu kỳ lặp (mỗi `a` phần tử).
-   `+b`: Bắt đầu đếm từ vị trí thứ `b`.

Ví dụ:

-   `li:nth-child(2n)`: Chọn các thẻ `li` ở vị trí chẵn (thứ 2, 4, 6,...).
-   `li:nth-child(2n+1)`: Chọn các thẻ `li` ở vị trí lẻ (thứ 1, 3, 5,...).
-   `li:nth-child(3n)`: Chọn các thẻ `li` thứ 3, 6, 9,...
-   `li:nth-child(n+5)`: Chọn tất cả các thẻ `li` *bắt đầu từ* vị trí thứ 5 trở đi (thứ 5, 6, 7,...).
-   `li:nth-child(-n+3)`: Chọn các thẻ `li` *lên đến* vị trí thứ 3 (thứ 1, 2, 3).
-   `li:nth-last-child(n)` và `li:nth-last-of-type(n)` hoạt động tương tự nhưng đếm từ *cuối* lên.

```css
.gallery li:nth-child(3n+1) { /* Chọn ảnh đầu tiên trong mỗi nhóm 3 ảnh */
    margin-left: 0;
}
```

### 13.2. Pseudo-classes `::selection` và `::marker`: Tùy Chỉnh Chi Tiết

-   `::selection`: Cho phép tạo kiểu cho văn bản mà người dùng đã bôi đen (chỉ hỗ trợ `color`, `background-color`, `text-decoration`, `text-shadow`, và `stroke`, `fill`, `stroke-width` cho text stroke/fill).
    ```css
    ::selection {
        background-color: #ff9900;
        color: white;
    }
    ::-moz-selection { /* Hỗ trợ Firefox */
        background-color: #ff9900;
        color: white;
    }
    ```
-   `::marker`: Cho phép tạo kiểu cho dấu đầu dòng hoặc số trong các phần tử danh sách (`<li>`) hoặc các phần tử khác được đặt `display: list-item`. Chỉ hỗ trợ một số thuộc tính nhất định (`color`, `font-size`, `content`, v.v.).
    ```css
    li::marker {
        color: red;
        font-size: 1.2em;
        content: "👉"; /* Thay thế dấu mặc định bằng icon */
    }
    ```

### 13.3. Nội Dung Tạo Sinh (Generated Content) Với `::before` và `::after`: Không Chỉ Dấu Ấn Thị Giác

`::before` và `::after` không chỉ để thêm các ký tự trang trí. Chúng có thể tạo ra các phần tử ảo để:

-   **Clearfix:** Kỹ thuật cũ để "fix" float layout, sử dụng `::after` với `content: ""; display: table; clear: both;`. (Flexbox/Grid hiện đã thay thế điều này trong nhiều trường hợp).
-   **Indicators/Icons:** Thêm mũi tên, icon trước hoặc sau liên kết hoặc phần tử.
-   **Decorations:** Thêm các đường kẻ, hình dạng đơn giản mà không cần thêm thẻ HTML.
-   **Tooltips/Badges:** Với `position: absolute` và nội dung từ thuộc tính `data-*` của HTML (sử dụng `content: attr(data-tooltip);`).

```css
.element-with-tooltip {
    position: relative; /* Để ::after absolute theo nó */
}

.element-with-tooltip::after {
    content: attr(data-tooltip); /* Lấy nội dung từ thuộc tính data-tooltip */
    position: absolute;
    bottom: 100%; /* Đặt tooltip phía trên phần tử */
    left: 50%;
    transform: translateX(-50%); /* Căn giữa */
    background-color: #333;
    color: white;
    padding: 5px 10px;
    border-radius: 4px;
    white-space: nowrap; /* Ngăn xuống dòng */
    opacity: 0; /* Mặc định ẩn */
    transition: opacity 0.3s ease;
    pointer-events: none; /* Không chắn click */
    /* Thêm triangle dưới tooltip */
    /* &::before { content: ""; position: absolute; top: 100%; left: 50%; margin-left: -5px; border-width: 5px; border-style: solid; border-color: #333 transparent transparent transparent; } */
}

.element-with-tooltip:hover::after {
    opacity: 1; /* Hiện tooltip khi hover */
}
```
Nội dung tạo sinh là công cụ mạnh mẽ giúp giảm lượng markup trong HTML cho các thành phần trang trí hoặc phụ trợ.

### 13.4. Pseudo-classes `:is()`, `:where()`, `:not()`, `:has()`

-   `:is(selector1, selector2, ...)`: Match *bất kỳ* selector nào trong danh sách. Giúp rút gọn code. Tính *specific* lấy của selector phức tạp nhất trong danh sách.
    ```css
    /* Thay vì */
    header h1, header h2, header h3,
    footer h1, footer h2, footer h3 {
        color: navy;
    }
    /* Sử dụng :is() */
    :is(header, footer) :is(h1, h2, h3) {
         color: navy;
    }
    ```
-   `:where(selector1, selector2, ...)`: Giống `:is()` nhưng độ ưu tiên luôn là **0**. Hữu ích khi muốn áp dụng style cơ bản mà không ảnh hưởng đến specificity.
    ```css
    /* Style cơ bản cho h1-h6 */
    :where(h1, h2, h3, h4, h5, h6) {
        margin-top: 1.5rem;
        margin-bottom: 1rem;
    }
    /* Các quy tắc khác sau đó dễ dàng ghi đè mà không cần Specificity cao */
    h2 { font-size: 1.8em; }
    ```
-   `:not(selector)`: Đã giới thiệu, chọn các phần tử không khớp với selector bên trong. Không đóng góp vào Specificity.
-   `:has(selector)`: Một selector rất mới (đã hỗ trợ rộng rãi trong các trình duyệt chính) - **Parent Selector**! Chọn một phần tử *cha* nếu nó chứa một phần tử con (hoặc descendant) khớp với selector bên trong `has()`.
    ```css
    /* Chọn tất cả các thẻ <a> có chứa một thẻ <img> bên trong */
    a:has(img) {
        border: 2px solid gold;
    }

    /* Chọn các thẻ article có H2 ĐỨNG NGAY SAU thẻ H1 */
    article:has(h1 + h2) {
         padding-top: 2em;
    }

    /* Style các thẻ label nếu input liên quan bị checked */
    label:has(input:checked) {
        font-weight: bold;
        color: blue;
    }
    ```
`:has()` là một tính năng thay đổi cuộc chơi, cho phép bạn tạo kiểu cho cha hoặc anh chị em dựa trên trạng thái hoặc sự hiện diện của con cháu, điều mà trước đây không thể làm chỉ với CSS thuần.

---

## Chương 14: Hoàn Thiện và Tinh Chỉnh - Hiệu Năng, Tiếp Cận Và Các Trạng Thái Nâng Cao

Điểm chạm cuối cùng trước khi đưa thiết kế ra "vũ trụ công cộng", đảm bảo mọi người đều có trải nghiệm tốt nhất.

### 14.1. Cải Thiện Tiếp Cận (A11y) - Focus và Preferencias

-   `outline`: Đừng xóa thuộc tính này một cách bừa bãi (`outline: none;`) trừ khi bạn cung cấp một trạng thái focus thay thế rõ ràng hơn. outline mặc định của trình duyệt rất quan trọng cho người dùng điều hướng bằng bàn phím. Thay vào đó, có thể tùy chỉnh nó:
    ```css
    *:focus {
        outline: 2px solid blue;
        outline-offset: 2px; /* Tạo khoảng trống giữa border/box và outline */
    }
    /* Hoặc tùy chỉnh chỉ cho các element cụ thể */
    button:focus, a:focus, input:focus, select:focus, textarea:focus {
        /* style tùy chỉnh của bạn */
    }
    ```
-   `:focus-visible`: Pseudo-class mới thông minh hơn. Nó chỉ áp dụng style focus khi trình duyệt tin rằng việc focus đó hữu ích cho người dùng (thường là khi dùng bàn phím, không phải khi click chuột).
    ```css
    /* Loại bỏ outline khi click bằng chuột/chạm màn hình */
    :focus:not(:focus-visible) {
        outline: none;
    }

    /* Style outline chỉ xuất hiện khi cần thiết (dùng bàn phím) */
    :focus-visible {
        outline: 2px dashed red;
        outline-offset: 2px;
    }
    ```
-   `@media (prefers-reduced-motion: reduce)`: Media Query này cho phép bạn tạo các style thay thế với ít hoặc không có chuyển động/animation cho những người dùng đã cài đặt tùy chọn giảm chuyển động trong hệ điều hành của họ.
    ```css
    /* Các animation mặc định */
    .element {
        animation: slidein 3s infinite alternate;
        transition: transform 0.5s ease;
    }

    @media (prefers-reduced-motion: reduce) {
        .element {
            animation: none; /* Tắt animation */
            transition: none; /* Tắt transition */
            /* Thêm các style static nếu cần */
        }
    }
    ```

### 14.2. Tối Ưu Font Web (`@font-face`)

Tải font tùy chỉnh có thể ảnh hưởng đến hiệu suất. `@font-face` rule cho phép bạn định nghĩa và nhúng font tùy chỉnh.

```css
@font-face {
    font-family: 'Space Odyssey'; /* Tên font bạn sẽ dùng trong CSS */
    src: url('spaceodyssey.woff2') format('woff2'),
         url('spaceodyssey.woff') format('woff'); /* Các định dạng file font */
    font-weight: normal;
    font-style: normal;
    font-display: swap; /* Quan trọng! Cách hiển thị font khi chưa tải xong */
                        /* swap: hiển thị fallback font rồi chuyển sang font chính */
                        /* fallback: hiển thị fallback rồi tải font chính, nếu lâu quá thì giữ fallback */
                        /* optional: tương tự fallback nhưng trình duyệt quyết định tải hay không */
                        /* block: chờ font tải xong (có thể gây Flash Of Unstyled Text - FOUT hoặc Invisible Text - FOIT) */
}

body {
    font-family: 'Space Odyssey', sans-serif; /* Sử dụng font tùy chỉnh, có font dự phòng */
}
```
Thuộc tính `font-display` rất quan trọng để quản lý trải nghiệm người dùng khi tải font web.

### 14.3. Tối Ưu Render Blocking CSS

CSS là resource blocking: trình duyệt phải tải và phân tích cú pháp tất cả CSS trước khi render trang (để tránh "flash of unstyled content"). File CSS lớn, nằm ở cuối trang có thể làm chậm quá trình hiển thị ban đầu.

-   Đặt thẻ `<link rel="stylesheet" href="styles.css">` trong `<head>`.
-   Giảm kích thước file CSS bằng cách minify, xóa bỏ style không dùng tới (audit code hoặc dùng công cụ).
-   Sử dụng kỹ thuật Critical CSS (đã nhắc ở chương trước).

### 14.4. Will-Change Property: Gợi Ý Về Sự Thay Đổi

Thuộc tính `will-change` cung cấp một gợi ý cho trình duyệt về những thuộc tính nào của một phần tử có khả năng thay đổi trong tương lai gần (ví dụ: qua animation hoặc transition). Điều này giúp trình duyệt tối ưu hóa render trước khi sự thay đổi xảy ra, thường bằng cách đẩy phần tử lên GPU.

```css
.moving-element {
    /* Báo cho trình duyệt rằng thuộc tính 'transform' sẽ thay đổi */
    will-change: transform, opacity;
}

.moving-element:hover {
     transform: translateX(100px);
     opacity: 0.8;
}
```
Sử dụng `will-change` cẩn thận, không áp dụng cho quá nhiều phần tử hoặc cho các thuộc tính thường xuyên thay đổi ngay lập tức, vì nó có thể tốn tài nguyên. Chỉ dùng cho các phần tử sẽ trải qua các biến đổi lớn hoặc phức tạp (animation kéo dài, cuộn trang parallax, v.v.).

---

## Chương 15: Các Phương Thức Lắp Ráp Mở Rộng - Tổng Quan Về Kiến Trúc CSS Hiện Đại

Ngoài các phương pháp cấu trúc code như BEM, OOCSS, SMACSS, thế giới CSS không ngừng sáng tạo các cách mới để tổ chức và viết style.

### 15.1. Utility-First CSS: Xây Dựng Từ Các Viên Gạch Nhỏ

Khác với phương pháp semantic CSS (class mô tả ý nghĩa - ví dụ: `.button-primary`), Utility-First (ví dụ: Tailwind CSS) tạo ra rất nhiều class rất nhỏ, chỉ làm một nhiệm vụ duy nhất (utility classes - ví dụ: `.margin-left-small`, `.flex-center`, `.text-bold`).

HTML sẽ có nhiều class hơn, nhưng code CSS tùy chỉnh lại giảm đi đáng kể. Bạn "lắp ráp" giao diện bằng cách kết hợp các utility class trực tiếp trong HTML.

```html
<!-- Ví dụ Utility-First (gần với cú pháp Tailwind) -->
<div class="flex items-center justify-center h-screen bg-gray-100">
    <div class="bg-white shadow-md rounded-lg p-6">
        <h2 class="text-2xl font-bold mb-4">Hello</h2>
        <button class="bg-blue-500 text-white font-bold py-2 px-4 rounded hover:bg-blue-700">
            Click Me
        </button>
    </div>
</div>
```
Phương pháp này tập trung vào tốc độ phát triển và việc dễ dàng tạo ra các biến thể thiết kế mà không phải viết CSS mới liên tục. Nó đòi hỏi một sự thay đổi trong cách tư duy so với CSS truyền thống.

### 15.2. CSS Modules & CSS-in-JS: Cô Lập Style Đến Từng Component

Trong các framework JavaScript hiện đại (React, Vue, Angular), việc quản lý CSS cho các component có thể khó khăn với vấn đề đặt tên class toàn cục dễ gây xung đột.

-   **CSS Modules:** File CSS mà class names được tự động hash để tạo ra các tên class duy nhất (scoped), đảm bảo style của component này không ảnh hưởng đến component khác.
    ```css
    /* component.module.css */
    .title {
        color: navy;
        font-size: 2em;
    }
    ```
    ```javascript
    /* React Component */
    import styles from './component.module.css';

    function MyComponent() {
      return <h1 className={styles.title}>Styled Title</h1>;
    }
    ```
-   **CSS-in-JS:** Viết CSS trực tiếp trong file JavaScript/JSX của component. Thư viện sẽ xử lý việc tạo ra CSS thực tế và đảm bảo tính scoped. (Ví dụ: styled-components, Emotion).
    ```javascript
    /* React Component with styled-components */
    import styled from 'styled-components';

    const Title = styled.h1`
      color: navy;
      font-size: 2em;
    `;

    function MyComponent() {
      return <Title>Styled Title</Title>;
    }
    ```
Các phương pháp này tập trung vào việc đưa CSS vào hệ sinh thái component của các SPA (Single Page Applications).


## Chương 16: Bố Cục Mở Rộng và Đặc Tính Hiển Thị - Floats, Clears và Overflow

Quay lại với những kỹ thuật bố cục truyền thống và cách kiểm soát khi nội dung tràn ra ngoài.

### 16.1. Floats: Thả Trôi Phần Tử (Kỹ Thuật Cũ)

Thuộc tính `float` ban đầu được dùng để làm cho hình ảnh "nổi" trong văn bản (giống như trong các báo giấy). Tuy nhiên, nó đã từng là kỹ thuật phổ biến để tạo ra layout đa cột trước khi Flexbox và Grid xuất hiện.

-   `float: left;`: Phần tử "nổi" sang bên trái và các phần tử block sau nó sẽ "quấn" quanh nó ở bên phải.
-   `float: right;`: Phần tử "nổi" sang bên phải và các phần tử block sau nó sẽ "quấn" quanh nó ở bên trái.
-   `float: none;`: Trở lại bình thường (giá trị mặc định).

Khi một phần tử được float, nó sẽ bị loại bỏ khỏi luồng tài liệu thông thường của các block element khác (nhưng vẫn ảnh hưởng đến inline element/text).

```css
.image-float {
    float: left; /* Ảnh nổi sang trái */
    margin-right: 10px; /* Tạo khoảng cách giữa ảnh và văn bản */
    margin-bottom: 10px;
}
```
**Hạn chế của Float:** Dễ gây các vấn đề như "container collapse" (chiều cao của container bị sụp đổ khi chứa float element) và cần dùng `clear` để quản lý luồng. Hiện nay, Float ít được dùng cho layout phức tạp, thay vào đó là Flexbox và Grid.

### 16.2. Clear: Dừng "Quấn Quanh" (Xử Lý Float)

Thuộc tính `clear` được đặt trên một phần tử để chỉ định rằng nó không được phép "quấn quanh" (allow floated elements to float beside) các phần tử float ở các phía được chỉ định.

-   `clear: left;`: Phần tử bắt đầu ngay *bên dưới* bất kỳ phần tử nào bị float sang trái.
-   `clear: right;`: Phần tử bắt đầu ngay *bên dưới* bất kỳ phần tử nào bị float sang phải.
-   `clear: both;`: Phần tử bắt đầu ngay *bên dưới* bất kỳ phần tử nào bị float ở cả hai bên (trái hoặc phải).

```css
.content-block {
    clear: both; /* Đảm bảo khối nội dung này luôn bắt đầu dưới cả float trái và float phải */
}
```
**Kỹ thuật Clearfix:** Một pattern phổ biến để ngăn chặn "container collapse" là sử dụng clearfix hack (thường dùng `::after` với `display: table` và `clear: both` trên container cha của các float element). Tuy nhiên, các kỹ thuật bố cục hiện đại (như làm cho container cha có `overflow: hidden` hoặc `display: flow-root`) hoặc đơn giản là sử dụng Flexbox/Grid đã làm cho clearfix trở nên ít cần thiết hơn nhiều.

### 16.3. Overflow: Quản Lý Nội Dung Tràn Bờ

Thuộc tính `overflow` kiểm soát cách trình duyệt xử lý nội dung của một phần tử khi nó tràn ra khỏi ranh giới hộp của phần tử đó.

-   `overflow: visible;`: Mặc định. Nội dung tràn sẽ hiển thị ra ngoài ranh giới.
-   `overflow: hidden;`: Nội dung tràn bị cắt bỏ và ẩn đi.
-   `overflow: scroll;`: Luôn hiển thị thanh cuộn (scrollbars), kể cả khi không cần thiết. Nội dung có thể cuộn được.
-   `overflow: auto;`: Hiển thị thanh cuộn *chỉ khi* nội dung tràn ra ngoài. (Hầu hết các trình duyệt coi như `scroll` nếu không đủ chỗ). Nội dung có thể cuộn được.
-   `overflow-x`, `overflow-y`: Điều khiển riêng biệt thanh cuộn ngang và dọc.

```css
.scrollable-box {
    width: 300px;
    height: 150px;
    overflow: auto; /* Chỉ hiển thị thanh cuộn khi cần */
    border: 1px solid black;
    /* Nội dung bên trong hộp này có thể cuộn nếu nó vượt quá 150px chiều cao hoặc 300px chiều rộng */
}

.hidden-content {
    width: 200px;
    height: 100px;
    overflow: hidden; /* Cắt bỏ phần nội dung tràn */
}
```

### 16.4. Visibility: Tàng Hình Nhưng Vẫn Chiếm Chỗ

Thuộc tính `visibility` ẩn hoặc hiển thị một phần tử nhưng vẫn giữ nguyên không gian chiếm chỗ của nó trong bố cục.

-   `visibility: visible;`: Mặc định, hiển thị phần tử.
-   `visibility: hidden;`: Ẩn phần tử, nhưng vẫn giữ chỗ trống. Tốt cho các hiệu ứng hiện/ẩn nơi bạn không muốn layout bị thay đổi.
-   `visibility: collapse;`: Hành xử như `hidden` cho các block element thông thường. Có ý nghĩa đặc biệt cho các hàng/cột trong table hoặc flex/grid item (giúp tiết kiệm không gian hiệu quả hơn).

```css
.modal {
    visibility: hidden; /* Ẩn modal, nhưng kích thước của nó vẫn ảnh hưởng đến luồng nếu position là static */
    opacity: 0; /* Thường dùng kết hợp opacity để tạo transition mượt mà khi ẩn/hiện */
    transition: visibility 0s linear 0.5s, opacity 0.5s linear; /* Transition opacity, delay visibility khi ẩn */
}

.modal.is-visible {
    visibility: visible;
    opacity: 1;
    transition-delay: 0s; /* Không delay khi hiện */
}
```
So sánh với `display: none;`: `display: none;` loại bỏ phần tử hoàn toàn khỏi luồng tài liệu, không chiếm không gian, và không tương tác (không click được, không focus được). `visibility: hidden;` thì ngược lại, phần tử vẫn tồn tại, vẫn chiếm không gian, chỉ là không nhìn thấy. Tuy nhiên, bạn vẫn không thể tương tác trực tiếp (ví dụ click chuột) vào phần tử có `visibility: hidden;` hay phần tử nằm dưới nó (trừ khi sử dụng `pointer-events`).

## Chương 17: Các Chế Độ Xem Đặc Biệt và Xuất Bản - Printing, Screen & Speech

CSS không chỉ dùng cho màn hình hiển thị thông thường của máy tính hoặc điện thoại. Nó có thể điều chỉnh style cho các ngữ cảnh khác.

### 17.1. Media Types trong Media Queries: Đích Đến Đa Dạng

Media Queries cho phép bạn chỉ định kiểu media áp dụng các style:

-   `screen`: Dành cho màn hình màu (desktop, mobile, tablet). Phổ biến nhất.
-   `print`: Dành cho việc in ấn.
-   `speech`: Dành cho trình đọc màn hình (screen readers). (Ít phổ biến trong thực tế).
-   `all`: Áp dụng cho tất cả các kiểu media.

Bạn có thể tạo stylesheet riêng cho từng media type hoặc sử dụng `@media` rule ngay trong file CSS chính.

```css
/* Style cho màn hình */
body {
    font-size: 1rem;
    margin: 20px;
}

/* Style chỉ cho in ấn */
@media print {
    body {
        font-size: 12pt; /* Sử dụng đơn vị points cho in ấn */
        color: black;
        background-color: white; /* Loại bỏ màu nền */
        margin: 0; /* Loại bỏ margin lớn */
    }
    nav, aside, footer, .sidebar, .ad {
        display: none; /* Ẩn các phần không cần in */
    }
    a {
        text-decoration: none; /* Bỏ gạch chân link */
        color: black; /* Đảm bảo link in ra màu đen */
    }
    /* Có thể thêm :after để hiển thị URL sau link */
    a[href]:after {
        content: " (" attr(href) ")";
        font-size: 9pt;
    }
}

/* Có thể nhúng file CSS cho print riêng biệt trong HTML */
/* <link rel="stylesheet" href="print.css" media="print"> */
```
Styling cho in ấn là một phần quan trọng để đảm bảo người dùng có thể xuất bản nội dung website của bạn một cách sạch đẹp.

### 17.2. Styling Cho Printing (`@media print`)

Khi styling cho print, hãy chú ý:

-   Sử dụng các đơn vị tuyệt đối như `pt`, `cm`, `in` mặc dù đơn vị tương đối cũng hoạt động.
-   Loại bỏ hoặc điều chỉnh các element không cần thiết cho in ấn (navbar, sidebar, quảng cáo).
-   Kiểm soát việc ngắt trang bằng thuộc tính `@page` (margin cho trang giấy) và các thuộc tính `break-before`, `break-after`, `break-inside`.
    ```css
    @media print {
        article {
            page-break-after: always; /* Bắt đầu bài viết tiếp theo trên trang mới */
        }
        h1, h2 {
            page-break-after: avoid; /* Tránh ngắt trang ngay sau tiêu đề */
        }
        table {
            page-break-inside: avoid; /* Tránh ngắt trang bên trong bảng */
        }
    }
    ```
-   Đảm bảo màu sắc và độ tương phản đủ tốt khi chuyển sang đơn sắc hoặc thang độ xám (nếu máy in không có màu).
-   Sử dụng background-color và background-image cần thận trọng vì nhiều trình duyệt mặc định không in background để tiết kiệm mực.

## Chương 18: Tương Lai Và Những Biên Giới Mới Của CSS

Thế giới CSS luôn chuyển động. Luôn có những đề xuất, những tính năng thử nghiệm đang được phát triển để giải quyết các thách thức mới.

### 18.1. Container Query Units (`cqw`, `cqh`, v.v.)

Đi cùng với `@container`, có các đơn vị tương đối mới dựa trên kích thước của container gần nhất đã được đánh dấu. Tương tự như `vw` và `vh` nhưng thay vì dựa vào viewport, chúng dựa vào container.

-   `cqw` (Container Query Width): 1% chiều rộng của container.
-   `cqh` (Container Query Height): 1% chiều cao của container.
-   `cqi` (Container Query Inline size): 1% kích thước theo chiều nội tuyến của container.
-   `cqb` (Container Query Block size): 1% kích thước theo chiều block của container.
-   `cqmin`: 1% kích thước nhỏ hơn giữa cqi và cqb.
-   `cqmax`: 1% kích thước lớn hơn giữa cqi và cqb.

```css
@container (min-width: 400px) {
    .card-item {
        font-size: 3cqi; /* Font size bằng 3% chiều rộng của container */
        padding: 2cqi; /* Padding bằng 2% chiều rộng của container */
    }
}
```
Các đơn vị này rất mạnh mẽ để tạo ra các component linh hoạt hoàn toàn độc lập với viewport.

### 18.2. Scroll-driven Animations (`@scroll-timeline`, `animation-timeline`)

Một lĩnh vực đang được phát triển cho phép điều khiển tiến trình của một animation dựa trên vị trí cuộn của một phần tử hoặc viewport. Mở ra khả năng tạo hiệu ứng parallax hoặc tiết lộ nội dung phức tạp chỉ bằng CSS.

```css
/* Ví dụ khái niệm (syntax có thể thay đổi tùy spec) */
@keyframes fade-in {
    from { opacity: 0; }
    to { opacity: 1; }
}

.element-to-animate {
    animation: fade-in linear;
    animation-timeline: scroll(); /* Liên kết animation với cuộn của root scroller (viewport) */
    /* animation-timeline: --my-timeline; (nếu định nghĩa timeline riêng) */
}
```
Đây là một ví dụ về sự đổi mới liên tục trong CSS.

### 18.3. `subgrid` (Trong CSS Grid)

Cho phép một grid item trở thành một grid container *nhưng sử dụng các dòng và cột* đã được định nghĩa bởi parent grid của nó. Hữu ích để căn chỉnh các element lồng nhau một cách chính xác với bố cục tổng thể của grid cha.

```css
.parent-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 10px;
}

.child-item {
    grid-column: 1 / span 3; /* Chiếm toàn bộ chiều rộng của parent grid */
    display: grid; /* Item này trở thành grid container */
    grid-template-columns: subgrid; /* Nhưng sử dụng lại 3 cột của parent */
    gap: inherit; /* Thừa hưởng gap từ parent */
}

.grandchild {
    /* Cháu giờ đây có thể đặt vị trí trực tiếp trên grid của parent */
    /* Ví dụ, cháu thứ nhất của child-item chiếm cột 2 của parent grid */
    grid-column: 2;
    /* ... hoặc bạn vẫn có thể định nghĩa hàng riêng cho cháu bên trong subgrid */
    grid-row: 1;
}
```
`subgrid` đã được hỗ trợ tốt hơn trên Firefox và đang được triển khai trên Chrome/Edge, là một bước tiến lớn cho khả năng căn chỉnh phức tạp với Grid.


## Chương 19: Hàm và Biểu Thức Trong CSS - Các Công Thức Động

CSS không chỉ là việc gán giá trị tĩnh. Với các hàm tích hợp, bạn có thể tính toán giá trị một cách linh hoạt dựa trên các yếu tố khác hoặc tạo ra các dải giá trị động.

### 19.1. Hàm `calc()`: Phép Tính Giữa Các Đơn Vị Khác Loại

Hàm `calc()` cho phép thực hiện các phép toán cơ bản (`+`, `-`, `*`, `/`) ngay trong giá trị của một thuộc tính CSS, thậm chí kết hợp các đơn vị khác nhau.

```css
.sidebar {
    /* Chiều rộng là 30% trừ đi 20px */
    width: calc(30% - 20px);
    float: left; /* Hoặc dùng flexbox/grid tốt hơn */
}

.header {
    height: calc(100vh - 50px); /* Chiều cao bằng 100% viewport trừ đi 50px của một element khác */
    /* Cần chú ý dấu cách xung quanh dấu +, -, * ,/ */
}

.dynamic-font {
    font-size: calc(1rem + 0.5vw); /* Font size tăng nhẹ theo chiều rộng viewport */
}

.grid-layout {
     display: grid;
     /* Định nghĩa cột: 100px + tự động + tự động */
     grid-template-columns: 100px calc(100% - 200px) 100px;
     /* Hoặc dùng fr units thường dễ hơn */
     /* grid-template-columns: 100px 1fr 100px; */
}
```
`calc()` là một công cụ mạnh mẽ để tạo ra các layout và kích thước linh hoạt hơn.

### 19.2. Hàm `min()`, `max()`, `clamp()`: Kiểm Soát Kích Thước Linh Hoạt

Các hàm này cho phép đặt ra các giới hạn hoặc một dải giá trị động cho thuộc tính.

-   `min(value1, value2, ...)`: Sử dụng giá trị *nhỏ nhất* trong danh sách các giá trị được cung cấp.
-   `max(value1, value2, ...)`: Sử dụng giá trị *lớn nhất* trong danh sách các giá trị được cung cấp.

```css
.responsive-element {
    width: min(90%, 500px); /* Chiều rộng là 90% của cha HOẶC 500px, lấy giá trị nhỏ hơn */
                            /* Nghĩa là: sẽ là 90% cho đến khi 90% lớn hơn 500px, lúc đó nó cố định ở 500px */

    padding: max(1em, 10px); /* Padding sẽ là 1em HOẶC 10px, lấy giá trị lớn hơn */
                             /* Nghĩa là: sẽ luôn có ít nhất 1em padding, hoặc 10px nếu 1em nhỏ hơn */
}
```
-   `clamp(min-value, preferred-value, max-value)`: Giới hạn một giá trị trong một khoảng nhất định. Hàm này nhận ba giá trị: giá trị tối thiểu, giá trị ưu tiên, và giá trị tối đa.
    ```css
    /* Kích thước font sẽ ưu tiên là 2vw, nhưng không nhỏ hơn 16px và không lớn hơn 24px */
    body {
        font-size: clamp(16px, 2vw, 24px);
    }

    /* Khoảng cách (padding/margin) sẽ ưu tiên là 5vw, nhưng không nhỏ hơn 20px và không lớn hơn 60px */
    .fluid-spacing {
        padding: clamp(20px, 5vw, 60px);
    }
    ```
`clamp()` là một kỹ thuật cực kỳ hiệu quả cho thiết kế Responsive Typography và khoảng cách linh hoạt. Nó giúp các giá trị co giãn mượt mà theo kích thước viewport nhưng không vượt quá các giới hạn cho phép.

### 19.3. Color Functions (`rgb()`, `rgba()`, `hsl()`, `hsla()` - Đã giới thiệu, Nâng cao hơn), `color-mix()`, `oklch()`, v.v.

CSS hiện đại có các hàm màu sắc mạnh mẽ hơn, cho phép thao tác với màu, kiểm soát độ trong suốt, và sử dụng các không gian màu tiên tiến.

-   `rgba(r, g, b, alpha)`, `hsla(h, s, l, alpha)`: Việc thêm kênh alpha đã được giới thiệu.
-   `color-mix(method, color1 percentage, color2)`: Pha trộn hai màu theo một tỷ lệ nhất định. Rất hữu ích để tạo các biến thể màu (ví dụ: một màu tối hơn hoặc nhạt hơn của màu chủ đạo).
    ```css
    :root {
        --brand-color: #007bff;
        --brand-color-dark: color-mix(in srgb, var(--brand-color) 80%, black); /* Pha 80% màu brand với 20% màu đen */
    }

    button {
        background-color: var(--brand-color);
    }
    button:hover {
        background-color: var(--brand-color-dark);
    }
    ```
-   `oklab()`, `oklch()`: Các không gian màu mới (đã hỗ trợ trên các trình duyệt hiện đại) mang tính ngữ nghĩa và dự đoán được kết quả hơn khi thao tác so với RGB hay HSL. Hữu ích cho gradient, animation màu.
-   `color()`: Cho phép sử dụng các không gian màu khác như `display-p3`.
-   Relative Color Syntax (`<color> of <color>`): Đề xuất cho phép thao tác trên một màu có sẵn (ví dụ: tạo màu mới sáng hơn màu `blue` một chút).

```css
/* Sử dụng oklch - L: Lightness (0-1), c: Chroma (mức độ màu sắc, 0-~0.4), h: Hue (0-360) */
background-color: oklch(0.7 0.15 200); /* Một màu lam */
```
Làm việc với màu sắc trong CSS đang ngày càng mạnh mẽ hơn.

## Chương 20: Các Thành Phần Tương Tác Đặc Biệt - Form Controls & Trạng Thái Nâng Cao

Form là xương sống của nhiều ứng dụng web, và tạo kiểu cho chúng thường gặp nhiều thách thức do các style mặc định phức tạp và không nhất quán giữa các trình duyệt.

### 20.1. Styling Inputs, Textareas, Selects

Các thành phần form gốc (`<input>`, `<textarea>`, `<select>`, `<button>`) rất khó để tùy chỉnh hoàn toàn vì trình duyệt render chúng bằng các widget gốc của hệ điều hành.

-   **Basic Styling:** Các thuộc tính như `width`, `padding`, `border`, `margin`, `font-size`, `color`, `background-color` thường hoạt động tốt.
-   **Thuộc tính `appearance: none;`:** Giúp loại bỏ hầu hết các style mặc định của trình duyệt/hệ điều hành trên các input (đặc biệt là `<select>`, radio/checkboxes), cho phép bạn style từ "đầu" dễ dàng hơn.
    ```css
    input[type="checkbox"],
    input[type="radio"] {
        appearance: none; /* Loại bỏ kiểu dáng mặc định */
        /* Từ đây, bạn có thể tự style hình vuông/tròn, background, border */
        /* Có thể dùng pseudo-elements ::before/::after để tạo dấu tích/chấm */
    }

    select {
        appearance: none; /* Loại bỏ mũi tên xổ xuống mặc định */
        padding-right: 20px; /* Tạo khoảng trống */
        background-image: url('down-arrow.svg'); /* Thêm mũi tên custom */
        background-repeat: no-repeat;
        background-position: right 5px center;
    }
    ```
-   **Styling Placeholders:** Sử dụng pseudo-element `::placeholder` (và các tiền tố `::-webkit-input-placeholder`, `:-moz-placeholder`, `::-ms-input-placeholder`, `:-ms-input-placeholder` cho khả năng tương thích tốt hơn).
    ```css
    input::placeholder {
        color: gray;
        font-style: italic;
    }
    /* Với tiền tố cho khả năng tương thích rộng hơn */
    ::-webkit-input-placeholder { color: gray; font-style: italic; }
    :-moz-placeholder           { color: gray; font-style: italic; opacity: 1; } /* Firefox cũ cần opacity */
    ::-moz-placeholder          { color: gray; font-style: italic; opacity: 1; } /* Firefox cũ cần opacity */
    :-ms-input-placeholder      { color: gray; font-style: italic; }
    ::-ms-input-placeholder     { color: gray; font-style: italic; }
    ```

### 20.2. Styling Trạng Thái Form: Validation, Disabled, Readonly

-   `:enabled`, `:disabled`, `:checked` (cho radio/checkbox): Đã giới thiệu.
-   `:read-only`: Áp dụng style cho các input có thuộc tính `readonly`.
-   `:required`: Áp dụng style cho các input có thuộc tính `required`.
-   `:valid`, `:invalid`: Áp dụng style dựa trên trạng thái hợp lệ của input (tuân theo type, required, pattern). Rất hữu ích cho visual feedback khi nhập liệu.
    ```css
    input:invalid {
        border-color: red;
        box-shadow: 0 0 5px rgba(255, 0, 0, 0.2);
    }

    input:valid {
        border-color: green;
    }
    ```
-   `:focus-within`: Pseudo-class áp dụng style cho một phần tử (ví dụ: container của form field) khi bất kỳ element nào *bên trong nó* nhận focus. Hữu ích để highlight cả một nhóm input liên quan hoặc wrapper form field.
    ```css
    .form-field:focus-within {
        outline: 2px solid blue; /* Tạo outline cho toàn bộ div khi input bên trong được focus */
    }
    ```

## Chương 21: Kiểm Soát Các Điểm Nhạy Cảm - Con Trỏ, Tương Tác Chuột/Chạm, Và Các Điểm Ngắt Bố Cục

Tinh chỉnh cách người dùng tương tác với giao diện ở mức độ cơ bản.

### 21.1. `cursor`: Tùy Chỉnh Con Trỏ Chuột

Kiểm soát hình dáng con trỏ chuột khi di chuyển qua một phần tử.

-   Các giá trị thông dụng: `auto` (mặc định), `default` (con trỏ mũi tên), `pointer` (hình bàn tay - cho các element có thể click), `text` (chữ I), `wait` (đồng hồ cát/xoay tròn), `help` (dấu chấm hỏi), `move`, `not-allowed` (cấm), `grab`, `grabbing`.
-   Có thể sử dụng hình ảnh tùy chỉnh: `cursor: url('my-custom-cursor.png'), auto;` (có thể fallback về giá trị chuẩn).

```css
.interactive-area {
    cursor: pointer; /* Biến con trỏ thành bàn tay */
}

.draggable-element {
    cursor: grab; /* Con trỏ nắm bàn tay chưa "bắt" */
}

.draggable-element:active {
     cursor: grabbing; /* Con trỏ nắm bàn tay đã "bắt" */
}
```

### 21.2. `pointer-events`: Kiểm Soát Các Sự Kiện Chuột/Chạm

Xác định khi nào một phần tử có thể trở thành mục tiêu của các sự kiện chuột (click, hover, drag, v.v.) hoặc sự kiện chạm.

-   `pointer-events: auto;`: Mặc định, phần tử nhận các sự kiện.
-   `pointer-events: none;`: Phần tử trở nên "trong suốt" với các sự kiện chuột/chạm. Các sự kiện sẽ "xuyên qua" nó và đến phần tử *bên dưới*.
    ```css
    .overlay {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.5);
        pointer-events: none; /* Dù overlay đang hiển thị, bạn vẫn có thể click vào các element nằm dưới nó */
        /* Khi bạn muốn cho phép click vào overlay (để đóng nó chẳng hạn), bạn cần dùng JS để bật lại pointer-events: auto; */
    }

    .disabled-button {
        opacity: 0.5;
        pointer-events: none; /* Button trông như disable và không click được */
    }
    ```
Đây là thuộc tính hữu ích cho các overlay không tương tác, disabled states, hoặc các hiệu ứng phức tạp nơi các lớp chồng lên nhau.

### 21.3. White-space & Overflow Wrapping

Chúng ta đã chạm vào `white-space` trước đó. Đi sâu hơn:

-   `white-space: nowrap;`: Ngăn văn bản xuống dòng. Khi kết hợp với `overflow: hidden` và `text-overflow: ellipsis;`, nó giúp cắt bớt văn bản dài bằng dấu "...".
-   `overflow-wrap: break-word;` (trước đây là `word-wrap`): Cho phép một từ dài không thể ngắt xuống dòng (ví dụ: URL dài) tự động ngắt ngay cả ở giữa từ đó, thay vì tràn ra ngoài container.
-   `word-break`: Kiểm soát chi tiết hơn việc ngắt từ (ví dụ: `break-all` sẽ ngắt giữa bất kỳ hai ký tự nào khi cần).

```css
.single-line-ellipsis {
    white-space: nowrap;      /* Ngăn xuống dòng */
    overflow: hidden;         /* Ẩn phần tràn */
    text-overflow: ellipsis;  /* Thay thế phần bị ẩn bằng dấu ... */
}

.long-url-container {
    width: 200px;
    word-break: break-all; /* Ngắt bất kỳ đâu trong từ nếu cần để vừa container */
    /* Hoặc phổ biến hơn, chỉ ngắt nếu không đủ chỗ cho cả từ */
    /* overflow-wrap: break-word; */
}
```

## Chương 22: Kiến Trúc Nâng Cao - Modular CSS và Pattern Library

Ngoài các phương pháp BEM/SMACSS, làm việc với CSS ở quy mô lớn đòi hỏi tư duy về module hóa và xây dựng các hệ thống thiết kế.

### 22.1. CSS Modular và Component-Based Thinking

-   **Component-Based:** Thay vì viết CSS cho từng trang riêng lẻ, hãy viết CSS cho các thành phần độc lập (ví dụ: button, card, modal, navigation). Điều này giúp tái sử dụng code, dễ dàng quản lý và kiểm thử. Các phương pháp như BEM hoặc sử dụng CSS Modules/CSS-in-JS hỗ trợ tư duy này.
-   **Đóng gói CSS:** Mỗi component nên "đóng gói" style của riêng nó. Điều này giảm khả năng xung đột giữa các component. CSS Modules và CSS-in-JS làm điều này một cách tự động. Với CSS thuần, bạn có thể dựa vào quy ước đặt tên (như BEM) hoặc sử dụng custom properties cục bộ cho component.

### 22.2. Thiết Kế Token (Design Tokens)

Design Tokens là các biến nhỏ nhất (nguyên tử) thể hiện các quyết định về thiết kế (ví dụ: màu sắc chủ đạo, spacing unit, kích thước font tiêu đề H1). Chúng không chỉ là biến CSS (`--primary-color`) mà còn có thể tồn tại dưới các định dạng khác (JSON, Sass variables, v.v.) để được chia sẻ giữa các nền tảng (web, mobile).

```css
/* Được biên dịch từ file Design Tokens */
:root {
    --spacing-xs: 4px;
    --spacing-sm: 8px;
    --spacing-md: 16px; /* etc. */
    --color-brand-primary: #007bff;
    --color-brand-secondary: #6c757d; /* etc. */
    --font-family-base: 'Arial', sans-serif;
    --font-size-body: 16px;
    --font-size-h1: 32px; /* etc. */
    --border-radius-base: 4px; /* etc. */
}

.button {
    padding: var(--spacing-md) var(--spacing-lg);
    background-color: var(--color-brand-primary);
    border-radius: var(--border-radius-base);
    font-size: var(--font-size-body);
    font-family: var(--font-family-base);
}
```
Design Tokens tạo ra một nguồn chân lý duy nhất cho các giá trị thiết kế, giúp đảm bảo sự nhất quán trên toàn bộ sản phẩm và cho phép thay đổi global dễ dàng hơn.

### 22.3. Style Guides và Pattern Libraries (Storybook, etc.)

Là các website hoặc tài liệu tổng hợp hiển thị tất cả các component và style trong dự án.

-   **Style Guides:** Tài liệu về cách sử dụng màu sắc, font, spacing, giọng điệu thương hiệu.
-   **Pattern Libraries / Component Libraries:** Tập hợp các component UI có thể tương tác được, kèm theo mã nguồn (HTML/CSS/JS). Công cụ như Storybook phổ biến cho việc này.

Việc xây dựng và duy trì một Pattern Library là cực kỳ quan trọng cho các dự án lớn, giúp đảm bảo sự nhất quán, tăng tốc độ phát triển và tạo điều kiện cộng tác giữa designer và developer.

## Chương 23: Kiểm Soát Luồng Và Hình Dạng Nâng Cao - Legacy Floats Revisited, Multi-columns, and Shapes

Dù Flexbox và Grid là hiện đại, hiểu về các phương pháp bố cục truyền thống hơn vẫn quan trọng khi làm việc với code cũ hoặc xử lý các trường hợp cụ thể.

### 23.1. Vị trí Theo Chiều Dọc Không Dùng Flex/Grid/Position

Trước Flexbox và Grid, việc căn giữa một phần tử theo chiều dọc (hoặc căn theo baseline) là một "nhiệm vụ bất khả thi" trong nhiều tình huống. Một số kỹ thuật "hack" đã ra đời:

-   **Sử dụng `display: table-cell;` và `vertical-align: middle;`:** Đặt container cha có `display: table;` và phần tử muốn căn giữa có `display: table-cell; vertical-align: middle;`. Kỹ thuật này khá hiệu quả nhưng làm thay đổi Box Model và cách hoạt động của `display: table-cell` không linh hoạt như Flex/Grid.
    ```css
    .parent {
        display: table;
        height: 200px; /* Cần có chiều cao xác định */
    }
    .child {
        display: table-cell;
        vertical-align: middle; /* Căn giữa theo chiều dọc */
        text-align: center; /* Căn giữa theo chiều ngang (nội dung inline/inline-block) */
        border: 1px solid red;
    }
    ```
-   **Kết hợp `position: absolute;` và `transform: translateY(-50%);`:** Phần tử con cần căn giữa có `position: absolute; top: 50%;`. `top: 50%` sẽ đặt mép trên của nó ở giữa container cha. Sau đó, dùng `transform: translateY(-50%);` để dịch chuyển nó *lên trên* 50% chính *chiều cao của nó*, đưa tâm của phần tử về đúng giữa.
    ```css
    .parent {
        position: relative; /* Cha cần relative (hoặc khác static) để con absolute theo nó */
        height: 200px;
    }
    .child {
        position: absolute;
        top: 50%;
        left: 50%; /* Kết hợp để căn giữa cả ngang và dọc */
        transform: translate(-50%, -50%); /* Dịch chuyển theo cả hai trục */
        width: 100px;
        height: 100px;
        background-color: blue;
    }
    ```
Cả hai kỹ thuật này đều có điểm mạnh và yếu riêng so với Flexbox (đặc biệt với `align-items: center`, `justify-content: center`) và Grid, nhưng rất cần biết khi xử lý các code base cũ.

### 23.2. Multi-column Layout: Chia Văn Bản Thành Các Cột Báo

CSS Multi-column Layout cho phép chia nội dung của một khối (block container) thành nhiều cột, giống như trong báo hoặc tạp chí.

-   `column-count`: Số lượng cột bạn muốn chia nội dung thành.
-   `column-width`: Chiều rộng lý tưởng của mỗi cột. Trình duyệt sẽ tự động tính số cột nếu chỉ định `column-width`. Nếu chỉ định cả hai, `column-count` sẽ được ưu tiên, nhưng trình duyệt sẽ không tạo cột nào nhỏ hơn giá trị `column-width`.
-   `columns`: Thuộc tính viết tắt cho `column-width` và `column-count`.
-   `column-gap`: Khoảng cách giữa các cột.
-   `column-rule`: Thêm đường phân cách giữa các cột (giống `border` nhưng chỉ giữa các cột).

```css
.newspaper-text {
    columns: 200px 3; /* Chiều rộng cột ~200px, tối đa 3 cột */
    /* hoặc */
    /* column-count: 3; */
    /* column-width: 200px; */

    column-gap: 40px;
    column-rule: 1px solid #ccc; /* Đường phân cách giữa các cột */
}

/* Sử dụng thuộc tính đặc biệt cho các element spanning columns (nối cột) */
.span-columns {
    column-span: all; /* Element này sẽ trải rộng qua tất cả các cột */
    /* column-span: none; (mặc định) */
}
```
Multi-column hữu ích cho các khối văn bản dài mà bạn muốn tổ chức gọn gàng hơn trên các màn hình rộng.

### 23.3. CSS Shapes: Làm Văn Bản Quấn Quanh Hình Dạng Bất Kỳ

Thuộc tính `shape-outside` cho phép văn bản (và inline content khác) quấn quanh một phần tử float theo một hình dạng phức tạp, thay vì chỉ là hình hộp bounding box mặc định.

-   `shape-outside: circle()`, `ellipse()`, `inset()`, `polygon()`: Tạo hình dạng từ các hàm định nghĩa hình học.
-   `shape-outside: url(...)`: Tạo hình dạng từ độ trong suốt của một hình ảnh (các vùng hoàn toàn trong suốt bị loại bỏ).
-   `shape-image-threshold`: Đặt ngưỡng alpha để xác định vùng shape khi dùng `shape-outside: url(...)`.
-   `shape-margin`: Thêm khoảng cách giữa shape và văn bản.

```css
.float-element {
    float: left; /* Chỉ hoạt động trên float element */
    width: 150px;
    height: 150px;
    background-color: transparent; /* Hoặc background-image */

    /* Tạo hình tròn */
    shape-outside: circle();
    /* Thêm margin 10px quanh hình dạng */
    shape-margin: 10px;
}

/* Ví dụ dùng hình ảnh có kênh alpha */
.float-image {
    float: right;
    width: 200px;
    height: 250px;
    background-image: url('transparent-shape.png');
    background-size: contain;
    background-repeat: no-repeat;

    shape-outside: url('transparent-shape.png');
    /* Chỉ định pixel nào có alpha lớn hơn 0.5 sẽ được coi là phần shape */
    shape-image-threshold: 0.5;
    shape-margin: 15px;
}
```
CSS Shapes là một công cụ mạnh mẽ cho các bố cục dạng tạp chí hoặc các thiết kế giàu hình ảnh nơi bạn muốn kiểm soát chính xác cách văn bản tương tác với hình ảnh hoặc các yếu tố đồ họa.

## Chương 24: Tinh Chỉnh Thành Phần Đặc Thù Và Trạng Thái Giao Diện

Kiểm soát các chi tiết nhỏ nhưng quan trọng, ảnh hưởng đến cảm nhận và tương tác của người dùng.

### 24.1. Styling Scrollbars: Lối Đi Riêng Của Thanh Cuộn

Thanh cuộn (scrollbars) mặc định của trình duyệt thường khó tùy chỉnh hoàn toàn bằng CSS chuẩn. WebKit (Chrome, Safari, Edge dựa trên Chromium) cung cấp một bộ pseudo-elements riêng cho phép tùy chỉnh:

-   `::-webkit-scrollbar`: Toàn bộ thanh cuộn.
-   `::-webkit-scrollbar-track`: Vùng track mà thanh cuộn chạy qua.
-   `::-webkit-scrollbar-thumb`: "Cần gạt" mà bạn kéo để cuộn.
-   `::-webkit-scrollbar-button`: Các nút lên/xuống ở đầu thanh cuộn.
-   `::-webkit-scrollbar-corner`: Góc dưới bên phải khi cả thanh cuộn ngang và dọc hiển thị.

```css
/* Styling thanh cuộn cho một div cụ thể */
.custom-scrollable::-webkit-scrollbar {
  width: 8px; /* Chiều rộng thanh cuộn dọc */
  height: 8px; /* Chiều cao thanh cuộn ngang */
}

.custom-scrollable::-webkit-scrollbar-track {
  background: #f1f1f1;
  border-radius: 10px;
}

.custom-scrollable::-webkit-scrollbar-thumb {
  background: #888;
  border-radius: 10px;
}

.custom-scrollable::-webkit-scrollbar-thumb:hover {
  background: #555;
}

/* Đối với Firefox (standard pending) - ít tùy chỉnh hơn */
/* scrollbar-color: #888 #f1f1f1; /* thumb color / track color */
/* scrollbar-width: thin | auto | none; */

/* Gutter của thanh cuộn */
/* scrollbar-gutter: auto | stable both-edges | stable; */
```
Lưu ý: Các pseudo-elements WebKit không phải là chuẩn CSS và có thể không hoạt động trên tất cả các trình duyệt. Các thuộc tính `scrollbar-color`, `scrollbar-width` đang được chuẩn hóa nhưng hỗ trợ vẫn hạn chế so với WebKit. `scrollbar-gutter` là một thuộc tính mới hữu ích giúp duy trì bố cục ổn định ngay cả khi thanh cuộn xuất hiện/biến mất.

### 24.2. `user-select` và `resize`: Kiểm Soát Tương Tác Nội Dung

-   `user-select`: Kiểm soát xem người dùng có thể chọn (bôi đen) văn bản của một phần tử hay không.
    -   `auto`: Mặc định, cho phép chọn văn bản (trừ các input, textarea, ...).
    -   `none`: Không thể chọn văn bản. Hữu ích cho các thành phần giao diện chỉ để hiển thị, không cho phép copy.
    -   `text`: Có thể chọn văn bản.
    -   `all`: Toàn bộ nội dung của element (nếu click vào bất kỳ đâu trong đó) sẽ được chọn.
    -   `contain`: Chỉ cho phép chọn văn bản bên trong element, không thể kéo chọn ra ngoài nó.
    ```css
    .non-selectable-header {
        user-select: none;
    }
    ```
-   `resize`: Cho phép người dùng thay đổi kích thước của các phần tử, đặc biệt là `<textarea>`.
    -   `none`: Không cho phép thay đổi kích thước.
    -   `both`: Cho phép thay đổi kích thước cả ngang và dọc.
    -   `horizontal`: Chỉ thay đổi chiều ngang.
    -   `vertical`: Chỉ thay đổi chiều dọc.
    ```css
    textarea {
        resize: vertical; /* Chỉ cho phép kéo giãn theo chiều dọc */
    }
    ```

### 24.3. Trạng Thái `:empty` và `:blank`

-   `:empty`: Chọn một phần tử không có con nào, kể cả text node hoặc whitespace node.
    ```css
    div:empty {
        border: 1px dashed red; /* Các div rỗng sẽ có border đứt nét */
    }
    ```
-   `:blank`: Tương tự `:empty` nhưng tinh tế hơn: nó *không* coi các whitespace node là nội dung. (Mức độ hỗ trợ chưa rộng rãi bằng `:empty`). Hữu ích để tạo kiểu cho các vùng placeholder chỉ khi chúng thực sự rỗng.

## Chương 25: Performance Thực Chiến và Công Cụ Hỗ Trợ Chuyên Sâu

Vượt ra ngoài lý thuyết, đây là các bước thực tế và các công cụ để đảm bảo CSS của bạn hiệu quả và dễ quản lý.

### 25.1. Auditing CSS và Loại Bỏ Code Chết (Dead Code)

Trong các dự án lớn, CSS có xu hướng phình to với các style không còn được sử dụng ("code chết"). Việc loại bỏ chúng giúp giảm kích thước file và cải thiện hiệu suất tải.

-   **Sử dụng Browser DevTools Coverage tab:** Tab này trong Chrome/Firefox DevTools giúp xác định lượng code CSS/JS đã được sử dụng trong quá trình duyệt trang. Sau khi tải và tương tác với trang, nó hiển thị tỷ lệ phần trăm và các đoạn code không được dùng tới.
-   **Công cụ tự động:** Các công cụ như PurgeCSS có thể phân tích code (HTML, template engines, JavaScript frameworks) và file CSS của bạn, sau đó xóa bỏ các style không tìm thấy trong code. Thường được tích hợp vào quá trình build.
    ```bash
    # Ví dụ sử dụng PurgeCSS (CLI)
    purgecss --css input.css --content index.html "src/**/*.js" --output output.css
    ```
-   **Refactoring thường xuyên:** Dành thời gian để xem xét và làm sạch code CSS. Sử dụng các phương pháp như BEM giúp dễ dàng nhận diện các class không dùng tới hoặc có thể tái sử dụng.

### 25.2. Tối Ưu Ảnh Nền và Biểu Tượng (Sprites, WebP/AVIF)

Kích thước và số lượng ảnh nền (`background-image`) ảnh hưởng lớn đến hiệu suất.

-   **CSS Sprites:** Kết hợp nhiều biểu tượng nhỏ thành một file ảnh duy nhất. CSS sau đó sử dụng `background-image` (đến file sprite đó) và `background-position` để hiển thị biểu tượng cụ thể bằng cách "cắt" phần ảnh tương ứng. Giúp giảm số lượng HTTP requests.
-   **Sử dụng các định dạng ảnh hiện đại:** Thay thế PNG/JPEG bằng WebP hoặc AVIF khi có thể. Chúng cung cấp khả năng nén tốt hơn đáng kể ở cùng chất lượng hoặc chất lượng tốt hơn ở cùng kích thước file. Có thể sử dụng Media Queries hoặc thuộc tính HTML `<picture>` để cung cấp định dạng dự phòng cho trình duyệt không hỗ trợ.
-   **Vector Graphics:** Sử dụng SVG cho biểu tượng và đồ họa đơn giản. SVG có thể thay đổi kích thước mà không giảm chất lượng, thường có kích thước file nhỏ hơn và có thể style bằng CSS.

### 25.3. CSS và Critical Rendering Path

CSS blocking the rendering path (trình duyệt chờ CSS tải và phân tích cú pháp xong mới bắt đầu hiển thị nội dung).

-   **Inline Critical CSS:** Đưa các style tối thiểu cần thiết để hiển thị phần nội dung đầu tiên của trang (above-the-fold) vào trong thẻ `<style>` ngay trong HTML `<head>`. Phần CSS còn lại có thể được tải không đồng bộ (asynchronously). Có công cụ tự động hóa việc này (critical CSS generators).
-   **Attribute `media` trong `<link>`:** Sử dụng `media="print"` hoặc `media="screen and (max-width: 600px)"` để báo cho trình duyệt rằng stylesheet này chỉ áp dụng trong các điều kiện nhất định, và trình duyệt có thể tải chúng với ưu tiên thấp hơn hoặc không chặn render ban đầu.
    ```html
    <link rel="stylesheet" href="styles-critical.css"> <!-- Blocking render -->
    <link rel="stylesheet" href="styles-large.css" media="screen and (min-width: 600px)"> <!-- Not render-blocking initially -->
    <link rel="stylesheet" href="styles-print.css" media="print"> <!-- Not render-blocking for screen -->
    ```
-   **Defer non-critical CSS:** Tải các file CSS lớn, không cần thiết cho render ban đầu bằng JavaScript sau khi trang đã hiển thị. Cần cẩn thận để tránh FOUC (Flash Of Unstyled Content).

## Chương 26: Chạm Tới Biên Giới Mới - `@property` và CSS Houdini

Bước vào vùng lãnh thổ thú vị nhất của CSS: khả năng mở rộng ngôn ngữ và tương tác sâu hơn với render engine của trình duyệt.

### 26.1. `@property`: Đăng Ký Biến CSS Với Kiểu Dữ Liệu và Khả Năng Kế Thừa/Animation

Rule `@property` cho phép đăng ký Custom Property (`--ten-bien`) để trình duyệt biết rõ kiểu dữ liệu của nó (ví dụ: `<color>`, `<number>`, `<length>`), giá trị ban đầu (initial value), và liệu nó có kế thừa từ cha xuống con hay không (`inherits`). Điều này mở ra khả năng animation (hoạt ảnh) các custom property, điều mà trước đây rất khó khăn hoặc không thể.

```css
/* Đăng ký biến --my-color */
@property --my-color {
    syntax: '<color>';       /* Kiểu dữ liệu là màu sắc */
    initial-value: blue;    /* Giá trị ban đầu */
    inherits: false;        /* Không kế thừa từ cha */
}

/* Đăng ký biến --my-number */
@property --my-number {
    syntax: '<number>';      /* Kiểu dữ liệu là số */
    initial-value: 0;
    inherits: false;
}

.element {
    --my-color: red; /* Gán giá trị ban đầu (đã được đăng ký kiểu) */
    --my-number: 100;

    transition: --my-color 0.5s ease, --my-number 0.5s ease; /* Giờ có thể animate biến! */
}

.element:hover {
    --my-color: green; /* Hover -> đổi màu */
    --my-number: 200; /* Hover -> đổi số */
}

/* Có thể dùng hàm calc() với biến kiểu số */
.element-size {
     --my-number: 10;
     width: calc(10px * var(--my-number)); /* Width 100px ban đầu */
     transition: --my-number 1s;
}
.element-size:hover {
     --my-number: 50; /* Width animate từ 100px đến 500px */
}
```
`@property` là một phần của CSS Houdini và là một tính năng thay đổi lớn, giúp các Custom Property trở nên mạnh mẽ và linh hoạt hơn bao giờ hết.

### 26.2. CSS Houdini: Lớp Tinh Chỉnh Mức Độ Thấp

Houdini là một nhóm các API cấp thấp cho phép nhà phát triển mở rộng CSS, làm cho việc tạo kiểu mạnh mẽ hơn và dễ đoán hơn. Nó mở "bên trong" trình duyệt, cho phép lập trình viên can thiệp vào quá trình render.

-   **Worklet API (Paint Worklet, Animation Worklet, Layout Worklet):** Cho phép chạy code JavaScript để can thiệp vào quá trình paint, animate hoặc layout mà không chặn main thread của trình duyệt (vì chạy ở Worklet). Ví dụ: tạo hiệu ứng background tùy chỉnh bằng Paint Worklet, hoặc tạo animation phức tạp được đồng bộ hóa với scroll bằng Animation Worklet.
-   **Properties and Values API (`@property`):** Như đã giới thiệu ở trên, đây là phần Houdini giúp định nghĩa Custom Properties một cách chặt chẽ.
-   **Typing Object Model (CSS Typed OM):** Cung cấp cách tiếp cận các giá trị CSS dưới dạng các object JavaScript có kiểu dữ liệu, thay vì chỉ là các chuỗi văn bản như DOM CSSOM truyền thống. Giúp thao tác và tính toán với giá trị CSS chính xác hơn.

```javascript
// Ví dụ ngắn về Typed OM
let element = document.querySelector('.my-element');
let computedStyle = element.computedStyleMap();

// Lấy giá trị width dưới dạng CSSUnitValue object (có kiểu và đơn vị)
let width = computedStyle.get('width');
console.log(width.value, width.unit); // ví dụ: 200 'px'

// Thực hiện phép toán
element.style.width = CSSUnitValue.add(width, new CSSUnitValue(50, 'px')); // Cộng thêm 50px
```
Houdini vẫn đang trong quá trình phát triển và áp dụng (đặc biệt là Worklets), nhưng `@property` đã khá phổ biến trên các trình duyệt hiện đại. Đây là hướng đi để CSS trở nên linh hoạt và có thể mở rộng theo cách chưa từng có.

