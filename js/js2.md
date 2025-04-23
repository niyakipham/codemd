

## File: 16_async_callbacks.md

```markdown
# ⏱️ Bài 16: Lập trình Bất đồng bộ (Asynchronous JS) & Callbacks

Cho đến nay, chúng ta chủ yếu làm việc với các đoạn code chạy theo thứ tự từ trên xuống dưới, từng dòng một. Đây là lập trình **Đồng bộ (Synchronous)**. Tuyệt vời khi mọi thứ diễn ra nhanh chóng.

Nhưng trong thế giới thực của web, có những tác vụ mất thời gian, ví dụ:

*   Đọc dữ liệu từ database hoặc server qua mạng (HTTP requests).
*   Đọc file từ đĩa cứng.
*   Thực thi các tác vụ phức tạp cần nhiều tài nguyên (video processing).
*   Đợi người dùng tương tác (bấm nút, gõ phím...).
*   Đặt hẹn giờ (`setTimeout`, `setInterval`).

Nếu sử dụng mô hình đồng bộ cho các tác vụ này, chương trình của bạn sẽ bị "đóng băng" (blocking) cho đến khi tác vụ hoàn thành. Tưởng tượng trình duyệt bị đơ cứng chỉ vì nó đang chờ dữ liệu từ server! Thật kinh khủng phải không? 🥶

Để tránh điều này, JavaScript sử dụng mô hình **Bất đồng bộ (Asynchronous)**.

### 🤔 Bất đồng bộ hoạt động thế nào?

Với bất đồng bộ, khi gặp một tác vụ "đợi chờ" (như gọi API), JavaScript KHÔNG DỪNG LẠI để chờ nó hoàn thành. Thay vào đó, nó gửi tác vụ đó đi để xử lý ở chế độ nền (ví dụ: nhờ trình duyệt xử lý yêu cầu mạng, hoặc đặt một timer) và **tiếp tục thực thi các dòng code tiếp theo**.

Khi tác vụ bất đồng bộ hoàn thành, JavaScript sẽ thực hiện một "thao tác nào đó" mà bạn đã chỉ định từ trước.

Cơ chế xử lý bất đồng bộ trong JS liên quan đến Event Loop, Call Stack, Callback Queue và Web APIs/Node APIs. Đây là kiến thức nâng cao hơn (đáng để tìm hiểu sau này), nhưng về mặt sử dụng, có vài cách để quản lý luồng bất đồng bộ: Callbacks (cũ), Promises (hiện đại), và Async/Await (hiện đại và dễ đọc nhất).

Bài này chúng ta bắt đầu với cách "cũ nhưng nền tảng": **Callbacks**.

### 👋 Callbacks là gì?

**Callback Function** là một hàm được truyền làm đối số cho một hàm khác, và hàm đó sẽ thực thi callback function này vào một thời điểm **nào đó trong tương lai**, sau khi hoàn thành công việc của nó (thường là một tác vụ bất đồng bộ).

**Ví dụ đơn giản với Hẹn giờ:**

Hàm `setTimeout` là một hàm bất đồng bộ kinh điển. Nó nhận một callback function và một khoảng thời gian (milliseconds). Hàm callback sẽ được thực thi sau khoảng thời gian đó.

```javascript
console.log("Bắt đầu công việc...");

setTimeout(function() { // Đây là hàm callback
    console.log("Tác vụ hẹn giờ hoàn thành sau 2 giây!");
}, 2000); // Chờ 2000 milliseconds = 2 giây

console.log("Kết thúc phần đồng bộ.");
console.log("Code này chạy NGAY LẬP TỨC, không chờ setTimeout.");

// Output thứ tự sẽ là:
// Bắt đầu công việc...
// Kết thúc phần đồng bộ.
// Code này chạy NGAY LẬP TỨC, không chờ setTimeout.
// (Chờ 2 giây)
// Tác vụ hẹn giờ hoàn thành sau 2 giây!
```
Như bạn thấy, JS không dừng lại chờ `setTimeout`. Nó đặt lệnh hẹn giờ, rồi đi tiếp. 2 giây sau, callback được đưa vào hàng đợi và thực thi khi Event Loop rảnh rỗi.

**Ví dụ về xử lý Event (đã thấy qua):**

Các hàm xử lý sự kiện DOM cũng là Callbacks. Khi bạn click vào nút, hàm callback bạn truyền vào `addEventListener` mới được thực thi.

```javascript
// Giả sử có một nút <button id="myBtn">
const myButton = document.getElementById('myBtn');

myButton.addEventListener('click', function(event) { // Đây là hàm callback
    console.log("Nút đã được click!");
    // Code xử lý khi nút được click
});

console.log("Chờ bạn click...");
```
Code "Chờ bạn click..." chạy đồng bộ. Hàm callback chỉ chờ sự kiện 'click' xảy ra mới chạy.

### 🌐 Callbacks trong Tác vụ IO/Network (Mô phỏng)

Trong các tình huống thực tế hơn như lấy dữ liệu từ server, mô hình callback trông như thế này (đây là mô phỏng cách các thư viện hoặc API cũ hơn hoạt động):

```javascript
function layDuLieuTuServer(url, successCallback, errorCallback) {
    console.log(`Đang gửi yêu cầu đến ${url}...`);

    // **Giả lập** tác vụ network mất thời gian
    setTimeout(function() {
        const data = { id: 1, name: "Dữ liệu hành tinh X" }; // Dữ liệu giả định nhận được

        // Giả định yêu cầu thành công sau 3 giây
        const success = Math.random() > 0.2; // 80% thành công

        if (success) {
            console.log("Yêu cầu thành công!");
            successCallback(data); // Gọi callback xử lý thành công
        } else {
            console.log("Yêu cầu thất bại!");
            errorCallback(new Error("Không thể kết nối server")); // Gọi callback xử lý lỗi
        }
    }, 3000); // Mất 3 giây để "nhận" dữ liệu
}

console.log("Chuẩn bị lấy dữ liệu...");

layDuLieuTuServer("http://galaxy-api.com/planets/1",
    function(data) { // Success Callback
        console.log("Đã nhận dữ liệu:");
        console.log(data);
        // Làm gì đó với data... ví dụ, lấy thêm dữ liệu khác dựa trên data này
        // ---> Bắt đầu hình thành "Callback Hell"!
    },
    function(error) { // Error Callback
        console.log("Có lỗi xảy ra:");
        console.error(error);
        // Xử lý lỗi...
    }
);

console.log("Chương trình tiếp tục chạy...");
```
Trong ví dụ này, `layDuLieuTuServer` không trả về dữ liệu ngay lập tức. Nó nhận hai hàm callback: một để xử lý khi thành công và một khi thất bại. Sau khi tác vụ giả định 3 giây hoàn thành, nó gọi một trong hai callback đó. Code SAU khi gọi `layDuLieuTuServer` vẫn chạy ngay, chứng tỏ tính bất đồng bộ.

### 😈 Callback Hell (Kim Tự Tháp Tử Thần)

Khi bạn có nhiều tác vụ bất đồng bộ phụ thuộc lẫn nhau, bạn phải gọi các callback lồng nhau bên trong các callback khác. Cấu trúc code trở nên thụt lề sâu và khó đọc, khó hiểu, và đặc biệt là khó xử lý lỗi. Đây là hiện tượng nổi tiếng được gọi là **Callback Hell** hoặc "Kim tự tháp tử thần" (Pyramid of Doom).

```javascript
layDuLieuUser("user/1", function(user) {
    layDuLieuPosts(user.id, function(posts) {
        layCommentsChoPost(posts[0].id, function(comments) {
            layLikesChoComment(comments[0].id, function(likes) {
                console.log("Cuối cùng đã có đủ dữ liệu:", likes);
                // Tiếp tục lồng nếu còn tác vụ bất đồng bộ nữa...
            }, function(err) { console.error(err); }); // Xử lý lỗi like
        }, function(err) { console.error(err); }); // Xử lý lỗi comments
    }, function(err) { console.error(err); }); // Xử lý lỗi posts
}, function(err) { console.error(err); }); // Xử lý lỗi user
```
Rõ ràng code này rất khó đọc và quản lý, đặc biệt là phần xử lý lỗi phải lặp đi lặp lại.

Callback Hell chính là động lực thúc đẩy sự ra đời của **Promises** và **Async/Await**, những kỹ thuật hiện đại hơn để xử lý bất đồng bộ một cách dễ đọc và dễ quản lý.

### 🛠 Luyện Tập

*   Sử dụng `setTimeout` để in ra một tin nhắn sau 3 giây.
*   Sử dụng `setInterval` để in ra một tin nhắn mỗi 1 giây, và dùng `clearInterval` sau 5 lần lặp (sử dụng một biến đếm) để dừng lại.
*   Mô phỏng một tác vụ bất đồng bộ đơn giản nhận một callback, ví dụ: một hàm `docDuLieuGianLan(callback)` in ra "Đang đọc..." rồi dùng `setTimeout` để gọi callback sau 1 giây, truyền vào một chuỗi "Dữ liệu đã đọc".
*   Thử tạo một ví dụ Callback Hell nhỏ với 2-3 cấp lồng nhau của các tác vụ bất đồng bộ giả lập (dùng `setTimeout`).

Hiểu Callback là nền tảng vì Promises và Async/Await cuối cùng cũng xây dựng dựa trên nó (Promises "bao bọc" các callback, Async/Await làm cú pháp để Promises trông giống đồng bộ hơn). Chúc bạn vượt qua cửa ải Callback Hell để sẵn sàng cho Promise nhé!

---

## File: 17_promises.md

```markdown
# 🤝 Bài 17: Promises - Lời hứa cho Tương lai (ES6+)

Như chúng ta đã thấy, Callback Hell khiến code bất đồng bộ trở nên phức tạp và khó bảo trì. **Promises** (Lời hứa) ra đời trong ES6 như một giải pháp tiêu chuẩn và có cấu trúc hơn để xử lý bất đồng bộ.

Một Promise là một đối tượng biểu diễn kết quả cuối cùng của một thao tác bất đồng bộ. Thay vì trả về kết quả ngay lập tức hoặc yêu cầu bạn cung cấp callback "ngay tại chỗ", Promise trả về một "lời hứa" rằng thao tác đó sẽ hoàn thành (hoặc thất bại) vào một thời điểm nào đó trong tương lai và khi đó, nó sẽ gọi hàm callback TẠI MỘT NƠI KHÁC.

Hãy nghĩ về Promise như việc bạn đặt hàng online: Khi bạn đặt hàng, bạn nhận được một **phiếu xác nhận đơn hàng** (đối tượng Promise). Bạn không nhận được sản phẩm ngay. Sau này, dựa trên phiếu xác nhận đó, bạn sẽ nhận được **sản phẩm** (nếu thành công) hoặc **hoàn tiền/thông báo lỗi** (nếu thất bại). Phiếu xác nhận này cho phép bạn "theo dõi" và chỉ định hành động cụ thể cho cả hai trường hợp.

### 🚦 Trạng Thái (State) của Promise

Một Promise luôn ở một trong ba trạng thái:

1.  **Pending (Đang chờ):** Trạng thái ban đầu, tác vụ bất đồng bộ chưa hoàn thành hoặc thất bại.
2.  **Fulfilled (Đã hoàn thành/Thành công):** Tác vụ hoàn thành VÀ thành công. Kết quả được trả về (resolved with a value).
3.  **Rejected (Đã thất bại):** Tác vụ hoàn thành VÀ thất bại. Một lý do (error) được trả về (rejected with a reason).

Một Promise ở trạng thái Fulfilled hoặc Rejected được coi là đã **Settled** (đã định đoạt) hoặc **Resolved** (từ này hơi gây nhầm lẫn vì đôi khi cũng dùng để chỉ Fulfilled, nhưng hiểu Settled là an toàn nhất). Từ Pending sang Settled là chuyển đổi **một chiều**, không thể thay đổi trạng thái sau khi đã Settled.

### ⚙️ Tạo Một Promise

Bạn có thể tạo một Promise mới bằng constructor `new Promise()`. Constructor này nhận một hàm (gọi là **executor function**) làm đối số. Hàm executor này nhận hai tham số là hai hàm callback do JavaScript cung cấp:

*   `resolve(value)`: Gọi khi tác vụ bất đồng bộ thành công. Truyền giá trị kết quả vào đây. Điều này sẽ chuyển Promise sang trạng thái **Fulfilled**.
*   `reject(error)`: Gọi khi tác vụ bất đồng bộ thất bại. Truyền đối tượng Error hoặc lý do thất bại vào đây. Điều này sẽ chuyển Promise sang trạng thái **Rejected**.

```javascript
const viDuPromise = new Promise((resolve, reject) => {
    // Mô phỏng một tác vụ bất đồng bộ, ví dụ: đợi 2 giây rồi thành công
    console.log("Đang thực thi tác vụ trong Promise...");

    const success = true; // Giả lập thành công

    setTimeout(() => {
        if (success) {
            const ketQua = "Dữ liệu đã được xử lý!";
            console.log("Tác vụ thành công, gọi resolve...");
            resolve(ketQua); // Thành công -> gọi resolve với kết quả
        } else {
            const loi = new Error("Đã có lỗi xảy ra trong tác vụ.");
            console.log("Tác vụ thất bại, gọi reject...");
            reject(loi); // Thất bại -> gọi reject với lỗi
        }
    }, 2000);
});

console.log("Promise đã được tạo. Trạng thái ban đầu: Pending.");
console.log("Chương trình vẫn tiếp tục chạy..."); // Đây là code đồng bộ chạy ngay
```

### ✨ Xử Lý Kết Quả (Chaining Promises)

Promise có các phương thức `.then()`, `.catch()`, và `.finally()` để bạn "đăng ký" các hàm callback sẽ chạy khi Promise Settled. Các phương thức này luôn **trả về một Promise mới**, cho phép bạn xâu chuỗi (chaining) nhiều thao tác bất đồng bộ liên tiếp.

*   **`.then(onFulfilled, onRejected)`:** Được gọi khi Promise đã **Fulfilled**. Tham số đầu tiên `onFulfilled` là callback xử lý khi thành công, nhận giá trị truyền vào `resolve()`. Tham số thứ hai `onRejected` là callback xử lý khi thất bại, nhận lỗi truyền vào `reject()`. Tham số `onRejected` là tùy chọn.

*   **`.catch(onRejected)`:** Là cách viết ngắn gọn hơn của `.then(null, onRejected)`. Được gọi khi Promise đã **Rejected**. Chỉ nhận callback xử lý lỗi, nhận lỗi truyền vào `reject()`. Nên dùng `.catch()` để xử lý lỗi ở cuối chuỗi Promise.

*   **`.finally(onSettled)` (ES9):** Được gọi khi Promise đã **Settled** (bất kể thành công hay thất bại). Thường dùng để thực hiện các thao tác dọn dẹp (ví dụ: ẩn spinner loading). Callback này không nhận đối số.

**Ví dụ sử dụng `.then()` và `.catch()`:**

```javascript
// Tiếp tục ví dụ viDuPromise ở trên
viDuPromise
    .then((result) => { // Callback xử lý khi Promise Fulfilled (kết quả là giá trị truyền vào resolve)
        console.log("Bước .then() nhận được:", result);
        console.log("Thành công! Giá trị:", result);

        // Bạn có thể trả về một giá trị MỚI từ .then()
        // Giá trị này sẽ là đầu vào cho .then() TIẾP THEO trong chuỗi
        return "Kết quả từ bước 1 đã được biến đổi";
    })
    .then((nextResult) => { // .then() thứ 2 nhận kết quả từ .then() trước
        console.log("Bước .then() thứ 2 nhận được:", nextResult);
        console.log("Hoàn thành xử lý thành công.");
        // Có thể trả về một Promise mới từ đây để xâu chuỗi các tác vụ bất đồng bộ liên tiếp
        // return new Promise((res, rej) => setTimeout(() => res("Hoàn thành tác vụ kế tiếp"), 1000));
    })
    .catch((error) => { // Callback xử lý khi Promise Rejected (nhận lỗi từ reject)
        console.error("Có lỗi xảy ra trong bất kỳ .then() nào phía trước hoặc trong Promise ban đầu:");
        console.error(error);
        // Từ đây, bạn có thể trả về một giá trị MẶC ĐỊNH hoặc ném ra một lỗi khác
    })
    .finally(() => { // Luôn chạy sau khi Promise Settled (Fulfilled hoặc Rejected)
        console.log("Hoàn thành quy trình xử lý Promise (dọn dẹp hoặc kết thúc loading).");
    });

// Chương trình vẫn chạy tiếp tục ở đây trong khi Promise đang Pending...
console.log("Chuỗi .then/.catch/.finally đã được thiết lập. Đang chờ Promise Settled...");

// Output thứ tự (với success = true):
// Promise đã được tạo. Trạng thái ban đầu: Pending.
// Chương trình vẫn tiếp tục chạy...
// Chuỗi .then/.catch/.finally đã được thiết lập. Đang chờ Promise Settled...
// Đang thực thi tác vụ trong Promise...
// (Sau 2 giây)
// Tác vụ thành công, gọi resolve...
// Bước .then() nhận được: Dữ liệu đã được xử lý!
// Thành công! Giá trị: Dữ liệu đã được xử lý!
// Bước .then() thứ 2 nhận được: Kết quả từ bước 1 đã được biến đổi
// Hoàn thành xử lý thành công.
// Hoàn thành quy trình xử lý Promise (dọn dẹp hoặc kết thúc loading).

// Output thứ tự (với success = false):
// ... (giống trên)
// Đang thực thi tác vụ trong Promise...
// (Sau 2 giây)
// Tác vụ thất bại, gọi reject...
// Có lỗi xảy ra trong bất kỳ .then() nào phía trước hoặc trong Promise ban đầu:
// Error: Đã có lỗi xảy ra trong tác vụ.
// Hoàn thành quy trình xử lý Promise (dọn dẹp hoặc kết thúc loading).
```

*   Mỗi `.then()` trả về một Promise mới. Nếu callback trong `.then()` trả về:
    *   Một giá trị: Promise tiếp theo sẽ Fulfilled với giá trị đó.
    *   Một Promise mới: Promise tiếp theo sẽ theo dõi trạng thái của Promise mới đó.
    *   Ném ra lỗi: Promise tiếp theo sẽ Rejected với lỗi đó.
*   Phương thức `.catch()` bắt lỗi từ bất kỳ Promise nào phía trước trong chuỗi `.then()`. Điều này giúp quản lý lỗi tập trung và thoát khỏi Callback Hell.
*   Thường đặt `.catch()` ở cuối cùng trong chuỗi để xử lý tất cả các lỗi có thể xảy ra trên đường đi.

### 🌟 Xâu Chuỗi Nhiều Promise (Replacing Callback Hell)

Promise giúp xử lý chuỗi các tác vụ bất đồng bộ phụ thuộc nhau một cách tuần tự và dễ đọc hơn Callback Hell.

```javascript
function layDuLieuUser(userId) {
    return new Promise((resolve, reject) => {
        setTimeout(() => { // Mô phỏng API call 1
            if (userId === "user/1") {
                console.log("-> Lấy dữ liệu user thành công");
                resolve({ id: "user/1", name: "Alice" });
            } else {
                reject(new Error("User không tồn tại"));
            }
        }, 1000);
    });
}

function layDuLieuPosts(userId) {
    return new Promise((resolve, reject) => {
        setTimeout(() => { // Mô phỏng API call 2 (phụ thuộc user)
            if (userId === "user/1") {
                console.log("--> Lấy dữ liệu posts thành công");
                resolve([{ id: "post/a", title: "Bài viết A" }, { id: "post/b", title: "Bài viết B" }]);
            } else {
                 reject(new Error("Không lấy được posts cho user này"));
            }
        }, 1500);
    });
}

// Sử dụng Promise Chaining để làm phẳng cấu trúc lồng nhau của Callbacks
layDuLieuUser("user/1")
    .then(user => { // Nhận user object từ Promise trước
        console.log("Bước 1 hoàn thành, User:", user);
        // Trả về Promise thứ 2
        return layDuLieuPosts(user.id); // Giá trị trả về này là Promise
    })
    .then(posts => { // Nhận posts array từ Promise thứ 2 (layDuLieuPosts)
        console.log("Bước 2 hoàn thành, Posts:", posts);
        console.log("Tất cả dữ liệu cần thiết đã có!");
        // Có thể tiếp tục trả về Promise khác nếu cần
    })
    .catch(error => { // Bất kỳ lỗi nào (từ layDuLieuUser hoặc layDuLieuPosts) đều bị bắt ở đây
        console.error("Có lỗi trong chuỗi promise:", error);
    });

console.log("Yêu cầu dữ liệu đã được gửi đi (bất đồng bộ)...");
```
Code này rõ ràng, dễ đọc hơn nhiều so với Callback Hell. Luồng xử lý được theo dõi tuần tự bằng các bước `.then()`.

### 🎯 Promise Combinators (Kết hợp Promises)

Có các hàm tích hợp sẵn để làm việc với nhiều Promises cùng lúc:

*   **`Promise.all([promise1, promise2, ...])`:** Nhận một mảng các Promise. Trả về một Promise **mới** sẽ Fulfilled khi **TẤT CẢ** các Promise trong mảng đều Fulfilled. Giá trị trả về là một mảng các kết quả (theo đúng thứ tự). Nếu BẤT KỲ Promise nào bị Rejected, `Promise.all` sẽ Rejected NGAY LẬP TỨC với lỗi của Promise đầu tiên bị Rejected.
*   **`Promise.race([promise1, promise2, ...])`:** Nhận một mảng các Promise. Trả về một Promise **mới** sẽ Fulfilled hoặc Rejected **ngay khi Promise ĐẦU TIÊN trong mảng Settled** (dù là Fulfilled hay Rejected), với kết quả hoặc lỗi của Promise đó.
*   **`Promise.allSettled([promise1, promise2, ...])` (ES11):** Nhận một mảng các Promise. Trả về một Promise **mới** sẽ Fulfilled khi **TẤT CẢ** các Promise trong mảng đều Settled (dù Fulfilled hay Rejected). Giá trị trả về là một mảng các đối tượng mô tả kết quả của từng Promise (`{status: 'fulfilled', value: result}` hoặc `{status: 'rejected', reason: error}`). Rất hữu ích khi bạn muốn biết trạng thái của tất cả các promise, kể cả khi có lỗi.
*   **`Promise.any([promise1, promise2, ...])` (ES12):** Nhận một mảng các Promise. Trả về một Promise **mới** sẽ Fulfilled ngay khi **Promise ĐẦU TIÊN Fulfilled**. Nếu TẤT CẢ các Promise đều bị Rejected, nó sẽ Rejected với một `AggregateError` chứa tất cả các lỗi.

**Ví dụ `Promise.all`:**

```javascript
const promise1 = Promise.resolve("Thành công 1"); // Promise Fulfilled ngay lập tức
const promise2 = new Promise(resolve => setTimeout(() => resolve("Thành công 2"), 1000));
const promise3 = new Promise((_, reject) => setTimeout(() => reject(new Error("Lỗi 3")), 500));

// Promise.all([promise1, promise2, promise3]) // Thử chạy đoạn này, nó sẽ bị Rejected do promise3
Promise.all([promise1, promise2]) // Chỉ chạy promise1 và promise2 (đều thành công)
    .then(results => {
        console.log("All thành công:", results); // Output: All thành công: ["Thành công 1", "Thành công 2"]
    })
    .catch(error => {
        console.error("Có promise bị lỗi:", error);
    });
```

### 🛠 Luyện Tập

*   Tạo một Promise đơn giản sẽ resolve sau 1 giây với một chuỗi tin nhắn thành công. Dùng `.then()` để in ra tin nhắn đó.
*   Tạo một Promise khác sẽ reject sau 1.5 giây với một đối tượng Error. Dùng `.catch()` để in ra lỗi đó.
*   Viết lại ví dụ Callback Hell bạn làm ở bài trước sang sử dụng Promise Chaining (`.then().then().catch()`).
*   Sử dụng `Promise.all` với một mảng gồm 3 Promise giả định (mỗi Promise dùng `setTimeout` với thời gian khác nhau). Quan sát khi tất cả đều Fulfilled và khi có ít nhất một cái bị Rejected.

Promises là bước nhảy vọt lớn trong lập trình bất đồng bộ. Nắm vững Promises sẽ giúp bạn dễ dàng tiếp cận và sử dụng các API hiện đại, cũng như chuẩn bị cho cú pháp `async/await` còn tuyệt vời hơn!

---

## File: 18_async_await.md

```markdown
# ✨ Bài 18: Async/Await - Lập trình Bất đồng bộ trông như Đồng bộ (ES8+)

Sau khi đã làm quen với Callback và Promises, chúng ta đến với đỉnh cao của việc xử lý bất đồng bộ trong JavaScript hiện đại: **Async/Await**. Ra mắt trong ES8 (ECMAScript 2017), cú pháp này giúp bạn viết code bất đồng bộ mà nhìn (và đọc) gần giống với code đồng bộ, giúp cải thiện đáng kể tính đọc hiểu và bảo trì của mã.

Hãy nghĩ về `async` và `await` như bộ "phiên dịch thời gian" của bạn: bạn viết các lệnh chờ đợi bình thường như trong lập trình đồng bộ, và `async/await` lo phần còn lại để đảm bảo chương trình không bị blocking.

### function `async` - Đánh dấu hàm bất đồng bộ

*   Để sử dụng từ khóa `await`, hàm chứa nó **phải** được đánh dấu bằng từ khóa `async`.
*   Hàm được đánh dấu `async` luôn trả về một **Promise**.

```javascript
// Một hàm async đơn giản
async function xinChaoAsync() {
    return "Xin chào từ Async Function!"; // Giá trị này sẽ được tự động bao bọc trong một Promise resolve
}

// Hàm async phức tạp hơn
async function lamViecBatDongBo() {
    // Code bất đồng bộ ở đây (có thể sử dụng await)
    console.log("Bắt đầu làm việc...");
    // ...
    // Kết thúc công việc
    // Giá trị trả về sẽ là giá trị resolved của Promise mà hàm async trả về
    return { status: "Hoàn thành", message: "Tác vụ bất đồng bộ đã xong" };
    // Nếu hàm async không trả về gì, nó sẽ return Promise.resolve(undefined)
    // Nếu có lỗi ném ra trong hàm async, Promise sẽ bị reject với lỗi đó
    // throw new Error("Something went wrong!"); // Điều này sẽ làm promise bị reject
}

// Bạn gọi hàm async như gọi hàm bình thường, nhưng kết quả trả về là một Promise
xinChaoAsync().then(result => {
    console.log(result); // Output: Xin chào từ Async Function!
});

lamViecBatDongBo()
    .then(resultObj => console.log("Kết quả của tác vụ:", resultObj))
    .catch(error => console.error("Tác vụ lỗi:", error));
```

### await `await` - Chờ đợi Promise

*   Từ khóa `await` **chỉ có thể sử dụng bên trong một hàm `async`**.
*   `await` dùng để đặt trước một **Promise**.
*   Khi JavaScript gặp `await`, nó sẽ tạm dừng việc thực thi hàm `async` hiện tại cho đến khi Promise phía sau `await` **Settled** (Fulfilled hoặc Rejected).
*   Nếu Promise được `resolve` (thành công), `await` sẽ trả về **giá trị mà Promise resolve đó mang theo**.
*   Nếu Promise bị `reject` (thất bại), `await` sẽ **ném ra một lỗi**. Lỗi này cần được xử lý bằng `try...catch`.

```javascript
function taoPromiseSauGiayLat(value, ms) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (value) { // Nếu value không rỗng/undefined/null...
                resolve(value);
            } else {
                reject(new Error("Giá trị không hợp lệ!"));
            }
        }, ms);
    });
}

async function demoAwait() {
    console.log("Bước 1: Đang chuẩn bị...");

    // Dừng lại ở đây, chờ Promise từ taoPromiseSauGiayLat(thành công) hoàn thành sau 2 giây
    const result1 = await taoPromiseSauGiayLat("Kết quả từ bước 2", 2000);
    console.log("Bước 2 hoàn thành, nhận được:", result1); // Code này chạy sau 2 giây

    // Dừng lại ở đây, chờ Promise từ taoPromiseSauGiayLat(thành công khác) hoàn thành sau 1 giây
    const result2 = await taoPromiseSauGiayLat("Kết quả từ bước 3", 1000);
    console.log("Bước 3 hoàn thành, nhận được:", result2); // Code này chạy sau 1 + 2 = 3 giây tổng cộng

    console.log("Hoàn thành chuỗi bất đồng bộ với await!");
}

console.log("Chạy hàm async...");
demoAwait();
console.log("Code đồng bộ VẪN chạy tiếp..."); // Chạy ngay lập tức
```

### ✅ Xử lý Lỗi với `try...catch` trong Async/Await

Vì `await` ném ra lỗi khi Promise bị Rejected, bạn có thể sử dụng khối `try...catch` quen thuộc để bắt và xử lý các lỗi xảy ra trong chuỗi `await`.

```javascript
async function demoAwaitXuLyLoi() {
    console.log("Bắt đầu chuỗi với xử lý lỗi...");
    try {
        // Await một promise có thể thành công
        const data1 = await taoPromiseSauGiayLat("Dữ liệu tốt", 1000);
        console.log("Tác vụ 1 OK:", data1);

        // Await một promise sẽ thất bại
        const data2 = await taoPromiseSauGiayLat(null, 1000); // Truyền null để gây lỗi
        console.log("Tác vụ 2 OK (nhưng lẽ ra lỗi):", data2); // Dòng này sẽ KHÔNG chạy

    } catch (error) { // Nếu bất kỳ await nào ném ra lỗi (promise bị reject)
        console.error("Oops! Có lỗi trong khối try:");
        console.error(error.message); // In ra thông báo lỗi

        // Sau khi bắt lỗi, bạn có thể quyết định làm gì tiếp
        // - Bỏ qua lỗi và tiếp tục (nếu code sau catch không dùng kết quả của đoạn lỗi)
        // - Trả về giá trị mặc định
        // - Ném ra lỗi khác
        // - ...
    } finally {
        console.log("Kết thúc khối try/catch (luôn chạy).");
    }

     console.log("Kết thúc hàm async demoAwaitXuLyLoi."); // Dòng này chạy sau khi try/catch hoàn tất
}

console.log("Chạy hàm async xử lý lỗi...");
demoAwaitXuLyLoi();
console.log("Code đồng bộ tiếp tục chạy.");
```

### 🔄 Ưu điểm của Async/Await so với Promises

*   **Dễ đọc và viết hơn:** Code trông và hoạt động giống code đồng bộ, đặc biệt với các chuỗi bất đồng bộ phức tạp.
*   **Xử lý lỗi tốt hơn:** Sử dụng cú pháp `try...catch` quen thuộc thay vì `.catch()`.
*   **Debug dễ dàng hơn:** Khi debug, bạn có thể "bước" (step) qua các dòng `await` như code đồng bộ, không như việc debug qua các callback của Promise (mỗi `.then` callback được lên lịch chạy sau).

### ❗️ Lưu Ý Khi Sử Dụng Async/Await

*   Luôn **`await` một Promise**. Nếu bạn `await` một giá trị không phải Promise, nó sẽ chỉ tạm dừng trong một khoảng thời gian cực ngắn (coi như 0) và trả về giá trị đó. Điều này thường không cần thiết.
*   **Không chặn (block) Event Loop:** Mặc dù cú pháp nhìn đồng bộ, `await` vẫn đảm bảo tính bất đồng bộ. Khi gặp `await`, hàm `async` được "tạm dừng", nhưng Event Loop vẫn rảnh rỗi để thực thi các tác vụ khác.
*   **Async Function luôn trả về Promise:** Ngay cả khi bạn không sử dụng `return`, hàm `async` sẽ tự động bao bọc giá trị trả về trong một Promise đã Fulfilled. Nếu ném lỗi, nó trả về một Promise đã Rejected.
*   `await` chỉ dùng trong `async` function. Nếu bạn muốn sử dụng `await` ở cấp độ global (tức là không trong bất kỳ function nào), cần dùng **Top-Level Await** (đã được hỗ trợ trong các môi trường Module - `type="module"` hoặc `.mjs`, và các phiên bản Node.js/Browser gần đây).

```javascript
// Ví dụ Top-Level Await (trong module JS)
// file: module.js (với type="module")
const duLieuKhoiTao = await taoPromiseSauGiayLat("Đã tải cấu hình", 1000);
console.log(duLieuKhoiTao);

// Code sau này có thể dùng duLieuKhoiTao ngay
```

### ⏱️ Chạy song song các Promise với Async/Await

Nếu bạn có nhiều Promise không phụ thuộc lẫn nhau và muốn chúng chạy song song (không chờ cái này xong mới đến cái kia), **KHÔNG** dùng `await` tuần tự:

```javascript
// SAI (chạy tuần tự, mất tổng cộng 1000 + 1500 + 500 = 3000ms)
async function sequentialFetch() {
    const res1 = await fetch('/api/data1'); // Chờ 1 giây
    const res2 = await fetch('/api/data2'); // Chờ 1.5 giây
    const res3 = await fetch('/api/data3'); // Chờ 0.5 giây
    console.log('Xong tất cả (tuần tự)!');
}

// ĐÚNG (chạy song song, mất khoảng 1.5 giây - là thời gian lâu nhất trong 3 promise)
async function parallelFetch() {
    const promise1 = fetch('/api/data1'); // Yêu cầu 1 được gửi đi
    const promise2 = fetch('/api/data2'); // Yêu cầu 2 được gửi đi
    const promise3 = fetch('/api/data3'); // Yêu cầu 3 được gửi đi

    // Bây giờ chờ kết quả của cả 3 Promise cùng lúc
    const [res1, res2, res3] = await Promise.all([promise1, promise2, promise3]);

    // res1, res2, res3 bây giờ chứa Response object
    const data1 = await res1.json(); // Chờ parse JSON
    const data2 = await res2.json();
    const data3 = await res3.json();

    console.log('Xong tất cả (song song)!', data1, data2, data3);
}
```
Hãy sử dụng `Promise.all()` (hoặc `Promise.allSettled`, `Promise.race`, `Promise.any`) kết hợp với `await` để quản lý nhiều Promise chạy song song một cách hiệu quả và dễ đọc trong async function.

### 🛠 Luyện Tập

*   Chuyển đổi một hàm sử dụng Promise Chaining (`.then()`) sang sử dụng cú pháp `async/await`. So sánh tính đọc hiểu.
*   Tạo một hàm `async` gọi một Promise mô phỏng có thể thành công hoặc thất bại. Sử dụng `try...catch` để xử lý trường hợp lỗi.
*   Viết một hàm `async` nhận một mảng URL. Bên trong hàm này, sử dụng `Promise.all` kết hợp với `fetch` và `await` để tải dữ liệu từ tất cả các URL đó **song song**.

Async/Await là công cụ mạnh mẽ nhất để xử lý bất đồng bộ trong JS hiện đại. Thực hành sử dụng nó sẽ làm cho code của bạn trở nên rõ ràng, đáng tin cậy và dễ bảo trì hơn rất nhiều! Bạn đã chính thức là một phi công kỳ cựu của bầu trời bất đồng bộ rồi đấy! 😉🌌

---

## File: 19_error_handling.md

```markdown
# 🔥 Bài 19: Xử Lý Lỗi (Error Handling) - Biến sự cố thành cơ hội!

Trong mọi chương trình, việc gặp lỗi là không thể tránh khỏi. Đó là một phần tự nhiên của quá trình phát triển. Tuy nhiên, một chương trình mạnh mẽ không chỉ dừng lại khi gặp lỗi mà cần biết cách **xử lý** chúng một cách duyên dáng. **Xử lý lỗi (Error Handling)** là kỹ thuật phát hiện và ứng phó với các lỗi xảy ra trong quá trình thực thi code.

Hãy nghĩ về xử lý lỗi như hệ thống "khẩn cấp" của phi thuyền bạn: khi có cảnh báo nguy hiểm, hệ thống sẽ kích hoạt các quy trình để giảm thiểu thiệt hại, thông báo cho phi hành đoàn và (hy vọng là!) cho phép chuyến bay tiếp tục.

### 💥 Các Loại Lỗi Trong JavaScript

Có nhiều loại lỗi khác nhau trong JS:

*   **Syntax Errors (Lỗi cú pháp):** Lỗi xảy ra khi code vi phạm ngữ pháp của JS (ví dụ: thiếu dấu ngoặc, sai chính tả từ khóa). Trình duyệt/engine JS sẽ phát hiện lỗi này ngay cả trước khi thực thi code. Code bị lỗi cú pháp thường sẽ KHÔNG CHẠY được.
*   **Runtime Errors (Lỗi khi chạy):** Lỗi xảy ra trong quá trình code đang chạy.
    *   `ReferenceError`: Cố gắng truy cập một biến hoặc hàm chưa được định nghĩa.
    *   `TypeError`: Thao tác trên một giá trị không đúng kiểu (ví dụ: gọi phương thức của `undefined`, thực thi giá trị không phải hàm).
    *   `RangeError`: Sử dụng một số nằm ngoài phạm vi giá trị hợp lệ (ít gặp trong JS thông thường).
    *   `URIError`: Lỗi khi sử dụng các hàm mã hóa/giải mã URI (ví dụ: `decodeURI`).
    *   `EvalError`: Lỗi liên quan đến hàm `eval()` (ít dùng trong code hiện đại).
    *   `InternalError`: Lỗi nghiêm trọng bên trong engine JS (ví dụ: quá tải đệ quy - stack overflow).
    *   `AggregateError` (ES11): Lỗi kết hợp nhiều lỗi khác (ví dụ: trong `Promise.any`).
*   **Logical Errors (Lỗi logic):** Code chạy bình thường nhưng kết quả không như mong đợi (ví dụ: tính toán sai, hiển thị sai dữ liệu). Đây là loại lỗi KHÓ bắt nhất vì JS engine không báo lỗi, bạn phải tìm bằng cách kiểm tra, debug và test.
*   **Custom Errors (Lỗi tùy chỉnh):** Lỗi do chính bạn chủ động ném ra trong code để báo hiệu một điều kiện đặc biệt.

Chúng ta tập trung vào việc xử lý **Runtime Errors** và **Custom Errors**.

### ✅ Khối `try...catch`

Đây là cấu trúc cơ bản nhất và phổ biến nhất để bắt và xử lý Runtime Errors.

Cú pháp:

```javascript
try {
    // Đoạn mã bạn muốn thử thực thi
    // Nếu có lỗi xảy ra ở đây, việc thực thi sẽ DỪNG LẠI NGAY LẬP TỨC
    // và chuyển đến khối catch
} catch (error) {
    // Đoạn mã xử lý lỗi
    // 'error' là một biến chứa đối tượng Error với thông tin chi tiết
    // Chỉ chạy nếu có lỗi trong khối try
} finally {
    // Đoạn mã TÙY CHỌN
    // Luôn luôn chạy, dù khối try thành công hay gặp lỗi,
    // và dù bạn có xử lý lỗi trong catch hay không.
    // Thường dùng cho việc dọn dẹp (đóng kết nối, giải phóng tài nguyên...)
}
```
*   `try`: Khối code được "giám sát" để tìm lỗi.
*   `catch(error)`: Nếu một lỗi * Runtime Error* xảy ra trong khối `try`, JS sẽ "nhảy" ngay đến khối `catch`. Đối tượng lỗi được truyền vào biến `error`. Bạn có thể bỏ qua tham số `error` trong cú pháp ES10+ nếu không cần dùng đến đối tượng lỗi.
*   `finally`: Khối này *luôn* chạy sau khi khối `try` hoặc `catch` đã hoàn thành. Nó là tùy chọn.

**Ví dụ:**

```javascript
function riskyOperation() {
    console.log("Đang thử một phép toán mạo hiểm...");
    const num = 10;
    // const divisor = "abc"; // Dòng này sẽ gây TypeError nếu bỏ comment
    const divisor = 0; // Dòng này sẽ gây ReferenceError nếu bienChuaDinhNghia chưa khai báo

    // try { // Có thể đặt try...catch ngay bên trong hàm riskyOperation
        // console.log(bienChuaDinhNghia); // Gây ReferenceError
        const ketQua = num / divisor; // Gây lỗi (NaN hoặc Infinity, tùy trường hợp)
        console.log("Phép toán thành công:", ketQua);
    // } catch (err) { console.error("Lỗi nội bộ trong hàm:", err.message); }
}

console.log("Trước khối try...");

try {
    riskyOperation(); // Gọi hàm có thể gây lỗi

    // Nếu riskyOperation không ném lỗi (không bị crash bên trong try/catch nội bộ),
    // thì code này sẽ chạy
    console.log("Thử thách thành công, không có lỗi nào được ném.");

} catch (err) { // Bắt lỗi nếu riskyOperation ném lỗi (không xử lý nội bộ)
    console.error("Một lỗi đã bị bắt ở khối try...catch ngoài:");
    console.error(err.name + ": " + err.message); // In ra tên loại lỗi và thông báo

} finally {
    console.log("Khối finally luôn chạy.");
}

console.log("Sau khối try...catch...");

/*
Kết quả khi divisor = 0 (không lỗi runtime, kết quả là Infinity):
Trước khối try...
Đang thử một phép toán mạo hiểm...
Phép toán thành công: Infinity
Thử thách thành công, không có lỗi nào được ném.
Khối finally luôn chạy.
Sau khối try...catch...

Kết quả khi divisor = "abc" (TypeError):
Trước khối try...
Đang thử một phép toán mạo hiểm...
Một lỗi đã bị bắt ở khối try...catch ngoài:
TypeError: Cannot read property '...' of undefined (Hoặc thông báo khác tùy ngữ cảnh)
Khối finally luôn chạy.
Sau khối try...catch...

Kết quả khi bienChuaDinhNghia chưa khai báo (ReferenceError):
Trước khối try...
Đang thử một phép toán mạo hiểm...
Một lỗi đã bị bắt ở khối try...catch ngoài:
ReferenceError: bienChuaDinhNghia is not defined
Khối finally luôn chạy.
Sau khối try...catch...
*/
```

### ✋ Từ khóa `throw` - Ném lỗi tùy chỉnh

Ngoài việc JS engine tự động ném lỗi, bạn có thể **chủ động ném ra lỗi** bằng từ khóa `throw`. Bạn có thể ném bất cứ giá trị nào, nhưng nên ném một đối tượng `Error` hoặc một instance của một lớp lỗi được tạo từ `Error`.

```javascript
function kiemTraTuoi(tuoi) {
    if (tuoi < 0 || !Number.isFinite(tuoi)) {
        throw new Error("Tuổi phải là một số dương hợp lệ."); // Ném ra đối tượng Error mới
    }
    if (tuoi < 18) {
        // Ném ra lỗi tùy chỉnh hơn, ví dụ bằng cách tạo class riêng kế thừa từ Error (nâng cao)
        // throw new NotAdultError("Chưa đủ tuổi.");
         throw new Error("Người dùng chưa đủ 18 tuổi.");
    }
    console.log("Đủ tuổi.");
}

try {
    kiemTraTuoi(20);
    kiemTraTuoi(16); // Dòng này sẽ ném lỗi, chuyển đến khối catch
    kiemTraTuoi(-5); // Dòng này sẽ KHÔNG chạy
} catch (err) {
    console.error("Bắt được lỗi khi kiểm tra tuổi:", err.message); // In ra thông báo từ lỗi bị ném
}

console.log("Tiếp tục sau khi kiểm tra tuổi...");
```
Việc chủ động ném lỗi giúp bạn báo hiệu các điều kiện không mong muốn xảy ra trong code logic của mình.

### 📡 Xử lý Lỗi trong Promise (nhắc lại)

Như đã thấy ở bài Promise:

*   Promise bị Rejected khi hàm executor gọi `reject(error)` hoặc khi bất kỳ lỗi nào được `throw` bên trong executor đó.
*   Các lỗi từ Rejected Promise được xử lý bởi callback `onRejected` trong `.then(onFulfilled, onRejected)` hoặc bằng `.catch(onRejected)`.
*   Nếu một lỗi được `throw` trong callback `.then(onFulfilled)` hoặc `.catch()`, nó sẽ khiến Promise TIẾP THEO trong chuỗi bị Rejected.

```javascript
new Promise((resolve, reject) => {
    // throw new Error("Lỗi trong Promise gốc!"); // Bị bắt bởi catch
    reject("Lỗi do reject()!"); // Bị bắt bởi catch
})
.then(result => {
    console.log("OK:", result);
    // throw new Error("Lỗi trong then!"); // Bị bắt bởi catch kế tiếp
})
.catch(error => { // Bắt lỗi từ Promise gốc hoặc các then() phía trước
    console.error("Lỗi Promise:", error);
})
.finally(() => {
    console.log("Kết thúc Promise chain.");
});
```

### 🤯 Xử lý Lỗi trong Async/Await (nhắc lại và nhấn mạnh)

Đây là điểm mạnh của `async/await`. `await` tự động "chờ" cho Promise Settled và:

*   Nếu Promise Fulfilled, nó trả về giá trị (như thành công đồng bộ).
*   Nếu Promise Rejected, nó **tự động ném ra lỗi** (như gặp lỗi đồng bộ).

Vì vậy, `try...catch` hoạt động cực kỳ hiệu quả với `async/await` để xử lý lỗi bất đồng bộ.

```javascript
function mayTaoLoiOrOk(success) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (success) {
                resolve("Thành công rực rỡ!");
            } else {
                reject(new Error("Đã bị tấn công!"));
            }
        }, 1000);
    });
}

async function thuHoatDongNguyenTu() {
    try {
        console.log("Đang khởi động lò phản ứng...");
        const ketQuaHoatDong1 = await mayTaoLoiOrOk(true); // Thành công
        console.log("Hoạt động 1:", ketQuaHoatDong1);

        console.log("Đang thực hiện tính toán phức tạp...");
        const ketQuaHoatDong2 = await mayTaoLoiOrOk(false); // Thất bại
        console.log("Hoạt động 2:", ketQuaHoatDong2); // Dòng này KHÔNG CHẠY

    } catch (error) { // Lỗi từ mayTaoLoiOrOk(false) bị ném ra và bắt ở đây
        console.error("Xảy ra lỗi khi thực hiện hoạt động nguyên tử!");
        console.error("Lỗi chi tiết:", error.message);
        // Hệ thống khẩn cấp đã được kích hoạt!
    } finally {
        console.log("Quy trình khẩn cấp/bình thường kết thúc.");
    }
}

console.log("Bắt đầu nhiệm vụ.");
thuHoatDongNguyenTu();
console.log("Các hệ thống khác vẫn chạy.");
```

### 🚩 Xử lý Lỗi Global (Chỉ bắt các lỗi không bị bắt ở đâu cả)

Trong môi trường trình duyệt và Node.js, có các sự kiện global được kích hoạt khi có lỗi không bị `try...catch` hoặc `.catch()` của Promise bắt.

*   **Trình duyệt:** `window.onerror` (cũ) và `window.addEventListener('error', ...)` (mới và mạnh mẽ hơn) cho các lỗi runtime không bắt được. `window.addEventListener('unhandledrejection', ...)` cho các Promise bị rejected mà không có `.catch()` nào xử lý.
*   **Node.js:** `process.on('uncaughtException', ...)` cho lỗi đồng bộ không bắt được. `process.on('unhandledRejection', ...)` cho Promise bị rejected không xử lý.

Việc xử lý lỗi global giúp bạn ghi lại (log) các lỗi mà bạn có thể đã bỏ sót, tránh trường hợp ứng dụng bị sập một cách im lặng.

### 💡 Nguyên tắc chung

*   **Đừng "nuốt" lỗi:** Không để khối `catch` rỗng hoặc chỉ in ra console và không làm gì thêm (trừ khi đó là hành vi mong muốn sau khi cân nhắc kỹ). Ít nhất hãy ghi log lỗi đó.
*   **Hiểu loại lỗi:** Đối tượng `error` chứa nhiều thông tin hữu ích (`name`, `message`, `stack` - dấu vết hàm gọi dẫn đến lỗi). Hãy in ra hoặc ghi log đầy đủ thông tin này để debug.
*   **Ném lỗi lại:** Đôi khi, sau khi bắt và xử lý lỗi cục bộ (ví dụ: ghi log), bạn cần ném lại lỗi đó (`throw error;`) để các khối `catch` ở cấp cao hơn có thể xử lý tiếp hoặc để dừng luồng chương trình.
*   **Sử dụng Custom Errors:** Tự tạo lớp lỗi kế thừa từ `Error` để biểu diễn các tình huống lỗi nghiệp vụ cụ thể trong ứng dụng của bạn, giúp code dễ hiểu và phân loại lỗi tốt hơn.
*   **Đảm bảo tài nguyên được giải phóng:** Dùng khối `finally` hoặc các mẫu thiết kế (như Resource Acquisition Is Initialization - RAII trong một số ngôn ngữ, hoặc các kỹ thuật quản lý tài nguyên khác trong JS) để đảm bảo các tài nguyên (kết nối mạng, file handle...) được đóng ngay cả khi có lỗi.

### 🛠 Luyện Tập

*   Tạo một hàm đơn giản có thể ném ra một đối tượng `Error` tùy theo điều kiện (ví dụ: nếu đối số không hợp lệ).
*   Gọi hàm đó bên trong một khối `try`, bắt lỗi bằng khối `catch` và in ra `error.message`. Thêm khối `finally`.
*   Viết một hàm `async` gọi một Promise giả định lúc thì thành công lúc thì thất bại. Dùng `try...catch` để xử lý thất bại đó.
*   Tìm hiểu cách bắt lỗi `unhandledrejection` trong môi trường trình duyệt hoặc Node.js và thử mô phỏng một promise bị reject mà không có `.catch()`.

Xử lý lỗi là một dấu hiệu của lập trình viên chuyên nghiệp. Một hệ thống có khả năng phục hồi tốt khi gặp lỗi mang lại trải nghiệm người dùng tốt hơn và giúp bạn debug hiệu quả hơn. Hãy xây dựng hệ thống phòng thủ cho code của bạn! 💪🛡️

---

## File: 20_dom_creation_manipulation.md

```markdown
# 🛠️ Bài 20: Thao tác DOM (Nâng cao) - Kiến tạo giao diện

Ở bài 9, chúng ta đã làm quen với việc chọn và thay đổi nội dung/thuộc tính đơn giản của các phần tử DOM đã có sẵn. Bây giờ, chúng ta sẽ nâng cấp đội quân robot xây dựng của mình để có thể **tạo mới**, **chèn**, **xóa**, và **di chuyển** các phần tử trong cây DOM một cách mạnh mẽ hơn.

Hãy coi việc này như việc bạn đang lắp ráp và điều chỉnh các bộ phận ngay trên thân tàu vũ trụ của mình trong không gian thực vậy!

### 🏭 Tạo Phần Tử Mới (`document.createElement()`)

Sử dụng phương thức `document.createElement()` để tạo một phần tử HTML mới hoàn toàn "trong không khí", chưa được chèn vào trang.

```javascript
const newDiv = document.createElement('div'); // Tạo một thẻ <div> mới
const newParagraph = document.createElement('p'); // Tạo một thẻ <p> mới
const newImage = document.createElement('img'); // Tạo một thẻ <img> mới

console.log(newDiv); // Output: <div></div>
console.log(newParagraph); // Output: <p></p>
console.log(newImage); // Output: <img>
```
Lúc này, các phần tử mới này mới chỉ tồn tại trong bộ nhớ của JS, chưa hiển thị trên trang web.

### 💬 Tạo Node Văn Bản (`document.createTextNode()`)

Đôi khi bạn chỉ cần tạo một đoạn văn bản thuần túy để thêm vào phần tử khác, không cần bao bọc trong thẻ HTML nào.

```javascript
const textNode = document.createTextNode('Đây là nội dung văn bản.');

console.log(textNode); // Output: "Đây là nội dung văn bản."
```
Trong thực tế, việc gán `element.textContent` hoặc `element.innerHTML` thường đơn giản hơn, nhưng `createTextNode` hữu ích khi bạn cần kiểm soát chính xác việc tạo và chèn từng nút vào DOM (ví dụ: lý do bảo mật hoặc hiệu năng trong một số trường hợp).

### 🧬 Nhân bản Phần Tử (`element.cloneNode()`)

Nếu bạn muốn tạo một bản sao của một phần tử đã có sẵn.

*   `element.cloneNode()`: Nhân bản phần tử đó **nhưng không** nhân bản nội dung con của nó.
*   `element.cloneNode(true)`: Nhân bản phần tử đó **cùng với TẤT CẢ** nội dung con của nó (recursive clone).

```javascript
// Giả sử có <div id="container"><p>Hello</p></div>
const container = document.getElementById('container');
const clonedContainerShallow = container.cloneNode(); // Chỉ nhân bản <div>
const clonedContainerDeep = container.cloneNode(true); // Nhân bản <div> và cả <p> bên trong

console.log(clonedContainerShallow); // Output: <div></div>
console.log(clonedContainerDeep);   // Output: <div><p>Hello</p></div>
```

### 📍 Chèn Phần Tử Vào DOM

Sau khi tạo phần tử, bạn cần "đính" nó vào cây DOM hiện tại để nó hiển thị trên trang. Bạn cần xác định **phần tử cha (parent element)** và **vị trí** muốn chèn.

*   **`parentElement.appendChild(childElement)`:** Chèn `childElement` vào **cuối** danh sách con của `parentElement`.
*   **`parentElement.prepend(childElement)`:** Chèn `childElement` vào **đầu tiên** trong danh sách con của `parentElement`.
*   **`parentElement.insertBefore(newElement, referenceElement)`:** Chèn `newElement` **vào trước** `referenceElement` (là một phần tử con hiện có của `parentElement`).
*   **`element.after(newElement)`:** Chèn `newElement` **ngay sau** `element` (không nhất thiết là con của `element`, chỉ cần là anh em của nó hoặc ở bất kỳ đâu liên quan trong cây DOM).
*   **`element.before(newElement)`:** Chèn `newElement` **ngay trước** `element`.
*   **`element.replaceWith(newElement)`:** Thay thế `element` bằng `newElement`.
*   **`element.insertAdjacentElement(position, newElement)`:** Cung cấp kiểm soát chi tiết hơn về vị trí chèn so với `element`. `position` là một trong 4 chuỗi: `'beforebegin'` (trước element), `'afterbegin'` (bên trong element, ở đầu), `'beforeend'` (bên trong element, ở cuối), `'afterend'` (sau element).
*   `element.insertAdjacentHTML(position, htmlString)`: Tương tự `insertAdjacentElement` nhưng chèn HTML dạng chuỗi.
*   `element.insertAdjacentText(position, text)`: Tương tự `insertAdjacentElement` nhưng chèn văn bản thuần.

**Ví dụ (sử dụng lại HTML cũ):**

```html
<body>
    <h1 id="tieuDe">Chào Mừng</h1>
    <div id="container">
        <p class="doanVan" id="p1">Đây là đoạn văn thứ nhất.</p>
    </div>
    <button id="nutBam">Bấm vào đây!</button>
    <!-- script.js -->
</body>
```

**Ví dụ JS (`script.js`):**

```javascript
const container = document.getElementById('container');
const firstParagraph = document.getElementById('p1'); // Đoạn văn thứ nhất

// Tạo một đoạn văn MỚI
const newP = document.createElement('p');
newP.textContent = "Đây là đoạn văn MỚI.";
newP.style.color = "purple";

// 1. Chèn newP vào CUỐI #container
container.appendChild(newP); // Bây giờ #container có 2 con: p#p1 và p.purple

// Tạo một đoạn văn khác
const anotherP = document.createElement('p');
anotherP.textContent = "Đây là đoạn văn THÊM vào đầu.";
anotherP.style.fontWeight = "bold";

// 2. Chèn anotherP vào ĐẦU #container
container.prepend(anotherP); // Bây giờ #container có 3 con: p.bold, p#p1, p.purple

// Tạo một div mới
const newDivContent = document.createElement('div');
newDivContent.innerHTML = "<em>Nội dung thêm vào trước đoạn văn 1.</em>";
newDivContent.style.border = "1px dashed gray";

// 3. Chèn newDivContent vào TRƯỚC firstParagraph (trong cùng container cha)
// Sử dụng insertBefore()
container.insertBefore(newDivContent, firstParagraph); // #container có 4 con theo thứ tự

// 4. Sử dụng after() để chèn sau button (ví dụ khác)
const button = document.getElementById('nutBam');
const textAfterButton = document.createElement('span');
textAfterButton.textContent = "Đã thêm nội dung sau nút!";
textAfterButton.style.marginLeft = "10px";

if (button) {
   button.after(textAfterButton); // textAfterButton được chèn sau nút button
}

// 5. Sử dụng replaceWith()
// const title = document.getElementById('tieuDe');
// const newTitle = document.createElement('h2');
// newTitle.textContent = "Tiêu đề đã bị thay thế!";
// if (title) {
//    title.replaceWith(newTitle); // h1#tieuDe bị xóa, h2 mới thế chỗ
// }

// 6. Sử dụng insertAdjacentElement
// const spanInsideBegin = document.createElement('span');
// spanInsideBegin.textContent = "TEXT_AFTER_BEGIN";
// if (container) {
//     container.insertAdjacentElement('afterbegin', spanInsideBegin); // Chèn vào trong container, ở đầu
// }

// console.log(container.innerHTML); // Xem kết quả cấu trúc HTML sau khi thao tác
```

### ❌ Xóa Phần Tử (`element.remove()`, `parentElement.removeChild()`)

Có hai cách phổ biến để xóa một phần tử khỏi DOM:

*   `element.remove()`: Phương thức đơn giản nhất, gọi trực tiếp trên phần tử bạn muốn xóa.
*   `parentElement.removeChild(childElement)`: Phương thức cũ hơn. Bạn phải truy cập phần tử cha và gọi `removeChild`, truyền vào phần tử con mà bạn muốn nó xóa.

```javascript
// Xóa newP (đã được thêm ở trên)
// Sử dụng element.remove()
// newP.remove();

// Sử dụng parentElement.removeChild() - Cần truy cập phần tử cha
// if (container && newP && newP.parentElement === container) { // Nên kiểm tra trước khi xóa
//     container.removeChild(newP);
// }

// Xóa chính container
// if (container) {
//     container.remove(); // Toàn bộ container và nội dung bên trong sẽ bị xóa
// }
```
`element.remove()` là cách hiện đại và dễ dùng hơn, nên ưu tiên sử dụng.

### ✨ Sao chép Mảng các Node từ HTMLCollection/NodeList

Các phương thức như `getElementsByClassName` hoặc `querySelectorAll` trả về HTMLCollection hoặc NodeList (không phải mảng thực sự). Đôi khi bạn muốn sao chép các node này vào một mảng thực để dễ dàng dùng các phương thức mảng (`map`, `filter`,...).

```javascript
const paragraphs = document.querySelectorAll('.doanVan'); // NodeList
const pArray = [...paragraphs]; // Sử dụng Spread Operator để sao chép NodeList vào Mảng
console.log(Array.isArray(pArray)); // Output: true

pArray.forEach(p => { // Bây giờ có thể dùng forEach như mảng
    console.log(p.textContent);
});
```

### 💡 Thực hành tốt nhất

*   **Hiệu năng:** Thao tác trực tiếp trên DOM có thể tốn tài nguyên, đặc biệt khi thay đổi nhiều phần tử hoặc lặp đi lặp lại trong vòng lặp hiệu năng cao. Đối với các ứng dụng phức tạp với giao diện thay đổi liên tục, việc sử dụng các thư viện/framework UI như React, Vue, Angular (sử dụng Virtual DOM hoặc các kỹ thuật hiệu quả khác) là lựa chọn tốt hơn nhiều.
*   **Tạo fragment:** Khi cần tạo và thêm nhiều phần tử mới vào DOM cùng lúc, thay vì thêm từng phần tử riêng lẻ (gây nhiều lần vẽ lại giao diện), hãy tạo một **Document Fragment**, thêm tất cả các phần tử mới vào fragment đó trước, sau đó chỉ thêm fragment vào DOM chỉ *một lần duy nhất*.

    ```javascript
    const fragment = document.createDocumentFragment();
    for (let i = 0; i < 10; i++) {
        const li = document.createElement('li');
        li.textContent = `Mục số ${i}`;
        fragment.appendChild(li); // Thêm vào fragment, không làm thay đổi DOM thật
    }
    // Sau khi tạo hết trong fragment
    const myList = document.getElementById('myList'); // Giả sử có <ul></ul> với id="myList"
    if (myList) {
        myList.appendChild(fragment); // Chèn toàn bộ nội dung fragment vào DOM chỉ 1 lần
    }
    ```
    Cách này cải thiện đáng kể hiệu năng khi thêm số lượng lớn phần tử.

*   **Tách logic và giao diện:** Cố gắng giữ code JS (xử lý logic) và code thao tác DOM (cập nhật giao diện) tách bạch nhau nếu có thể.

### 🛠 Luyện Tập

*   Tạo một file HTML chỉ chứa một div rỗng (`<div id="output"></div>`).
*   Trong file JS, tạo một vòng lặp (ví dụ `for` từ 0 đến 9). Bên trong vòng lặp:
    *   Tạo một thẻ `<p>`.
    *   Đặt nội dung `textContent` của `<p>` là "Đoạn văn số [số lặp]".
    *   Thêm thẻ `<p>` này vào div `#output` bằng `appendChild`.
*   Thay đổi bài tập trên: thay vì thêm trực tiếp, tạo một Document Fragment, thêm các thẻ `<p>` vào fragment, và sau đó chỉ thêm fragment vào `#output` một lần duy nhất.
*   Tạo một button và một danh sách (`<ul>`) có sẵn một vài mục (`<li>`) trong HTML. Thêm trình lắng nghe sự kiện click cho button. Khi button được click, tạo một `<li>` mới và thêm vào danh sách `<ul>`.

Làm chủ việc tạo và thao tác với các phần tử DOM giúp bạn xây dựng các giao diện năng động và phản ứng với người dùng một cách chuyên nghiệp. Bạn giờ đã có thể tự mình xây dựng các cấu trúc phức tạp trên trang web rồi đấy!

