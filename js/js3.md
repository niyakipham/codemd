

## File: 21_event_delegation.md

```markdown
# 👂 Bài 21: Event Delegation - Kỹ thuật xử lý sự kiện thông minh

Ở Bài 9, chúng ta đã học cách thêm trình lắng nghe sự kiện (`addEventListener`) cho từng phần tử DOM. Cách này hoạt động tốt với số lượng nhỏ phần tử. Nhưng nếu bạn có một danh sách dài hàng trăm, hàng nghìn mục (ví dụ: danh sách sản phẩm, comment) và muốn xử lý cùng một sự kiện (như click) cho mỗi mục, việc thêm trình lắng nghe cho từng mục sẽ trở nên RẤT kém hiệu quả:

1.  **Hiệu năng:** Tốn bộ nhớ và thời gian xử lý để tạo và quản lý số lượng lớn trình lắng nghe.
2.  **Code rườm rà:** Viết code lặp đi lặp lại để thêm listener.
3.  **Phần tử thêm sau:** Các phần tử mới được thêm vào DOM sau khi code gắn listener ban đầu chạy sẽ không có trình lắng nghe sự kiện nào.

**Event Delegation** (Ủy quyền sự kiện) là một kỹ thuật tối ưu dựa trên cơ chế **lan truyền sự kiện (event bubbling)** trong DOM để giải quyết những vấn đề này.

### 🤔 Lan Truyền Sự Kiện (Event Bubbling)

Khi một sự kiện xảy ra trên một phần tử DOM (ví dụ: bạn click vào một nút `<button>`), sự kiện đó không chỉ "cháy" tại phần tử đó. Theo mặc định, nó sẽ **lan truyền (bubble up)** lên cây DOM, từ phần tử gốc lên phần tử cha của nó, rồi lên ông, bà nó, cứ thế lên đến tận gốc của DOM (`document` hoặc `window`).

```html
<!-- Cấu trúc lồng nhau -->
<div id="grandparent">
  <div id="parent">
    <button id="child">Click me</button>
  </div>
</div>
```

```javascript
// HTML tương ứng

document.getElementById('grandparent').addEventListener('click', function() {
  console.log('Grandparent clicked!');
});

document.getElementById('parent').addEventListener('click', function() {
  console.log('Parent clicked!');
});

document.getElementById('child').addEventListener('click', function() {
  console.log('Child clicked!');
});

// Khi click vào nút button#child, output sẽ là:
// Child clicked!    (listener trên element gốc chạy trước)
// Parent clicked!   (listener trên element cha chạy tiếp)
// Grandparent clicked! (listener trên element ông/bà chạy cuối)

// Event Capture Phase: Sự kiện lan truyền từ gốc xuống trước (ít dùng trong addEventListener thông thường)
// Event Bubbling Phase: Sự kiện lan truyền từ gốc lên sau (mặc định của addEventListener)
// Bạn có thể điều chỉnh bằng tham số thứ 3 của addEventListener ({ capture: true })
```

Event Delegation tận dụng chính cơ chế Event Bubbling này.

### ✨ Event Delegation hoạt động thế nào?

Thay vì gắn trình lắng nghe cho MỖI phần tử con, bạn chỉ cần gắn **MỘT trình lắng nghe** cho một **phần tử cha chung** (container) của chúng.

Khi một sự kiện xảy ra trên một phần tử con, nó sẽ nổi bọt lên phần tử cha. Trình lắng nghe trên phần tử cha sẽ "bắt" được sự kiện này. Bên trong trình lắng nghe đó, bạn có thể kiểm tra:

1.  **Phần tử NÀO thực sự đã kích hoạt sự kiện?** (Dùng `event.target`)
2.  **Phần tử đó có phải là phần tử mà chúng ta QUAN TÂM để xử lý sự kiện không?** (Ví dụ: là một item trong danh sách, là một nút có class cụ thể)

Dựa vào thông tin này, bạn có thể thực thi logic xử lý tương ứng.

**Ví dụ: Danh sách có nhiều mục**

```html
<!-- file: index.html -->
<!DOCTYPE html>
<html>
<head>
    <title>Event Delegation Demo</title>
    <style>
        #myList li {
            padding: 5px;
            cursor: pointer;
            border: 1px solid #ccc;
            margin-bottom: 2px;
        }
         #myList li:hover {
            background-color: #f0f0f0;
        }
    </style>
</head>
<body>

    <h1>Danh sách vật phẩm</h1>
    <ul id="myList">
        <li>Vật phẩm 1</li>
        <li>Vật phẩm 2</li>
        <li>Vật phẩm 3</li>
        <!-- Các vật phẩm sẽ được thêm vào sau -->
    </ul>
    <button id="addItem">Thêm vật phẩm mới</button>

    <script src="script.js"></script>
</body>
</html>
```

```javascript
// file: script.js

const myList = document.getElementById('myList');
const addItemButton = document.getElementById('addItem');
let itemCount = 3; // Bắt đầu từ 3 vì đã có sẵn 3 mục

// KHÔNG THÊM listener cho từng li riêng lẻ ban đầu

// Sử dụng Event Delegation: Thêm listener cho phần tử cha (ul)
myList.addEventListener('click', function(event) {
    // 'event.target' là phần tử GỐC nơi sự kiện click xảy ra (li, hoặc ul nếu click vào khoảng trống,...)

    // Kiểm tra xem phần tử được click CÓ PHẢI là một thẻ LI hay không
    // Hoặc có phải là một phần tử mà bạn muốn xử lý sự kiện hay không
    if (event.target.tagName === 'LI') {
        console.log("Bạn vừa click vào vật phẩm:");
        console.log(event.target.textContent); // In ra nội dung của LI

        // Làm gì đó với LI được click, ví dụ: đổi màu
        event.target.style.backgroundColor = 'yellow';
    }
    // Nếu click vào chỗ khác trong ul (ví dụ: padding hoặc border), tagName sẽ là UL, không thỏa mãn điều kiện
});


// Thêm chức năng cho nút "Thêm vật phẩm mới"
addItemButton.addEventListener('click', function() {
    itemCount++;
    const newLi = document.createElement('li');
    newLi.textContent = `Vật phẩm ${itemCount}`;
    myList.appendChild(newLi);

    console.log(`Đã thêm "Vật phẩm ${itemCount}".`);
    // Dù là LI mới thêm sau, khi click vào nó, sự kiện vẫn bubble lên UL và được xử lý bởi listener của UL.
});
```
Với Event Delegation, dù bạn thêm bao nhiêu `<li>` mới vào danh sách `#myList` đi chăng nữa, chúng đều TỰ ĐỘNG được xử lý khi click vì chỉ có duy nhất một listener trên `#myList` đang "chờ" sự kiện click nổi bọt lên.

### ✨ Ưu điểm của Event Delegation

*   **Hiệu năng:** Giảm đáng kể số lượng trình lắng nghe sự kiện, tiết kiệm bộ nhớ và CPU.
*   **Đơn giản hóa code:** Code gắn listener chỉ cần viết một lần.
*   **Hỗ trợ phần tử được thêm động:** Các phần tử mới được thêm vào DOM SAU khi trình lắng nghe trên cha được gắn vẫn hoạt động bình thường.
*   **Quản lý dễ hơn:** Dễ dàng xóa hoặc thêm listener khi cần (chỉ cần xử lý listener trên phần tử cha).

### ❗️ Kiểm Tra Loại Phần Tử Mục Tiêu

Có nhiều cách để kiểm tra `event.target` có phải là phần tử bạn muốn hay không:

*   `event.target.tagName === 'TEN_THE_HOA'` (Luôn là chữ hoa, ví dụ 'LI', 'BUTTON') - Tốt cho kiểm tra theo tên thẻ.
*   `event.target.classList.contains('ten-class')` - Tốt cho kiểm tra theo class CSS.
*   `event.target.matches(cssSelector)`: Phương thức mạnh mẽ hơn. Kiểm tra xem `event.target` có khớp với CSS selector được truyền vào hay không. Hữu ích khi selector phức tạp hơn (`.item .title`, `button[data-action="delete"]`).
*   Đi lên cây DOM từ `event.target` để tìm phần tử cha mong muốn (sử dụng `.closest(cssSelector)` - tìm phần tử cha gần nhất khớp với selector). Cách này tốt khi `event.target` có thể là một phần tử NẰM TRONG mục đích của bạn (ví dụ: click vào `<em>` hoặc `<span>` bên trong một `<li>`).

```javascript
// Sử dụng matches()
myList.addEventListener('click', function(event) {
    if (event.target.matches('li')) { // Kiểm tra có khớp selector 'li' không
        console.log("Clicked on an LI:", event.target.textContent);
    } else if (event.target.matches('#addItem')) { // Kiểm tra có phải nút "add item" không
        console.log("Clicked on the Add button!");
        // CẨN THẬN: Nút addItem không nằm trong #myList, sự kiện sẽ bubble lên BODY/HTML/DOCUMENT.
        // Nếu listener này được đặt trên BODY, nó sẽ bắt được.
    }
});

// Sử dụng closest()
// Giả sử cấu trúc là <li data-id="123">... <button class="delete-btn">X</button> ...</li>
myList.addEventListener('click', function(event) {
    const liItem = event.target.closest('li'); // Tìm thẻ LI cha gần nhất của element được click
    if (liItem) {
         console.log("Clicked inside LI with ID:", liItem.dataset.id); // Đọc thuộc tính data-id
        // Nếu click vào nút delete-btn, event.target là nút đó, nhưng closest('li') sẽ trả về LI chứa nút đó.
        // Có thể kiểm tra cụ thể hơn:
        if (event.target.classList.contains('delete-btn')) {
            console.log("Đang xóa mục có ID:", liItem.dataset.id);
            liItem.remove(); // Xóa phần tử LI cha tìm được
        }
    } else {
        console.log("Clicked somewhere in UL, but not inside an LI");
    }
});
```
Phương thức `closest()` rất hữu ích trong Event Delegation vì nó giúp bạn lấy được phần tử "mục tiêu thực sự" của thao tác dựa trên một selector cụ thể, bất kể người dùng click chính xác vào đâu bên trong phần tử đó.

### 🛠 Luyện Tập

*   Tạo một trang HTML có một `<div id="container">` rỗng và một button để thêm các div con mới vào trong container đó (ví dụ: `<div class="box">Box 1</div>`).
*   Sử dụng Event Delegation: Thay vì thêm listener cho từng box mới, hãy thêm MỘT listener click vào `#container`.
*   Trong listener của `#container`, kiểm tra xem `event.target` có class `"box"` hay không. Nếu có, in ra nội dung text của phần tử đó (ví dụ: "Box 1 được click!").
*   Thử thêm nhiều box mới vào container bằng nút, kiểm tra xem việc click vào chúng có hoạt động không.

Event Delegation là một trong những "patterns" quan trọng bạn nên biết khi làm việc với DOM hiệu quả. Nó là chìa khóa để xử lý các danh sách dài và các thành phần giao diện được thêm động!

---

## File: 22_fetch_api.md

```markdown
# 🌐 Bài 22: Fetch API - Liên lạc với Server (HTTP Requests)

Phần lớn các ứng dụng web hiện đại cần giao tiếp với server để lấy hoặc gửi dữ liệu (ví dụ: hiển thị danh sách sản phẩm, đăng bài viết mới, đăng nhập...). JavaScript trong trình duyệt thực hiện điều này bằng cách gửi các yêu cầu **HTTP** đến server. Trước đây, cách phổ biến là dùng đối tượng `XMLHttpRequest` (thường gọi là AJAX). Nhưng kể từ ES6, cách tiếp cận hiện đại và dựa trên Promise là **Fetch API**.

Hãy coi Fetch API là hệ thống truyền tin hiện đại trên phi thuyền của bạn, cho phép bạn gửi tín hiệu (requests) và nhận phản hồi (responses) từ các trạm không gian khác (servers).

### 🤔 HTTP Requests (Yêu cầu HTTP)

Khi trình duyệt của bạn truy cập một trang web hoặc khi JS của bạn sử dụng Fetch/AJAX, nó đang gửi các yêu cầu HTTP đến một địa chỉ (URL). Các yêu cầu này có **phương thức (Method)** xác định loại thao tác:

*   **GET:** Yêu cầu lấy dữ liệu từ server. Dữ liệu yêu cầu (nếu có) nằm trong URL. Không có body trong request.
*   **POST:** Gửi dữ liệu đến server để tạo một tài nguyên mới hoặc thực hiện một hành động có dữ liệu. Dữ liệu được gửi nằm trong body của request.
*   **PUT:** Cập nhật một tài nguyên hiện có trên server. Dữ liệu mới nằm trong body.
*   **DELETE:** Yêu cầu xóa một tài nguyên trên server.
*   **PATCH:** Cập nhật MỘT PHẦN của tài nguyên trên server.
*   Và một số phương thức khác ít dùng hơn.

Server nhận yêu cầu, xử lý và gửi lại một **phản hồi (Response)**, bao gồm:

*   **Status Code:** Mã số báo trạng thái của yêu cầu (ví dụ: 200 OK, 404 Not Found, 500 Internal Server Error, 401 Unauthorized).
*   **Headers:** Thông tin meta về phản hồi (kiểu nội dung, mã hóa, cookie...).
*   **Body:** Dữ liệu thực tế được server trả về (ví dụ: HTML, JSON, XML...).

### ✨ Fetch API

`fetch()` là hàm global trong trình duyệt, nhận một tham số BẮT BUỘC là **URL** mà bạn muốn gửi request tới. Nó nhận một tham số TÙY CHỌN thứ hai là một object chứa các **tùy chọn cấu hình** (phương thức HTTP, headers, body...).

`fetch()` luôn trả về một **Promise**. Promise này sẽ Fulfilled với một đối tượng **`Response`** ngay sau khi server trả về response **HEADERS** (bất kể status code là gì - trừ lỗi mạng). Nếu gặp lỗi mạng (ví dụ: không kết nối được), Promise sẽ bị Rejected.

**Ví dụ GET Request cơ bản:**

```javascript
// Gọi một API endpoint giả định để lấy danh sách hành tinh
const apiURL = 'https://swapi.dev/api/planets/'; // API công khai về Star Wars data

console.log("Đang gửi GET request đến:", apiURL);

fetch(apiURL)
    .then(response => {
        // Promise Fulfilled ngay khi nhận được headers
        console.log("Đã nhận Response.");
        console.log("Status:", response.status); // Mã trạng thái (ví dụ: 200)
        console.log("OK:", response.ok);       // true nếu status là 2xx
        console.log("Headers:", response.headers);

        // Để lấy dữ liệu từ body response (văn bản, JSON...), cần gọi một phương thức khác
        // response.json(), response.text(), response.blob(), ...
        // Các phương thức này cũng trả về Promise!
        return response.json(); // Xử lý response body dưới dạng JSON. Trả về Promise mới
    })
    .then(data => {
        // Đây là bước nhận DỮ LIỆU thực tế sau khi .json() Promise Fulfilled
        console.log("Dữ liệu nhận được (JSON):");
        console.log(data);
        // Bây giờ bạn có thể làm việc với data (object hoặc array)
        if (data && data.results) {
            console.log("Danh sách hành tinh:");
            data.results.forEach(planet => {
                console.log("-", planet.name);
            });
        }
    })
    .catch(error => { // Bắt lỗi mạng HOẶC lỗi xảy ra trong bất kỳ .then() nào phía trước (bao gồm lỗi parse JSON)
        console.error("Có lỗi xảy ra trong quá trình fetch hoặc xử lý:", error);
    })
    .finally(() => {
        console.log("Quá trình fetch kết thúc.");
    });

console.log("Chương trình tiếp tục chạy (bất đồng bộ)...");
```
Ví dụ trên cho thấy tính bất đồng bộ và chuỗi Promise của Fetch. Bước đầu tiên là nhận đối tượng `Response`. Bước thứ hai (thường dùng) là xử lý body của response thành định dạng mong muốn (`.json()`, `.text()`,...).

### 📬 Gửi Yêu cầu POST (hoặc PUT, PATCH)

Để gửi dữ liệu đến server (thường với POST, PUT, PATCH), bạn cần cấu hình các tùy chọn trong tham số thứ hai của `fetch()`:

1.  `method`: Đặt phương thức là `'POST'`, `'PUT'`, v.v. (mặc định là `'GET'`).
2.  `headers`: Thiết lập các headers cần thiết, ví dụ `Content-Type` để báo cho server biết kiểu dữ liệu bạn đang gửi (thường là `'application/json'`).
3.  `body`: Dữ liệu bạn muốn gửi. Thường là chuỗi JSON (`JSON.stringify(yourDataObject)`).

**Ví dụ POST Request:**

```javascript
async function guiDuLieuLenServer(userData) {
    const apiPostURL = 'https://reqres.in/api/users'; // Một API giả để test POST

    console.log("Đang gửi POST request đến:", apiPostURL);
    console.log("Dữ liệu gửi:", userData);

    try {
        const response = await fetch(apiPostURL, {
            method: 'POST', // Đặt phương thức là POST
            headers: {
                // Báo cho server biết body là JSON
                'Content-Type': 'application/json'
            },
            // Chuyển object dữ liệu sang chuỗi JSON
            body: JSON.stringify(userData)
        });

        console.log("Đã nhận Response POST. Status:", response.status);

        // Xử lý trường hợp lỗi HTTP (ví dụ: status 4xx hoặc 5xx)
        // Fetch Promise KHÔNG bị reject với các mã lỗi HTTP!
        // Bạn cần tự kiểm tra response.ok (true cho 2xx) hoặc response.status
        if (!response.ok) {
            const errorMessage = `Lỗi HTTP! status: ${response.status}`;
            const errorResponse = await response.json(); // Thử lấy thông tin lỗi từ body nếu có
             console.error(errorResponse);
             throw new Error(errorMessage); // Ném lỗi để khối catch bắt lấy
        }

        const result = await response.json(); // Đọc response body dưới dạng JSON
        console.log("Kết quả POST thành công:");
        console.log(result); // Server reqres.in trả về object có id và createdAt

        return result; // Trả về kết quả để sử dụng tiếp nếu cần

    } catch (error) { // Bắt lỗi mạng HOẶC lỗi HTTP tự ném ở trên HOẶC lỗi parse JSON
        console.error("Có lỗi xảy ra khi gửi POST request:", error);
        throw error; // Có thể ném lỗi lên trên nữa nếu muốn
    } finally {
        console.log("Quá trình POST kết thúc.");
    }
}

const userMoiCanTao = {
    name: "Morpheus",
    job: "leader"
};

guiDuLieuLenServer(userMoiCanTao); // Gọi hàm async để gửi dữ liệu

console.log("Chương trình tiếp tục chạy trong lúc gửi POST...");
```
**Lưu ý quan trọng về xử lý lỗi Fetch:** `fetch` chỉ `reject` Promise khi có lỗi mạng (không kết nối được, lỗi DNS...). Nó **KHÔNG** tự động reject cho các lỗi HTTP thông thường như 404 (Not Found) hoặc 500 (Internal Server Error). Trong các trường hợp này, Promise vẫn `fulfilled` với một đối tượng `Response`, và bạn phải tự kiểm tra thuộc tính `response.ok` hoặc `response.status` để xác định xem request có thành công về mặt logic hay không.

### ✨ Ưu điểm của Fetch API

*   **API hiện đại, dựa trên Promise:** Giúp dễ dàng làm việc với bất đồng bộ và chaining các request, loại bỏ "Callback Hell".
*   **Cú pháp gọn gàng:** So với `XMLHttpRequest` phức tạp.
*   **Phân tách Headers và Body:** Xử lý headers và body của request/response rõ ràng hơn.
*   **Hỗ trợ Service Workers:** API tiêu chuẩn để tương tác với Service Workers (kỹ thuật Progressive Web App).

### 🛠 Luyện Tập

*   Tìm một API công khai khác (ví dụ: API thời tiết đơn giản, API trả về danh sách các loại tiền tệ...). Sử dụng `fetch()` để gửi GET request đến một endpoint của API đó.
*   Sử dụng `.then()` để xử lý response, kiểm tra `response.ok` hoặc `response.status`. Nếu OK, gọi `response.json()` và in dữ liệu nhận được. Nếu không OK, in ra mã trạng thái lỗi. Dùng `.catch()` để bắt các lỗi mạng hoặc lỗi parse JSON.
*   Mô phỏng việc gửi dữ liệu người dùng: Tạo một đối tượng user (ví dụ: `{ name: "Test User", email: "test@example.com" }`). Sử dụng `fetch()` để gửi POST request đối tượng này đến một endpoint thử nghiệm POST (như `https://jsonplaceholder.typicode.com/posts` hoặc `https://reqres.in/api/users`). Cấu hình `method`, `headers` (Content-Type) và `body` (`JSON.stringify`).
*   (Nâng cao) Chuyển đổi các ví dụ fetch ở trên sang sử dụng cú pháp `async/await` thay vì `.then().catch()`. Dùng `try...catch` để xử lý lỗi.

Fetch API là công cụ không thể thiếu cho mọi lập trình viên web hiện đại. Làm chủ nó giúp ứng dụng của bạn kết nối và tương tác với thế giới bên ngoài thông qua dữ liệu!

---

## File: 23_local_session_storage.md

```markdown
# 💾 Bài 23: Web Storage (Local & Session) - Lưu trữ dữ liệu trên trình duyệt

Ngoài Cookie (cơ chế lưu trữ cũ và có nhiều hạn chế), trình duyệt hiện đại cung cấp **Web Storage API**, bao gồm `localStorage` và `sessionStorage`. Đây là những cách lưu trữ dữ liệu key-value đơn giản trực tiếp trên máy người dùng. Rất hữu ích để lưu trữ thông tin nhỏ gọn trên client-side, giúp ứng dụng ghi nhớ trạng thái hoặc cấu hình giữa các lần truy cập hoặc trong một phiên làm việc.

Hãy tưởng tượng đây là kho lưu trữ cá nhân nhỏ gọn trên bảng điều khiển của phi thuyền bạn, dùng để ghi nhớ các cài đặt ưa thích hoặc nhật ký ngắn hạn.

### 🤔 `localStorage` vs `sessionStorage`

Sự khác biệt chính giữa hai loại storage này nằm ở **thời gian tồn tại** của dữ liệu:

*   **`localStorage`:** Dữ liệu được lưu trữ **vĩnh viễn** (hoặc cho đến khi bị xóa thủ công bởi người dùng hoặc bởi code). Dữ liệu vẫn tồn tại ngay cả khi người dùng đóng trình duyệt và mở lại. Phạm vi lưu trữ là theo **domain** (tất cả các tab hoặc cửa sổ trên cùng một domain có thể truy cập cùng `localStorage`).
*   **`sessionStorage`:** Dữ liệu chỉ tồn tại trong **phiên làm việc** hiện tại của người dùng (phiên kéo dài cho đến khi tab hoặc cửa sổ trình duyệt bị đóng). Dữ liệu sẽ bị xóa khi đóng tab/cửa sổ. Dữ liệu chỉ có thể truy cập được bởi các trang web trên cùng **origin** (protocol + domain + port) VÀ trong cùng **phiên làm việc** đó (mở một tab mới cùng domain sẽ có `sessionStorage` khác).

Cả hai đều có cùng các phương thức và đều lưu trữ dữ liệu dưới dạng **CHUỖI**.

### ✨ Phương Thức Chung (`localStorage` và `sessionStorage`)

API của cả hai đối tượng (`localStorage` và `sessionStorage`) đều giống nhau:

1.  **`setItem(key, value)`:** Lưu trữ một cặp key-value. Key và value sẽ được chuyển thành chuỗi.
2.  **`getItem(key)`:** Lấy giá trị dựa trên key. Trả về chuỗi hoặc `null` nếu key không tồn tại.
3.  **`removeItem(key)`:** Xóa cặp key-value dựa trên key.
4.  **`clear()`:** Xóa **tất cả** dữ liệu khỏi storage hiện tại (localStorage hoặc sessionStorage).
5.  **`key(index)`:** Lấy tên (key) của item tại một chỉ mục cụ thể.
6.  **`length`:** Thuộc tính trả về số lượng item hiện có trong storage.

**Ví dụ với `localStorage`:**

```javascript
// --- Lưu trữ dữ liệu ---
localStorage.setItem('tenNguoiDung', 'Capitan Alpha'); // Lưu chuỗi
localStorage.setItem('diemCao', '5000'); // Lưu số (tự động chuyển thành chuỗi '5000')

console.log("Số item trong localStorage:", localStorage.length); // Output: 2

// Lưu trữ Boolean
localStorage.setItem('daHoanThanhBai1', true); // Lưu boolean (tự động chuyển thành chuỗi 'true')

// **Quan trọng:** Lưu trữ Object/Array
// Không thể lưu trực tiếp Object hoặc Array
const settings = { theme: 'dark', notifications: true };
// localStorage.setItem('caiDat', settings); // Sẽ lưu "[object Object]"!

// Cần chuyển Object/Array sang chuỗi JSON trước khi lưu
localStorage.setItem('caiDatJSON', JSON.stringify(settings));

console.log("Đã lưu các mục vào localStorage.");


// --- Lấy dữ liệu ---
const storedName = localStorage.getItem('tenNguoiDung');
console.log("Tên đã lưu:", storedName); // Output: Capitan Alpha (chuỗi)

const storedScore = localStorage.getItem('diemCao');
console.log("Điểm cao đã lưu:", storedScore, typeof storedScore); // Output: 5000 string (nhớ nó là chuỗi!)
const scoreNumber = parseInt(storedScore); // Cần chuyển đổi nếu muốn dùng làm số
console.log("Điểm cao (dạng số):", scoreNumber, typeof scoreNumber); // Output: 5000 number

const storedBoolean = localStorage.getItem('daHoanThanhBai1');
console.log("Bài 1 hoàn thành?", storedBoolean, typeof storedBoolean); // Output: true string
const booleanValue = storedBoolean === 'true'; // Cần chuyển đổi sang boolean thực sự
console.log("Bài 1 hoàn thành (dạng boolean)?", booleanValue, typeof booleanValue); // Output: true boolean

const storedSettingsJSON = localStorage.getItem('caiDatJSON');
console.log("Cài đặt JSON đã lưu (chuỗi):", storedSettingsJSON); // Output: {"theme":"dark","notifications":true}

// Cần phân tích cú pháp (parse) chuỗi JSON trở lại thành Object/Array khi lấy ra
const loadedSettings = JSON.parse(storedSettingsJSON);
console.log("Cài đặt đã lấy (Object):", loadedSettings); // Output: { theme: 'dark', notifications: true }
console.log("Truy cập thuộc tính:", loadedSettings.theme); // Output: dark


// --- Xóa dữ liệu ---
// localStorage.removeItem('diemCao');
// console.log("Sau khi xóa 'diemCao', số item:", localStorage.length); // Output: 1

// localStorage.clear(); // Xóa tất cả
// console.log("Sau khi xóa ALL, số item:", localStorage.length); // Output: 0

const nonExistentItem = localStorage.getItem('keyKhongTonTai');
console.log("Lấy item không tồn tại:", nonExistentItem); // Output: null


// --- Duyệt qua tất cả các item trong localStorage (Nếu cần) ---
console.log("Các item trong localStorage:");
for (let i = 0; i < localStorage.length; i++) {
    const key = localStorage.key(i); // Lấy key theo chỉ mục
    const value = localStorage.getItem(key); // Lấy giá trị theo key
    console.log(`Key: ${key}, Value: ${value}`);
}

// Cách duyệt khác (không dùng key(index), ít phổ biến cho storage)
// for (let key in localStorage) {
//     // Cẩn thận với các thuộc tính prototype tích hợp của localStorage object
//     if (localStorage.hasOwnProperty(key)) {
//          const value = localStorage.getItem(key); // Phải dùng getItem(key)
//          console.log(`Key: ${key}, Value: ${value}`);
//     }
// }
```

**Ví dụ với `sessionStorage`:** Hoàn toàn tương tự, chỉ cần thay `localStorage` bằng `sessionStorage`. Dữ liệu sẽ bị xóa khi đóng tab/cửa sổ.

### 🚧 Lưu ý và Giới hạn

*   **Chỉ lưu CHUỖI:** Đây là giới hạn quan trọng nhất. Bạn LUÔN cần dùng `JSON.stringify()` khi lưu Object hoặc Array và `JSON.parse()` khi đọc chúng ra.
*   **Kích thước giới hạn:** Dung lượng lưu trữ có giới hạn (thường khoảng 5-10 MB mỗi domain, tùy trình duyệt). Không dùng để lưu trữ dữ liệu lớn (hình ảnh, video...).
*   **Đồng bộ:** API Web Storage là đồng bộ (Synchronous). Khi bạn gọi `setItem` hoặc `getItem`, trình duyệt sẽ thực hiện tác vụ ngay lập tức và có thể "khóa" luồng xử lý chính trong một thời gian ngắn nếu dữ liệu lớn, điều này HIẾM khi là vấn đề với kích thước dữ liệu nhỏ, nhưng cần lưu ý.
*   **Không bảo mật:** Dữ liệu lưu trữ trên client KHÔNG BẢO MẬT. Người dùng có thể xem và chỉnh sửa dễ dàng. Tuyệt đối không lưu thông tin nhạy cảm như mật khẩu, thông tin cá nhân bí mật ở đây. Dữ liệu có thể bị tấn công Cross-Site Scripting (XSS).
*   **Chỉ hoạt động trong môi trường trình duyệt:** Không có sẵn trong Node.js.
*   **Cookie không bị ảnh hưởng:** Web Storage khác biệt với Cookie và thao tác trên Web Storage không ảnh hưởng đến Cookie của domain đó.

### ✨ Khi nào nên dùng?

*   Lưu trữ cài đặt giao diện (chế độ tối/sáng, ngôn ngữ...).
*   Lưu trạng thái ứng dụng (ví dụ: tab nào đang mở, ID của mục đang xem...).
*   Lưu dữ liệu tạm thời giữa các trang trong cùng một phiên (sessionStorage).
*   Lưu dữ liệu cache nhỏ (ví dụ: kết quả tìm kiếm gần đây nhất - cân nhắc thời điểm hết hạn).

### 🛠 Luyện Tập

*   Tạo một trang HTML đơn giản. Thêm một input text và một button. Khi click button, lấy giá trị từ input và lưu vào `localStorage` với một key cố định (ví dụ: 'userInputValue').
*   Khi trang được tải lại, kiểm tra xem có giá trị 'userInputValue' trong `localStorage` không. Nếu có, điền giá trị đó vào input text.
*   Tạo một đối tượng JavaScript đơn giản (ví dụ: thông tin cấu hình nhỏ `{ showWelcome: true, itemCount: 15 }`). Lưu đối tượng này vào `sessionStorage` (nhớ `JSON.stringify`) với key 'myConfig'.
*   Lấy 'myConfig' từ `sessionStorage` (nhớ `JSON.parse`), truy cập một thuộc tính của nó và in ra console. Thử đóng và mở lại tab trình duyệt, xem dữ liệu có còn không (đối với sessionStorage là không).

Web Storage là công cụ tiện lợi để tạo ra trải nghiệm người dùng liền mạch và cá nhân hóa bằng cách ghi nhớ một chút thông tin về họ ngay trên trình duyệt!

---

## File: 24_json.md

```markdown
# 📦 Bài 24: JSON - Ngôn ngữ chung của dữ liệu

Trong thế giới web, khi các ứng dụng (frontend) cần giao tiếp và trao đổi dữ liệu với các server (backend), họ cần một định dạng dữ liệu tiêu chuẩn mà cả hai bên đều hiểu. **JSON (JavaScript Object Notation)** đã nổi lên như là định dạng dữ liệu phổ biến NHẤT cho mục đích này.

Mặc dù tên là JavaScript Object Notation, JSON không chỉ dùng riêng cho JavaScript. Nó là một định dạng văn bản NHẸ VÀ ĐỘC LẬP VỚI NGÔN NGỮ, nhưng cấu trúc của nó RẤT giống với cách biểu diễn đối tượng và mảng trong JavaScript, điều này làm cho JS xử lý JSON cực kỳ dễ dàng và hiệu quả.

Hãy coi JSON như ngôn ngữ "Liên sao" được sử dụng để trao đổi thông tin cấu trúc giữa các tàu vũ trụ khác nhau (các server và client của bạn).

### 🤔 Cấu trúc dữ liệu trong JSON

JSON có cấu trúc dựa trên hai cấu trúc cơ bản từ nhiều ngôn ngữ lập trình:

1.  **Một tập hợp các cặp Tên-Giá trị (Key-Value pairs):** Tương tự như đối tượng trong JavaScript. Trong JSON, được bao bọc bởi dấu ngoặc nhọn `{}`. Khóa (Key) phải là một **chuỗi** (được bao bọc bởi dấu nháy kép `"`) và giá trị (Value) có thể là một trong các kiểu dữ liệu JSON sau.
2.  **Một danh sách có thứ tự các giá trị:** Tương tự như mảng trong JavaScript. Trong JSON, được bao bọc bởi dấu ngoặc vuông `[]`. Các giá trị được phân cách bằng dấu phẩy.

**Các kiểu dữ liệu HỢP LỆ trong JSON:**

*   **Strings:** Chuỗi ký tự, BẮT BUỘC dùng dấu nháy kép `""`.
*   **Numbers:** Số nguyên hoặc số thực.
*   **Booleans:** `true` hoặc `false`.
*   **Arrays:** Một danh sách các giá trị khác (`[ value, value, ... ]`).
*   **Objects:** Một tập hợp các cặp key-value khác (`{ "key": value, ... }`).
*   `null`: Biểu diễn giá trị rỗng.

**Ví dụ về dữ liệu JSON:**

```json
{
  "tenHanhtinh": "Triton",
  "laVeTinh": true,
  "thuocHanhtinh": "Neptune",
  "khoiLuong": 2.147e22,
  "dieuKienSong": null,
  "cacTauThamHiem": [
    {
      "tenTau": "Voyager 2",
      "namDenNoi": 1989,
      "cacCamBien": ["Camera", "Spectrometer"]
    },
    {
      "tenTau": "Triton Observer",
      "namDenNoi": 2045,
      "daHaCanh": false
    }
  ],
  "thongSo": {
    "apSuatKhiQuyen": 1.4,
    "nhietDoBieuKien": -237.15
  }
}
```
**Quan trọng:** JSON KHÔNG HỖ TRỢ: `undefined`, hàm, `Date` (sẽ là chuỗi ISO format), `RegExp`, `Symbol`,... Khi gặp những kiểu này, chúng sẽ bị loại bỏ hoặc chuyển đổi không như ý khi chuyển từ JS Object sang JSON string.

### ✨ Sử dụng JSON trong JavaScript

Đối tượng global `JSON` trong JavaScript cung cấp hai phương thức chính để làm việc với JSON:

1.  **`JSON.parse(jsonString)`:** Chuyển đổi một chuỗi JSON thành một đối tượng hoặc mảng JavaScript. Hữu ích khi nhận dữ liệu JSON từ server (thông qua Fetch API, XMLHttpRequest) hoặc đọc từ Web Storage.

    ```javascript
    const jsonString = '{"ten": "Alpha", "id": 7, "isOnline": true}';
    try {
        const jsObject = JSON.parse(jsonString); // Parse chuỗi JSON
        console.log(jsObject);          // Output: { ten: 'Alpha', id: 7, isOnline: true }
        console.log(jsObject.ten);      // Output: Alpha
        console.log(jsObject.isOnline); // Output: true
    } catch (error) {
        console.error("Lỗi khi parse JSON:", error); // Bắt lỗi nếu chuỗi JSON không hợp lệ
    }


    const jsonArrayString = '[{"id": 1, "name": "Item A"}, {"id": 2, "name": "Item B"}]';
     try {
        const jsArray = JSON.parse(jsonArrayString); // Parse chuỗi JSON (mảng)
        console.log(jsArray);        // Output: [ { id: 1, name: 'Item A' }, { id: 2, name: 'Item B' } ]
        console.log(jsArray[0].name); // Output: Item A
    } catch (error) {
        console.error("Lỗi khi parse JSON mảng:", error);
    }
    ```
    Bạn nên sử dụng `try...catch` khi `JSON.parse` để xử lý trường hợp chuỗi đầu vào không phải là JSON hợp lệ.

2.  **`JSON.stringify(jsValue, replacer, space)`:** Chuyển đổi một đối tượng hoặc mảng JavaScript thành một chuỗi JSON. Hữu ích khi bạn muốn gửi dữ liệu JavaScript đến server (qua Fetch/AJAX) hoặc lưu trữ Object/Array trong Web Storage.

    *   `jsValue`: Giá trị JS (Object, Array, primitive) bạn muốn chuyển đổi.
    *   `replacer` (Tùy chọn): Có thể là một hàm hoặc một mảng chuỗi/số để lọc hoặc biến đổi dữ liệu trước khi stringify.
    *   `space` (Tùy chọn): Số khoảng trắng hoặc một chuỗi để định dạng chuỗi JSON kết quả (làm cho dễ đọc hơn, hữu ích cho debug).

    ```javascript
    const jsObject = {
        shipName: "Voyager",
        speed: 9000,
        captain: { name: "Janeway", rank: "Captain" },
        missions: ["Exploration", "Discovery"],
        isCrewSleeping: false,
        // logFunction: function() { console.log("Log"); }, // Hàm sẽ bị BỎ QUA
        lastLogDate: new Date() // Date object sẽ được chuyển thành chuỗi ISO 8601
    };

    const jsonString = JSON.stringify(jsObject); // Chuyển đổi sang chuỗi JSON
    console.log(jsonString); // Output: {"shipName":"Voyager","speed":9000,"captain":{"name":"Janeway","rank":"Captain"},"missions":["Exploration","Discovery"],"isCrewSleeping":false,"lastLogDate":"2023-10-27T...Z"} (dạng chuỗi không định dạng)

    // Sử dụng 'space' để định dạng
    const prettyJsonString = JSON.stringify(jsObject, null, 2); // Null cho replacer, 2 khoảng trắng để thụt lề
    console.log(prettyJsonString);
    /*
    Output:
    {
      "shipName": "Voyager",
      "speed": 9000,
      "captain": {
        "name": "Janeway",
        "rank": "Captain"
      },
      "missions": [
        "Exploration",
        "Discovery"
      ],
      "isCrewSleeping": false,
      "lastLogDate": "2023-10-27T...Z" // Chuỗi
    }
    */

    // Sử dụng 'replacer' (mảng các key muốn giữ lại)
    const filteredJsonString = JSON.stringify(jsObject, ['shipName', 'speed']);
    console.log(filteredJsonString); // Output: {"shipName":"Voyager","speed":9000} (Chỉ giữ lại các key trong mảng)

    // Sử dụng 'replacer' (hàm) - hàm nhận (key, value)
    const filteredJsonStringWithReplacerFunc = JSON.stringify(jsObject, (key, value) => {
        // Bỏ qua các giá trị là boolean
        if (typeof value === 'boolean') {
            return undefined; // Trả về undefined để bỏ qua cặp key-value này
        }
         // Chuyển đổi số thành chuỗi tiền tệ đơn giản
        if (typeof value === 'number' && key === 'speed') {
             return `~ ${value} ly/giây`;
        }
        return value; // Trả về giá trị gốc cho các trường hợp khác
    }, 2);
    console.log(filteredJsonStringWithReplacerFunc);
     /*
    Output:
    {
      "shipName": "Voyager",
      "speed": "~ 9000 ly/giây", // Đã chuyển đổi
      "captain": {
        "name": "Janeway",
        "rank": "Captain"
      },
      "missions": [
        "Exploration",
        "Discovery"
      ],
      // "isCrewSleeping": false, // Đã bị bỏ qua vì là boolean
      "lastLogDate": "2023-10-27T...Z"
    }
    */

     // JSON.stringify với giá trị undefined, function, Symbol sẽ bị bỏ qua (không ném lỗi)
     const objWithSpecialTypes = {
         a: 1,
         b: undefined, // Sẽ bị bỏ qua
         c: function() {}, // Sẽ bị bỏ qua
         d: Symbol('s') // Sẽ bị bỏ qua
     };
     console.log(JSON.stringify(objWithSpecialTypes)); // Output: {"a":1}
    ```

### 🌟 Các Trường Hợp Sử Dụng Phổ Biến của JSON

*   **Giao tiếp Client-Server (APIs):** Định dạng chuẩn cho Request/Response body trong RESTful APIs.
*   **Lưu trữ dữ liệu (Web Storage, File, Database):** Dữ liệu có cấu trúc đơn giản.
*   **File cấu hình:** Các file cấu hình (`.json`) trong dự án phần mềm (ví dụ: `package.json` của Node.js).

### 🛠 Luyện Tập

*   Tạo một đối tượng JavaScript biểu diễn thông tin cá nhân (tên, tuổi, địa chỉ, sở thích - là một mảng).
*   Sử dụng `JSON.stringify()` để chuyển đổi đối tượng này thành một chuỗi JSON và in ra console. Thử sử dụng tham số `space` để làm cho chuỗi JSON dễ đọc hơn.
*   Viết một hàm JavaScript nhận một chuỗi (giả định là JSON). Bên trong hàm đó, sử dụng `JSON.parse()` trong khối `try...catch` để chuyển đổi chuỗi thành đối tượng JS. Nếu thành công, trả về đối tượng đó. Nếu thất bại, in ra lỗi và trả về `null` hoặc một giá trị báo hiệu lỗi.
*   Kiểm tra hàm vừa viết với một chuỗi JSON hợp lệ và một chuỗi KHÔNG hợp lệ (ví dụ: thiếu dấu nháy kép ở key, thừa dấu phẩy ở cuối).

JSON là định dạng "ngôn ngữ" của Internet. Thành thạo việc chuyển đổi giữa JSON và các kiểu dữ liệu JavaScript là điều kiện tiên quyết để làm việc hiệu quả với backend APIs và các hệ thống lưu trữ dữ liệu!

---

## File: 25_advanced_array_methods.md

```markdown
# ⚡ Bài 25: Các Phương Thức Mảng Nâng Cao - Xử lý dữ liệu kiểu Functional

Bạn đã biết các phương thức cơ bản của Mảng như `push`, `pop`, `shift`, `unshift`, `splice`, `slice`. Bây giờ, chúng ta sẽ khám phá những phương thức mạnh mẽ và cực kỳ phổ biến trong JavaScript hiện đại (đặc biệt là từ ES5/ES6+), giúp bạn làm việc với mảng theo phong cách lập trình **hàm (Functional Programming)**.

Các phương thức này giúp code gọn gàng hơn, dễ đọc hơn và thường tránh được việc phải tự quản lý vòng lặp phức tạp. Chúng thường nhận một hàm callback để áp dụng logic cho từng phần tử hoặc toàn bộ mảng.

Hãy coi những phương thức này như các "đội hình" tự động cho các tác vụ xử lý dữ liệu trên phi đội tàu của bạn: đội dò quét (`filter`), đội biến đổi (`map`), đội tổng hợp (`reduce`), v.v.

### map `array.map()` - Biến đổi từng phần tử

Phương thức `map()` tạo một **mảng MỚI** bằng cách áp dụng một hàm callback cho **MỖI phần tử** của mảng gốc. Nó không thay đổi mảng gốc.

*   Callback nhận 3 đối số (thường chỉ dùng đối số đầu tiên): `item`, `index`, `array`.
*   Giá trị mà callback trả về sẽ là phần tử tương ứng trong mảng mới.

```javascript
const speedsKmS = [3000, 5000, 1200, 8000]; // Tốc độ theo Km/giây

// Chuyển đổi tốc độ sang tốc độ ánh sáng (Khoảng 299792 Km/s)
// Tao một mảng mới chứa tốc độ tương đối
const speedsLightUnits = speedsKmS.map(function(speed) {
    return speed / 299792;
});

// Với Arrow Function ngắn gọn hơn:
const speedsLightUnitsArrow = speedsKmS.map(speed => speed / 299792);

console.log("Tốc độ gốc:", speedsKmS);         // Output: [3000, 5000, 1200, 8000] (Không thay đổi)
console.log("Tốc độ theo ánh sáng:", speedsLightUnits); // Output: [0.0100069..., 0.016678..., ...]

const names = ["alpha", "beta", "gamma"];
const capitalizedNames = names.map(name => name.charAt(0).toUpperCase() + name.slice(1));
console.log("Tên viết hoa chữ cái đầu:", capitalizedNames); // Output: ["Alpha", "Beta", "Gamma"]

// map với index
const indexedSpeeds = speedsKmS.map((speed, index) => `Vật phẩm ${index}: ${speed} km/s`);
console.log("Tốc độ theo index:", indexedSpeeds); // Output: ["Vật phẩm 0: 3000 km/s", ...]
```
`map()` là công cụ không thể thiếu khi bạn cần "ánh xạ" một mảng dữ liệu sang một mảng dữ liệu mới có cấu trúc khác hoặc các giá trị đã biến đổi.

### filter `array.filter()` - Lọc các phần tử

Phương thức `filter()` tạo một **mảng MỚI** chứa **chỉ** các phần tử từ mảng gốc mà thỏa mãn điều kiện kiểm tra do hàm callback cung cấp. Nó không thay đổi mảng gốc.

*   Callback nhận 3 đối số: `item`, `index`, `array`.
*   Callback **phải** trả về `true` hoặc `false`.
*   Nếu callback trả về `true` cho một phần tử, phần tử đó sẽ được đưa vào mảng mới. Nếu `false`, nó bị loại bỏ.

```javascript
const sensorReadings = [10, -5, 120, 5, 80, -15, 50]; // Các chỉ số từ cảm biến

// Lọc chỉ lấy các chỉ số dương
const positiveReadings = sensorReadings.filter(function(reading) {
    return reading >= 0; // Giữ lại nếu giá trị >= 0
});

// Với Arrow Function:
const positiveReadingsArrow = sensorReadings.filter(reading => reading >= 0);

console.log("Các chỉ số gốc:", sensorReadings);   // Output: [10, -5, 120, 5, 80, -15, 50] (Không thay đổi)
console.log("Các chỉ số dương:", positiveReadings); // Output: [10, 120, 5, 80, 50]

// Lọc các objects trong mảng
const items = [{id: 1, active: true}, {id: 2, active: false}, {id: 3, active: true}];
const activeItems = items.filter(item => item.active); // Giữ lại item nếu thuộc tính active là true
console.log("Các item đang hoạt động:", activeItems); // Output: [ { id: 1, active: true }, { id: 3, active: true } ]
```
`filter()` được sử dụng rộng rãi khi bạn cần trích xuất một tập con dữ liệu từ một mảng dựa trên một tiêu chí cụ thể.

### reduce `array.reduce()` - Tổng hợp/Thu gọn mảng

Phương thức `reduce()` thực thi một hàm callback (gọi là **reducer function**) trên **từng phần tử** của mảng, từ trái sang phải, để "thu gọn" mảng về một **giá trị duy nhất**. Giá trị duy nhất này có thể là một số (tổng, tích), một chuỗi, một đối tượng, một mảng khác, hay bất kỳ kiểu dữ liệu nào.

*   Callback (reducer) nhận 4 đối số: `accumulator`, `currentItem`, `index`, `array`.
    *   `accumulator`: Giá trị được tích lũy qua mỗi lần lặp. Đây là kết quả của lần gọi callback TRƯỚC đó, hoặc `initialValue` (nếu cung cấp) ở lần lặp đầu tiên.
    *   `currentItem`: Phần tử hiện tại của mảng đang được xử lý.
    *   `index` (Tùy chọn): Chỉ mục của phần tử hiện tại.
    *   `array` (Tùy chọn): Mảng gốc đang được duyệt.
*   Phương thức `reduce()` nhận một tham số TÙY CHỌN thứ hai là `initialValue` (giá trị khởi tạo) cho `accumulator`. Nếu không cung cấp, `accumulator` ở lần lặp đầu tiên sẽ là phần tử ĐẦU TIÊN của mảng, và `currentItem` sẽ là phần tử THỨ HAI. **NÊN** luôn cung cấp `initialValue` để code dễ hiểu và tránh lỗi với mảng rỗng hoặc mảng có 1 phần tử.

**Ví dụ tính tổng:**

```javascript
const numbers = [1, 2, 3, 4, 5];

// Tính tổng các số
const sum = numbers.reduce(function(accumulator, currentNumber) {
    console.log(`Accumulator: ${accumulator}, Current Number: ${currentNumber}`);
    return accumulator + currentNumber; // Trả về giá trị tích lũy cho lần lặp tiếp theo
}, 0); // Giá trị khởi tạo ban đầu cho accumulator là 0

console.log("Tổng của mảng:", sum); // Output: Tổng của mảng: 15

// Với Arrow Function và cú pháp gọn hơn:
const sumArrow = numbers.reduce((acc, current) => acc + current, 0);
console.log("Tổng (Arrow):", sumArrow); // Output: 15
```

**Ví dụ thu gọn mảng objects thành một object duy nhất:**

```javascript
const objects = [{ key: 'a', value: 1 }, { key: 'b', value: 2 }, { key: 'c', value: 3 }];

// Chuyển đổi mảng objects thành một object { a: 1, b: 2, c: 3 }
const resultObject = objects.reduce((accumulator, currentItem) => {
    // Ở mỗi bước, thêm cặp key-value từ currentItem vào accumulator object
    accumulator[currentItem.key] = currentItem.value;
    return accumulator; // Trả về object accumulator
}, {}); // Giá trị khởi tạo là một object rỗng {}

console.log("Mảng objects thu gọn thành object:", resultObject); // Output: { a: 1, b: 2, c: 3 }
```

**Ví dụ đếm tần suất xuất hiện:**

```javascript
const fruits = ["apple", "banana", "apple", "orange", "banana", "apple"];

const fruitCounts = fruits.reduce((accumulator, currentFruit) => {
    // Kiểm tra xem loại quả hiện tại đã có trong object đếm chưa
    if (accumulator[currentFruit]) {
        accumulator[currentFruit]++; // Tăng số đếm lên 1
    } else {
        accumulator[currentFruit] = 1; // Lần đầu tiên thấy loại quả này, đặt số đếm là 1
    }
    return accumulator; // Trả về object đếm được cập nhật
}, {}); // Giá trị khởi tạo là một object rỗng {}

console.log("Tần suất xuất hiện các loại quả:", fruitCounts); // Output: { apple: 3, banana: 2, orange: 1 }
```
`reduce()` cực kỳ linh hoạt. Nó có thể làm hầu hết mọi thứ mà `map()` và `filter()` làm (nhưng code có thể phức tạp hơn) và còn làm được nhiều việc khác nữa. Nó đòi hỏi chút thời gian để làm quen nhưng rất mạnh mẽ.

### find `array.find()` / `array.findIndex()`

*   `find()`: Trả về **phần tử ĐẦU TIÊN** trong mảng thỏa mãn điều kiện do hàm callback cung cấp. Trả về `undefined` nếu không tìm thấy phần tử nào thỏa mãn. Callback giống `filter`.
*   `findIndex()`: Trả về **CHỈ MỤC ĐẦU TIÊN** trong mảng thỏa mãn điều kiện. Trả về `-1` nếu không tìm thấy.

```javascript
const scientists = [{ name: "Einstein", field: "Physics" }, { name: "Curie", field: "Chemistry" }, { name: "Newton", field: "Physics" }];

const firstPhysicist = scientists.find(person => person.field === "Physics");
console.log("Nhà vật lý đầu tiên:", firstPhysicist); // Output: { name: "Einstein", field: "Physics" }

const firstChemistIndex = scientists.findIndex(person => person.field === "Chemistry");
console.log("Chỉ mục nhà hóa học đầu tiên:", firstChemistIndex); // Output: 1

const firstBiologist = scientists.find(person => person.field === "Biology");
console.log("Nhà sinh vật học đầu tiên:", firstBiologist); // Output: undefined
```

### some `array.some()` / `array.every()`

*   `some()`: Kiểm tra xem **ít nhất một** phần tử trong mảng có thỏa mãn điều kiện hay không. Trả về `true` NGAY LẬP TỨC khi tìm thấy phần tử thỏa mãn, hoặc `false` nếu duyệt hết mảng mà không tìm thấy. Callback trả về `true`/`false`.
*   `every()`: Kiểm tra xem **TẤT CẢ** các phần tử trong mảng có thỏa mãn điều kiện hay không. Trả về `false` NGAY LẬP TỨC khi tìm thấy một phần tử KHÔNG thỏa mãn, hoặc `true` nếu duyệt hết mảng mà tất cả đều thỏa mãn. Callback trả về `true`/`false`.

```javascript
const crewTemperatures = [36.5, 37.0, 38.1, 36.8, 37.2]; // Nhiệt độ cơ thể

const hasFever = crewTemperatures.some(temp => temp > 38);
console.log("Có ai bị sốt không?", hasFever); // Output: true (vì có 38.1)

const allHealthy = crewTemperatures.every(temp => temp <= 37.5);
console.log("Tất cả đều khỏe mạnh?", allHealthy); // Output: false (vì có 38.1)

const allValid = crewTemperatures.every(temp => typeof temp === 'number');
console.log("Tất cả chỉ số đều là số?", allValid); // Output: true
```

### forEach `array.forEach()` (Đã nhắc, nhưng quan trọng để phân biệt)

Nhắc lại, `forEach()` thực thi một hàm callback cho MỖI phần tử. Khác với `map`, `filter`, `reduce`, `forEach` **KHÔNG trả về giá trị** (thực tế trả về `undefined`). Nó chỉ dùng để lặp và thực hiện tác vụ với mỗi phần tử (ví dụ: in ra, sửa đổi bên ngoài, v.v.) mà không tạo ra mảng mới.

```javascript
const messages = ["Scan complete.", "No anomalies found.", "Proceeding to next sector."];
messages.forEach(message => console.log("Log:", message)); // Chỉ thực thi side effect (in ra console)
```

### ✨ Lựa Chọn Phương Thức Phù Hợp

*   Cần biến đổi mảng gốc thành mảng mới có cùng số phần tử nhưng giá trị khác? → Dùng **`map()`**.
*   Cần tạo mảng mới chứa chỉ các phần tử từ mảng gốc thỏa mãn điều kiện? → Dùng **`filter()`**.
*   Cần tính tổng hợp một giá trị duy nhất từ mảng (tổng, đếm, object tổng kết...)? → Dùng **`reduce()`**.
*   Cần tìm phần tử đầu tiên thỏa mãn điều kiện? → Dùng **`find()`**.
*   Cần tìm chỉ mục của phần tử đầu tiên thỏa mãn điều kiện? → Dùng **`findIndex()`**.
*   Cần kiểm tra ít nhất một phần tử có thỏa mãn điều kiện không? → Dùng **`some()`**.
*   Cần kiểm tra tất cả các phần tử có thỏa mãn điều kiện không? → Dùng **`every()`**.
*   Chỉ cần lặp qua các phần tử và thực hiện tác vụ mà không tạo mảng mới hay thu gọn? → Dùng **`forEach()`** hoặc vòng lặp `for...of` / `for` truyền thống.

### 🛠 Luyện Tập

*   Tạo một mảng các số. Sử dụng `map()` để trả về một mảng mới mà mỗi số trong đó đã được nhân đôi.
*   Sử dụng `filter()` trên mảng gốc đó để trả về một mảng mới chỉ chứa các số lớn hơn 10.
*   Sử dụng `reduce()` trên mảng gốc để tính trung bình cộng của tất cả các số.
*   Tạo một mảng các đối tượng (ví dụ: danh sách phi hành đoàn với tên và chức vụ). Sử dụng `find()` để tìm đối tượng của phi hành đoàn có chức vụ là "Captain".
*   Sử dụng `some()` để kiểm tra xem có bất kỳ ai trong phi hành đoàn có chức vụ là "Doctor" không.

Làm quen và thành thạo các phương thức mảng nâng cao này là một dấu hiệu rõ ràng của việc bạn đang chuyển đổi sang tư duy lập trình hiện đại hơn trong JavaScript. Chúng sẽ làm cho code của bạn mạnh mẽ, biểu đạt tốt và thường là hiệu quả hơn!

---

