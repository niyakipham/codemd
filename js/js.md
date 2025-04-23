

## File: 01_gioi_thieu_js.md

```markdown
# 🌐 Bài 1: Chào Mừng Đến Với Thế Giới JavaScript

### 🤔 JavaScript là gì?

Xin chào! Bài học đầu tiên của chúng ta sẽ là màn chào hỏi thân mật với JavaScript (JS). Đừng nhầm lẫn với Java nhé, chúng hoàn toàn khác nhau, giống như một chiếc xe thể thao tốc độ cao và một tàu vũ trụ vậy! (À, tàu vũ trụ có lẽ hơi phóng đại, nhưng ý tôi là chúng không giống nhau).

JavaScript là một ngôn ngữ lập trình thông dịch (interpreted language) chủ yếu được sử dụng để tạo ra các nội dung động và tương tác trên các trang web. Tức là, thay vì trang web chỉ là những thông tin tĩnh, bạn có thể có các nút bấm phản ứng, hiệu ứng đẹp mắt, các form thông minh, hay thậm chí là các trò chơi trực tuyến ngay trong trình duyệt!

### 🕰 Lịch sử Hình Thành

JavaScript được Brendan Eich tạo ra trong vòng 10 ngày vào năm 1995 khi ông làm việc tại Netscape Communications. Ban đầu, nó có tên là Mocha, sau đổi thành LiveScript, và cuối cùng là JavaScript. Tên gọi này có thể là một chiến lược marketing để "dựa hơi" sự phổ biến của Java thời bấy giờ, nhưng thực sự JS đã chứng minh được sức mạnh độc lập và độc đáo của mình.

### 🚀 JavaScript Chạy Ở Đâu?

1.  **Trong Trình Duyệt (Client-side JS):** Đây là môi trường phổ biến nhất. Mã JS của bạn được nhúng vào trang HTML và trình duyệt sẽ đọc, phân tích và thực thi nó. JS có thể thao tác với nội dung trang (DOM), phản ứng lại hành động của người dùng (Event Handling), gửi/nhận dữ liệu từ server mà không cần tải lại trang (AJAX), v.v.
2.  **Ngoài Trình Duyệt (Server-side JS, Mobile, Desktop, ...):** Nhờ có các nền tảng như Node.js (để chạy JS ở server), React Native (cho mobile), Electron (cho desktop), JS đã vượt ra khỏi ranh giới của trình duyệt web. Điều này mở ra những khả năng phi thường: xây dựng toàn bộ ứng dụng web (frontend và backend) chỉ với một ngôn ngữ!

### ✨ Tại Sao Nên Học JavaScript?

*   **Phổ Biến Khổng Lồ:** JavaScript là ngôn ngữ lập trình được sử dụng nhiều nhất trên thế giới.
*   **Đa Năng:** Xây dựng website, ứng dụng di động, ứng dụng desktop, game, thậm chí cả IoT (Internet of Things)!
*   **Cộng Đồng Lớn:** Dễ dàng tìm kiếm tài liệu, hướng dẫn và sự trợ giúp khi gặp khó khăn.
*   **Nhu Cầu Thị Trường Cao:** Lập trình viên JavaScript luôn là một trong những vị trí hot nhất trên thị trường lao động công nghệ.
*   **Cập Nhật Liên Tục:** JS (qua chuẩn ECMAScript) luôn được cải tiến, bổ sung các tính năng hiện đại, giúp code ngày càng gọn gàng và mạnh mẽ.

### 🔧 Công Cụ Cần Chuẩn Bị

Bạn không cần gì quá "ngầu" hay đắt tiền đâu! Chỉ cần:

1.  **Một Trình Duyệt Hiện Đại:** Chrome, Firefox, Edge, Safari... (có cả DevTools tích hợp, rất hữu ích để gỡ lỗi).
2.  **Một Trình Soạn Thảo Code:** VS Code (miễn phí, cực kỳ phổ biến và mạnh mẽ), Sublime Text, Atom, hoặc thậm chí Notepad++ cũng được.
3.  **Kết Nối Internet:** Để tra cứu và cài đặt thêm nếu cần.

### 🚦 Bước Tiếp Theo

Ở các bài học tiếp theo, chúng ta sẽ cùng đi sâu vào những khái niệm cơ bản nhất: cách lưu trữ dữ liệu (biến, kiểu dữ liệu), cách ra lệnh cho máy tính thực hiện các phép toán (toán tử), và cách điều khiển luồng thực thi chương trình (câu lệnh điều kiện, vòng lặp).

Hãy sẵn sàng để bật chế độ "deep learning" nào! 🚀
```

---

## File: 02_bien_va_kieu_du_lieu.md

```markdown
# 💾 Bài 2: Biến và Các Kiểu Dữ Liệu trong JavaScript

### ✨ Biến (Variables)

Hãy tưởng tượng bạn có một cái hộp nhỏ, bạn muốn lưu một thứ gì đó vào đó (ví dụ: số 10, hoặc đoạn văn bản "Xin chào"). Cái hộp đó chính là **biến**. Biến dùng để lưu trữ dữ liệu trong chương trình của bạn.

Trong JavaScript, bạn dùng các từ khóa sau để khai báo biến:

1.  **`var` (Cũ):** Ít được dùng trong code hiện đại do có những quirks (đặc điểm hơi khó lường) về scope.
2.  **`let` (ES6+):** Nên dùng khi bạn biết rằng giá trị của biến sẽ thay đổi. Có scope tốt hơn `var`.
3.  **`const` (ES6+):** Nên dùng khi giá trị của biến sẽ KHÔNG thay đổi sau khi được gán lần đầu. Nếu cố gắng gán lại, sẽ báo lỗi. Dùng `const` giúp code dễ đọc và an toàn hơn.

**Ví dụ:**

```javascript
let tenNguoiDung = "Alice"; // Khai báo biến tenNguoiDung với giá trị ban đầu
const PI = 3.14159;       // Khai báo hằng số PI
var tuoi = 30;            // Ví dụ dùng var (hạn chế dùng)

console.log(tenNguoiDung); // Output: Alice

tenNguoiDung = "Bob";      // Có thể thay đổi giá trị của biến let
console.log(tenNguoiDung); // Output: Bob

// PI = 3.14;            // Sẽ gây lỗi nếu cố gắng gán lại cho biến const
```

### 🏷 Quy Tắc Đặt Tên Biến

*   Tên biến có thể bắt đầu bằng chữ cái (a-z, A-Z), dấu gạch dưới (`_`), hoặc dấu đô la (`$`).
*   Các ký tự tiếp theo có thể bao gồm số (0-9).
*   Không được bắt đầu bằng số.
*   Không được dùng các từ khóa dành riêng của JavaScript (như `if`, `else`, `for`, `function`, `let`, `const`, `var`, v.v.).
*   Nên đặt tên có ý nghĩa và tuân theo quy ước (ví dụ: `camelCase` - từ đầu tiên viết thường, các từ sau viết hoa chữ cái đầu tiên, như `tenNguoiDung`).

### 🧩 Các Kiểu Dữ Liệu (Data Types)

Dữ liệu bạn lưu trong biến có thể có nhiều "loại" khác nhau. JavaScript có 8 kiểu dữ liệu (tính đến hiện tại, trong đó 7 kiểu nguyên thủy và 1 kiểu đối tượng).

**7 Kiểu Nguyên Thủy (Primitive Types):**

1.  **`string` (Chuỗi):** Biểu diễn văn bản. Được bao bọc bởi dấu nháy đơn (`'...'`), nháy kép (`"..."`), hoặc backticks (`` `...` `` - cho template literals).
    ```javascript
    let ten = "Hoàng";
    let loiChao = 'Chào bạn!';
    let thoTinh = `Đây là một dòng
    xuống dòng được này!
    Biến: ${ten}`; // Template literals cho phép nhúng biến
    ```
2.  **`number` (Số):** Biểu diễn số nguyên hoặc số thập phân. JavaScript không phân biệt rõ ràng số nguyên và số thực như một số ngôn ngữ khác.
    ```javascript
    let tuoi = 25;
    let giaTien = 99.99;
    let soLon = 1e6; // Biểu diễn số 1,000,000 (ký hiệu khoa học)
    ```
    Có các giá trị đặc biệt như `Infinity` (vô cực dương), `-Infinity` (vô cực âm), và `NaN` (Not-a-Number - không phải là số, kết quả của các phép toán không hợp lệ, ví dụ: `10 / 'abc'`).
3.  **`boolean` (Logic):** Biểu diễn một trong hai giá trị: `true` (đúng) hoặc `false` (sai). Thường dùng trong các câu lệnh điều kiện.
    ```javascript
    let daDangNhap = true;
    let isGameOver = false;
    ```
4.  **`null`:** Biểu diễn sự "rỗng", "không có giá trị", hoặc "chưa được gán giá trị một cách rõ ràng". Khác với 0 hay chuỗi rỗng.
    ```javascript
    let bienTam = null; // Khai báo và gán null
    ```
5.  **`undefined`:** Biểu diễn biến đã được *khai báo* nhưng *chưa được gán* bất kỳ giá trị nào.
    ```javascript
    let chuaDuocGanGiaTri; // Biến này mặc định có giá trị undefined
    console.log(chuaDuocGanGiaTri); // Output: undefined
    ```
    Lưu ý: Thường thì `undefined` có nghĩa là "hệ thống chưa gán", còn `null` có nghĩa là "lập trình viên chủ động gán là rỗng".
6.  **`symbol` (ES6+):** Dùng để tạo các định danh (identifiers) duy nhất. Ít gặp ở các bài học cơ bản.
    ```javascript
    const id = Symbol('id');
    ```
7.  **`bigint` (ES11+):** Dùng để biểu diễn các số nguyên có giá trị lớn hơn giới hạn của kiểu `number` thông thường.
    ```javascript
    const soRatLon = 1234567890123456789012345678901234567890n; // thêm 'n' ở cuối
    ```

**1 Kiểu Đối Tượng (Object Type):**

1.  **`object` (Đối Tượng):** Kiểu phức tạp hơn. Có thể lưu trữ các tập hợp dữ liệu và các hàm phức tạp hơn. Các ví dụ bao gồm:
    *   **Plain Object:** Dùng cặp `key: value` để lưu trữ thuộc tính.
        ```javascript
        let nguoi = {
            ten: "An",
            tuoi: 20,
            ngheNghiep: "Sinh viên"
        };
        ```
    *   **Array (Mảng):** Danh sách các giá trị được đánh số theo chỉ mục (index), bắt đầu từ 0.
        ```javascript
        let danhSachSo = [1, 2, 3, 4, 5];
        let danhSachTen = ["Alice", "Bob", "Charlie"];
        ```
    *   **Function (Hàm):** Khối code có thể gọi để thực thi lại nhiều lần.
        ```javascript
        function xinChao() {
            console.log("Xin chào các bạn!");
        }
        ```
    *   Và nhiều loại đối tượng tích hợp sẵn khác như `Date`, `RegExp`, `Map`, `Set`, v.v.

### 🔎 Kiểm Tra Kiểu Dữ Liệu (`typeof`)

Bạn có thể dùng toán tử `typeof` để kiểm tra kiểu dữ liệu của một biến hoặc một giá trị.

```javascript
console.log(typeof "hello");      // Output: "string"
console.log(typeof 123);          // Output: "number"
console.log(typeof true);         // Output: "boolean"
console.log(typeof null);         // Output: "object" (Đây là một "sai lầm" lịch sử của JS, nên typeof null trả về object dù nó là primitive type)
console.log(typeof undefined);    // Output: "undefined"
console.log(typeof { a: 1 });     // Output: "object"
console.log(typeof [1, 2]);       // Output: "object" (Mảng cũng là một loại object)
console.log(typeof function(){}); // Output: "function" (Hàm cũng là một loại object)
console.log(typeof Symbol('id')); // Output: "symbol"
console.log(typeof 10n);          // Output: "bigint"
```

### ⚙ Ép Kiểu Dữ Liệu (Type Conversion/Coercion)

JavaScript đôi khi tự động chuyển đổi kiểu dữ liệu khi thực hiện các phép toán (coercion). Tuy nhiên, bạn cũng có thể ép kiểu một cách rõ ràng.

**Chuyển sang String:**
*   `String(value)`
*   `value.toString()` (không dùng được với `null` và `undefined`)

**Chuyển sang Number:**
*   `Number(value)`
*   Toán tử `+` đứng trước giá trị (`+'123'` sẽ ra số `123`)
*   `parseInt(string)`, `parseFloat(string)` (phân tích cú pháp chuỗi để lấy số)

**Chuyển sang Boolean:**
*   `Boolean(value)`
*   Các giá trị được coi là `false` (falsy values): `0`, `""` (chuỗi rỗng), `null`, `undefined`, `NaN`, `false`.
*   Các giá trị khác đều được coi là `true` (truthy values).

**Ví dụ:**

```javascript
let soString = "123";
let soNumber = Number(soString); // soNumber = 123 (number)

let soNguy = parseInt("456px");  // soNguy = 456
let soThuc = parseFloat("7.89"); // soThuc = 7.89

let numberToString = String(12345); // numberToString = "12345" (string)

let stringToBool = Boolean("");     // stringToBool = false
let numberToBool = Boolean(10);    // numberToBool = true
let nullToBool = Boolean(null);     // nullToBool = false

console.log(5 + "5");   // Output: "55" (Số 5 bị ép thành chuỗi "5", phép cộng trở thành nối chuỗi)
console.log(5 - "2");   // Output: 3   (Chuỗi "2" bị ép thành số 2, phép trừ vẫn là phép trừ)
console.log(true + 1);  // Output: 2   (true bị ép thành số 1)
console.log(false + 1); // Output: 1   (false bị ép thành số 0)
```
Sự tự động ép kiểu (coercion) đôi khi có thể gây nhầm lẫn, đó là lý do nên hiểu rõ về nó hoặc ép kiểu một cách rõ ràng khi cần thiết.

### 🛠 Luyện Tập

Hãy thử khai báo vài biến với các kiểu dữ liệu khác nhau (string, number, boolean, null, undefined, object, array). Sử dụng `console.log` và `typeof` để in ra giá trị và kiểu của chúng. Thử các phép ép kiểu đơn giản.

---

## File: 03_toan_tu.md

```markdown
# 🧮 Bài 3: Toán Tử (Operators) trong JavaScript

Chào mừng đến với trung tâm điều khiển logic của chương trình! Toán tử là những ký hiệu đặc biệt dùng để thực hiện các thao tác trên các giá trị hoặc biến (gọi là "operand").

### ➕➖✖️➗ Toán Tử Số Học (Arithmetic Operators)

Dùng để thực hiện các phép tính toán học cơ bản.

*   `+`: Cộng
*   `-`: Trừ
*   `*`: Nhân
*   `/`: Chia
*   `%`: Chia lấy phần dư (Modulo)
*   `**`: Lũy thừa (Exponentiation, ES7+)
*   `++`: Tăng giá trị lên 1 (Increment)
*   `--`: Giảm giá trị đi 1 (Decrement)

**Ví dụ:**

```javascript
let a = 10;
let b = 5;

console.log(a + b); // Output: 15
console.log(a - b); // Output: 5
console.log(a * b); // Output: 50
console.log(a / b); // Output: 2
console.log(a % b); // Output: 0 (10 chia 5 dư 0)
console.log(2 ** 3); // Output: 8 (2 mũ 3)

let counter = 0;
counter++;         // counter = 1 (Increment sau)
console.log(counter); // Output: 1
++counter;         // counter = 2 (Increment trước)
console.log(counter); // Output: 2

let x = 5;
let y = x++;       // y = 5 (giá trị của x trước khi tăng), x = 6
console.log(x, y); // Output: 6 5

let m = 5;
let n = ++m;       // m = 6, n = 6 (giá trị của m sau khi tăng)
console.log(m, n); // Output: 6 6

// Toán tử ++ và -- cũng có dạng prefix (đặt trước biến) và postfix (đặt sau biến), khác nhau ở thứ tự lấy giá trị và tăng/giảm biến.
```

### ✍️ Toán Tử Gán (Assignment Operators)

Dùng để gán giá trị cho biến.

*   `=`: Gán đơn giản (`x = 10`)
*   `+=`: Cộng rồi gán (`x += y` tương đương `x = x + y`)
*   `-=`: Trừ rồi gán (`x -= y` tương đương `x = x - y`)
*   `*=`: Nhân rồi gán (`x *= y` tương đương `x = x * y`)
*   `/=`: Chia rồi gán (`x /= y` tương đương `x = x / y`)
*   `%=`: Modulo rồi gán (`x %= y` tương đương `x = x % y`)
*   `**=`: Lũy thừa rồi gán (`x **= y` tương đương `x = x ** y`)

**Ví dụ:**

```javascript
let count = 5;
count += 3; // count bây giờ là 8
console.log(count); // Output: 8
```

### 비교 Toán Tử So Sánh (Comparison Operators)

Dùng để so sánh hai giá trị và trả về kết quả boolean (`true` hoặc `false`).

*   `==`: Bằng giá trị (có thể bỏ qua kiểu dữ liệu - coercion)
*   `!=`: Không bằng giá trị (có thể bỏ qua kiểu dữ liệu - coercion)
*   `===`: Bằng giá trị và bằng kiểu dữ liệu (Strict equality)
*   `!==`: Không bằng giá trị hoặc không bằng kiểu dữ liệu (Strict non-equality)
*   `>`: Lớn hơn
*   `<`: Nhỏ hơn
*   `>=`: Lớn hơn hoặc bằng
*   `<=`: Nhỏ hơn hoặc bằng

**Ví dụ:**

```javascript
console.log(10 == "10");  // Output: true (10 bị ép thành chuỗi "10" hoặc ngược lại)
console.log(10 === "10"); // Output: false (khác kiểu dữ liệu)

console.log(5 != 5);      // Output: false
console.log(5 != "5");    // Output: false (giống ==)
console.log(5 !== 5);     // Output: false (cùng kiểu, cùng giá trị)
console.log(5 !== "5");   // Output: true (khác kiểu dữ liệu)

console.log(10 > 5);     // Output: true
console.log(10 < 5);     // Output: false
console.log(10 >= 10);   // Output: true
console.log(5 <= 10);    // Output: true
```
**Lưu ý quan trọng:** Luôn ưu tiên dùng `===` và `!==` để tránh các vấn đề không mong muốn do ép kiểu tự động (`==` và `!=`).

### 💡 Toán Tử Logic (Logical Operators)

Kết hợp hoặc đảo ngược các giá trị boolean.

*   `&&` (AND): Trả về `true` nếu cả hai vế đều là `true`.
*   `||` (OR): Trả về `true` nếu một trong hai vế (hoặc cả hai) là `true`.
*   `!` (NOT): Đảo ngược giá trị boolean (`true` thành `false`, `false` thành `true`).

**Ví dụ:**

```javascript
let age = 20;
let isStudent = true;

console.log(age > 18 && isStudent); // Output: true (20 > 18 là true, isStudent là true)
console.log(age < 18 || isStudent); // Output: true (isStudent là true)
console.log(!isStudent);            // Output: false

let isLoggedIn = false;
if (!isLoggedIn) {
    console.log("Vui lòng đăng nhập!");
}
```
Các toán tử `&&` và `||` có tính năng "short-circuiting" (đoản mạch). Nếu kết quả của biểu thức có thể xác định từ vế đầu tiên, vế thứ hai sẽ không được thực thi.

*   Với `&&`: Nếu vế trái là `false`, kết quả là `false` và vế phải bị bỏ qua.
*   Với `||`: Nếu vế trái là `true`, kết quả là `true` và vế phải bị bỏ qua.

Ngoài ra, `&&` và `||` cũng có thể trả về giá trị không phải boolean, tùy thuộc vào giá trị của các vế (tham khảo "Logical AND/OR return the value" trong tài liệu JS).

### ⭐ Toán Tử Ba Ngôi (Ternary Operator)

Cú pháp ngắn gọn cho câu lệnh `if...else` đơn giản.

Cú pháp: `điềuKiện ? giáTrịNếuĐúng : giáTrịNếuSai;`

**Ví dụ:**

```javascript
let canShow = (age >= 18) ? true : false; // Nếu age >= 18 là true thì canShow = true, ngược lại canShow = false

let message = (isLoggedIn) ? "Chào mừng trở lại!" : "Hãy đăng nhập để tiếp tục.";
console.log(message);
```

### 👋 Các Toán Tử Khác

*   `typeof`: Trả về kiểu dữ liệu (như đã học)
*   `instanceof`: Kiểm tra một đối tượng có phải là thể hiện (instance) của một lớp (class) cụ thể không.
*   Toán tử bitwise (thao tác trên bit): `&`, `|`, `^`, `~`, `<<`, `>>`, `>>>`.
*   ... và nhiều toán tử khác nữa!

### 🧩 Thứ Tự Ưu Tiên Của Toán Tử

Khi có nhiều toán tử trong cùng một biểu thức, JavaScript tuân theo một thứ tự ưu tiên nhất định (giống như "Nhân chia trước, cộng trừ sau" trong toán học). Bạn có thể dùng dấu ngoặc đơn `()` để thay đổi thứ tự ưu tiên này.

Ví dụ: `(a + b) * c` sẽ tính `a + b` trước rồi mới nhân với `c`.

### 🛠 Luyện Tập

*   Thử sử dụng các toán tử số học khác nhau.
*   So sánh các giá trị bằng `==`, `!=`, `===`, `!==` và quan sát kết quả.
*   Kết hợp các điều kiện bằng `&&` và `||`.
*   Chuyển một câu lệnh `if/else` đơn giản sang dùng toán tử ba ngôi.

Hiểu rõ các toán tử này giống như việc bạn có đầy đủ dụng cụ trong bộ kit của mình để xây dựng nên logic phức tạp cho chương trình vậy! Tiếp theo, chúng ta sẽ xem cách sử dụng chúng để đưa ra quyết định trong code.

---

## File: 04_cau_lenh_dieu_kien.md

```markdown
# 🚦 Bài 4: Các Câu Lệnh Điều Kiện

Lập trình không chỉ là làm theo từng bước một, mà còn là việc *đưa ra quyết định* dựa trên các tình huống khác nhau. Các câu lệnh điều kiện giúp chúng ta làm điều đó!

### 🤔 Câu Lệnh `if`

Câu lệnh `if` là cấu trúc điều kiện cơ bản nhất. Nó thực thi một khối mã chỉ khi một điều kiện nào đó là `true`.

Cú pháp:

```javascript
if (điều_kiện) {
    // Đoạn mã sẽ được thực thi nếu điều kiện là true
}
```
Trong đó, `điều_kiện` là một biểu thức (thường sử dụng toán tử so sánh hoặc logic) mà kết quả cuối cùng sẽ được ép về kiểu boolean (`true` hoặc `false`).

**Ví dụ:**

```javascript
let nhietDo = 30;

if (nhietDo > 25) {
    console.log("Trời đang nóng!");
}
```

### 👇 Câu Lệnh `if...else`

Để cung cấp một lựa chọn thay thế khi điều kiện trong `if` là `false`, chúng ta dùng `else`.

Cú pháp:

```javascript
if (điều_kiện) {
    // Đoạn mã thực thi nếu điều kiện đúng
} else {
    // Đoạn mã thực thi nếu điều kiện sai
}
```

**Ví dụ:**

```javascript
let tuoi = 17;

if (tuoi >= 18) {
    console.log("Bạn đã đủ tuổi bầu cử.");
} else {
    console.log("Bạn chưa đủ tuổi bầu cử.");
}
```

### 🧱 Câu Lệnh `if...else if...else`

Khi có nhiều hơn hai trường hợp cần xử lý, chúng ta sử dụng cấu trúc `else if`. JavaScript sẽ kiểm tra điều kiện theo thứ tự từ trên xuống. Chỉ khối mã *đầu tiên* có điều kiện là `true` mới được thực thi, và các phần còn lại (bao gồm cả `else` cuối cùng) sẽ bị bỏ qua. Phần `else` cuối cùng là tùy chọn và xử lý trường hợp không có điều kiện nào ở trên là `true`.

Cú pháp:

```javascript
if (điều_kiện_1) {
    // Code nếu điều kiện 1 đúng
} else if (điều_kiện_2) {
    // Code nếu điều kiện 2 đúng
} else if (điều_kiện_3) {
    // Code nếu điều kiện 3 đúng
} else {
    // Code nếu không có điều kiện nào ở trên đúng (tùy chọn)
}
```

**Ví dụ:**

```javascript
let diem = 85;

if (diem >= 90) {
    console.log("Điểm A - Xuất sắc!");
} else if (diem >= 80) {
    console.log("Điểm B - Giỏi.");
} else if (diem >= 70) {
    console.log("Điểm C - Khá.");
} else {
    console.log("Cần cố gắng thêm.");
}
```

### 📁 Câu Lệnh `switch`

Khi bạn có nhiều trường hợp cần kiểm tra giá trị CỦA CÙNG MỘT BIẾN, câu lệnh `switch` có thể là lựa chọn gọn gàng hơn so với chuỗi `if...else if...`.

Cú pháp:

```javascript
switch (biến_cần_kiểm_tra) {
    case gia_tri_1:
        // Code thực thi nếu biến_cần_kiểm_tra == gia_tri_1 (dùng === - strict equality)
        break; // Quan trọng: dùng break để thoát khỏi switch sau khi thực thi
    case gia_tri_2:
        // Code thực thi nếu biến_cần_kiểm_tra == gia_tri_2
        break;
    case gia_tri_3:
        // Code thực thi nếu biến_cần_kiểm_tra == gia_tri_3
        break;
    // ... thêm các case khác
    default: // Tùy chọn: code thực thi nếu biến không khớp với case nào
        // Code cho trường hợp mặc định
}
```

*   `break;`: Rất quan trọng! Nếu bỏ qua `break`, JavaScript sẽ tiếp tục thực thi code ở các `case` tiếp theo (hiện tượng "fall-through") cho đến khi gặp `break` hoặc kết thúc khối `switch`.
*   `default:`: Xử lý trường hợp không có `case` nào khớp. Nó là tùy chọn.

**Ví dụ:**

```javascript
let ngayTrongTuan = "Thứ Hai";

switch (ngayTrongTuan) {
    case "Thứ Hai":
        console.log("Bắt đầu tuần mới đầy năng lượng!");
        break;
    case "Thứ Sáu":
        console.log("Sắp cuối tuần rồi!");
        break;
    case "Thứ Bảy":
    case "Chủ Nhật": // Có thể gộp nhiều case nếu cùng xử lý một khối lệnh
        console.log("Cuối tuần, thư giãn nào!");
        break;
    default:
        console.log("Một ngày bình thường trong tuần.");
}
```

### ✨ Toán Tử Ba Ngôi (Đã giới thiệu ở bài Toán Tử, nhắc lại ở đây vì tính liên quan)

Nhắc lại một chút về toán tử ba ngôi (ternary operator): Đây là cách viết ngắn gọn cho câu lệnh `if...else` đơn giản trả về một giá trị.

Cú pháp: `điềuKiện ? giáTrịNếuĐúng : giáTrịNếuSai;`

**Ví dụ:**
```javascript
let status = (isLoggedIn) ? "Online" : "Offline";
```

### 🛠 Luyện Tập

*   Viết một câu lệnh `if` kiểm tra xem một số có dương không.
*   Mở rộng nó thành `if...else` để in ra "Số dương" hoặc "Số âm/bằng không".
*   Viết một cấu trúc `if...else if...else` để phân loại điểm số (A, B, C, D, F).
*   Viết một câu lệnh `switch` để in ra tên của tháng dựa trên số tháng (1-12).
*   Sử dụng toán tử ba ngôi để xác định tin nhắn hiển thị dựa trên trạng thái (ví dụ: đã đăng nhập/chưa đăng nhập).

Thành thạo các cấu trúc điều kiện này là bạn đã nắm trong tay bộ não điều khiển luồng chạy của chương trình rồi đấy! Giống như bạn đang lập trình các module tự hành cho phi thuyền của mình vậy! 💪

---

## File: 05_vong_lap.md

```markdown
# 🔄 Bài 5: Vòng Lặp (Loops)

Đôi khi, chúng ta cần lặp đi lặp lại một khối lệnh nhiều lần. Thay vì viết đi viết lại đoạn code đó, chúng ta sử dụng **vòng lặp**. Vòng lặp là những cỗ máy lặp tự động mạnh mẽ trong lập trình!

JavaScript cung cấp một số loại vòng lặp khác nhau:

### 🌀 Vòng Lặp `for`

Vòng lặp `for` là vòng lặp phổ biến nhất khi bạn biết trước số lần lặp (hoặc dễ dàng tính toán được).

Cú pháp:

```javascript
for (khởi_tạo; điều_kiện_tiếp_tục; cập_nhật) {
    // Đoạn mã sẽ được thực thi trong mỗi lần lặp
}
```
*   `khởi_tạo`: Thực thi *một lần duy nhất* ở đầu vòng lặp, thường dùng để khởi tạo biến đếm.
*   `điều_kiện_tiếp_tục`: Kiểm tra *trước mỗi lần lặp*. Nếu `true`, vòng lặp tiếp tục. Nếu `false`, vòng lặp dừng lại.
*   `cập_nhật`: Thực thi *sau mỗi lần lặp*, thường dùng để cập nhật biến đếm.

**Ví dụ:**

```javascript
// In ra các số từ 0 đến 4
for (let i = 0; i < 5; i++) {
    console.log("Lần lặp thứ " + i);
}

// In ra các số chẵn từ 2 đến 10
for (let j = 2; j <= 10; j += 2) {
    console.log(j);
}
```

### ✨ Vòng Lặp `while`

Vòng lặp `while` thực thi một khối lệnh *miễn là* điều kiện vẫn còn là `true`. Bạn dùng `while` khi không biết trước số lần lặp chính xác, mà chỉ biết khi nào thì vòng lặp dừng lại.

Cú pháp:

```javascript
while (điều_kiện_tiếp_tục) {
    // Đoạn mã sẽ được thực thi miễn là điều kiện là true
    // Đảm bảo có một bước cập nhật bên trong để điều kiện cuối cùng trở thành false
}
```
**Quan trọng:** Bạn phải *tự tay* thay đổi các biến trong điều kiện để điều kiện cuối cùng trở thành `false`, nếu không vòng lặp sẽ chạy mãi mãi (vòng lặp vô hạn - infinite loop), khiến trình duyệt hoặc chương trình bị treo!

**Ví dụ:**

```javascript
let count = 0;

while (count < 5) {
    console.log("Count là: " + count);
    count++; // Bước cập nhật để thoát vòng lặp
}
```

### 👇 Vòng Lặp `do...while`

Tương tự `while`, nhưng vòng lặp `do...while` *luôn* thực thi khối mã ít nhất *một lần*, trước khi kiểm tra điều kiện.

Cú pháp:

```javascript
do {
    // Đoạn mã thực thi ít nhất một lần
    // Đảm bảo có bước cập nhật
} while (điều_kiện_tiếp_tục); // Điều kiện được kiểm tra sau lần lặp đầu tiên
```

**Ví dụ:**

```javascript
let input;
let userInput = "";

do {
    input = prompt("Nhập 'thoat' để dừng:"); // Lệnh prompt hiển thị hộp thoại yêu cầu người dùng nhập liệu trong trình duyệt
    userInput += input + "\n";
} while (input !== "thoat");

console.log("Bạn đã nhập:\n" + userInput);
```
Trong ví dụ này, dù người dùng nhập "thoat" ngay lần đầu tiên, khối code bên trong `do` vẫn chạy *một lần* để hiển thị hộp thoại prompt.

### 🎯 Lệnh `break` và `continue`

*   **`break;`**: Thoát *ngay lập tức* khỏi vòng lặp gần nhất chứa nó.
*   **`continue;`**: Bỏ qua phần còn lại của *lần lặp hiện tại* và nhảy sang lần lặp tiếp theo.

**Ví dụ `break`:**

```javascript
for (let i = 0; i < 10; i++) {
    if (i === 5) {
        console.log("Tìm thấy số 5, dừng vòng lặp.");
        break; // Dừng ngay khi i bằng 5
    }
    console.log(i);
}
// Output: 0, 1, 2, 3, 4, "Tìm thấy số 5, dừng vòng lặp."
```

**Ví dụ `continue`:**

```javascript
for (let i = 0; i < 10; i++) {
    if (i % 2 === 0) { // Nếu i là số chẵn
        console.log("Bỏ qua số chẵn: " + i);
        continue; // Bỏ qua phần còn lại của lần lặp này, nhảy sang i tiếp theo
    }
    console.log("Số lẻ: " + i);
}
// Output: "Bỏ qua số chẵn: 0", "Số lẻ: 1", "Bỏ qua số chẵn: 2", "Số lẻ: 3", ...
```

### ✨ Vòng Lặp Cho Mảng và Đối Tượng (sẽ đi sâu hơn khi học Mảng và Đối Tượng)

JavaScript có các vòng lặp đặc biệt hữu ích cho việc duyệt qua các phần tử của Mảng và các thuộc tính của Đối tượng:

*   **`for...of` (ES6+):** Duyệt qua các phần tử (giá trị) của các đối tượng lặp (Iterable objects) như Mảng, Chuỗi, Map, Set...
    ```javascript
    const colors = ["red", "green", "blue"];
    for (const color of colors) {
        console.log(color); // red, green, blue
    }
    ```
*   **`for...in`:** Duyệt qua các khóa (keys/property names) của các đối tượng. CẨN THẬN khi dùng với Mảng vì nó duyệt qua cả các thuộc tính khác (như phương thức, protoype) chứ không chỉ index số, và thứ tự duyệt có thể không đảm bảo. Thường dùng cho đối tượng thường (plain objects).
    ```javascript
    const user = { name: "Anna", age: 28 };
    for (const key in user) {
        console.log(key + ": " + user[key]); // name: Anna, age: 28
    }
    ```
*   **Các Phương Thức Duyệt Mảng:** Các phương thức tích hợp của Array như `forEach()`, `map()`, `filter()`, `reduce()`... Đây là những cách *hiện đại và functional* hơn để lặp và thao tác với mảng. Sẽ học kỹ hơn ở bài về Mảng.

### 🛠 Luyện Tập

*   Sử dụng vòng lặp `for` để tính tổng các số từ 1 đến 100.
*   Sử dụng vòng lặp `while` để đếm ngược từ 10 về 0.
*   Sử dụng vòng lặp `do...while` để yêu cầu người dùng nhập mật khẩu cho đến khi nhập đúng (với một mật khẩu "giả" nào đó).
*   Kết hợp `break` hoặc `continue` trong các vòng lặp trên.
*   (Thử) Dùng `for...of` để in từng ký tự của một chuỗi.

Nắm vững vòng lặp giống như bạn đã lắp thêm hệ thống đẩy và định vị vào phi thuyền của mình vậy! Nó cho phép bạn thực hiện các tác vụ lặp đi lặp lại một cách tự động và hiệu quả.

---

## File: 06_ham.md

```markdown
# 🧱 Bài 6: Hàm (Functions)

Trong lập trình, chúng ta thường có những khối mã thực hiện một công việc cụ thể, lặp đi lặp lại hoặc có thể cần tái sử dụng ở nhiều nơi khác nhau. **Hàm** là công cụ cho phép chúng ta đóng gói những khối mã này lại, đặt tên cho chúng và gọi chúng để thực thi khi cần. Điều này giúp code của bạn ngăn nắp, dễ đọc, dễ bảo trì và tránh lặp lại chính mình (Nguyên tắc DRY - Don't Repeat Yourself).

Hãy nghĩ hàm như những "robot" chuyên dụng của bạn, mỗi robot làm một việc riêng biệt!

### 🤖 Khai Báo Hàm (Function Declaration)

Đây là cách khai báo hàm truyền thống.

Cú pháp:

```javascript
function tenHam(tham_số_1, tham_số_2, ...) {
    // Khối mã của hàm
    // Có thể thực hiện các lệnh
    // Có thể trả về một giá trị
    return gia_tri; // Tùy chọn
}
```

*   `function`: Từ khóa để khai báo hàm.
*   `tenHam`: Tên của hàm (tuân theo quy tắc đặt tên biến).
*   `(tham_số_1, tham_số_2, ...)`: Danh sách các tham số mà hàm nhận vào (đặt trong ngoặc đơn, cách nhau bởi dấu phẩy). Tham số là tùy chọn.
*   `{ ... }`: Khối mã (body) của hàm.
*   `return`: Từ khóa dùng để trả về một giá trị từ hàm. Nếu không có `return` (hoặc `return;`), hàm sẽ trả về `undefined` mặc định.

**Ví dụ:**

```javascript
function chaoTheGioi() {
    console.log("Xin chào, thế giới!");
}

function tinhTong(a, b) {
    return a + b; // Hàm trả về tổng của a và b
}

// Gọi hàm để thực thi
chaoTheGioi(); // Output: Xin chào, thế giới!

let ketQua = tinhTong(5, 7);
console.log("Tổng là: " + ketQua); // Output: Tổng là: 12
console.log("Tổng khác: " + tinhTong(10, 20)); // Output: Tổng khác: 30
```

### 🚀 Biểu Thức Hàm (Function Expression)

Một hàm cũng có thể được gán cho một biến, giống như bất kỳ giá trị nào khác.

Cú pháp:

```javascript
let tenBienChuaHam = function(tham_số_1, ...) {
    // Khối mã
}; // Chú ý dấu chấm phẩy ở cuối
```

**Ví dụ:**

```javascript
let sayHello = function() {
    console.log("Hi!");
};

sayHello(); // Output: Hi!

let multiply = function(x, y) {
    return x * y;
};

console.log("Kết quả nhân: " + multiply(3, 4)); // Output: Kết quả nhân: 12
```
Sự khác biệt chính giữa khai báo hàm và biểu thức hàm liên quan đến Hoisting (sẽ nói kỹ hơn sau): Khai báo hàm có thể được gọi *trước* khi nó được định nghĩa trong code, còn biểu thức hàm thì không.

### 🏹 Hàm Mũ Tên (Arrow Functions - ES6+)

Cú pháp ngắn gọn và hiện đại để viết hàm, đặc biệt hữu ích cho các hàm đơn giản.

Cú pháp cơ bản:

```javascript
let tenHam = (tham_số_1, ...) => {
    // Khối mã
    return gia_tri;
};
```

*   Nếu chỉ có MỘT tham số, có thể bỏ qua dấu ngoặc đơn `()` ở tham số.
    `let gapDoi = so => { return so * 2; };`
*   Nếu hàm CHỈ có một dòng lệnh `return` biểu thức, có thể bỏ qua `{}`, `return`, và dấu chấm phẩy.
    `let gapDoi = so => so * 2;` // Rất ngắn gọn!
*   Nếu không có tham số nào, cần cặp ngoặc đơn rỗng `()`.
    `let sayGoodbye = () => console.log("Goodbye!");`

**Ví dụ:**

```javascript
let chia = (a, b) => {
    if (b === 0) {
        return "Không thể chia cho 0";
    }
    return a / b;
};

let binhPhuong = so => so * so; // Cú pháp ngắn gọn

console.log(chia(10, 2));     // Output: 5
console.log(chia(10, 0));     // Output: Không thể chia cho 0
console.log(binhPhuong(5));   // Output: 25
```
Hàm mũi tên có một số khác biệt quan trọng so với hàm truyền thống về cách xử lý `this` (sẽ tìm hiểu ở bài nâng cao), khiến chúng rất phù hợp cho các hàm callback.

### 🔄 Tham Số Mặc Định (Default Parameters - ES6+)

Bạn có thể gán một giá trị mặc định cho tham số. Nếu khi gọi hàm, bạn không truyền giá trị cho tham số đó, giá trị mặc định sẽ được sử dụng.

**Ví dụ:**

```javascript
function chao(ten = "bạn ẩn danh") { // Gán giá trị mặc định "bạn ẩn danh" cho tham số ten
    console.log("Xin chào, " + ten + "!");
}

chao("Quân"); // Output: Xin chào, Quân!
chao();      // Output: Xin chào, bạn ẩn danh! (Không truyền tham số nào)
```

### 📚 Scope (Phạm Vi) của Biến trong Hàm

Các biến được khai báo *bên trong* một hàm (sử dụng `let` hoặc `const`) chỉ tồn tại và có thể truy cập được *trong phạm vi* của hàm đó. Chúng được gọi là biến **local (cục bộ)**. Các biến được khai báo *bên ngoài* bất kỳ hàm nào là biến **global (toàn cục)** và có thể truy cập được ở mọi nơi.

**Ví dụ:**

```javascript
let bienGlobal = "Tôi là toàn cục"; // Biến Global

function hamViDu() {
    let bienLocal = "Tôi chỉ là cục bộ"; // Biến Local
    console.log(bienGlobal); // Có thể truy cập biến Global
    console.log(bienLocal);  // Có thể truy cập biến Local
}

hamViDu();

console.log(bienGlobal); // Có thể truy cập biến Global
// console.log(bienLocal); // Sẽ gây lỗi: ReferenceError, bienLocal không tồn tại ở ngoài hàm
```
Hiểu về phạm vi (scope) rất quan trọng để tránh nhầm lẫn giữa các biến và giữ cho code của bạn ngăn nắp, an toàn.

### ⚙️ Khi Nào Sử Dụng Hàm?

*   Khi có một khối mã thực hiện một công việc cụ thể.
*   Khi bạn cần thực hiện công việc đó nhiều lần.
*   Khi bạn muốn làm cho code của mình dễ đọc hơn bằng cách chia nhỏ nó thành các phần logic có tên rõ ràng.
*   Khi bạn muốn tránh việc lặp lại code.

### 🛠 Luyện Tập

*   Viết một hàm khai báo (function declaration) nhận vào hai số và trả về số lớn hơn.
*   Viết một biểu thức hàm (function expression) nhận vào một chuỗi và trả về chuỗi viết hoa tất cả các ký tự.
*   Chuyển đổi hàm vừa rồi thành hàm mũi tên (arrow function) với cú pháp ngắn gọn nhất có thể.
*   Viết một hàm với tham số mặc định. Gọi hàm với và không có tham số đó.
*   Quan sát sự khác biệt về scope bằng cách khai báo biến trong và ngoài hàm, rồi thử truy cập chúng.

Hàm là một trong những viên gạch cấu tạo cốt lõi của bất kỳ chương trình nào. Nắm vững hàm là bạn đã có thể bắt đầu xây dựng những "tòa nhà" phức tạp hơn từ những khối "robot" chuyên dụng này rồi!

---

## File: 07_mang_array.md

```markdown
# 🧱 Bài 7: Mảng (Arrays)

Trong cuộc sống, chúng ta thường làm việc với danh sách: danh sách mua sắm, danh sách sinh viên, danh sách các hành tinh,... Trong lập trình, khi muốn lưu trữ một **tập hợp các giá trị** (có thể cùng kiểu hoặc khác kiểu, dù thường là cùng kiểu), chúng ta sử dụng **Mảng (Array)**.

Mảng trong JavaScript giống như một "tủ kéo" kỹ thuật số, mỗi ngăn kéo được đánh số, và bạn có thể bỏ bất cứ thứ gì vào đó.

### 🛠 Khai Báo Mảng

Có hai cách phổ biến để tạo mảng:

1.  **Dùng Literal Mảng (Array Literal - phổ biến nhất):**
    ```javascript
    let danhSachRong = []; // Mảng rỗng
    let cacLoaiQua = ["Táo", "Chuối", "Cam"]; // Mảng với các phần tử ban đầu (kiểu string)
    let cacLoaiSo = [1, 2, 3, 4, 5]; // Mảng với các phần tử kiểu number
    let honTap = [1, "Hai", true, { ten: "Đối tượng" }]; // Mảng có thể chứa các kiểu dữ liệu khác nhau
    ```

2.  **Dùng Constructor `Array()`:**
    ```javascript
    let arr1 = new Array(); // Mảng rỗng
    let arr2 = new Array(3); // Mảng rỗng với dung lượng ban đầu là 3 (có 3 vị trí empty)
    let arr3 = new Array("A", "B", "C"); // Mảng với các phần tử ban đầu
    ```
    Cách dùng literal mảng thường được ưu tiên vì ngắn gọn và dễ đọc hơn.

### 📦 Truy Cập và Sửa Đổi Phần Tử Mảng

Các phần tử trong mảng được đánh số thứ tự (gọi là **chỉ mục - index**), BẮT ĐẦU TỪ **0**.

*   **Truy cập:** Sử dụng ngoặc vuông `[]` và chỉ mục.
    ```javascript
    let colors = ["Red", "Green", "Blue"];
    console.log(colors[0]); // Output: Red (Phần tử ở chỉ mục 0)
    console.log(colors[1]); // Output: Green
    console.log(colors[2]); // Output: Blue
    ```
*   **Sửa đổi:** Sử dụng chỉ mục và toán tử gán `=`.
    ```javascript
    let numbers = [10, 20, 30];
    numbers[1] = 25; // Sửa phần tử ở chỉ mục 1
    console.log(numbers); // Output: [10, 25, 30]
    ```
*   Nếu truy cập một chỉ mục *không tồn tại*, kết quả sẽ là `undefined`.
    ```javascript
    let simpleArray = [1, 2];
    console.log(simpleArray[10]); // Output: undefined
    ```
*   Bạn có thể thêm phần tử mới bằng cách gán giá trị cho một chỉ mục lớn hơn chỉ mục cuối cùng. Các chỉ mục ở giữa chưa được gán sẽ là `empty`.
    ```javascript
    let anotherArray = ["A", "B"];
    anotherArray[4] = "E";
    console.log(anotherArray); // Output: ["A", "B", empty, empty, "E"]
    console.log(anotherArray.length); // Output: 5
    ```

### 📏 Độ Dài Mảng (`length`)

Thuộc tính `length` trả về số lượng phần tử trong mảng.

```javascript
let danhSachSinhVien = ["An", "Bình", "Cường"];
console.log(danhSachSinhVien.length); // Output: 3

// Lưu ý: Thay đổi thuộc tính length có thể cắt ngắn hoặc kéo dài mảng
danhSachSinhVien.length = 1; // Cắt ngắn mảng
console.log(danhSachSinhVien); // Output: ["An"]
```

### 🚀 Các Phương Thức Mảng Quan Trọng (Array Methods)

Mảng có rất nhiều phương thức tích hợp sẵn để thực hiện các thao tác phổ biến một cách hiệu quả.

*   **Thêm/Xóa phần tử ở CUỐI mảng:**
    *   `push(phanTu1, phanTu2, ...)`: Thêm các phần tử vào cuối mảng. Trả về độ dài mới của mảng.
    *   `pop()`: Xóa phần tử cuối cùng của mảng. Trả về phần tử bị xóa.
    ```javascript
    let fruits = ["Apple", "Banana"];
    fruits.push("Orange"); // fruits bây giờ là ["Apple", "Banana", "Orange"]
    let lastFruit = fruits.pop(); // lastFruit là "Orange", fruits là ["Apple", "Banana"]
    ```

*   **Thêm/Xóa phần tử ở ĐẦU mảng:** (Ít dùng hơn `push/pop` vì có thể chậm hơn với mảng lớn do phải dịch chuyển các phần tử còn lại)
    *   `unshift(phanTu1, phanTu2, ...)`: Thêm các phần tử vào đầu mảng. Trả về độ dài mới.
    *   `shift()`: Xóa phần tử đầu tiên của mảng. Trả về phần tử bị xóa.
    ```javascript
    let animals = ["Tiger", "Lion"];
    animals.unshift("Elephant"); // animals bây giờ là ["Elephant", "Tiger", "Lion"]
    let firstAnimal = animals.shift(); // firstAnimal là "Elephant", animals là ["Tiger", "Lion"]
    ```

*   **Xóa/Thay thế/Thêm phần tử tại BẤT KỲ VỊ TRÍ NÀO:**
    *   `splice(indexBắtĐầu, sốLượngPhầnTửMuốnXóa, phanTu1MuốnThem, phanTu2MuốnThem, ...)`
        *   `indexBắtĐầu`: Vị trí (chỉ mục) bắt đầu thực hiện thao tác.
        *   `sốLượngPhầnTửMuốnXóa`: Số lượng phần tử muốn xóa kể từ `indexBắtĐầu`. Nếu là 0, sẽ không xóa phần tử nào.
        *   `phanTu...MuốnThem`: Các phần tử tùy chọn muốn thêm vào bắt đầu từ `indexBắtĐầu`.
    *   `splice` trả về một mảng chứa các phần tử đã bị xóa (nếu có).
    ```javascript
    let arr = [1, 2, 3, 4, 5];
    let deletedItems1 = arr.splice(1, 2); // Xóa 2 phần tử từ chỉ mục 1: [2, 3]
    // arr bây giờ là [1, 4, 5]
    console.log(arr, deletedItems1); // Output: [1, 4, 5] [2, 3]

    let arr2 = [1, 2, 3];
    let deletedItems2 = arr2.splice(1, 0, "a", "b"); // Từ chỉ mục 1, xóa 0 phần tử, thêm "a", "b"
    // arr2 bây giờ là [1, "a", "b", 2, 3]
    console.log(arr2, deletedItems2); // Output: [1, "a", "b", 2, 3] [] (Không có phần tử nào bị xóa)
    ```

*   **Tạo một bản sao MỚI của mảng hoặc một phần của mảng:**
    *   `slice(indexBắtĐầu, indexKếtThúc)`
        *   `indexBắtĐầu`: Chỉ mục BẮT ĐẦU (bao gồm).
        *   `indexKếtThúc`: Chỉ mục KẾT THÚC (KHÔNG bao gồm).
        *   Nếu bỏ qua cả hai tham số, nó tạo bản sao của toàn bộ mảng.
    *   `slice` KHÔNG thay đổi mảng gốc.
    ```javascript
    let originalArray = [1, 2, 3, 4, 5];
    let saoChep = originalArray.slice();    // Sao chép toàn bộ: [1, 2, 3, 4, 5]
    let phanCon = originalArray.slice(1, 3); // Lấy từ chỉ mục 1 đến trước chỉ mục 3: [2, 3]
    let denCuoi = originalArray.slice(2);   // Lấy từ chỉ mục 2 đến cuối: [3, 4, 5]

    console.log(saoChep, phanCon, denCuoi);
    console.log(originalArray); // Mảng gốc không thay đổi
    ```

*   **Tìm kiếm phần tử:**
    *   `indexOf(phanTu, startIndex)`: Trả về chỉ mục ĐẦU TIÊN của `phanTu`, tìm kiếm từ `startIndex`. Trả về `-1` nếu không tìm thấy.
    *   `lastIndexOf(phanTu, startIndex)`: Trả về chỉ mục CUỐI CÙNG.
    *   `includes(phanTu, startIndex)` (ES7+): Trả về `true` nếu mảng chứa `phanTu`, `false` nếu không.

*   **Duyệt (lặp qua) Mảng:**
    *   Dùng vòng lặp `for` truyền thống (`for (let i = 0; i < array.length; i++)`).
    *   Dùng vòng lặp `for...of` (duyệt qua giá trị).
    *   Dùng phương thức `forEach()`: Thực thi một hàm (callback) cho MỖI phần tử của mảng.
        ```javascript
        let numbers = [10, 20, 30];
        numbers.forEach(function(item, index, array) {
            console.log(`Phần tử ${item} ở chỉ mục ${index} trong mảng ${array}`);
        });
        // Cũng có thể dùng arrow function
        numbers.forEach((item, index) => {
             console.log(`Item: ${item}, Index: ${index}`);
        });
        ```
    `forEach` không dừng được bằng `break`, muốn dừng giữa chừng phải dùng vòng lặp `for`, `while` hoặc các phương thức khác như `some()`, `every()`.

### 📌 Lưu Ý: Mảng là Đối Tượng (Object)

Mảng trong JavaScript thực chất là một kiểu đặc biệt của đối tượng. Chỉ mục số (index) được coi như là các "khóa" (keys) ở dạng chuỗi, và thuộc tính `length` được cập nhật tự động khi bạn thêm/xóa phần tử bằng các phương thức như `push`, `pop`, `shift`, `unshift`, `splice` hoặc gán trực tiếp qua index *tăng dần* như `arr[arr.length] = newValue;`.

Tuy nhiên, chúng ta thường xem mảng như một cấu trúc dữ liệu riêng vì cách thao tác và các phương thức chuyên dụng của nó.

### 🛠 Luyện Tập

*   Tạo một mảng chứa tên của 5 cuốn sách yêu thích của bạn.
*   In ra tên cuốn sách đầu tiên và cuối cùng trong mảng.
*   Thêm một cuốn sách mới vào cuối mảng.
*   Xóa cuốn sách đầu tiên.
*   Sử dụng `splice` để chèn thêm 2 cuốn sách vào giữa mảng.
*   Sử dụng `slice` để tạo một mảng mới chỉ chứa 3 cuốn sách ở giữa của mảng ban đầu.
*   Dùng vòng lặp `for`, `for...of` và phương thức `forEach` để in ra tất cả tên sách trong mảng.

Mảng là một cấu trúc dữ liệu vô cùng quan trọng và tiện lợi. Nó là nền tảng để xử lý các bộ sưu tập dữ liệu. Hãy dành thời gian thực hành các phương thức mảng, chúng sẽ là những trợ thủ đắc lực cho bạn!

---

## File: 08_doi_tuong_objects.md

```markdown
# 🪐 Bài 8: Đối Tượng (Objects)

Ngoài các kiểu dữ liệu nguyên thủy như chuỗi, số, boolean,... chúng ta còn có kiểu **Object**. Object trong JavaScript giống như các "vật thể" trong thế giới thực, chúng có các **thuộc tính (properties)** (ví dụ: màu sắc, kích thước, tên) và có thể có **hành động (methods)** (ví dụ: chạy, nói, tính toán).

Object là cách để nhóm dữ liệu và chức năng liên quan lại với nhau thành một đơn vị duy nhất.

Hãy nghĩ Object như những "bản thiết kế" hoặc "các thực thể" mà bạn xây dựng trong thế giới kỹ thuật số của mình.

### 🛠 Khai Báo Đối Tượng

Cách phổ biến nhất và dễ nhất là dùng **Object Literal**:

```javascript
// Khai báo một đối tượng RỖNG
let nguoi = {};

// Khai báo một đối tượng với các thuộc tính ban đầu
let nguoiMay = {
    // key: value (cặp khóa-giá trị)
    ten: "Model XYZ",
    mauSac: "Bạc",
    namSanXuat: 2050,
    dangHoatDong: true
};
```
Trong `Object Literal`, bạn định nghĩa các thuộc tính dưới dạng các cặp `key: value` (khóa và giá trị) cách nhau bằng dấu phẩy. Key (khóa) thường là chuỗi (bạn có thể bỏ dấu ngoặc kép nếu tên khóa hợp lệ như tên biến), và value (giá trị) có thể là bất kỳ kiểu dữ liệu nào (bao gồm cả các object khác hoặc hàm).

### 📦 Truy Cập và Sửa Đổi Thuộc Tính

Có hai cách chính để truy cập và sửa đổi thuộc tính của object:

1.  **Dùng Dấu Chấm (`.` - Dot Notation):** Phổ biến khi bạn biết tên thuộc tính (khóa).
    ```javascript
    console.log(nguoiMay.ten);       // Output: Model XYZ
    console.log(nguoiMay.namSanXuat); // Output: 2050

    nguoiMay.mauSac = "Vàng";      // Sửa giá trị thuộc tính
    console.log(nguoiMay.mauSac);   // Output: Vàng

    nguoiMay.canNang = 150;         // Thêm thuộc tính mới
    console.log(nguoiMay.canNang);  // Output: 150
    ```

2.  **Dùng Ngoặc Vuông (`[]` - Bracket Notation):** Hữu ích khi tên thuộc tính phức tạp (có dấu cách, ký tự đặc biệt) hoặc khi tên thuộc tính được lưu trong một biến.
    ```javascript
    let sach = {
        tieuDe: "Hành trình giữa các vì sao",
        "tac gia": "Arthur C. Clarke", // Tên thuộc tính có dấu cách
        namXuatBan: 1968
    };

    console.log(sach["tieuDe"]);     // Output: Hành trình giữa các vì sao
    console.log(sach["tac gia"]);    // Output: Arthur C. Clarke (BẮT BUỘC phải dùng ngoặc vuông)

    let keyTacGia = "tac gia";
    console.log(sach[keyTacGia]);    // Output: Arthur C. Clarke (Truy cập tên thuộc tính lưu trong biến)

    sach["namXuatBan"] = 2001;        // Sửa thuộc tính
    console.log(sach.namXuatBan);     // Output: 2001

    sach["ngon ngu"] = "Tiếng Anh"; // Thêm thuộc tính
    console.log(sach["ngon ngu"]);  // Output: Tiếng Anh
    ```

### ✨ Thêm Phương Thức (Methods) cho Đối Tượng

Nếu giá trị của một thuộc tính là một **hàm**, thuộc tính đó được gọi là **phương thức** của đối tượng. Phương thức biểu diễn "hành động" mà đối tượng có thể thực hiện.

**Ví dụ:**

```javascript
let mayTinh = {
    // Thuộc tính
    nhanHieu: "Cosmic Corp",
    loaiCPU: "Quantium-X",
    gia: 2500,

    // Phương thức
    bat: function() { // Dùng Function Expression
        console.log(this.nhanHieu + " đang khởi động...");
    },
    tat: function() {
        console.log(this.nhanHieu + " đang tắt.");
    },
    tinhGiaSauKhuyenMai: function(tyLe) { // Hàm nhận tham số
        return this.gia * (1 - tyLe);
    },
    baoCao: () => { // CẨN THẬN khi dùng Arrow function làm method
        // 'this' trong arrow function KHÔNG trỏ đến object mayTinh mà trỏ ra ngoài (global object)
        //console.log("Thông tin: " + this.nhanHieu); // --> Sẽ in ra 'undefined' hoặc thông tin global
        console.log("Máy đang hoạt động.");
    }
};

// Gọi phương thức
mayTinh.bat();                      // Output: Cosmic Corp đang khởi động...
mayTinh["tat"]();                   // Cũng gọi được bằng ngoặc vuông
let giaSauKM = mayTinh.tinhGiaSauKhuyenMai(0.1); // Tính giá giảm 10%
console.log("Giá sau khuyến mãi: $" + giaSauKM); // Output: Giá sau khuyến mãi: $2250

mayTinh.baoCao(); // Output: Máy đang hoạt động. (Lưu ý: ví dụ này tránh dùng 'this')
```

*   **Từ khóa `this`:** Trong một phương thức (được định nghĩa bằng `function`), từ khóa `this` trỏ đến chính đối tượng chứa phương thức đó. Điều này cho phép bạn truy cập các thuộc tính khác của đối tượng bên trong phương thức. **Như đã đề cập, `this` trong arrow function hoạt động khác.**

### 🗑 Xóa Thuộc Tính

Dùng toán tử `delete` để xóa một thuộc tính của object.

```javascript
let sinhVien = { ten: "Linh", tuoi: 19, nganh: "Khoa học máy tính" };
console.log(sinhVien);       // Output: { ten: 'Linh', tuoi: 19, nganh: 'Khoa học máy tính' }

delete sinhVien.tuoi;        // Xóa thuộc tính tuoi
delete sinhVien["nganh"];    // Xóa thuộc tính nganh dùng ngoặc vuông

console.log(sinhVien);       // Output: { ten: 'Linh' }
```

### 🔍 Kiểm Tra Sự Tồn Tại Của Thuộc Tính

*   **Toán tử `in`:**
    ```javascript
    console.log("ten" in sinhVien);    // Output: true
    console.log("tuoi" in sinhVien);   // Output: false (đã bị xóa)
    ```
*   **So sánh với `undefined`:**
    ```javascript
    console.log(sinhVien.nganh === undefined); // Output: true (sau khi bị xóa)
    ```
    Lưu ý: Cách so sánh với `undefined` không phân biệt được thuộc tính không tồn tại và thuộc tính tồn tại nhưng có giá trị là `undefined`. Toán tử `in` đáng tin cậy hơn trong việc kiểm tra *sự tồn tại* thực sự của thuộc tính.

### ♻️ Duyệt (lặp qua) Đối Tượng

Dùng vòng lặp `for...in` để lặp qua các khóa (tên thuộc tính) của object.

```javascript
let robot = { model: "RT1", chucNang: ["Đi", "Nói"], daKhoiDong: true };

for (let key in robot) {
    // 'key' sẽ là "model", "chucNang", "daKhoiDong"
    console.log(key + ": " + robot[key]);
}
/*
Output:
model: RT1
chucNang: Đi,Nói (Khi in mảng, nó được chuyển thành chuỗi)
daKhoiDong: true
*/
```
Lưu ý về `for...in` đã nhắc ở bài vòng lặp: nó cũng duyệt qua các thuộc tính "thừa kế" từ prototype. Để tránh điều này và chỉ duyệt qua các thuộc tính "trực tiếp" của đối tượng, bạn có thể thêm điều kiện kiểm tra:

```javascript
for (let key in robot) {
    if (robot.hasOwnProperty(key)) { // Kiểm tra xem thuộc tính có phải của riêng object đó không
         console.log(key + ": " + robot[key]);
    }
}
```
*   **Các Phương Thức Object Khác (ES6+):**
    *   `Object.keys(obj)`: Trả về một MẢNG chứa tên (khóa) của các thuộc tính "đếm được" (enumerable) của object.
    *   `Object.values(obj)`: Trả về một MẢNG chứa giá trị của các thuộc tính "đếm được" của object.
    *   `Object.entries(obj)`: Trả về một MẢNG chứa các cặp `[khóa, giá trị]` dưới dạng mảng con, cho các thuộc tính "đếm được".

    ```javascript
    console.log(Object.keys(robot));   // Output: ['model', 'chucNang', 'daKhoiDong']
    console.log(Object.values(robot)); // Output: ['RT1', ['Đi', 'Nói'], true]
    console.log(Object.entries(robot)); // Output: [['model', 'RT1'], ['chucNang', ['Đi', 'Nói']], ['daKhoiDong', true]]
    ```
    Sau đó bạn có thể sử dụng các vòng lặp thông thường (`for`, `for...of`, `forEach`) để duyệt qua các mảng trả về từ các phương thức này.

### 🛠 Luyện Tập

*   Tạo một object biểu diễn thông tin về một hành tinh (ví dụ: tên, khối lượng, có vệ tinh không, danh sách các vệ tinh nếu có).
*   Truy cập và in ra các thuộc tính của hành tinh đó bằng cả Dot Notation và Bracket Notation.
*   Thêm một thuộc tính mới (ví dụ: "khoảng cách từ mặt trời").
*   Viết một phương thức cho object hành tinh, ví dụ: phương thức `moTa()` in ra tóm tắt thông tin về hành tinh đó.
*   Dùng vòng lặp `for...in` để in ra tất cả các thuộc tính và giá trị của object hành tinh.
*   (Nâng cao) Sử dụng `Object.keys()` và `forEach` để in ra tương tự.

Đối tượng là trái tim của lập trình hướng đối tượng trong JavaScript. Hiểu về cách tạo, thao tác và duyệt object sẽ mở ra cánh cửa tới các kiến thức nâng cao hơn rất nhiều! Hãy coi đây là việc bạn đang chế tạo ra những cấu trúc dữ liệu phức tạp của riêng mình vậy! 🌌

---

## File: 09_dom_va_su_kien_intro.md

```markdown
# 🖥️ Bài 9: Thao Tác Với DOM và Xử Lý Sự Kiện (Giới thiệu)

Cho đến bây giờ, chúng ta chủ yếu chạy code trong console. Tuyệt vời đấy, nhưng làm sao để JavaScript có thể "nói chuyện" với trang web thực tế và phản ứng với người dùng? Câu trả lời nằm ở **DOM (Document Object Model)** và **Xử Lý Sự Kiện (Event Handling)**.

Hãy coi trang web HTML của bạn như một bản đồ thiết kế kiến trúc, và JavaScript là đội robot xây dựng có thể đọc bản đồ đó (DOM) và phản ứng lại các sự kiện xảy ra (người dùng bấm vào nút, nhập dữ liệu...).

### 🏗️ DOM (Document Object Model) là gì?

Khi trình duyệt tải một trang HTML, nó sẽ tạo ra một mô hình cấu trúc dạng cây (tree structure) của trang đó. Mô hình này gọi là DOM. Mỗi thẻ HTML (như `<html>`, `<head>`, `<body>`, `<p>`, `<div>`, `<button>`) đều trở thành một **nút (node)** trong cây DOM.

DOM cung cấp một API (Application Programming Interface) cho phép JavaScript:

*   Tìm kiếm các phần tử HTML (các nút trong cây DOM).
*   Thay đổi nội dung văn bản và thuộc tính của các phần tử.
*   Thay đổi kiểu dáng CSS của các phần tử.
*   Thêm mới hoặc xóa bỏ các phần tử.
*   Phản ứng với các sự kiện của người dùng.

### 🎯 Truy Cập Các Phần Tử HTML (Chọn Element)

Đây là bước đầu tiên: tìm phần tử bạn muốn thao tác!

Các phương thức phổ biến trong đối tượng `document` (đại diện cho toàn bộ trang web):

*   `document.getElementById('id_cua_phan_tu')`: Tìm một phần tử duy nhất dựa trên thuộc tính `id`. Trả về phần tử hoặc `null` nếu không tìm thấy. ID phải là duy nhất trên trang!
*   `document.getElementsByClassName('class_cua_cac_phan_tu')`: Tìm tất cả phần tử có cùng thuộc tính `class`. Trả về một **HTMLCollection** (giống mảng, nhưng không có tất cả các phương thức mảng).
*   `document.getElementsByTagName('ten_the_html')`: Tìm tất cả phần tử có cùng tên thẻ (ví dụ: 'p', 'div', 'button'). Trả về một HTMLCollection.
*   `document.querySelector('css_selector')`: Tìm **phần tử ĐẦU TIÊN** khớp với CSS selector được chỉ định (có thể là id, class, tên thẻ, kết hợp,...).
*   `document.querySelectorAll('css_selector')`: Tìm **TẤT CẢ** các phần tử khớp với CSS selector. Trả về một **NodeList** (giống mảng hơn HTMLCollection).

**Ví dụ HTML:**

```html
<!DOCTYPE html>
<html>
<head>
    <title>Demo DOM</title>
</head>
<body>
    <h1 id="tieuDe">Chào Mừng</h1>
    <p class="doanVan">Đây là đoạn văn thứ nhất.</p>
    <p class="doanVan">Đây là đoạn văn thứ hai.</p>
    <button id="nutBam">Bấm vào đây!</button>

    <script src="script.js"></script> <!-- Nơi chúng ta sẽ viết JS -->
</body>
</html>
```

**Ví dụ JS (`script.js`):**

```javascript
// Truy cập phần tử bằng ID
let tieuDeElement = document.getElementById('tieuDe');
console.log(tieuDeElement); // In ra toàn bộ phần tử h1

// Truy cập các phần tử bằng Class
let doanVanElements = document.getElementsByClassName('doanVan');
console.log(doanVanElements); // In ra HTMLCollection chứa cả hai đoạn văn

// Truy cập các phần tử bằng Tên thẻ
let paragraphElements = document.getElementsByTagName('p');
console.log(paragraphElements); // In ra HTMLCollection chứa cả hai thẻ p

// Truy cập phần tử ĐẦU TIÊN khớp với selector
let firstParagraph = document.querySelector('.doanVan'); // Chọn thẻ có class 'doanVan' đầu tiên
console.log(firstParagraph);

let buttonElement = document.querySelector('#nutBam'); // Chọn thẻ có ID 'nutBam'
console.log(buttonElement);

// Truy cập TẤT CẢ phần tử khớp với selector
let allParagraphs = document.querySelectorAll('.doanVan'); // Chọn tất cả thẻ có class 'doanVan'
console.log(allParagraphs); // In ra NodeList
```

### ✏️ Thao Tác Với Nội Dung và Thuộc Tính

Sau khi có được một phần tử DOM, bạn có thể thay đổi nó:

*   `element.innerHTML`: Lấy hoặc đặt toàn bộ nội dung HTML bên trong phần tử (có thể chứa cả thẻ HTML).
*   `element.textContent`: Lấy hoặc đặt chỉ nội dung văn bản bên trong phần tử (an toàn hơn `innerHTML` khi làm việc với dữ liệu từ người dùng để tránh tấn công XSS).
*   `element.attributeName`: Lấy hoặc đặt giá trị của các thuộc tính HTML thông thường (ví dụ: `element.id`, `element.src`, `element.href`).
*   `element.setAttribute(name, value)`: Đặt giá trị cho một thuộc tính bất kỳ.
*   `element.getAttribute(name)`: Lấy giá trị của một thuộc tính bất kỳ.
*   `element.removeAttribute(name)`: Xóa một thuộc tính.

**Ví dụ (`script.js` tiếp theo):**

```javascript
// Thay đổi nội dung
tieuDeElement.textContent = "Chào mừng bạn đã đến với hệ thống!"; // Thay đổi chỉ text
// tieuDeElement.innerHTML = "<span>Nội dung MỚI</span>"; // Thay đổi cả HTML bên trong

// Thay đổi thuộc tính
let linkElement = document.createElement('a'); // Tạo thẻ 'a' mới (sẽ học sau)
linkElement.href = "https://viblo.asia"; // Đặt thuộc tính href
linkElement.setAttribute('target', '_blank'); // Đặt thuộc tính target bằng setAttribute
linkElement.textContent = "Đến Viblo";
// Để linkElement hiển thị, bạn cần chèn nó vào DOM

// Ví dụ sửa đổi thuộc tính của một hình ảnh (nếu có img trên trang)
// let imgElement = document.querySelector('img');
// imgElement.src = 'duong/dan/anh/moi.jpg';
// imgElement.setAttribute('alt', 'Hình ảnh mới');
```

### 🎨 Thay Đổi Kiểu Dáng (CSS)

Bạn có thể truy cập và sửa đổi các thuộc tính CSS của một phần tử thông qua thuộc tính `style`. Tên thuộc tính CSS gạch nối (như `background-color`) được chuyển thành `camelCase` (như `backgroundColor`) trong JS.

```javascript
tieuDeElement.style.color = "blue";         // Đổi màu chữ thành xanh dương
tieuDeElement.style.fontSize = "24px";     // Đổi kích thước font
tieuDeElement.style.border = "1px solid black"; // Thêm viền
// Lưu ý: Cách này chỉ thêm CSS inline. Thường tốt hơn là thêm/xóa class CSS (xem dưới).
```

*   **Thêm/Xóa/Chuyển đổi (Toggle) Class CSS:** Cách này hiệu quả hơn để thay đổi nhiều thuộc tính CSS cùng lúc và tách biệt logic JS với kiểu dáng. Sử dụng thuộc tính `classList`.
    *   `element.classList.add('ten-class')`
    *   `element.classList.remove('ten-class')`
    *   `element.classList.toggle('ten-class')` (thêm class nếu chưa có, xóa nếu đã có)
    *   `element.classList.contains('ten-class')` (kiểm tra xem có class đó không)

    ```javascript
    // Giả sử có CSS: .noiBat { background-color: yellow; font-weight: bold; }
    firstParagraph.classList.add('noiBat'); // Thêm class 'noiBat' vào đoạn văn đầu tiên
    // Để xóa class đó:
    // firstParagraph.classList.remove('noiBat');
    // Để bật/tắt:
    // firstParagraph.classList.toggle('noiBat');
    ```

### 💥 Xử Lý Sự Kiện (Event Handling)

Các "sự kiện" xảy ra khi người dùng tương tác với trang (click chuột, gõ phím, di chuyển chuột...) hoặc khi trạng thái trang thay đổi (tải xong, thay đổi kích thước...). JavaScript có thể "lắng nghe" các sự kiện này và thực thi một khối code (hàm **Event Handler**) khi chúng xảy ra.

Cách phổ biến và hiện đại để gắn trình lắng nghe sự kiện (event listener):

`element.addEventListener('ten_su_kien', function_handler);`

*   `element`: Phần tử DOM mà bạn muốn lắng nghe sự kiện.
*   `'ten_su_kien'`: Tên của sự kiện dưới dạng chuỗi (ví dụ: 'click', 'mouseover', 'submit', 'load', 'keydown').
*   `function_handler`: Một hàm sẽ được thực thi khi sự kiện xảy ra. Hàm này thường nhận một tham số là đối tượng **Event**, chứa thông tin chi tiết về sự kiện.

**Ví dụ (`script.js` tiếp theo):**

```javascript
// Lắng nghe sự kiện click trên nút bấm
buttonElement.addEventListener('click', function(event) {
    // Đoạn code này chạy khi nút được click
    console.log("Nút đã được bấm!");
    // console.log(event); // In ra đối tượng sự kiện với nhiều thông tin hữu ích

    tieuDeElement.textContent = "Bạn vừa bấm nút!"; // Thay đổi nội dung tiêu đề
    buttonElement.style.backgroundColor = 'lightblue'; // Đổi màu nút tạm thời
});

// Lắng nghe sự kiện di chuột qua một đoạn văn
firstParagraph.addEventListener('mouseover', function() {
    firstParagraph.style.color = 'red'; // Đổi màu chữ khi rê chuột qua
});

firstParagraph.addEventListener('mouseout', function() {
    firstParagraph.style.color = 'black'; // Trở lại màu ban đầu khi di chuột ra
});
```
*   Bạn có thể xóa trình lắng nghe sự kiện bằng `removeEventListener('ten_su_kien', function_handler)`. Hàm handler cần phải là cùng một tham chiếu hàm khi bạn thêm vào.

### ⚙️ Cấu Trúc Cơ Bản Khi Làm Việc Với DOM

Thường thì, code JS thao tác DOM nên được đặt SAU khi cấu trúc HTML đã được tạo xong (cuối thẻ `<body>`) hoặc trong một sự kiện lắng nghe khi toàn bộ trang đã tải (`DOMContentLoaded`).

```javascript
document.addEventListener('DOMContentLoaded', function() {
    // Toàn bộ code JS thao tác DOM của bạn nên đặt ở đây
    // Đảm bảo rằng tất cả các phần tử HTML đã có sẵn khi JS chạy

    const myButton = document.getElementById('myButton');
    if (myButton) { // Luôn kiểm tra xem phần tử có tồn tại không
        myButton.addEventListener('click', function() {
            alert("Button clicked!");
        });
    }
});
```

### 🛠 Luyện Tập

*   Tạo một trang HTML đơn giản với một tiêu đề (`<h1>`), một đoạn văn bản (`<p>`), và một nút bấm (`<button>`). Gán ID hoặc class cho các phần tử này.
*   Trong file JS riêng (hoặc trong thẻ `<script>` đặt cuối body), truy cập tiêu đề và đoạn văn bằng ID/Class.
*   Thay đổi nội dung của tiêu đề và đoạn văn.
*   Đổi màu nền và màu chữ của đoạn văn bằng `style`.
*   Tạo một class CSS (ví dụ `.noiBat`) trong file CSS, sau đó dùng JS để `classList.add('noiBat')` cho đoạn văn khi trang tải xong.
*   Thêm trình lắng nghe sự kiện `click` vào nút bấm. Khi nút được click, thay đổi nội dung hoặc kiểu dáng của tiêu đề hoặc đoạn văn.

Thao tác DOM và xử lý sự kiện là kỹ năng cực kỳ thiết yếu để tạo ra các trang web động và phản ứng. Đây mới chỉ là bước khởi đầu!

----


## File: 10_scope_closure.md

```markdown
# 🔬 Bài 10: Phạm Vi (Scope) và Closure - Cái nhìn sâu hơn

Hiểu về **Phạm vi (Scope)** là một trong những khái niệm QUAN TRỌNG NHẤT trong JavaScript để viết code an toàn, dễ dự đoán và tránh lỗi không đáng có. Scope quy định "ở đâu" bạn có thể truy cập một biến hoặc một hàm. **Closure** là một khái niệm mạnh mẽ được xây dựng dựa trên Scope.

Hãy coi Scope là các "vùng không gian" trong chương trình của bạn, và biến chỉ có thể "thở" trong vùng không gian mà nó được khai báo.

### 🌌 Phạm Vi (Scope)

Trong JavaScript, có 3 loại Scope chính:

1.  **Global Scope:** Biến được khai báo bên ngoài bất kỳ hàm hoặc khối lệnh nào. Các biến trong Global Scope có thể truy cập được ở **bất cứ đâu** trong chương trình.
    ```javascript
    let tenToanCau = "Tên Global"; // Global Variable

    function hamToanCau() {
        console.log(tenToanCau); // Có thể truy cập biến Global
    }

    hamToanCau();
    console.log(tenToanCau); // Có thể truy cập biến Global
    ```
    Việc lạm dụng Global Scope có thể gây ra xung đột tên biến trong các dự án lớn hoặc khi làm việc với nhiều thư viện. Nên hạn chế khai báo biến global.

2.  **Function Scope:** Biến được khai báo *bên trong* một hàm (sử dụng `var`). Các biến này chỉ tồn tại và có thể truy cập được **bên trong hàm đó và các hàm con** bên trong nó (nếu có).
    ```javascript
    function hamPhamVi() {
        var bienCucBoVar = "Biến trong Function Scope";
        console.log(bienCucBoVar); // Có thể truy cập
    }

    hamPhamVi();
    // console.log(bienCucBoVar); // Lỗi: ReferenceError, biến không tồn tại ở đây
    ```

3.  **Block Scope (ES6+):** Biến được khai báo *bên trong một khối lệnh* (block) được bao bởi cặp ngoặc nhọn `{}` (ví dụ: bên trong `if`, `for`, `while`, hoặc một khối độc lập) sử dụng từ khóa **`let`** hoặc **`const`**. Các biến này chỉ tồn tại và có thể truy cập được **bên trong khối lệnh đó**.
    ```javascript
    if (true) {
        let bienBlockLet = "Biến trong Block Scope";
        const bienBlockConst = "Hằng số trong Block Scope";
        var bienGlobalVar = "Biến VAR mặc dù ở trong khối!"; // **Quan trọng:** var KHÔNG có block scope!
        console.log(bienBlockLet);   // Có thể truy cập
        console.log(bienBlockConst); // Có thể truy cập
        console.log(bienGlobalVar);  // Có thể truy cập (vì nó vẫn là Function/Global Scope)
    }

    // console.log(bienBlockLet);   // Lỗi: ReferenceError
    // console.log(bienBlockConst); // Lỗi: ReferenceError
    console.log(bienGlobalVar);    // Có thể truy cập (vì var không có block scope)

    for (let i = 0; i < 3; i++) {
        // biến i chỉ tồn tại trong vòng lặp này
        console.log(i);
    }
    // console.log(i); // Lỗi: ReferenceError
    ```
    Vì `let` và `const` có Block Scope và giải quyết được nhiều vấn đề của `var` (như "hoisting" không mong muốn - sẽ nói thêm sau), `let` và `const` là lựa chọn ưu tiên trong code JS hiện đại.

### 🧗‍♂️ Chuỗi Phạm Vi (Scope Chain)

Khi bạn cố gắng truy cập một biến, JavaScript sẽ tìm kiếm nó:

1.  Trong phạm vi hiện tại.
2.  Nếu không tìm thấy, nó sẽ nhảy ra phạm vi chứa bên ngoài (outer scope).
3.  Cứ tiếp tục như vậy cho đến khi lên đến Global Scope.
4.  Nếu vẫn không tìm thấy sau khi lên Global Scope, sẽ báo lỗi `ReferenceError`.

Chuỗi các phạm vi lồng nhau này tạo thành **Scope Chain**.

```javascript
let bienA = "A (Global)"; // Global Scope

function hamOuter() {
    let bienB = "B (Outer Function)"; // Outer Function Scope

    function hamInner() {
        let bienC = "C (Inner Function)"; // Inner Function Scope
        console.log(bienC);    // Truy cập C (trong phạm vi hiện tại) -> C (Inner Function)
        console.log(bienB);    // Truy cập B (trong phạm vi chứa Outer) -> B (Outer Function)
        console.log(bienA);    // Truy cập A (trong phạm vi chứa Global) -> A (Global)
        // console.log(bienD); // Lỗi: ReferenceError, D không tồn tại
    }

    hamInner();
    // console.log(bienC); // Lỗi: ReferenceError, C không tồn tại trong Outer Scope
}

hamOuter();
// console.log(bienB); // Lỗi: ReferenceError, B không tồn tại trong Global Scope
```

### 🎩 Closure (Bao đóng)

Đây là khái niệm cực kỳ mạnh mẽ và đôi khi khó hiểu lúc đầu. **Closure** là khả năng của một hàm bên trong (inner function) để **ghi nhớ và truy cập các biến từ phạm vi hàm chứa bên ngoài (outer function) của nó**, ngay cả sau khi hàm ngoài đã kết thúc thực thi.

Hãy nghĩ như thế này: khi hàm bên trong được tạo ra, nó "gói" theo các biến từ phạm vi bên ngoài mà nó sử dụng. Cái gói đó chính là Closure.

**Ví dụ kinh điển về Closure:**

```javascript
function taoHamDem() {
    let dem = 0; // Biến này nằm trong phạm vi của taoHamDem

    return function() { // Hàm bên trong ẩn danh này được trả về
        dem++; // Hàm bên trong truy cập và sửa đổi biến 'dem' của hàm ngoài
        console.log(dem);
    };
}

let demThuNhat = taoHamDem(); // Gọi hàm ngoài, nó trả về hàm bên trong
// Lúc này, hàm taoHamDem() đã chạy xong, nhưng biến 'dem' (của instance được tạo ra khi gọi taoHamDem) vẫn được "ghi nhớ" bởi hàm trả về.

demThuNhat(); // Gọi hàm trả về lần 1 -> output 1. Biến 'dem' là 1.
demThuNhat(); // Gọi hàm trả về lần 2 -> output 2. Biến 'dem' là 2.

let demThuHai = taoHamDem(); // Tạo một hàm đếm mới (instance mới của Closure)
demThuHai(); // Gọi hàm mới lần 1 -> output 1. Đây là một biến 'dem' độc lập.
demThuNhat(); // Gọi lại hàm đếm cũ -> output 3.
```

Trong ví dụ này:
*   `taoHamDem()` là hàm bên ngoài.
*   Hàm `function() { dem++; console.log(dem); }` là hàm bên trong.
*   Biến `dem` là biến từ phạm vi hàm ngoài.
*   Khi `taoHamDem()` chạy xong, lẽ ra biến `dem` phải bị "biến mất" (garbage collected). Nhưng vì hàm bên trong vẫn cần truy cập nó, Closure giữ cho biến `dem` (của *instance* cụ thể của hàm `taoHamDem` đã tạo ra nó) vẫn tồn tại trong bộ nhớ.

Mỗi lần gọi `taoHamDem()`, một *instance* mới của Closure (với biến `dem` độc lập) được tạo ra.

### ✨ Các Ứng Dụng Của Closure

*   **Giữ trạng thái (State encapsulation):** Như ví dụ hàm đếm, closure giúp "giấu" biến `dem` khỏi bên ngoài và chỉ cho phép sửa đổi nó thông qua hàm được trả về. Điều này tương tự với cách các đối tượng giữ trạng thái bên trong.
*   **Mẫu Module (Module Pattern):** Dùng closure để tạo các module code với biến private (ẩn đi) và hàm public (lộ ra).
*   **Currying (Trong functional programming):** Tạo ra chuỗi các hàm mà mỗi hàm nhận một đối số.
*   **Callback functions:** Closure thường xảy ra tự nhiên khi sử dụng callbacks trong các thao tác bất đồng bộ (ví dụ: `setTimeout`, xử lý sự kiện, Fetch API...).

**Ví dụ Closure trong Callback `setTimeout`:**

```javascript
function displayMessage(message, delay) {
    setTimeout(function() { // Hàm callback này là một closure
        console.log(message); // Nó ghi nhớ biến 'message' từ phạm vi ngoài
    }, delay);
}

displayMessage("Chào từ tương lai!", 2000); // Message "Chào từ tương lai!" sẽ được ghi nhớ

// Lưu ý: Nếu dùng vòng lặp với var trong các phiên bản JS cũ hơn ES6 và setTimeout, dễ gặp lỗi vì var không có block scope và closure sẽ ghi nhớ biến đếm (var) ở trạng thái cuối cùng của vòng lặp. let giải quyết vấn đề này nhờ block scope.
// for (var i = 0; i < 5; i++) {
//     setTimeout(function() { console.log(i); }, i * 1000); // In ra 5, 5, 5, 5, 5 (var)
// }
for (let j = 0; j < 5; j++) {
    setTimeout(function() { console.log(j); }, j * 1000); // In ra 0, 1, 2, 3, 4 (let nhờ block scope)
}
```

### 🛠 Luyện Tập

*   Giải thích lại bằng lời của bạn về các loại phạm vi: Global, Function, Block. Phân biệt sự khác nhau giữa `var` và `let`/`const` về phạm vi.
*   Vẽ sơ đồ Scope Chain cho một ví dụ code có các hàm lồng nhau.
*   Viết một hàm tạo (factory function) trả về một đối tượng đơn giản có một biến "private" được giữ bởi closure và một phương thức "public" có thể tương tác với biến đó. Ví dụ: một hàm tạo đối tượng `Wallet` có số dư private và các phương thức `deposit()`, `withdraw()`, `getBalance()`.
*   Tìm một ví dụ thực tế trong dự án của bạn (hoặc một ví dụ trên mạng) nơi Closure được sử dụng.

Phạm vi và Closure có thể là những chủ đề khó hiểu lúc đầu, nhưng một khi bạn nắm vững chúng, khả năng viết code JS của bạn sẽ được nâng lên đáng kể. Chúng là nền tảng cho nhiều design patterns và cách JS quản lý bộ nhớ. Cố lên nhé, phi hành gia! 👩‍🚀👨‍🚀

---

## File: 11_this_keyword.md

```markdown
# 🔮 Bài 11: Từ khóa `this` - Người bí ẩn

Từ khóa `this` trong JavaScript là một trong những khía cạnh khó hiểu và gây nhầm lẫn nhất đối với người mới (và cả người cũ!). `this` KHÔNG đề cập đến bản thân hàm, và giá trị của nó **thay đổi tùy thuộc vào cách hàm được gọi**.

Hãy nghĩ về `this` như một "người chỉ định", nó trỏ đến **đối tượng đang "sở hữu" đoạn mã đang được thực thi**. Nhưng ai sở hữu nó? Đó là lúc mọi thứ trở nên thú vị!

Chúng ta sẽ xem `this` hoạt động như thế nào trong các ngữ cảnh gọi hàm phổ biến.

### 🌍 `this` trong Global Context

Khi `this` được sử dụng ở cấp độ global (bên ngoài bất kỳ hàm nào), nó trỏ đến đối tượng global.

*   Trong trình duyệt web: Đối tượng global là **`window`**.
*   Trong Node.js: Đối tượng global là **`global`** (hoặc `undefined` trong chế độ module nghiêm ngặt).

```javascript
// Trong trình duyệt:
console.log(this === window); // Output: true

// Khi bạn khai báo biến global với var, nó trở thành thuộc tính của window
var bienGlobalVar = 10;
console.log(window.bienGlobalVar); // Output: 10

// Với let và const, nó KHÔNG trở thành thuộc tính của window
let bienGlobalLet = 20;
console.log(window.bienGlobalLet); // Output: undefined
```

### 🧱 `this` trong Object Methods

Đây là ngữ cảnh phổ biến nhất và dễ hiểu nhất. Khi một hàm được gọi như một phương thức của một đối tượng, `this` bên trong hàm đó sẽ trỏ đến **đối tượng sở hữu phương thức đó**.

```javascript
const hanhTinh = {
    ten: "Trái đất",
    khoiLuong: "5.97 x 10^24 kg",

    // Phuong thức
    baoCao: function() {
        // 'this' ở đây trỏ đến đối tượng hanhTinh
        console.log("Tên hành tinh: " + this.ten);
        console.log("Khối lượng: " + this.khoiLuong);
    }
};

hanhTinh.baoCao(); // Gọi phương thức báoCao của đối tượng hanhTinh
// Output:
// Tên hành tinh: Trái đất
// Khối lượng: 5.97 x 10^24 kg

const hanhTinhKhac = {
    ten: "Sao Hỏa",
    khoiLuong: "0.64 x 10^24 kg",
    // Có thể sử dụng lại phương thức của object khác nếu được gán
    // Ví dụ:
    // baoCao: hanhTinh.baoCao // Gán tham chiếu hàm
};
// Nếu gọi hanhTinhKhac.baoCao() (sau khi gán), this sẽ là hanhTinhKhac
```

###  chức_năng `this` trong Simple Function Calls (Non-Method)

Khi một hàm được gọi "một mình" (không phải là phương thức của đối tượng), `this` thường trỏ đến đối tượng global (trong strict mode thì là `undefined`). Đây là một trong những nguồn gốc gây nhầm lẫn phổ biến nhất.

*   Trong non-strict mode: `this` là `window` (trình duyệt) hoặc `global` (Node.js).
*   Trong strict mode (`'use strict';` ở đầu file hoặc hàm): `this` là `undefined`. Nên dùng strict mode để code dự đoán được hơn.

```javascript
function xinChaoDonLe() {
    console.log("Giá trị của 'this' trong hàm đơn lẻ:", this);
}

xinChaoDonLe(); // Output: object Window {...} (non-strict mode trình duyệt)
                // Output: undefined (strict mode hoặc Node.js module)


function coCheDoStrict() {
    'use strict'; // Chế độ strict mode chỉ áp dụng trong hàm này
    console.log("Giá trị của 'this' trong strict mode:", this);
}

coCheDoStrict(); // Output: undefined
```

### ️️ arrow `this` trong Arrow Functions (Hàm Mũ Tên)

Đây là một điểm khác biệt QUAN TRỌNG của hàm mũi tên. Arrow functions **KHÔNG tạo ra `this` context của riêng chúng**. Thay vào đó, `this` bên trong arrow function giữ nguyên giá trị của `this` trong **phạm vi chứa (lexical scope)** của nó khi hàm được ĐỊNH NGHĨA.

Điều này làm cho arrow function RẤT hữu ích cho các callback hoặc các tình huống cần giữ nguyên `this` của ngữ cảnh bên ngoài (ví dụ: `this` của một đối tượng).

```javascript
const quanLySuKien = {
    ten: "Quản lý sự kiện",
    tasks: ["Lên kế hoạch", "Thực hiện", "Báo cáo"],

    logTasksTruyenThong: function() {
        console.log("Đây là THIS trong logTasksTruyenThong:", this); // this là quanLySuKien
        this.tasks.forEach(function(task) {
            // **VẤN ĐỀ:** this ở đây (trong hàm callback thông thường của forEach) KHÔNG trỏ đến quanLySuKien
            // mà thường là window hoặc undefined (trong strict mode)
            // console.log(this.ten + " đang xử lý task: " + task); // Lỗi: this.ten is undefined hoặc tương tự
        });
    },

    logTasksArrow: function() {
        console.log("Đây là THIS trong logTasksArrow:", this); // this là quanLySuKien
        this.tasks.forEach(task => { // Dùng arrow function
            // this ở đây giữ nguyên giá trị của this trong phạm vi chứa nó (logTasksArrow)
            console.log(this.ten + " đang xử lý task: " + task); // OK: this trỏ đến quanLySuKien
        });
    }
};

quanLySuKien.logTasksTruyenThong(); // Sẽ thấy vấn đề về this

console.log("-------------------");

quanLySuKien.logTasksArrow();
// Output:
// Đây là THIS trong logTasksArrow: { ten: "Quản lý sự kiện", ... }
// Quản lý sự kiện đang xử lý task: Lên kế hoạch
// Quản lý sự kiện đang xử lý task: Thực hiện
// Quản lý sự kiện đang xử lý task: Báo cáo
```

### ⚙️ Gán giá trị `this` (Call, Apply, Bind)

Bạn có thể gán giá trị `this` cho một hàm một cách rõ ràng bằng các phương thức của hàm (`Function.prototype`):

1.  **`call(thisValue, arg1, arg2, ...)`:** Gọi hàm NGAY LẬP TỨC, với `thisValue` là giá trị `this`, và các đối số được truyền riêng lẻ.
    ```javascript
    function saySomething(message) {
        console.log(message + " bởi " + this.ten);
    }

    const user = { ten: "Alice" };

    saySomething.call(user, "Hello"); // Gọi saySomething với this là user
    // Output: Hello bởi Alice
    ```

2.  **`apply(thisValue, [argsArray])`:** Giống `call`, nhưng các đối số được truyền dưới dạng một **mảng**.
    ```javascript
    function sum(a, b) {
        return this.prefix + (a + b); // Ví dụ this có thuộc tính prefix
    }

    const calculator = { prefix: "Kết quả: " };

    console.log(sum.apply(calculator, [10, 20])); // Gọi sum với this là calculator, đối số là mảng [10, 20]
    // Output: Kết quả: 30
    ```

3.  **`bind(thisValue, arg1, arg2, ...)`:** KHÔNG gọi hàm ngay lập tức. Nó trả về một **phiên bản MỚI** của hàm gốc với `thisValue` đã được GẮN (bound) vĩnh viễn và (tùy chọn) một vài đối số đã được gán trước. Hàm mới này có thể được gọi sau. Rất hữu ích trong Event Handling hoặc các callback.
    ```javascript
    const person = { name: "Bob" };
    function introduce() { console.log("Tôi là " + this.name); }

    const boundIntroduce = introduce.bind(person); // Tạo hàm mới boundIntroduce
    // this trong boundIntroduce luôn là person

    boundIntroduce(); // Gọi hàm mới
    // Output: Tôi là Bob

    // Ví dụ trong Event Handling (phổ biến hơn trước khi có arrow function):
    // element.addEventListener('click', object.method.bind(object));
    // Giúp this bên trong object.method trỏ đúng đến object thay vì phần tử DOM
    ```

### 🏢 `this` trong Class Constructors (ES6+)

Khi dùng cú pháp `class` (sẽ học ở bài sau), trong constructor và các phương thức, `this` trỏ đến **instance (thể hiện) mới được tạo ra** của lớp đó.

```javascript
class TinhThe {
    constructor(ten) {
        this.ten = ten; // 'this' trỏ đến instance mới
        console.log("Đang tạo tinh thể: " + this.ten);
    }

    baoTon() {
        // 'this' trỏ đến instance gọi phương thức baoTon
        console.log(this.ten + " đang được bảo tồn.");
    }
}

let phaLeX = new TinhThe("Pha lê X"); // Gọi constructor bằng 'new'. 'this' trong constructor là phaLeX
// Output: Đang tạo tinh thể: Pha lê X

phaLeX.baoTon(); // 'this' trong baoTon là phaLeX
// Output: Pha lê X đang được bảo tồn.
```

### 🤯 Tóm Lược `this` (Siêu ngắn gọn)

Giá trị của `this` phụ thuộc vào cách hàm được gọi:

1.  **Global Context:** `window` (trình duyệt) hoặc `global`/`undefined` (Node.js).
2.  **Object Method:** Đối tượng gọi phương thức đó.
3.  **Simple Function:** `window`/`global` (non-strict) hoặc `undefined` (strict).
4.  **Arrow Function:** Giữ nguyên `this` của phạm vi cha (lexical scope).
5.  **Constructor (with `new`):** Instance mới được tạo ra.
6.  **`call`, `apply`, `bind`:** Giá trị bạn truyền vào làm đối số đầu tiên.

Hiểu được các quy tắc này giúp bạn biết được `this` đang trỏ đến đâu trong các tình huống khác nhau!

### 🛠 Luyện Tập

*   Viết một đối tượng đơn giản có một phương thức sử dụng `this` để in ra một thuộc tính của nó. Gọi phương thức đó.
*   Thử gọi hàm đó một mình (không thông qua đối tượng) và quan sát giá trị `this` (có thể cần `'use strict'`).
*   Chuyển phương thức trong đối tượng thành Arrow function và quan sát xem nó hoạt động như thế nào (lưu ý `this` của arrow function trỏ ra ngoài).
*   Viết hai hàm nhỏ và một đối tượng. Sử dụng `call` và `apply` để gọi một hàm với `this` trỏ đến đối tượng, truyền các đối số khác nhau.
*   Sử dụng `bind` để tạo một phiên bản hàm mới đã gắn sẵn `this`, sau đó gọi hàm mới này.

Kiến thức về `this` đòi hỏi thời gian và thực hành để thật sự "thấm". Đừng nản lòng nếu thấy khó hiểu ban đầu nhé! Đây là một bước quan trọng để chinh phục JavaScript!

---

## File: 12_destructuring.md

```markdown
# ✨ Bài 12: Destructuring - Phép giải cấu trúc tiện lợi (ES6+)

JavaScript ES6 đã giới thiệu rất nhiều tính năng tuyệt vời giúp code trở nên ngắn gọn và dễ đọc hơn. **Destructuring Assignment** là một trong số đó. Nó cho phép bạn "giải nén" các giá trị từ MẢNG (Arrays) hoặc các thuộc tính từ ĐỐI TƯỢNG (Objects) vào các biến riêng lẻ một cách nhanh chóng.

Hãy coi Destructuring như việc bạn có một "gói quà" (mảng hoặc đối tượng) và muốn lấy ra các "món quà" (các phần tử/thuộc tính) bên trong nó và đặt chúng vào các "chiếc hộp" (các biến) đã được dán nhãn trước.

### 🧩 Giải Cấu Trúc Mảng (Array Destructuring)

Cho phép gán các phần tử của mảng vào các biến theo thứ tự.

Cú pháp:

```javascript
let [bien1, bien2, ..., bienN] = tenMang;
```

**Ví dụ cơ bản:**

```javascript
const colors = ["Red", "Green", "Blue"];

let [mau1, mau2, mau3] = colors; // Gán phần tử theo thứ tự

console.log(mau1); // Output: Red
console.log(mau2); // Output: Green
console.log(mau3); // Output: Blue
```

**Bỏ qua các phần tử không cần thiết:** Dùng dấu phẩy.

```javascript
const numbers = [1, 2, 3, 4, 5];

let [first, , third, , fifth] = numbers; // Bỏ qua phần tử thứ 2 và thứ 4

console.log(first);  // Output: 1
console.log(third);  // Output: 3
console.log(fifth);  // Output: 5
```

**Gán phần tử còn lại vào một mảng mới (Rest element):** Dùng cú pháp `...tenBien`. Phải là phần tử CUỐI CÙNG trong phép gán destructuring.

```javascript
const hobbies = ["Đọc sách", "Chơi game", "Đi bộ", "Xem phim", "Nấu ăn"];

let [soThich1, soThich2, ...cacSoThichKhac] = hobbies;

console.log(soThich1);        // Output: Đọc sách
console.log(soThich2);        // Output: Chơi game
console.log(cacSoThichKhac); // Output: ["Đi bộ", "Xem phim", "Nấu ăn"] (một mảng mới)
```

**Giá trị mặc định:** Cung cấp giá trị mặc định cho biến nếu phần tử tương ứng trong mảng là `undefined`.

```javascript
const settings = ["Vietnamese"]; // Thiếu timezone, theme

let [language, timezone = "UTC", theme = "dark"] = settings;

console.log(language); // Output: Vietnamese
console.log(timezone); // Output: UTC (được gán mặc định)
console.log(theme);    // Output: dark (được gán mặc định)

const emptyArray = [];
let [a = 1, b = 2] = emptyArray;
console.log(a, b); // Output: 1 2
```

**Trao đổi giá trị hai biến:** Một cách nhanh gọn mà không cần biến tạm.

```javascript
let x = 10;
let y = 20;

[x, y] = [y, x]; // Giải cấu trúc mảng [20, 10] vào lại biến x và y

console.log(x); // Output: 20
console.log(y); // Output: 10
```

### 📦 Giải Cấu Trúc Đối Tượng (Object Destructuring)

Cho phép gán các thuộc tính của đối tượng vào các biến sử dụng tên thuộc tính (hoặc tên khác).

Cú pháp:

```javascript
let { key1, key2, ..., keyN } = tenDoiTuong;
```

*Quan trọng:* Tên biến mặc định sẽ là tên KEY của thuộc tính trong đối tượng.

**Ví dụ cơ bản:**

```javascript
const userProfile = {
    firstName: "Alice",
    lastName: "Wonderland",
    age: 25
};

let { firstName, age } = userProfile; // Gán thuộc tính firstName vào biến firstName, age vào biến age

console.log(firstName); // Output: Alice
console.log(age);       // Output: 25
// console.log(lastName); // Lỗi: ReferenceError, lastName không được giải nén thành biến cùng tên
```

**Gán vào tên biến KHÁC:** Dùng cú pháp `key: tenBienMoi`.

```javascript
const product = {
    id: 123,
    name: "Smartphone X",
    price: 799
};

let { name: productName, price: productPrice } = product; // Gán thuộc tính name vào biến productName, price vào productPrice

console.log(productName); // Output: Smartphone X
console.log(productPrice); // Output: 799
// console.log(name); // Lỗi: ReferenceError
```

**Gán phần còn lại vào một đối tượng mới (Rest properties):** Dùng cú pháp `...tenBien`. Phải là thuộc tính CUỐI CÙNG trong phép gán destructuring.

```javascript
const complexUser = {
    id: 1,
    name: "Bob",
    email: "bob@example.com",
    isActive: true,
    role: "Admin"
};

let { id, name, ...restInfo } = complexUser; // Lấy id và name, các thuộc tính còn lại cho vào object restInfo

console.log(id);       // Output: 1
console.log(name);     // Output: Bob
console.log(restInfo); // Output: { email: "bob@example.com", isActive: true, role: "Admin" } (một object mới)
```

**Giá trị mặc định:** Cung cấp giá trị mặc định cho biến nếu thuộc tính tương ứng không tồn tại hoặc có giá trị là `undefined`.

```javascript
const book = {
    title: "Coding Galactic Empires"
    // author: "Cmdr. Alpha", // Bỏ qua thuộc tính này
    // year: undefined,      // Có thuộc tính nhưng là undefined
    pages: 500
};

let {
    title,
    author = "Tác giả Khuyết danh", // Sẽ lấy giá trị mặc định
    year = 2024,                     // Sẽ lấy giá trị mặc định (vì year là undefined)
    pages
} = book;

console.log(title);  // Output: Coding Galactic Empires
console.log(author); // Output: Tác giả Khuyết danh
console.log(year);   // Output: 2024
console.log(pages);  // Output: 500
```

### ✨ Các Trường Hợp Sử Dụng Phổ Biến

*   **Trích xuất dữ liệu từ Responses API:** Dữ liệu nhận được thường dưới dạng object/array lồng nhau, destructuring giúp lấy thông tin cần thiết nhanh chóng.
*   **Làm việc với Props trong React/Component Frameworks:** Destructuring props là cách cực kỳ phổ biến.
*   **Lấy đối số cho hàm:** Dùng destructuring ngay trong phần tham số của hàm, đặc biệt khi hàm nhận một đối tượng cấu hình lớn.

    ```javascript
    // Hàm nhận đối tượng cấu hình
    function createUser({ name, age, city = "Unknown" }) {
        console.log(`Created user: ${name}, Age: ${age}, City: ${city}`);
    }

    const userData = { name: "Charlie", age: 35, occupation: "Engineer" };
    createUser(userData); // Output: Created user: Charlie, Age: 35, City: Unknown (occupation bị bỏ qua)

    createUser({ name: "David", age: 28 }); // Sử dụng giá trị mặc định cho city
    // Output: Created user: David, Age: 28, City: Unknown
    ```
*   **Làm cho code gọn gàng hơn:** Thay vì viết `const name = user.name; const age = user.age;` bạn chỉ cần `const { name, age } = user;`.

### 🛠 Luyện Tập

*   Tạo một mảng có 5 màu. Sử dụng Array Destructuring để lấy màu thứ nhất, thứ ba, và tất cả các màu còn lại vào một biến mảng khác. In chúng ra.
*   Tạo hai biến `a` và `b`. Sử dụng Destructuring để hoán đổi giá trị của chúng.
*   Tạo một object `car` với các thuộc tính `model`, `year`, `color`. Sử dụng Object Destructuring để lấy `model` và gán nó vào biến `carModel`, đồng thời lấy `color`. In ra `carModel` và `color`.
*   Tạo một object `config` với một số thuộc tính và giá trị mặc định cho một thuộc tính. Viết một hàm nhận object này làm tham số và sử dụng Object Destructuring (kèm giá trị mặc định) trong signature của hàm. Gọi hàm với object có hoặc thiếu thuộc tính đó.

Destructuring là một công cụ nhỏ nhưng vô cùng hữu ích giúp giảm thiểu boilerplate code và cải thiện tính đọc hiểu. Hãy dùng nó thường xuyên!

---

## File: 13_spread_rest.md

```markdown
# 🎒 Bài 13: Toán tử Spread (...) và Rest Parameters (...) (ES6+)

ES6 còn giới thiệu hai khái niệm liên quan, sử dụng cùng một cú pháp ba dấu chấm `...`, nhưng ở các ngữ cảnh khác nhau mang ý nghĩa khác nhau: **Toán tử Spread (Toán tử rải/phân tán)** và **Rest Parameters (Tham số còn lại)**.

Chúng đều liên quan đến việc xử lý các tập hợp (arrays, objects), giúp bạn làm việc với chúng một cách linh hoạt hơn.

### 🚀 Toán tử Spread (...) - Phân tán các phần tử

Toán tử Spread dùng để "rải" hoặc "phân tán" các phần tử của một đối tượng lặp (iterable) như mảng hoặc chuỗi, hoặc các thuộc tính của một đối tượng (trong Object Literals - ES9), vào nơi chúng được sử dụng. Nó giống như "bung" nội dung ra.

**Sử dụng với Mảng (Arrays):**

*   **Sao chép mảng (Shallow Copy):** Tạo một bản sao *mới* của mảng mà không làm ảnh hưởng đến mảng gốc (copy các phần tử cấp 1). Rất phổ biến để tránh side effect khi sửa đổi mảng.
    ```javascript
    const originalArray = [1, 2, 3];
    const copiedArray = [...originalArray]; // Sao chép các phần tử của originalArray vào mảng mới

    console.log(copiedArray); // Output: [1, 2, 3]
    console.log(copiedArray === originalArray); // Output: false (Đây là một mảng mới)

    copiedArray.push(4); // Thay đổi mảng mới
    console.log(copiedArray);    // Output: [1, 2, 3, 4]
    console.log(originalArray); // Output: [1, 2, 3] (mảng gốc không bị ảnh hưởng)
    ```
    Lưu ý: Đây là shallow copy. Nếu mảng chứa các đối tượng lồng nhau, chỉ tham chiếu của đối tượng lồng nhau được copy, không phải bản sao sâu (deep copy).

*   **Kết hợp mảng (Concatenating):** Nối nhiều mảng lại với nhau. Ngắn gọn hơn phương thức `concat()`.
    ```javascript
    const arr1 = [1, 2];
    const arr2 = [3, 4];
    const combinedArray = [...arr1, ...arr2, 5, 6]; // Nối arr1, arr2 và thêm các phần tử khác

    console.log(combinedArray); // Output: [1, 2, 3, 4, 5, 6]
    ```

*   **Thêm phần tử vào giữa mảng:** Kết hợp với destructuring.
    ```javascript
    const arr = [1, 5, 6];
    const newArr = [arr[0], 2, 3, 4, ...arr.slice(1)]; // Khá thủ công nếu chỉ dùng spread

    const easierWay = [1, ...[2, 3, 4], 5, 6]; // Dễ hình dung hơn, chèn mảng [2, 3, 4] vào
    console.log(easierWay); // Output: [1, 2, 3, 4, 5, 6]
    ```

*   **Truyền các phần tử mảng làm đối số cho hàm:** Ngắn gọn hơn `apply()`.
    ```javascript
    function displayNumbers(a, b, c) {
        console.log(a, b, c);
    }

    const numbers = [10, 20, 30];
    displayNumbers(...numbers); // Rải các phần tử của mảng numbers thành 3 đối số
    // Output: 10 20 30
    ```

**Sử dụng với Chuỗi (Strings):** Rải chuỗi thành mảng các ký tự.

```javascript
const greeting = "Hello";
const chars = [...greeting];

console.log(chars); // Output: ["H", "e", "l", "l", "o"]
```

**Sử dụng với Đối tượng (Objects) - ES9+:** Sao chép hoặc kết hợp các thuộc tính của đối tượng (shallow copy).

```javascript
const userBasic = { name: "Alice", age: 25 };
const userDetails = { city: "New York", job: "Engineer" };

// Sao chép object
const copiedUser = { ...userBasic };
console.log(copiedUser); // Output: { name: "Alice", age: 25 }
console.log(copiedUser === userBasic); // Output: false

// Kết hợp objects (thuộc tính của các object sau sẽ ghi đè thuộc tính của object trước nếu trùng tên)
const fullUser = { ...userBasic, ...userDetails, isActive: true };
console.log(fullUser);
// Output: { name: "Alice", age: 25, city: "New York", job: "Engineer", isActive: true }

// Ghi đè thuộc tính khi sao chép/kết hợp
const config = { debug: false, port: 3000 };
const updatedConfig = { ...config, debug: true }; // Sao chép config và ghi đè debug

console.log(updatedConfig); // Output: { debug: true, port: 3000 }
```
Lưu ý: Spread Object cũng là shallow copy.

### 📦 Rest Parameters (...) - Gộp các đối số

Rest Parameters được dùng trong định nghĩa **tham số của một hàm**. Nó cho phép thu thập tất cả các đối số "còn lại" (chưa được gán cho tham số cụ thể nào) thành một **MẢNG duy nhất**.

Cú pháp:

```javascript
function tenHam(param1, param2, ...restParamsArray) {
    // ... restParamsArray sẽ là một MẢNG chứa các đối số còn lại
}
```
*Quan trọng:* Rest Parameters phải là tham số CUỐI CÙNG trong danh sách tham số của hàm.

**Ví dụ:**

```javascript
function multiply(multiplier, ...args) { // Thu thập các đối số còn lại vào mảng 'args'
    console.log("Đối số cố định (nhân):", multiplier);
    console.log("Các đối số còn lại (để nhân):", args); // args là một mảng

    // Nhân từng đối số còn lại với multiplier
    const results = args.map(num => num * multiplier); // Sử dụng phương thức map của mảng

    return results;
}

const finalResults = multiply(5, 1, 2, 3, 4); // 5 là multiplier, 1, 2, 3, 4 là args
console.log("Kết quả nhân:", finalResults); // Output: Kết quả nhân: [ 5, 10, 15, 20 ]

const resultsOnlyMultiplier = multiply(2); // multiplier là 2, args là mảng rỗng []
console.log("Kết quả nhân:", resultsOnlyMultiplier); // Output: Kết quả nhân: []
```

### 🎯 Rest Parameters vs `arguments` object (cũ)

Trước ES6, để làm việc với số lượng đối số không xác định, người ta dùng đối tượng `arguments` có sẵn bên trong mỗi hàm (trừ arrow function). Tuy nhiên, `arguments` có một số hạn chế:

*   Nó không phải là một MẢNG THỰC SỰ (true Array), chỉ giống mảng. Để dùng các phương thức mảng (như `map`, `filter`), bạn phải chuyển đổi nó sang mảng thực.
*   Nó chứa TẤT CẢ các đối số, không chỉ những đối số "còn lại".
*   Không dùng được trong Arrow function.

Rest Parameters giải quyết những vấn đề này:
*   Rest parameters luôn là một **mảng thực sự**.
*   Nó chỉ chứa các đối số "còn lại".
*   Hoạt động bình thường với Arrow function (ghi nhận các đối số không được gán cụ thể).

Nên ưu tiên dùng Rest Parameters thay vì `arguments` trong code hiện đại.

### 🤔 Spread và Rest: Nhận diện và phân biệt

Nhận diện dựa vào ngữ cảnh sử dụng:

*   Trong phần **tham số khi ĐỊNH NGHĨA HÀM**: Đó là **Rest Parameters** (thu thập các đối số thành mảng).
*   Khi **GỌI hàm** hoặc trong **literal mảng/đối tượng** (`[]` hoặc `{}`): Đó là **Spread Operator** (phân tán các phần tử/thuộc tính).

```javascript
// Context: ĐỊNH NGHĨA HÀM -> Rest Parameter
function myFunction(a, b, ...remainingArgs) {
    console.log(remainingArgs); // Một MẢNG chứa các đối số 3, 4, 5
}
myFunction(1, 2, 3, 4, 5);

// Context: GỌI HÀM -> Spread Operator
const data = [1, 2, 3];
function anotherFunction(x, y, z) {
    console.log(x + y + z); // 6
}
anotherFunction(...data); // Rải mảng data thành 3 đối số riêng lẻ

// Context: LITERAL MẢNG -> Spread Operator
const arrA = [1, 2];
const arrB = [...arrA, 3, 4]; // Rải arrA vào mảng mới

// Context: LITERAL ĐỐI TƯỢNG -> Spread Operator
const objA = { a: 1 };
const objB = { ...objA, b: 2 }; // Rải objA vào object mới
```

### 🛠 Luyện Tập

*   Tạo một mảng `planets`. Sử dụng toán tử Spread để tạo một mảng `solarSystem` mới bằng cách sao chép `planets` và thêm một vài hành tinh lùn hoặc vật thể khác vào.
*   Tạo hai đối tượng đơn giản, ví dụ: `address` và `contactInfo`. Sử dụng Spread Operator để tạo một đối tượng `fullDetails` mới chứa tất cả thuộc tính từ cả hai object đó.
*   Viết một hàm `sumAll` sử dụng Rest Parameters để nhận vào bất kỳ số lượng số nào, sau đó tính và trả về tổng của chúng. Gọi hàm với 3, 5, 10 số khác nhau.
*   Giải thích bằng lời sự khác nhau cơ bản giữa Spread Operator và Rest Parameters, mặc dù chúng dùng cùng ký hiệu `...`.

Spread và Rest là những công cụ vô giá để làm việc hiệu quả hơn với dữ liệu trong JS, đặc biệt khi xử lý các tập hợp. Sử dụng thành thạo chúng sẽ làm code của bạn gọn gàng và dễ bảo trì hơn nhiều!

---

## File: 14_classes.md

```markdown
# 👽 Bài 14: Class (Lớp) - Kiến tạo các thực thể (ES6+)

Trong lập trình hướng đối tượng (OOP), Class là một **bản thiết kế (blueprint)** để tạo ra các đối tượng (objects). Đối tượng được tạo từ một lớp được gọi là **thể hiện (instance)** của lớp đó. Mặc dù JavaScript về cốt lõi dựa trên **prototype** (một cơ chế thừa kế dựa trên đối tượng, khác với cơ chế thừa kế dựa trên lớp truyền thống), ES6 đã giới thiệu cú pháp `class` như một cách viết "giả lập" (syntactic sugar) thân thiện và quen thuộc hơn với những người quen thuộc với lập trình hướng đối tượng dựa trên lớp (như Java, C++).

Hãy nghĩ Class như một khuôn đúc các robot. Mỗi con robot được đúc ra từ khuôn đó là một instance, và tất cả chúng đều có cấu trúc và khả năng (thuộc tính và phương thức) giống như bản thiết kế của khuôn.

### ✏️ Khai Báo Class (Class Declaration)

Cách phổ biến để tạo một class.

Cú pháp:

```javascript
class TenClass {
    // Constructor (phương thức khởi tạo)
    constructor(parameters) {
        // Khởi tạo các thuộc tính của instance
        // this.propertyName = parameter;
    }

    // Các phương thức của instance
    tenPhuongThuc(parameters) {
        // Code thực thi bởi instance
    }

    // Getter và Setter (tùy chọn)
    get tenThuocTinhAo() { ... }
    set tenThuocTinhAo(value) { ... }

    // Phương thức static (gọi trên chính class, không phải instance)
    static tenPhuongThucStatic(parameters) {
        // Code không cần instance để chạy
    }
}
```
*   **`constructor()`:** Là phương thức đặc biệt. Nó tự động chạy khi bạn tạo một instance mới bằng từ khóa `new`. Bạn dùng nó để khởi tạo các thuộc tính của instance mới (`this.propertyName = value;`). Một class chỉ có thể có một constructor.
*   **Phương thức Instance:** Các hàm được định nghĩa bên trong class (ngoài constructor). Chúng trở thành phương thức của MỌI instance được tạo từ class đó. Bạn gọi chúng trên instance (ví dụ: `myInstance.myMethod()`). `this` bên trong các phương thức instance trỏ đến chính instance đó.
*   **Getter/Setter:** Cho phép bạn truy cập/thiết lập các thuộc tính theo cú pháp `.propertyName` như thể chúng là thuộc tính dữ liệu, nhưng đằng sau đó là một hàm (kiểm soát việc lấy/thiết lập giá trị).
*   **Phương thức Static:** Khai báo với từ khóa `static`. Các phương thức này thuộc về CHÍNH class, không phải bất kỳ instance cụ thể nào. Bạn gọi chúng trực tiếp trên class (ví dụ: `MyClass.staticMethod()`). `this` bên trong phương thức static trỏ đến CHÍNH class đó (không phải instance).

**Ví dụ:**

```javascript
class TauVuTru {
    constructor(ten, loaiNhienLieu) {
        this.ten = ten; // Thuộc tính của instance
        this.loaiNhienLieu = loaiNhienLieu;
        this._vanToc = 0; // Dấu gạch dưới thường để chỉ thuộc tính "private" (theo quy ước, JS không có private thực sự trước Private Fields)
        console.log(`${this.ten} [${this.loaiNhienLieu}] sẵn sàng.`);
    }

    tangToc(giaToc) {
        this._vanToc += giaToc;
        console.log(`${this.ten} tăng tốc! Vận tốc hiện tại: ${this._vanToc}`);
    }

    haCanh() {
        this._vanToc = 0;
        console.log(`${this.ten} hạ cánh. Vận tốc: ${this._vanToc}`);
    }

    // Getter cho vận tốc
    get vanTocHienTai() {
        return this._vanToc;
    }

    // Setter cho vận tốc (có thể thêm logic kiểm tra)
    set vanTocHienTai(value) {
        if (value >= 0) {
            this._vanToc = value;
        } else {
            console.log("Vận tốc không thể âm.");
        }
    }

    // Phương thức Static
    static huongDanSuDung() {
        console.log("Hướng dẫn chung cho tất cả Tàu vũ trụ: Kiểm tra nhiên liệu, xác định tọa độ, bay!");
    }
}

// Tạo instance từ class
let enterprise = new TauVuTru("Enterprise", "Plasma"); // Gọi constructor
// Output: Enterprise [Plasma] sẵn sàng.

let millenniumFalcon = new TauVuTru("Millennium Falcon", "Hyperdrive");
// Output: Millennium Falcon [Hyperdrive] sẵn sàng.

// Gọi phương thức instance
enterprise.tangToc(100); // Output: Enterprise tăng tốc! Vận tốc hiện tại: 100
millenniumFalcon.tangToc(250); // Output: Millennium Falcon tăng tốc! Vận tốc hiện tại: 250

// Sử dụng Getter
console.log("Vận tốc Enterprise:", enterprise.vanTocHienTai); // Output: Vận tốc Enterprise: 100

// Sử dụng Setter
enterprise.vanTocHienTai = 150;
console.log("Vận tốc mới Enterprise:", enterprise.vanTocHienTai); // Output: Vận tốc mới Enterprise: 150
enterprise.vanTocHienTai = -50; // Output: Vận tốc không thể âm.

// Gọi phương thức static
TauVuTru.huongDanSuDung(); // Output: Hướng dẫn chung cho tất cả Tàu vũ trụ: Kiểm tra nhiên liệu, xác định tọa độ, bay!
// enterprise.huongDanSuDung(); // Lỗi: TypeError, huongDanSuDung is not a function (của instance)
```

### ➡️ Thừa Kế (Inheritance)

Một class có thể "thừa kế" các thuộc tính và phương thức từ một class khác bằng từ khóa `extends`. Class mới được gọi là lớp **con (child class)** hoặc lớp **dẫn xuất (derived class)**, và lớp mà nó thừa kế được gọi là lớp **cha (parent class)** hoặc lớp **cơ sở (base class)**.

*   `extends`: Thiết lập mối quan hệ thừa kế.
*   `super()`: Trong constructor của lớp con, bạn phải gọi `super()` TRƯỚC KHI sử dụng `this`. `super()` gọi constructor của lớp cha và thiết lập phần thuộc tính từ lớp cha cho instance hiện tại. Bạn cũng dùng `super.tenPhuongThuc()` để gọi phương thức của lớp cha từ lớp con.

**Ví dụ Thừa kế:**

```javascript
class TauChoHang extends TauVuTru { // TauChoHang thừa kế từ TauVuTru
    constructor(ten, loaiNhienLieu, dungTich) {
        // Gọi constructor của lớp cha (TauVuTru)
        super(ten, loaiNhienLieu);

        this.dungTich = dungTich; // Thêm thuộc tính mới cho lớp con
        this._luongHangHienTai = 0;
    }

    napHang(luong) {
        if (this._luongHangHienTai + luong <= this.dungTich) {
            this._luongHangHienTai += luong;
            console.log(`${this.ten} đã nạp ${luong}. Tổng: ${this._luongHangHienTai}/${this.dungTich}`);
        } else {
            console.log(`${this.ten}: Không đủ dung tích để nạp ${luong}.`);
        }
    }

    // Ghi đè (override) phương thức của lớp cha
    haCanh() {
        if (this._luongHangHienTai > 0) {
            console.log(`${this.ten}: Cần dỡ hàng trước khi hạ cánh.`);
        } else {
            super.haCanh(); // Gọi phương thức haCanh của lớp cha
            console.log("Khoang chứa rỗng, hạ cánh an toàn.");
        }
    }

    // Có thể thêm phương thức khác hoặc ghi đè các phương thức khác
}

let titanicVanTai = new TauChoHang("Titanic Tải", "Warp", 5000);
// Output: Titanic Tải [Warp] sẵn sàng.

titanicVanTai.tangToc(50);      // Thừa kế từ TauVuTru -> Output: Titanic Tải tăng tốc!...
titanicVanTai.napHang(2000);     // Phương thức riêng của TauChoHang -> Output: Titanic Tải đã nạp...
titanicVanTai.haCanh();          // Ghi đè phương thức haCanh -> Output: Titanic Tải: Cần dỡ hàng...
titanicVanTai.napHang(-2000); // Dỡ hàng
titanicVanTai.haCanh();          // Bây giờ mới gọi super.haCanh() -> Output: Titanic Tải hạ cánh... Khoang chứa rỗng...

```

### ⚠️ Class là Syntactic Sugar!

Như đã đề cập, cú pháp `class` chỉ là cách viết khác cho cơ chế prototype dựa trên hàm tạo (constructor functions) có từ trước. Mặc dù chúng trông giống OOP dựa trên lớp, hiểu biết sâu sắc về prototype vẫn hữu ích. Tuy nhiên, với hầu hết các trường hợp sử dụng hiện đại, cú pháp `class` là đủ và nên dùng vì nó dễ đọc và quản lý hơn.

### 🔐 Thuộc tính Private (Private Class Fields - Experimental)

Gần đây hơn, có đề xuất cú pháp cho các thuộc tính và phương thức private thực sự trong class sử dụng dấu `#` ở đầu. Tính năng này vẫn đang trong quá trình chuẩn hóa nhưng đang ngày càng được hỗ trợ rộng rãi.

```javascript
class BankAccount {
    #balance = 0; // Thuộc tính private

    constructor(initialBalance) {
        if (initialBalance >= 0) {
            this.#balance = initialBalance;
        }
    }

    deposit(amount) {
        if (amount > 0) {
            this.#balance += amount;
            console.log(`Deposited ${amount}. New balance: ${this.#balance}`);
        }
    }

    withdraw(amount) {
        if (amount > 0 && amount <= this.#balance) {
            this.#balance -= amount;
            console.log(`Withdrew ${amount}. New balance: ${this.#balance}`);
        } else {
            console.log("Invalid withdrawal amount or insufficient funds.");
        }
    }

    getBalance() {
        return this.#balance; // Có thể truy cập từ bên trong class
    }
}

let myAccount = new BankAccount(100);
myAccount.deposit(50); // Output: Deposited 50. New balance: 150
myAccount.withdraw(30); // Output: Withdrew 30. New balance: 120
console.log(myAccount.getBalance()); // Output: 120

// console.log(myAccount.#balance); // Lỗi: SyntaxError (hoặc Private field '#balance' must be declared ...) - Không thể truy cập từ bên ngoài
```

### 🛠 Luyện Tập

*   Tạo một class `Robot` với constructor nhận tên và chức năng ban đầu. Thêm phương thức `report()` in ra tên và chức năng của robot đó. Tạo một instance và gọi phương thức `report()`.
*   Thêm phương thức `addFunction()` vào class `Robot` để thêm chức năng mới vào một mảng chức năng của robot.
*   Tạo một class `ChienDauRobot` thừa kế từ `Robot`. Thêm thuộc tính `sucTanCong` và phương thức `attack()` (ví dụ in ra tin nhắn tấn công). Trong constructor của `ChienDauRobot`, đừng quên gọi `super()`.
*   (Nâng cao) Thêm một phương thức static `getCapabilities()` vào class `Robot` trả về một danh sách các khả năng chung của robot (ví dụ: `['move', 'speak']`).

Class là cách hiệu quả để cấu trúc code của bạn khi bạn làm việc với nhiều đối tượng cùng loại. Nó giúp code của bạn trở nên mô-đun hơn và dễ quản lý, đặc biệt trong các dự án lớn.

---

## File: 15_modules_es.md

```markdown
# 📦 Bài 15: Modules (Mô-đun) với ES Modules - Đóng gói code hiệu quả (ES6+)

Khi các dự án JavaScript trở nên lớn hơn, việc đặt tất cả code vào một file duy nhất trở nên lộn xộn và khó quản lý. Biến và hàm khai báo ở cấp global dễ dàng bị trùng tên và ghi đè lên nhau (xung đột namespace). **Mô-đun (Modules)** ra đời để giải quyết vấn đề này.

Mô-đun cho phép bạn chia code thành các file riêng biệt, mỗi file xử lý một phần chức năng cụ thể. Biến và hàm được định nghĩa bên trong một mô-đun mặc định là **private** (chỉ có thể truy cập bên trong mô-đun đó). Để một phần tử (biến, hàm, class) có thể sử dụng được ở mô-đun khác, bạn phải **xuất (export)** nó ra. Các mô-đun khác muốn sử dụng chúng thì phải **nhập (import)** vào.

Hãy nghĩ về các mô-đun như những khoang riêng biệt của tàu vũ trụ: mỗi khoang có thiết bị và chức năng riêng, và bạn chỉ có thể chuyển đồ hoặc liên lạc giữa các khoang thông qua các cửa hoặc hệ thống truyền dẫn (export/import) được thiết kế sẵn.

JavaScript hiện đại (từ ES6 trở đi) có hệ thống mô-đun riêng gọi là **ES Modules**.

### ➡️ Xuất (Export)

Bạn dùng từ khóa `export` để làm cho biến, hàm, class, ... có sẵn cho các mô-đun khác sử dụng.

*   **Xuất riêng lẻ từng thành phần:** Đặt `export` trước khai báo.
    ```javascript
    // file: math.js

    export const PI = 3.14159; // Xuất một hằng số

    export function cong(a, b) { // Xuất một hàm
        return a + b;
    }

    export function tru(a, b) {
        return a - b;
    }

    export class MayTinh { // Xuất một class
        tinhNhac(a, b, p) {
            return a * b / p; // Một phép tính ngẫu nhiên :D
        }
    }
    ```
*   **Xuất cùng lúc nhiều thành phần (cuối file):** Dùng `{}`.
    ```javascript
    // file: utils.js

    const defaultLimit = 100;
    function processData(data) {
        // ... xử lý
        console.log("Đã xử lý dữ liệu.");
    }
    class Logger { /* ... */ }

    export { defaultLimit, processData, Logger }; // Xuất các thành phần đã khai báo trước đó
    ```

*   **Xuất với tên khác (renaming during export):** Dùng `as`.
    ```javascript
    // file: config.js
    const secretKey = "supersecret";
    const dbPassword = "password123"; // Tên biến không thân thiện lắm để xuất

    export {
        secretKey as apiSecretKey, // Xuất secretKey dưới tên apiSecretKey
        dbPassword // Vẫn xuất với tên gốc (hoặc đổi tên luôn cả hai)
    };
    ```

*   **Xuất Mặc định (Default Export):** Mỗi mô-đun có thể có TỐI ĐA một `export default`. Đây thường là thành phần chính hoặc phổ biến nhất của mô-đun đó. Khi nhập, bạn không cần dùng `{}` và có thể đặt tên tùy ý khi nhập.

    ```javascript
    // file: user.js
    const defaultUser = { name: "Khách", isLoggedIn: false }; // Có thể có các thành phần khác

    // Chỉ có thể có một default export trong file
    export default class User { // Xuất class User làm default export
        constructor(name, isLoggedIn = true) {
            this.name = name;
            this.isLoggedIn = isLoggedIn;
        }
        sayHello() { console.log(`Chào, ${this.name}!`); }
    }
    // export default defaultUser; // Lỗi: chỉ được có 1 default export
    ```
    *Lưu ý:* Bạn có thể export default cả hàm, object, biến... chứ không riêng gì class. Cú pháp `export default myVariable;` hoặc `export default function() { ... }` (anonymous default export) cũng hợp lệ.

### ⬅️ Nhập (Import)

Bạn dùng từ khóa `import` để sử dụng các thành phần đã được xuất từ các mô-đun khác. Đường dẫn mô-đun có thể là đường dẫn tương đối (`./myFile.js`, `../utils/helpers.js`) hoặc đường dẫn tuyệt đối (từ thư mục gốc dự án hoặc URL HTTP trong trình duyệt), hoặc tên package khi sử dụng Module Bundlers/Node.js.

*   **Nhập riêng lẻ các thành phần (Named Imports):** Dùng `{}` và tên THẬT (hoặc tên đã đổi khi xuất) của các thành phần.

    ```javascript
    // file: main.js
    // Đường dẫn './math.js' giả định file main.js và math.js nằm trong cùng thư mục
    import { PI, cong } from './math.js';
    // import { tru, cong } from './math.js'; // Nhập nhiều cái cùng lúc
    // import { PI, cong as addFunction } from './math.js'; // Nhập và đổi tên lúc nhập

    console.log(PI); // Output: 3.14159
    console.log(cong(1, 2)); // Output: 3

    // Không thể truy cập các thành phần chưa được export hoặc không import
    // let m = new MayTinh(); // Lỗi: MayTinh không được import
    ```

*   **Nhập tất cả thành phần xuất riêng lẻ vào một object (Namespace Import):** Dùng `* as TenBienChuaTatCa`.

    ```javascript
    // file: main.js
    import * as math from './math.js'; // Nhập tất cả từ math.js vào object 'math'

    console.log(math.PI);      // Output: 3.14159
    console.log(math.cong(1, 2)); // Output: 3
    let may = new math.MayTinh(); // Có thể truy cập Class MayTinh
    ```

*   **Nhập thành phần Xuất Mặc định (Default Import):** KHÔNG dùng `{}`. Tên biến khi nhập (`TenTuDatKhiNhap`) có thể tùy ý.

    ```javascript
    // file: app.js
    // file user.js có export default class User { ... }
    import TenTuyY choTenDefault from './user.js'; // Nhập class User làm biến TenTuyY

    let khach1 = new TenTuyY("Quan");
    khach1.sayHello(); // Output: Chào, Quan!

    // import defaultUser from './user.js'; // Nếu user.js có export default defaultUser;
    // console.log(defaultUser); // Output: { name: "Khách", isLoggedIn: false }
    ```
*   **Nhập cả default và named imports cùng lúc:**

    ```javascript
    // file userMath.js
    // export default class User { ... }; // user.js
    // export { PI, cong } from './math.js'; // math.js

    import DefaultUser, { PI, cong } from './user.js';
    // import TenTuyY, { PI, cong as addFunc } from './user.js'; // Nhập và đổi tên Named Import

    let userMoi = new DefaultUser("Lan");
    userMoi.sayHello();
    console.log(PI);
    console.log(cong(5, 3));
    ```

*   **Chỉ chạy code trong mô-đun (side effects) mà không cần nhập gì:**
    ```javascript
    // file: init.js (chỉ chứa code setup)
    console.log("Mô-đun khởi tạo đã chạy!");

    // Trong một file khác:
    import './init.js'; // Chỉ cần nhập để code trong init.js chạy
    ```

### 🌐 Sử Dụng ES Modules Trong Trình Duyệt

Để trình duyệt hiểu được cú pháp `import`/`export`, bạn cần thêm thuộc tính `type="module"` vào thẻ `<script>`.

```html
<!DOCTYPE html>
<html>
<head>
    <title>Modules Demo</title>
</head>
<body>
    <h1>Xem console để thấy kết quả module</h1>

    <!-- Script type="module" để trình duyệt xử lý cú pháp import/export -->
    <script type="module" src="./main.js"></script>
</body>
</html>
```
*Lưu ý:* Khi chạy trực tiếp trong trình duyệt, đường dẫn import phải là đường dẫn tương đối đầy đủ (bao gồm `.js`). Module không chạy khi mở file HTML trực tiếp (`file:///...`) do giới hạn an ninh CORS (Cross-Origin Resource Sharing) của trình duyệt. Bạn cần chạy một local web server đơn giản để nó hoạt động (ví dụ: dùng VS Code Live Server extension hoặc `http-server` của Node.js).

### 📦 Sử Dụng ES Modules Trong Node.js

Từ các phiên bản Node.js gần đây, ES Modules đã được hỗ trợ mà không cần cờ đặc biệt, nhưng cần thiết lập một trong các cách sau:

1.  Lưu file với đuôi mở rộng `.mjs` thay vì `.js`.
    `import { readFile } from 'fs'; // Import từ module tích hợp của Node.js`
2.  Trong file `package.json` của dự án, thêm dòng `"type": "module"`. Khi đó tất cả file `.js` trong dự án (trừ khi có file `package.json` riêng trong thư mục con ghi đè thiết lập này) sẽ được hiểu là ES Modules.

    ```json
    {
      "type": "module",
      "...": "..."
    }
    ```

### 🆚 So Sánh với CommonJS (cũ, Node.js)

Trước khi ES Modules được hỗ trợ rộng rãi, Node.js sử dụng hệ thống module CommonJS với cú pháp `require()` và `module.exports`. Bạn vẫn sẽ thấy cú pháp này trong các dự án Node.js hoặc các thư viện cũ hơn.

```javascript
// CommonJS export (Node.js)
// file: mathCommonJS.js
const PI = 3.14159;
function cong(a, b) { return a + b; }

module.exports = { // Xuất các thành phần
    PI,
    cong
};

// CommonJS import (Node.js)
// file: mainCommonJS.js
const math = require('./mathCommonJS'); // Nhập các thành phần vào biến math

console.log(math.PI);
console.log(math.cong(1, 2));
```
Các Module Bundlers như Webpack, Parcel, Rollup có thể giúp bạn sử dụng cú pháp ES Modules ngay cả khi deploy ra môi trường cũ không hỗ trợ hoặc để đóng gói code hiệu quả hơn.

### 🛠 Luyện Tập

*   Tạo hai file JavaScript: `data.js` và `app.js`.
*   Trong `data.js`, khai báo một hằng số `APP_VERSION` và một hàm `getLogger()`. Export cả hai.
*   Trong `app.js`, import cả `APP_VERSION` và `getLogger()`. In ra `APP_VERSION` và gọi `getLogger()` (hàm này có thể chỉ in ra một dòng text đơn giản).
*   Trong `data.js`, tạo thêm một biến hoặc hàm, nhưng không export nó. Thử import và sử dụng nó trong `app.js` (bạn sẽ thấy lỗi).
*   Chuyển `getLogger()` thành default export trong `data.js` và cập nhật cách import trong `app.js`.
*   (Nâng cao) Cài đặt một local web server đơn giản hoặc dùng tính năng của IDE (ví dụ: Live Server của VS Code), tạo một file `index.html` và nhúng `app.js` bằng `<script type="module" src="app.js"></script>`. Mở file `index.html` qua server và kiểm tra console.

Sử dụng mô-đun là cách thực hành tốt nhất trong phát triển JavaScript hiện đại. Nó giúp tổ chức code của bạn, quản lý các phần phụ thuộc và tránh các vấn đề với Global Scope.

---

Wow! Chúng ta vừa cùng nhau "du hành" qua Scope & Closure (cấu trúc logic bên trong JS), `this` (người bí ẩn hay thay đổi), Destructuring & Spread/Rest (những phép thuật cú pháp ES6+ tiện lợi), Class (xây dựng các thực thể) và Modules (đóng gói code).

Mỗi bài học đều là một mảnh ghép quan trọng, đưa bạn đến gần hơn với việc làm chủ JavaScript và xây dựng những hệ thống phức tạp.

Còn rất nhiều vùng đất mới để khám phá, như:

*   **Lập trình Bất đồng bộ (Asynchronous Programming):** Xử lý các tác vụ tốn thời gian (gọi API, đọc file, hẹn giờ...) mà không làm "đơ" chương trình.
*   **Promises và Async/Await:** Các cách hiện đại để xử lý bất đồng bộ, giúp code sạch sẽ hơn callbacks "chuồng gà".
*   **Xử lý lỗi (Error Handling):** Làm cho chương trình của bạn vững vàng hơn trước những sự cố.
*   **Làm việc sâu hơn với DOM:** Tạo mới, thêm, xóa các phần tử trên trang.
*   **Local Storage & Session Storage:** Lưu trữ dữ liệu nhỏ trên trình duyệt.
*   **Fetching Data (AJAX/Fetch API):** Gửi/nhận dữ liệu từ server.
*   ... và nhiều hơn thế nữa!

