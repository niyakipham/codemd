# Hành Trình Làm Chủ Lập Trình Bash Scripting

Xin chào các bạn! Hôm nay, chúng ta sẽ cùng nhau khai phá một trong những công cụ mạnh mẽ và linh hoạt nhất trong thế giới hệ điều hành Unix/Linux: **Bash Scripting**. Bash không chỉ đơn thuần là cái "vỏ" (shell) để bạn gõ lệnh, mà nó còn là một ngôn ngữ lập trình đích thực, giúp bạn tự động hóa công việc, quản lý hệ thống, và thực hiện hàng loạt các tác vụ phức tạp chỉ với vài dòng mã.

Tài liệu này sẽ đưa bạn đi từ những khái niệm cơ bản nhất cho đến những kỹ thuật nâng cao, giúp bạn xây dựng nên những script hiệu quả và mạnh mẽ. Hãy cùng nhau đi sâu vào từng ngóc ngách của Bash nhé!

---

## Mục Lục (Table of Contents)

1.  [Giới thiệu về Bash](#1-giới-thiệu-về-bash)
    *   Bash là gì? Bourne Again SHell.
    *   Lịch sử và Vai trò.
    *   Tại sao lại học Bash Scripting?
2.  [Bắt Đầu: Script Bash Đầu Tiên](#2-bắt-đầu-script-bash-đầu-tiên)
    *   Tạo và Lưu file Script (.sh).
    *   Dòng Shebang `#!/bin/bash`.
    *   Cấp Quyền Thực thi (`chmod +x`).
    *   Chạy Script.
    *   Thêm Chú thích (Comments).
3.  [Biến và Dữ Liệu trong Bash](#3-biến-và-dữ-liệu-trong-bash)
    *   Khai báo và Sử dụng Biến.
    *   Gán Giá trị và Truy cập Biến.
    *   Biến Môi trường (Environment Variables).
    *   Biến Đặc biệt (Special Variables).
    *   Kiểu dữ liệu (hoạt động như chuỗi mặc định).
    *   Biến cục bộ trong hàm.
4.  [Thao Tác Input/Output (I/O) Cơ Bản](#4-thao-tác-inputoutput-io-cơ-bản)
    *   In Output ra màn hình (`echo`).
    *   Đọc Input từ người dùng (`read`).
    *   Sử dụng Herestring/Here Document.
5.  [Các Loại Toán Tử và Biểu Thức](#5-các-loại-toán-tử-và-biểu-thức)
    *   Toán tử Số học (Arithmetic Operators).
    *   Toán tử So sánh (Comparison Operators - Số học & Chuỗi).
    *   Toán tử Logic (Logical Operators - `&&`, `||`, `!`).
    *   Sử dụng `[[...]]` và `((...))`.
6.  [Cấu Trúc Điều Khiển (Control Flow)](#6-cấu-trúc-điều-khiển-control-flow)
    *   Câu lệnh `if`, `elif`, `else`.
    *   Kiểm tra điều kiện (`test`, `[` , `[[`).
    *   Câu lệnh `case`.
7.  [Vòng Lặp (Loops)](#7-vòng-lặp-loops)
    *   Vòng lặp `for`.
        *   Lặp qua danh sách.
        *   Lặp theo kiểu C-style.
    *   Vòng lặp `while`.
    *   Vòng lặp `until`.
    *   Các lệnh điều khiển vòng lặp (`break`, `continue`).
8.  [Hàm (Functions)](#8-hàm-functions)
    *   Khai báo và Gọi Hàm.
    *   Tham số của Hàm.
    *   Giá trị trả về của Hàm (Return Status & Output).
    *   Biến cục bộ (local variables).
9.  [Mảng (Arrays)](#9-mảng-arrays)
    *   Khai báo Mảng.
    *   Truy cập phần tử Mảng.
    *   Kích thước Mảng.
    *   Lặp qua Mảng.
    *   Mảng liên hợp (Associative Arrays - Bash 4+).
10. [Thao Tác Với Chuỗi (String Manipulation)](#10-thao-tác-với-chuỗi-string-manipulation)
    *   Độ dài Chuỗi.
    *   Trích xuất Chuỗi con.
    *   Thay thế và Xóa Chuỗi con.
    *   So sánh Chuỗi.
11. [Thao Tác Với File và Directory](#11-thao-tác-với-file-và-directory)
    *   Kiểm tra sự tồn tại, loại và quyền hạn của File/Directory (`-f`, `-d`, `-r`, `-w`, `-x`, etc.).
    *   Đọc nội dung File.
    *   Ghi nội dung vào File.
12. [Quản Lý Tiến Trình (Process Management)](#12-quản-lý-tiến-trình-process-management)
    *   Thực thi lệnh bên ngoài.
    *   PID (Process ID).
    *   Chờ tiến trình kết thúc (`wait`).
    *   Gửi tín hiệu (`kill`).
13. [Xử Lý Lỗi và Mã Thoát (Error Handling & Exit Codes)](#13-xử-lý-lỗi-và-mã-thoát-error-handling--exit-codes)
    *   Mã thoát của lệnh (`$?`).
    *   Thoát script với mã cụ thể (`exit`).
    *   Redirect Output và Error.
14. [Regex và Các Công Cụ Văn Bản Mạnh Mẽ (grep, sed, awk)](#14-regex-và-các-công-cụ-văn-bản-mạnh-mẽ-grep-sed-awk)
    *   Giới thiệu về Regex.
    *   `grep`: Tìm kiếm theo mẫu.
    *   `sed`: Chỉnh sửa dòng (Stream Editor).
    *   `awk`: Xử lý văn bản theo cột và mẫu.
15. [Chuyển Hướng I/O (Redirection) và Pipes](#15-chuyển-hướng-io-redirection-và-pipes)
    *   `>`, `>>`: Chuyển hướng Output Stdout.
    *   `2>`: Chuyển hướng Output Stderr.
    *   `&>`: Chuyển hướng cả Stdout & Stderr.
    *   `<`: Chuyển hướng Input Stdin.
    *   Pipes (`|`): Kết nối output của lệnh này với input của lệnh khác.
16. [Quản Lý Job (Job Control - Background/Foreground)](#16-quản-lý-job-job-control---backgroundforeground)
    *   Chạy lệnh nền (`&`).
    *   Đưa lệnh nền ra trước (`fg`).
    *   Đưa lệnh trước vào nền (`bg`).
    *   Danh sách các job (`jobs`).
17. [Tín Hiệu (Signals) và Bẫy (Trap)](#17-tín-hiệu-signals-và-bẫy-trap)
    *   Giới thiệu về Signals (SIGINT, SIGTERM, SIGHUP...).
    *   Sử dụng lệnh `trap` để bắt và xử lý tín hiệu.
    *   Trap EXIT cho việc dọn dẹp.
18. [Mở Rộng Biến Nâng Cao (Advanced Parameter Expansion)](#18-mở-rộng-biến-nâng-cao-advanced-parameter-expansion)
    *   Mặc định giá trị (`${var:-word}`, `${var:=word}`).
    *   Báo lỗi nếu biến rỗng (`${var:?message}`).
    *   Sử dụng giá trị khác (`${var:+word}`).
    *   Loại bỏ tiền tố/hậu tố (`${var%word}`, `${var%%word}`, `${var#word}`, `${var##word}`).
    *   Tìm và thay thế (`${var/pattern/string}`, `${var//pattern/string}`).
    *   Độ dài, chỉ mục/phần tử.
19. [Debugging Script Bash](#19-debugging-script-bash)
    *   Các tùy chọn Debug: `set -x`, `set -v`, `set -e`.
    *   Sử dụng các công cụ khác.
20. [Viết Script Bash Mạnh Mẽ và Bảo Mật (Best Practices)](#20-viết-script-bash-mạnh-mẽ-và-bảo-mật-best-practices)
    *   Luôn sử dụng Shebang.
    *   Sử dụng tùy chọn `set -euo pipefail`.
    *   Đóng ngoặc kép cho biến và tham số.
    *   Sử dụng hàm cho các tác vụ lặp lại.
    *   Kiểm tra Input đầu vào.
    *   Viết code dễ đọc (thụt lề, chú thích).
    *   Tránh Parse Output của `ls`.
21. [Các Ví Dụ Thực Tế (Real-world Examples)](#21-các-ví-dụ-thực-tế-real-world-examples)
    *   Script sao lưu file đơn giản.
    *   Script giám sát dung lượng đĩa.
    *   Script xử lý hàng loạt file.
    *   Script tự động hóa tác vụ định kỳ (Cron jobs).
22. [Kết Luận và Bước Tiếp Theo](#22-kết-luận-và-bước-tiếp-theo)
    *   Tóm tắt.
    *   Tài nguyên học thêm.
    *   Khuyến khích thực hành.

---

## 1. Giới thiệu về Bash

### Bash là gì? Bourne Again SHell

Bash là tên viết tắt của **B**ourne **A**gain **SH**ell. Nó là trình thông dịch lệnh (command interpreter) hoặc "vỏ" (shell) phổ biến nhất được sử dụng trên hầu hết các hệ điều hành dựa trên Unix và Linux. Khi bạn mở một cửa sổ terminal, bạn đang tương tác với một shell, và rất có thể đó là Bash.

### Lịch sử và Vai trò

Bash được phát triển bởi Brian Fox cho dự án GNU vào năm 1989 như là một phiên bản thay thế miễn phí và cải tiến cho Bourne Shell (sh) ban đầu được viết bởi Stephen Bourne. Nó tích hợp các tính năng hữu ích từ KornShell (ksh) và C Shell (csh).

Vai trò chính của Bash là:
*   **Giao diện tương tác:** Nhận lệnh từ người dùng thông qua bàn phím và thực thi chúng.
*   **Ngôn ngữ Scripting:** Cho phép viết các chương trình (script) để tự động hóa các tác vụ hoặc kết hợp nhiều lệnh với nhau.

### Tại sao lại học Bash Scripting?

*   **Tự động hóa:** Biến các chuỗi lệnh lặp đi lặp lại thành script chạy tự động.
*   **Quản lý Hệ thống:** Thực hiện các tác vụ quản trị như quản lý file, cài đặt phần mềm, giám sát hệ thống.
*   **Tích hợp:** Kết nối các chương trình tiện ích khác nhau trên hệ thống (như `grep`, `sed`, `awk`, `find`, v.v.) một cách mạnh mẽ.
*   **Tiện lợi:** Giải quyết nhanh các bài toán xử lý dữ liệu, xử lý văn bản mà không cần viết code bằng các ngôn ngữ phức tạp hơn.
*   **Phổ biến:** Bash có mặt hầu như trên mọi máy chủ Linux, macOS (trước đây), và cả Windows thông qua WSL (Windows Subsystem for Linux).

---

## 2. Bắt Đầu: Script Bash Đầu Tiên

Script Bash chỉ đơn giản là một file văn bản chứa một loạt các lệnh theo thứ tự mà bạn muốn thực thi.

### Tạo và Lưu file Script (.sh)

Bạn có thể sử dụng bất kỳ trình soạn thảo văn bản nào (như `nano`, `vim`, `gedit`, `VS Code`, v.v.) để tạo file script. Tên file thường kết thúc bằng đuôi `.sh` theo quy ước, ví dụ: `hello.sh`.

```bash
# Mở trình soạn thảo nano
nano hello.sh
```

Sau đó gõ nội dung sau vào file:

```bash
#!/bin/bash
# Đây là script Bash đầu tiên của chúng ta!

echo "Xin chào, thế giới Bash!"
```

Lưu file (Ctrl+O, Enter, Ctrl+X nếu dùng nano).

### Dòng Shebang `#!/bin/bash`

Dòng đầu tiên trong script, bắt đầu bằng `#!`, được gọi là **Shebang**. Nó chỉ cho hệ điều hành biết trình thông dịch nào (interpreter) sẽ được sử dụng để thực thi script này. `#!/bin/bash` có nghĩa là script này sẽ được thực thi bởi chương trình `/bin/bash`. Luôn luôn thêm dòng này vào đầu các script Bash của bạn!

### Cấp Quyền Thực thi (`chmod +x`)

Theo mặc định, file bạn tạo không có quyền thực thi. Bạn cần cấp quyền này để có thể chạy nó như một chương trình:

```bash
chmod +x hello.sh
```

Lệnh này thêm quyền thực thi (`+x`) cho chủ sở hữu file.

### Chạy Script

Bây giờ bạn có thể chạy script bằng cách gọi đường dẫn tương đối hoặc tuyệt đối đến file:

```bash
./hello.sh
```

Hoặc nếu bạn ở thư mục khác:

```bash
/path/to/your/script/hello.sh
```

Output sẽ là:

```
Xin chào, thế giới Bash!
```

### Thêm Chú thích (Comments)

Các dòng bắt đầu bằng `#` được coi là chú thích và sẽ bị bỏ qua khi script thực thi. Chú thích rất quan trọng để giải thích mã của bạn, giúp người khác (và chính bạn sau này) dễ hiểu hơn. Dòng Shebang là trường hợp ngoại lệ, nó bắt đầu bằng `#!` nhưng được hệ điều hành hiểu theo cách đặc biệt.

---

## 3. Biến và Dữ Liệu trong Bash

Biến (Variable) là các thùng chứa (containers) để lưu trữ dữ liệu trong script của bạn.

### Khai báo và Sử dụng Biến

Trong Bash, việc khai báo biến rất đơn giản. Bạn chỉ cần gán giá trị cho một tên:

```bash
ten="Alice"
tuoi=30
duong_dan="/home/user/documents"
```

**Lưu ý quan trọng:** Khi gán giá trị cho biến, **không được có khoảng trắng** xung quanh dấu `=`.

```bash
# Sai: ten = "Bob"
# Sai: duong_dan = "/tmp"

# Đúng: ten="Bob"
# Đúng: duong_dan="/tmp"
```

### Gán Giá trị và Truy cập Biến

Để truy cập giá trị của một biến, bạn đặt ký tự `$` trước tên biến:

```bash
#!/bin/bash

my_name="AI Vui Tinh"
greeting="Chào bạn,"

echo "$greeting $my_name!"
echo "Hôm nay là một ngày đẹp trời!"

# Cập nhật giá trị biến
my_name="Trợ lý Bá đạo"

echo "Bây giờ tôi là: $my_name"
```

Khi sử dụng biến trong chuỗi hoặc khi cần rõ ràng ranh giới tên biến (ví dụ: nối tên biến với ký tự khác), nên dùng cú pháp `${ten_bien}`:

```bash
file_name="bao_cao"
extension=".txt"

# Tốt hơn so với $file_name$extension
echo "${file_name}${extension}" # Output: bao_cao.txt

# Nếu chỉ dùng $variable thì cũng được trong trường hợp này
echo "$file_name$extension" # Output: bao_cao.txt

# Ví dụ cần thiết dùng {}
duoi="txt"
echo "Ten file co duoi ${duoi}ty" # Output: Ten file co duoi txtty
# echo "Ten file co duoi $duoisty" # --> Bash se tim bien $duoisty thay vi $duoi noi voi 'sty'
```

### Biến Môi trường (Environment Variables)

Đây là các biến được hệ điều hành và shell sử dụng để lưu trữ thông tin cấu hình môi trường làm việc. Chúng thường được viết hoa.
Ví dụ: `PATH`, `HOME`, `USER`, `LANG`, `PWD`.
Bạn có thể xem tất cả biến môi trường bằng lệnh `env` hoặc `printenv`.
Bạn có thể truy cập chúng giống như biến thường: `echo $HOME`, `echo $PATH`.

Để khai báo một biến môi trường *mới* cho các lệnh *con* được sinh ra từ shell hiện tại, bạn sử dụng lệnh `export`:

```bash
export MY_CONFIG="path/to/config.file"
```
Các biến không dùng `export` là biến **local** chỉ có giá trị trong shell hiện tại hoặc script hiện tại.

### Biến Đặc biệt (Special Variables)

Bash có một số biến đặc biệt được tự động cập nhật bởi shell, rất hữu ích trong script:

*   `$0`: Tên của script đang chạy.
*   `$1`, `$2`, `$3`, ...: Các tham số truyền vào script (đối số). `$1` là tham số đầu tiên, `$2` là tham số thứ hai, v.v.
*   `$#`: Tổng số tham số được truyền vào.
*   `$?`: Mã thoát (exit code) của lệnh cuối cùng vừa được thực thi. `0` thường nghĩa là thành công, khác `0` là có lỗi.
*   `$$`: PID (Process ID) của script hiện tại.
*   `$*`: Biểu diễn tất cả các tham số dưới dạng một chuỗi duy nhất (mỗi tham số cách nhau bởi ký tự phân cách được định nghĩa trong biến `$IFS`). `"$*"` giữ nguyên sự phân cách này.
*   `$@`: Biểu diễn tất cả các tham số dưới dạng một danh sách các chuỗi riêng biệt. `" $@ "` là cách dùng phổ biến nhất, nó mở rộng thành các tham số riêng biệt, mỗi tham số được đóng trong ngoặc kép, ví dụ: nếu input là `a "b c" d`, thì `"$@"` sẽ là `"a"` `"b c"` `"d"`.

**Ví dụ:**

```bash
#!/bin/bash
# Luu ten file script: arguments.sh

echo "Ten script: $0"
echo "So tham so: $#"
echo "Tham so dau tien: $1"
echo "Tham so thu hai: $2"
echo "Tat ca tham so (\$*): $*"
echo "Tat ca tham so (\$@): $@"

echo "---"
echo "Vong lap voi \$*:"
for arg in $*; do
  echo "- $arg"
done

echo "---"
echo "Vong lap voi \$@:"
for arg in $@; do
  echo "- $arg"
done

echo "---"
echo "Vong lap voi \"\$@\":" # Luu y dau ngoac kep
for arg in "$@"; do
  echo "- $arg"
done
```

Chạy script:

```bash
./arguments.sh mot "hai ba" bon
```

Output:

```
Ten script: ./arguments.sh
So tham so: 3
Tham so dau tien: mot
Tham so thu hai: hai ba
Tat ca tham so ($*): mot hai ba bon
Tat ca tham so ($@): mot hai ba bon
---
Vong lap voi $*:
- mot
- hai
- ba
- bon
---
Vong lap voi $@:
- mot
- hai
- ba
- bon
---
Vong lap voi "$@":
- mot
- hai ba
- bon
```
Ví dụ trên minh họa sự khác biệt quan trọng giữa `$*` và `" $@" `. Luôn luôn ưu tiên sử dụng `"$@"` khi bạn cần xử lý từng tham số một, đặc biệt khi các tham số có khoảng trắng.

### Kiểu dữ liệu (hoạt động như chuỗi mặc định)

Bash xử lý *tất cả* biến dưới dạng chuỗi ký tự (string). Tuy nhiên, khi bạn thực hiện các phép toán số học trong môi trường đặc biệt (như `((...))` hoặc lệnh `let`), Bash sẽ tự động diễn giải giá trị là số nếu có thể.

```bash
#!/bin/bash

a="10"
b="20"
chuoi="xin chao"

# Toán học đơn giản (se hieu la string, ket qua la ghep chuoi)
# ketqua=$a + $b # SE KHONG HOAT DONG THEO Y MUON SO HOC

# Sử dụng $((...)) để thực hiện tính toán số học
tong=$(( a + b ))
echo "Tong so hoc: $tong" # Output: 30

# Phep toan voi bien khong phai so? Bao loi.
# phep_loi=$(( a + chuoi )) # --> error

# Chuỗi vẫn là chuỗi
chuoi_moi="$a $b"
echo "Ket hop chuoi: $chuoi_moi" # Output: 10 20
```

### Biến cục bộ trong hàm

Mặc định, biến trong Bash là biến toàn cục. Để tạo biến cục bộ chỉ tồn tại trong hàm, bạn dùng từ khóa `local`:

```bash
#!/bin/bash

bien_toan_cuc="Toan cuc ngoai ham"

ham_demo() {
  local bien_cuc_bo="Cuc bo trong ham"
  echo "Trong ham:"
  echo "Bien toan cuc: $bien_toan_cuc"
  echo "Bien cuc bo: $bien_cuc_bo"
  bien_toan_cuc="Da thay doi trong ham" # Thay doi bien toan cuc
}

echo "Ngoai ham (truoc khi goi ham):"
echo "Bien toan cuc: $bien_toan_cuc"
# echo "Bien cuc bo: $bien_cuc_bo" # SE BAO LOI hoac rong vi chua ton tai/la rong

ham_demo

echo "Ngoai ham (sau khi goi ham):"
echo "Bien toan cuc: $bien_toan_cuc"
# echo "Bien cuc bo: $bien_cuc_bo" # Van bao loi/rong
```
Output:
```
Ngoai ham (truoc khi goi ham):
Bien toan cuc: Toan cuc ngoai ham
Trong ham:
Bien toan cuc: Toan cuc ngoai ham
Bien cuc bo: Cuc bo trong ham
Ngoai ham (sau khi goi ham):
Bien toan cuc: Da thay doi trong ham
```
Sử dụng `local` là Best Practice để tránh xung đột tên biến không mong muốn, đặc biệt trong các script lớn hoặc khi sử dụng các hàm được viết bởi người khác.

---

## 4. Thao Tác Input/Output (I/O) Cơ Bản

Giao tiếp với người dùng hoặc hiển thị thông tin là tác vụ thiết yếu của script.

### In Output ra màn hình (`echo`)

Lệnh `echo` được dùng để hiển thị dòng văn bản lên màn hình (chuẩn đầu ra - standard output).

```bash
echo "Xin chao!"
echo "Day la mot dong khac."

# Su dung ky tu dac biet (\n: new line, \t: tab, ...) can them tuy chon -e
echo -e "Dong dau tien\nDung \ttep theo"
```
Output:
```
Xin chao!
Day la mot dong khac.
Dong dau tien
	Tep theo
```

*   `-n`: Không thêm ký tự xuống dòng cuối cùng.

```bash
echo -n "Day la dong ma "
echo "se tiep tuc ngay ben canh."
```
Output:
```
Day la dong ma se tiep tuc ngay ben canh.
```

Bạn có thể sử dụng `printf` thay cho `echo` cho khả năng định dạng phức tạp hơn, tương tự như hàm `printf` trong ngôn ngữ C.

```bash
printf "Ten: %s\nTuoi: %d\n" "Bob" 25
```
Output:
```
Ten: Bob
Tuoi: 25
```

### Đọc Input từ người dùng (`read`)

Lệnh `read` dùng để đọc một dòng input từ chuẩn đầu vào (standard input), thường là từ bàn phím, và lưu trữ vào một biến.

```bash
#!/bin/bash

echo "Nhap ten cua ban:"
read ten_cua_ban
echo "Chao mung, $ten_cua_ban!"

# Doc input ma khong in ky tu (password)
read -s -p "Nhap mat khau cua ban: " mat_khau
echo # Xuong dong sau khi nhap mat khau
echo "Mat khau da nhap (khong in ra that): ${mat_khau}"

# Doc nhieu bien tren cung mot dong
read -p "Nhap ten va tuoi (cach nhau bang khoang trang): " ten tuoi
echo "Ten: $ten, Tuoi: $tuoi"
```
*   `-p "Prompt"`: Hiển thị lời nhắc trước khi đọc input.
*   `-s`: Không hiển thị input trên màn hình (Silent).
*   `-r`: Không xử lý ký tự thoát ngược `\`. Nên dùng tùy chọn này để tránh các lỗi không mong muốn khi nhập đường dẫn chứa ký tự thoát ngược.

### Sử dụng Herestring/Here Document

Đây là các cách để cung cấp một khối văn bản làm input cho một lệnh.

*   **Here String (`<<<`)**: Cung cấp một chuỗi duy nhất làm standard input.

    ```bash
    doc="Day la mot chuoi nhieu dong\nva day la dong thu hai."
    grep "dong" <<< "$doc" # Tìm kiếm "dong" trong biến $doc
    ```
    Output:
    ```
    Day la mot chuoi nhieu dong
    va day la dong thu hai.
    ```
*   **Here Document (`<<EOF` hoặc `<<'END'`)**: Cung cấp một khối văn bản nhiều dòng làm standard input. Sử dụng `EOF` hoặc một từ đánh dấu bất kỳ, và kết thúc khối bằng chính từ đó ở một dòng riêng biệt. Nếu sử dụng `<<-`, thụt lề bằng tab ở đầu dòng sẽ bị loại bỏ. Nếu sử dụng `<<'EOF'` (có dấu ngoặc kép), các biến và lệnh bên trong khối sẽ không được mở rộng.

    ```bash
    cat << EOF
    Day la dong 1.
    Day la dong 2 cua
    Here Document.
    Variables work here: $USER
    EOF
    ```
    Output (giả sử USER là `tester`):
    ```
    Day la dong 1.
    Day la dong 2 cua
    Here Document.
    Variables work here: tester
    ```

    ```bash
    cat << 'END_TEXT'
    Variables do NOT work here: $USER
    Neither do commands: $(pwd)
    END_TEXT
    ```
    Output:
    ```
    Variables do NOT work here: $USER
    Neither do commands: $(pwd)
    ```

---

## 5. Các Loại Toán Tử và Biểu Thức

Bash hỗ trợ các phép toán số học, so sánh và logic.

### Toán tử Số học (Arithmetic Operators)

Bạn có thể thực hiện tính toán số học bên trong biểu thức `((...))` hoặc với lệnh `let`. Các toán tử bao gồm: `+`, `-`, `*`, `/`, `%` (modulo), `**` (lũy thừa), `++` (tăng), `--` (giảm).

```bash
#!/bin/bash

a=10
b=3

# Sử dụng $((...))
tong=$((a + b))
hieu=$((a - b))
tich=$((a * b))
thuong=$((a / b)) # Ket qua nguyen (integer division)
du=$((a % b))

echo "a = $a, b = $b"
echo "Tong: $tong"     # Output: 13
echo "Hieu: $hieu"     # Output: 7
echo "Tich: $tich"     # Output: 30
echo "Thuong: $thuong"   # Output: 3
echo "Du: $du"        # Output: 1

# Increment/Decrement
((a++)) # a tro thanh 11
echo "a sau khi tang: $a"
((b--)) # b tro thanh 2
echo "b sau khi giam: $b"

# Tính luỹ thừa
luy_thua=$((2**3)) # 2 mũ 3
echo "Luy thua: $luy_thua" # Output: 8

# Lưu ý: $b cần phải được đóng trong ngoặc kép khi sử dụng ở các ngữ cảnh khác để tránh lỗi
# Nếu $b là kết quả của một lệnh hoặc chứa ký tự đặc biệt. Tuy nhiên trong ((...)) hoặc [[...]] thì thường không cần.
```
Kết quả của `((...))` có thể được sử dụng như mã thoát: 0 nếu biểu thức đúng, 1 nếu sai.

### Toán tử So sánh (Comparison Operators)

Có hai bộ toán tử so sánh chính:
*   **Toán tử số học:** Dùng để so sánh các *số nguyên*. Chỉ sử dụng trong `((...))` hoặc `[[...]]`.
    *   `-eq`: Equal (Bằng)
    *   `-ne`: Not Equal (Không bằng)
    *   `-gt`: Greater Than (Lớn hơn)
    *   `-lt`: Less Than (Nhỏ hơn)
    *   `-ge`: Greater than or Equal (Lớn hơn hoặc bằng)
    *   `-le`: Less than or Equal (Nhỏ hơn hoặc bằng)
*   **Toán tử chuỗi:** Dùng để so sánh các *chuỗi*. Sử dụng trong `[[...]]` hoặc `[... ]`.
    *   `=`, `==`: Equal (Bằng). `= ` được sử dụng trong `[ ... ]` để so sánh chuỗi, `==` được khuyến khích dùng trong `[[ ... ]]` và cho phép so sánh regex.
    *   `!=`: Not Equal (Không bằng).
    *   `<`: Nhỏ hơn theo thứ tự từ điển (Lexicographical Less Than).
    *   `>`: Lớn hơn theo thứ tự từ điển (Lexicographical Greater Than).
    *   `-z`: Chuỗi rỗng (độ dài bằng 0).
    *   `-n`: Chuỗi không rỗng (độ dài > 0).

**Ví dụ:**

```bash
#!/bin/bash

so1=15
so2=10
chuoi1="apple"
chuoi2="banana"
chuoi3=""

# So sánh số học trong [[...]]
if [[ $so1 -gt $so2 ]]; then
  echo "$so1 lon hon $so2"
fi

if [[ $((so1 % so2)) -ne 5 ]]; then # Ket hop toan tu so hoc va so sanh
  echo "15 % 10 khong bang 5"
fi

# So sánh chuỗi trong [[...]]
if [[ "$chuoi1" != "$chuoi2" ]]; then
  echo "$chuoi1 khac $chuoi2"
fi

if [[ "$chuoi3" == "" ]]; then # Hoặc dùng -z
  echo "Chuoi 3 rong"
fi
if [[ -z "$chuoi3" ]]; then
  echo "Chuoi 3 rong (dung -z)"
fi

if [[ -n "$chuoi1" ]]; then
  echo "Chuoi 1 khong rong"
fi

# So sánh chuỗi theo thứ tự từ điển
if [[ "$chuoi1" < "$chuoi2" ]]; then # 'a' < 'b'
  echo "$chuoi1 dung truoc $chuoi2 theo bang chu cai"
fi
```

**Lưu ý về `[` và `[[`:**
*   `[` thực chất là một lệnh alias cho `test`. Nó cũ hơn, tương thích hơn trên các hệ thống Unix khác nhau, nhưng có cú pháp hạn chế hơn. Ví dụ: không hỗ trợ toán tử logic `&&`, `||` trực tiếp bên trong, cần dùng `-a`, `-o`; không hỗ trợ so sánh regex; dễ gặp lỗi nếu biến chứa khoảng trắng và không được đóng ngoặc kép.
*   `[[` là từ khóa tích hợp sẵn của Bash. Nó mới hơn, linh hoạt và mạnh mẽ hơn. Hỗ trợ `&&`, `||`, `=~` (regex match). Đây là cú pháp được khuyến khích sử dụng trong script Bash hiện đại.
**Luôn dùng dấu ngoặc kép cho biến khi sử dụng trong `[ ... ]` để tránh lỗi phân tách từ (word splitting) hoặc mở rộng đường dẫn (pathname expansion). Với `[[ ... ]]`, bạn *thường* không cần dấu ngoặc kép trừ khi cần đảm bảo biến trống được coi là rỗng hoàn toàn trong các phép so sánh regex hoặc các trường hợp phức tạp khác, nhưng việc đóng ngoặc kép *không gây hại* và thường là thói quen tốt.**

### Toán tử Logic (Logical Operators - `&&`, `||`, `!`)

Kết hợp các điều kiện logic.
*   `&&`: AND logic (Đúng nếu cả hai vế đúng). `lenh1 && lenh2`: thực thi `lenh2` CHỈ khi `lenh1` thành công (mã thoát 0).
*   `||`: OR logic (Đúng nếu ít nhất một vế đúng). `lenh1 || lenh2`: thực thi `lenh2` CHỈ khi `lenh1` thất bại (mã thoát khác 0).
*   `!`: NOT logic (Phủ định).

Có thể sử dụng trong `if` hoặc `[[...]]` hoặc trực tiếp giữa các lệnh.

```bash
#!/bin/bash

a=10
b=20

# Trong [[...]]
if [[ $a -lt $b && $b -gt 15 ]]; then
  echo "a < b VA b > 15"
fi

if [[ $a -eq 5 || $b -eq 20 ]]; then
  echo "a == 5 HOAC b == 20"
fi

if [[ ! ( $a -gt $b ) ]]; then
  echo "Khong phai a > b (tuc la a <= b)"
fi

echo "---"

# Giua cac lenh (dựa vào exit code)
echo "Lenh 1" && echo "Lenh 2 chay vi Lenh 1 thanh cong"

false_command () { return 1; } # Ham luon tra ve ma thoat 1 (false)
false_command || echo "Lenh 2 chay vi Lenh 1 that bai"
```
Output:
```
a < b VA b > 15
a == 5 HOAC b == 20
Khong phai a > b (tuc la a <= b)
---
Lenh 1
Lenh 2 chay vi Lenh 1 thanh cong
Lenh 2 chay vi Lenh 1 that bai
```

### Sử dụng `[[...]]` và `((...))`

*   `[[...]]`: Dùng để đánh giá biểu thức có điều kiện, thường kết hợp với các toán tử so sánh chuỗi (`==`, `!=`, `<`, `>`, `-z`, `-n`), số học (`-eq`, `-ne`, `-gt`, etc.) và logic (`&&`, `||`, `!`). Nó mạnh mẽ hơn `[...]`.
*   `((...))`: Dùng để đánh giá biểu thức số học. Biến bên trong không cần dùng `$`. Nó cũng có thể dùng như biểu thức điều kiện, trả về 0 nếu kết quả khác 0 (true), và 1 nếu kết quả bằng 0 (false).

```bash
#!/bin/bash

count=5

# Sử dụng ((...)) trong điều kiện
if (( count > 0 && (count % 5) == 0 )); then
  echo "Count ($count) lon hon 0 va la boi so cua 5."
fi

# Sử dụng [[...]] với toán tử so sánh file (sẽ học sau)
# if [[ -f "/etc/passwd" ]]; then
#  echo "File /etc/passwd ton tai."
# fi
```

---

## 6. Cấu Trúc Điều Khiển (Control Flow)

Cấu trúc điều khiển cho phép script đưa ra quyết định dựa trên các điều kiện.

### Câu lệnh `if`, `elif`, `else`

Cú pháp cơ bản:

```bash
if [ condition ]; then
  # code khi condition dung
elif [ other_condition ]; then # Elif la optional, co the co nhieu Elif
  # code khi condition truoc sai, other_condition dung
else # Else la optional
  # code khi tat ca cac condition tren sai
fi
```

Sử dụng `[[ condition ]]` được khuyến khích thay vì `[ condition ]`.

```bash
#!/bin/bash

diem=75

if [[ $diem -ge 90 ]]; then
  echo "Dat loai A"
elif [[ $diem -ge 80 ]]; then
  echo "Dat loai B"
elif [[ $diem -ge 70 ]]; then
  echo "Dat loai C"
else
  echo "Can co gang them"
fi

# Ví dụ kiem tra file
ten_file="my_script.sh"

if [[ -f "$ten_file" ]]; then
  echo "$ten_file la mot file thuong."
elif [[ -d "$ten_file" ]]; then
  echo "$ten_file la mot thu muc."
else
  echo "$ten_file khong ton tai hoac co kieu khac."
fi
```
Xem phần [11. Thao Tác Với File và Directory](#11-thao-tác-với-file-và-directory) để biết thêm về các phép kiểm tra file/directory.

### Kiểm tra điều kiện (`test`, `[`, `[[`)

*   `test condition`: Đánh giá một điều kiện. Mã thoát là 0 (thành công) nếu điều kiện đúng, 1 nếu sai.
*   `[ condition ]`: Tương đương với `test condition`, `[ ]` chỉ là một cách viết khác.
*   `[[ condition ]]`: Tích hợp sẵn của Bash, mạnh mẽ hơn (`&&`, `||`, `=~`, tránh lỗi word splitting/pathname expansion).

Tất cả đều có thể được sử dụng sau `if` hoặc trong vòng lặp `while`/`until`.

### Câu lệnh `case`

Câu lệnh `case` cho phép bạn so khớp một giá trị (thường là giá trị của một biến) với nhiều mẫu khác nhau và thực hiện các khối code tương ứng. Tương tự như `switch` trong các ngôn ngữ khác.

```bash
#!/bin/bash

lua_chon="$1" # Doc tham so dau tien

case "$lua_chon" in
  "bat dau" | "start") # Nhieu mau co the cach nhau bang |
    echo "Khoi dong dich vu..."
    ;; # Ket thuc mot nhan (pattern)
  "dung" | "stop")
    echo "Ngung dich vu..."
    ;;
  "khoi dong lai" | "restart")
    echo "Khoi dong lai dich vu..."
    ;;
  "trang_thai")
    echo "Kiem tra trang thai..."
    ;;
  *) # Nhan mac dinh (catch-all), chay neu khong khop voi mau nao tren
    echo "Lua chon '$lua_chon' khong hop le."
    echo "Su dung: $0 {bat dau|dung|khoi dong lai|trang_thai}"
    exit 1 # Thoat voi ma loi
    ;;
esac

# Mã thoát thành công nếu một trong các trường hợp trên được khớp (trừ *)
exit 0
```

Lưu ý: Dấu `;;` kết thúc mỗi "nhãn" trong `case`. Dấu `*)` bắt tất cả các trường hợp còn lại. `esac` kết thúc khối `case`. Nên đóng ngoặc kép `"$biến"` để tránh các vấn đề nếu biến trống hoặc chứa ký tự đặc biệt.

---

## 7. Vòng Lặp (Loops)

Vòng lặp cho phép thực thi một khối code nhiều lần.

### Vòng lặp `for`

#### Lặp qua danh sách

Cú pháp cơ bản lặp qua các phần tử trong một danh sách (từ, chuỗi, kết quả lệnh, etc.):

```bash
for bien_lap in danh_sach; do
  # code thuc thi voi moi gia tri cua bien_lap
done
```
Danh sách có thể là chuỗi các từ cách nhau bởi khoảng trắng (hoặc ký tự trong `$IFS`), các mẫu file (wildcards), hoặc kết quả của phép mở rộng chuỗi/biến.

```bash
#!/bin/bash

echo "Lặp qua danh sách chuỗi:"
for item in "apple" "banana" "cherry" "date"; do
  echo "- $item"
done

echo "Lặp qua các số (sequence):"
for i in {1..5}; do
  echo "Số: $i"
done

echo "Lặp qua các file trong thư mục hiện tại:"
for file in *.txt; do
  echo "File text tìm thấy: $file"
done
```

#### Lặp theo kiểu C-style

Cú pháp quen thuộc với lập trình viên từ C/C++/Java/JavaScript, sử dụng `((...))` cho điều kiện và các biểu thức khởi tạo/cập nhật.

```bash
for ((khoi_tao; dieu_kien; cap_nhat)); do
  # code thuc thi
done
```

```bash
#!/bin/bash

echo "Lặp C-style từ 1 đến 10:"
for (( i=1; i<=10; i++ )); do
  # Các biến trong ((...)) khong can $ khi dung noi bo
  tong=$((tong + i)) # Su dung $i de truy cap trong code ben trong do..done
  echo "i = $i"
done
echo "Tổng từ 1 đến 10: $tong" # tong bien luy ke ngoai vong lap
```

### Vòng lặp `while`

Vòng lặp `while` thực thi một khối code **trong khi** một điều kiện còn đúng.

```bash
while [ condition ]; do # hoac while [[ condition ]]; do, hoac while (( condition )); do
  # code thuc thi khi condition dung
done
```

```bash
#!/bin/bash

count=5

while [[ $count -gt 0 ]]; do
  echo "Đếm ngược: $count"
  ((count--)) # Giảm count di 1
  sleep 1 # Tam dung 1 giay
done
echo "Hết giờ!"

echo "---"

# Doc file tung dong mot
echo "Noi dung file /etc/passwd (vài dòng đầu):"
while read -r line; do # -r tranh xu ly ky tu thoat nguoc '\'
  echo "-> $line"
done < /etc/passwd | head -n 3 # Đọc 3 dòng đầu của /etc/passwd
```
`read -r line` rất phổ biến khi đọc file. Nó đọc từng dòng vào biến `line`. Toán tử `< file` chuyển hướng nội dung file làm input cho vòng lặp `while`. `| head -n 3` chỉ lấy 3 dòng đầu tiên để tránh in toàn bộ file `/etc/passwd`.

### Vòng lặp `until`

Vòng lặp `until` thực thi một khối code **cho đến khi** một điều kiện trở thành đúng. Tức là nó chạy khi điều kiện là *sai*.

```bash
until [ condition ]; do # hoac until [[ condition ]]; do, hoac until (( condition )); do
  # code thuc thi khi condition SAI
done
```

```bash
#!/bin/bash

thanh_cong=false

until [[ "$thanh_cong" == "true" ]]; do
  echo "Dang thu ket noi den may chu..."
  # Mô phỏng viec thu ket noi (gia dinh lenh nay se return 0 khi thanh cong)
  if (( RANDOM % 2 == 0 )); then # Gia dinh 50% thanh cong
    echo "Ket noi thanh cong!"
    thanh_cong=true
  else
    echo "Ket noi that bai, thu lai..."
    sleep 2
  fi
done

echo "Thoat khoi vong lap until."
```

### Các lệnh điều khiển vòng lặp (`break`, `continue`)

*   `break`: Thoát khỏi vòng lặp gần nhất ngay lập tức.
*   `continue`: Bỏ qua phần còn lại của lần lặp hiện tại và chuyển sang lần lặp tiếp theo.

```bash
#!/bin/bash

echo "Ví dụ về break:"
for i in {1..10}; do
  if [[ $i -eq 5 ]]; then
    echo "Gap 5, thoat vong lap!"
    break # Thoat khoi vong for
  fi
  echo "Số hiện tại: $i"
done

echo "---"

echo "Ví dụ về continue:"
for j in {1..10}; do
  if [[ $((j % 2)) -ne 0 ]]; then
    echo "$j là số lẻ, bỏ qua..."
    continue # Chuyen sang lan lap tiep theo
  fi
  echo "Số chẵn hiện tại: $j"
done
```

---

## 8. Hàm (Functions)

Hàm (Functions) cho phép nhóm một khối code thành một đơn vị có thể tái sử dụng. Giúp code gọn gàng, dễ quản lý và tránh lặp lại.

### Khai báo và Gọi Hàm

Có hai cách khai báo hàm trong Bash:

1.  Sử dụng từ khóa `function` (linh hoạt hơn một chút với ngoặc đơn):
    ```bash
    function ten_ham {
      # code trong ham
    }
    ```
2.  Cú pháp đơn giản hơn (thường dùng):
    ```bash
    ten_ham () {
      # code trong ham
    }
    ```
Sau khi khai báo, bạn gọi hàm đơn giản bằng tên của nó:

```bash
#!/bin/bash

# Khai bao ham
chao_buoi_sang() {
  echo "Chúc buổi sáng tốt lành!"
}

# Goi ham
chao_buoi_sang
chao_buoi_sang
```

### Tham số của Hàm

Tham số truyền vào hàm được truy cập giống như tham số truyền vào script, sử dụng các biến đặc biệt: `$1`, `$2`, ... `$#`, `$*`, `$@`.

```bash
#!/bin/bash

chao_ten() {
  if [[ $# -eq 0 ]]; then
    echo "Xin chào, bạn chưa nhập tên!"
  else
    echo "Xin chào, $1!" # Tham so dau tien
    echo "Các tham số khác: $@"
    echo "Tổng số tham số: $#"
  fi
}

chao_ten "Alice"
echo "---"
chao_ten "Bob" "tran" "tai"
echo "---"
chao_ten # Goi ham khong co tham so
```

### Giá trị trả về của Hàm (Return Status & Output)

Hàm trong Bash có hai loại "giá trị trả về":

1.  **Mã thoát (Exit Status/Return Status):** Là một số nguyên từ 0-255, báo hiệu thành công (0) hay thất bại (khác 0) của hàm. Sử dụng lệnh `return` để thiết lập mã thoát của hàm. Mã thoát của hàm được truy cập bằng `$?` sau khi gọi hàm, giống như các lệnh khác. Nếu hàm không có lệnh `return` tường minh, mã thoát của nó là mã thoát của lệnh cuối cùng trong hàm.
2.  **Standard Output (Kết quả):** Là văn bản mà hàm in ra standard output (dùng `echo`, `printf`, hoặc output của các lệnh khác). Đây là cách phổ biến nhất để "trả về" dữ liệu thực tế từ hàm. Output này có thể được "bắt" vào một biến bằng phép thay thế lệnh (command substitution): `$(ten_ham ...)`.

```bash
#!/bin/bash

kiem_tra_so() {
  local so="$1"
  if (( so % 2 == 0 )); then
    echo "Số $so là số chẵn."
    return 0 # 0: thanh cong
  else
    echo "Số $so là số lẻ."
    return 1 # 1: that bai
  fi
}

lay_thoi_gian() {
  date +"%H:%M:%S" # In gio phut giay
}

kiem_tra_so 10
exit_code=$?
echo "Mã thoát của kiem_tra_so 10: $exit_code"

kiem_tra_so 7
exit_code=$?
echo "Mã thoát của kiem_tra_so 7: $exit_code"

thoi_gian_hien_tai=$(lay_thoi_gian) # Bat output cua ham vao bien
echo "Thời gian hiện tại từ hàm: $thoi_gian_hien_tai"
```

Output:
```
Số 10 là số chẵn.
Mã thoát của kiem_tra_so 10: 0
Số 7 là số lẻ.
Mã thoát của kiem_tra_so 7: 1
Thời gian hiện tại từ hàm: XX:YY:ZZ (giờ hiện tại)
```

### Biến cục bộ (local variables)

Như đã đề cập ở phần biến, sử dụng `local bien_ten=gia_tri` trong hàm là best practice để tránh ghi đè lên các biến có cùng tên ở phạm vi ngoài hàm (global) và giữ cho hàm độc lập.

---

## 9. Mảng (Arrays)

Mảng là một tập hợp các phần tử được lưu trữ tuần tự dưới một tên biến duy nhất. Bash hỗ trợ mảng chỉ mục (indexed arrays - bắt đầu từ index 0) và mảng liên hợp (associative arrays - sử dụng chuỗi làm key, yêu cầu Bash 4+).

### Khai báo Mảng

*   Mảng chỉ mục:
    ```bash
    mang_chi_muc=(phan_tu1 phan_tu2 phan_tu3)
    ```
    Hoặc gán từng phần tử:
    ```bash
    mang_chi_muc[0]="phan_tu_dau"
    mang_chi_muc[1]="phan_tu_hai"
    ```
*   Mảng liên hợp (cần `declare -A` và Bash 4+):
    ```bash
    declare -A mang_lien_hop
    mang_lien_hop[key1]="gia_tri1"
    mang_lien_hop[key2]="gia_tri2"
    ```

### Truy cập phần tử Mảng

*   Mảng chỉ mục: ` ${ten_mang[index]} `
*   Mảng liên hợp: ` ${ten_mang[key]} `

```bash
#!/bin/bash

# Mảng chỉ mục
cac_loai_trai_cay=("apple" "banana" "cherry")
echo "Phần tử đầu tiên: ${cac_loai_trai_cay[0]}" # Output: apple
echo "Phần tử thứ hai: ${cac_loai_trai_cay[1]}" # Output: banana

# Gán lại hoặc thêm phần tử
cac_loai_trai_cay[3]="date" # Thêm phần tử thứ 4
cac_loai_trai_cay[1]="berry" # Thay đổi phần tử thứ hai
echo "Mảng sau khi sửa đổi: ${cac_loai_trai_cay[@]}" # Output: apple berry cherry date

# Mảng liên hợp (Bash 4+)
if declare -A test 2>/dev/null; then # Kiem tra xem bash co ho tro mang lien hop khong
  declare -A sinh_vien
  sinh_vien[id]="SV001"
  sinh_vien[ten]="Nguyen Van A"
  sinh_vien[diem]=9.5

  echo "Thông tin sinh viên:"
  echo "ID: ${sinh_vien[id]}"       # Output: SV001
  echo "Tên: ${sinh_vien[ten]}"     # Output: Nguyen Van A
  echo "Điểm: ${sinh_vien[diem]}"   # Output: 9.5

  # In tat ca keys hoac values
  echo "Keys: ${!sinh_vien[@]}"  # Output cac key: diem id ten (thu tu co the khac)
  echo "Values: ${sinh_vien[@]}" # Output cac value: 9.5 SV001 Nguyen Van A (thu tu tuong ung voi keys)
fi
```

### Kích thước Mảng

Sử dụng `${#ten_mang[@]}` hoặc `${#ten_mang[*]}` để lấy số lượng phần tử.

```bash
#!/bin/bash
cac_loai_trai_cay=("apple" "banana" "cherry" "date")
echo "Số lượng trái cây: ${#cac_loai_trai_cay[@]}" # Output: 4
```

### Lặp qua Mảng

Sử dụng vòng lặp `for` với `${ten_mang[@]}` hoặc `${ten_mang[*]}`.

```bash
#!/bin/bash
cac_loai_trai_cay=("apple" "banana" "cherry" "date")

echo "Danh sách trái cây:"
for trai_cay in "${cac_loai_trai_cay[@]}"; do # Luon dung ngoac kep "$@" de xu ly cac phan tu co khoang trang
  echo "- $trai_cay"
done

# Lặp qua index (mảng chỉ mục)
echo "Lặp qua index:"
for index in "${!cac_loai_trai_cay[@]}"; do
  echo "Index $index: ${cac_loai_trai_cay[index]}"
done
```
**Quan trọng:** Luôn sử dụng ngoặc kép cho `"${mang[@]}"` hoặc `"${mang[*]"` để mỗi phần tử của mảng được coi là một chuỗi riêng biệt ngay cả khi nó chứa khoảng trắng. Sử dụng `"${!mang[@]}"` để lặp qua các chỉ mục/keys của mảng.

---

## 10. Thao Tác Với Chuỗi (String Manipulation)

Bash có khả năng thao tác chuỗi đáng ngạc nhiên ngay từ cú pháp mở rộng biến (Parameter Expansion).

### Độ dài Chuỗi

Sử dụng `${#ten_bien}`.

```bash
#!/bin/bash
my_string="Xin chào thế giới"
echo "Chuỗi: $my_string"
echo "Độ dài chuỗi: ${#my_string}" # Output: 17
```

### Trích xuất Chuỗi con

Sử dụng `${chuoi:vi_tri:do_dai}`. Vị trí bắt đầu từ 0. Độ dài là số ký tự cần lấy.

```bash
#!/bin/bash
my_string="Lập trình Bash rất thú vị!"

# Lấy 5 ký tự đầu tiên (từ index 0)
sub_string_1=${my_string:0:5}
echo "5 ký tự đầu: $sub_string_1" # Output: Lập t

# Lấy từ index 6 cho đến hết
sub_string_2=${my_string:6}
echo "Từ index 6 đến hết: $sub_string_2" # Output: trình Bash rất thú vị!

# Lấy 4 ký tự cuối cùng (vị trí âm tính từ cuối lên)
sub_string_3=${my_string: -5:4} # Lưu ý khoảng trắng sau : khi dùng vị trí âm
echo "4 ký tự cuối: $sub_string_3" # Output: vị!

# Cũng có thể dùng ${#my_string} để tính vị trí kết thúc
start_pos=$(( ${#my_string} - 5 ))
sub_string_4=${my_string:start_pos:4}
echo "4 ký tự cuối (cách khác): $sub_string_4" # Output: vị!
```

### Thay thế và Xóa Chuỗi con

Sử dụng `${chuoi/mau/thay_the}` và các biến thể.

*   `${chuoi/mau/thay_the}`: Thay thế lần xuất hiện đầu tiên của `mau` bằng `thay_the`.
*   `${chuoi//mau/thay_the}`: Thay thế **tất cả** lần xuất hiện của `mau` bằng `thay_the`.
*   `${chuoi/mau/}`: Xóa lần xuất hiện đầu tiên của `mau`.
*   `${chuoi//mau/}`: Xóa **tất cả** lần xuất hiện của `mau`.
*   `mau` có thể là một pattern đơn giản hoặc mẫu Regex.

```bash
#!/bin/bash
file_name="bao_cao_final_v1.txt"

# Thay the dau tien
new_name1=${file_name/v1/v2}
echo "Thay thế 'v1' bằng 'v2': $new_name1" # Output: bao_cao_final_v2.txt

path="/usr/local/bin:/home/user/scripts:/usr/bin"
# Thay the tat ca dau ':' bang '-'
new_path=${path//:/ - }
echo "Thay thế tất cả ':' bằng '-': $new_path" # Output: /usr/local/bin - /home/user/scripts - /usr/bin

text="xin chao xin mung ban da den"
# Xoa lan xuat hien dau tien
text_xoa_dau=${text/xin chao/}
echo "Xóa lần đầu 'xin chao': $text_xoa_dau" # Output:  xin mung ban da den (lưu ý khoảng trắng ban đầu)

# Xoa tat ca
text_xoa_het=${text//xin/}
echo "Xóa tất cả 'xin': $text_xoa_het" # Output:  chao  mung ban da den (lưu ý khoảng trắng)

# Thay the dua tren regex (dung =~)
text_with_nums="san pham id=12345 va code=abcde"
# Thay the tat ca cac chu so ([0-9]+) thanh "[NUMBER]"
if [[ "$text_with_nums" =~ [0-9]+ ]]; then # Kiem tra ton tai mau regex truoc
    # ((chuoi // regex / thay the)): can bash 4+, it pho bien, hay dung sed hon
    # sed 's/[0-9]\+/[NUMBER]/g' <<< "$text_with_nums"
    # Cách truyền thống hơn
    text_san_pham_sach=$(echo "$text_with_nums" | sed 's/[[:digit:]]\+/[NUMBER]/g')
    echo "Thay số bằng [NUMBER] (dùng sed): $text_san_pham_sach" # Output: san pham id=[NUMBER] va code=abcde
fi
```

### So sánh Chuỗi

Sử dụng các toán tử `=` (hoặc `==` trong `[[ ... ]]`), `!=`, `<`, `>`. Đã đề cập trong mục [5. Các Loại Toán Tử và Biểu Thức](#5-các-loại-toán-tử-và-biểu-thức).

---

## 11. Thao Tác Với File và Directory

Bash có các toán tử điều kiện mạnh mẽ để kiểm tra thuộc tính của file và directory trong câu lệnh `test` (`[ ... ]`) hoặc `[[ ... ]]`.

Các toán tử kiểm tra file/directory phổ biến (dùng trong `if [ ... ]` hoặc `if [[ ... ]]`):

*   `-a file`: `file` tồn tại. (Tương tự `-e`)
*   `-e file`: `file` tồn tại.
*   `-f file`: `file` tồn tại và là một file thường.
*   `-d file`: `file` tồn tại và là một directory.
*   `-s file`: `file` tồn tại và không rỗng (kích thước lớn hơn 0).
*   `-L file`: `file` tồn tại và là symbolic link.
*   `-b file`: `file` tồn tại và là block device.
*   `-c file`: `file` tồn tại và là character device.
*   `-p file`: `file` tồn tại và là named pipe (FIFO).
*   `-S file`: `file` tồn tại và là socket.
*   `-t fd`: File descriptor `fd` (ví dụ: 0 cho stdin, 1 cho stdout, 2 cho stderr) được mở trên một terminal.
*   `-r file`: Chủ sở hữu hiệu lực có quyền đọc `file`.
*   `-w file`: Chủ sở hữu hiệu lực có quyền ghi `file`.
*   `-x file`: Chủ sở hữu hiệu lực có quyền thực thi `file`.
*   `-g file`: Sticky bit hoặc set-group-ID bit được đặt.
*   `-k file`: Sticky bit được đặt.
*   `-u file`: Set-user-ID bit được đặt.
*   `-O file`: Chủ sở hữu hiệu lực sở hữu `file`.
*   `-G file`: Chủ sở hữu hiệu lực có nhóm (`gid`) trùng với nhóm của `file`.
*   `file1 -nt file2`: `file1` mới hơn `file2`.
*   `file1 -ot file2`: `file1` cũ hơn `file2`.
*   `file1 -ef file2`: `file1` và `file2` cùng trỏ tới cùng một inode (cùng file).

**Ví dụ:**

```bash
#!/bin/bash

test_file="/tmp/my_test_file.txt"
test_dir="/tmp/my_test_dir"

# Xoa file/dir cu neu ton tai de test moi
[[ -e "$test_file" ]] && rm "$test_file"
[[ -d "$test_dir" ]] && rm -r "$test_dir"

# Tao file va dir de test
touch "$test_file"
mkdir "$test_dir"

# Kiem tra su ton tai va loai
if [[ -e "$test_file" ]]; then
  echo "$test_file ton tai."
fi
if [[ -f "$test_file" ]]; then
  echo "$test_file la file thuong."
fi
if [[ -d "$test_dir" ]]; then
  echo "$test_dir la directory."
fi

# Kiem tra quyen
if [[ -w "$test_file" ]]; then
  echo "$test_file co quyen ghi."
fi
if [[ -x "$test_dir" ]]; then
  echo "$test_dir co quyen thuc thi (di vao)."
fi

# Kiem tra kich thuoc file
if [[ ! -s "$test_file" ]]; then
  echo "$test_file dang rong."
fi

# Don dep
rm "$test_file"
rm -r "$test_dir"
```

### Đọc nội dung File

Sử dụng vòng lặp `while read` (đã ví dụ ở mục Vòng lặp) hoặc các lệnh tiện ích như `cat`, `head`, `tail`, `less`.

```bash
# Đọc toàn bộ file
cat ten_file.txt

# Đọc các dòng đầu/cuối
head -n 5 ten_file.txt
tail -n 10 ten_file.txt

# Đọc từng từ hoặc từng ký tự
# Vòng lặp read có thể dùngIFS (Internal Field Separator) để đọc tung tu hoac ky tu
echo "a:b:c:d" | while IFS=: read -r p1 p2 p3 p4; do
  echo "Truong 1: $p1, Truong 2: $p2"
done
```

### Ghi nội dung vào File

Sử dụng chuyển hướng Output (`>`, `>>`).

```bash
# Ghi đè nội dung vào file (xóa nội dung cũ)
echo "Day la dong moi nhat" > output.txt

# Thêm nội dung vào cuối file (giữ nội dung cũ)
echo "Day la dong duoc them vao" >> output.txt

# Ghi output của một lệnh vào file
ls -l > file_list.txt

# Ghi output của script vào file
{
  echo "Start time: $(date)"
  echo "Script executing..."
  # ... code logic ...
  echo "End time: $(date)"
} > log_file.txt # Toan bo output trong {} se duoc ghi vao file
```

---

## 12. Quản Lý Tiến Trình (Process Management)

Script Bash thường cần thực thi các lệnh khác và đôi khi tương tác với chúng như các tiến trình con.

### Thực thi lệnh bên ngoài

Đơn giản chỉ cần viết tên lệnh cùng các tham số. Bash sẽ tìm lệnh đó trong `PATH` và thực thi nó như một tiến trình con.

```bash
# Thuc thi mot lenh
ls -l

# Thuc thi mot script khac
./other_script.sh arg1 arg2
```

Bash tạo một tiến trình con (child process) cho mỗi lệnh thực thi bên ngoài hoặc mỗi script con. Biến và môi trường trong script con là bản sao từ script cha, các thay đổi trong script con không ảnh hưởng đến script cha (trừ khi sử dụng lệnh `source` hoặc `.`).

### PID (Process ID)

`$$`: PID của shell/script hiện tại.
`$!`: PID của lệnh nền (background command) được chạy gần nhất.

```bash
#!/bin/bash
echo "PID cua script nay: $$"

# Chay mot lenh nen va in PID cua no
sleep 10 &
echo "PID cua lenh sleep chay nen: $!"
```

### Chờ tiến trình kết thúc (`wait`)

Lệnh `wait [pid]` đợi cho tiến trình con có PID được chỉ định kết thúc. Nếu không có PID, nó đợi tất cả các tiến trình con đang chạy nền kết thúc.

```bash
#!/bin/bash

echo "Bat dau hai tien trinh nen..."

# Chay cac tien trinh nen
sleep 5 &
pid1=$!
echo "Sleep 5s chay nen voi PID $pid1"

sleep 3 &
pid2=$!
echo "Sleep 3s chay nen voi PID $pid2"

echo "Dang doi tien trinh $pid1 ket thuc..."
wait $pid1
echo "Tien trinh $pid1 da ket thuc."

echo "Dang doi tien trinh $pid2 ket thuc..."
wait $pid2
echo "Tien trinh $pid2 da ket thuc."

echo "Tat ca tien trinh nen da xong."
```

### Gửi tín hiệu (`kill`)

Lệnh `kill [signal] pid` gửi một tín hiệu (signal) đến tiến trình có PID được chỉ định. Tín hiệu phổ biến:
*   `SIGTERM` (15): Yêu cầu tiến trình thoát một cách "nhã nhặn".
*   `SIGKILL` (9): Buộc tiến trình thoát ngay lập tức, không thể bị bắt bởi `trap`.
*   `SIGHUP` (1): Gửi tín hiệu cho tiến trình daemon để tải lại cấu hình.
Bạn có thể dùng tên tín hiệu (ví dụ: `-SIGTERM`, `-KILL`) hoặc số (`-15`, `-9`). Mặc định là `SIGTERM`.

```bash
#!/bin/bash

echo "Chay mot lenh lau nen..."
sleep 30 & # Chay sleep 30 giay nen
bg_pid=$!
echo "Lenh sleep chay nen voi PID $bg_pid"

echo "Doi 3 giay..."
sleep 3

echo "Gui tin hieu SIGTERM ($bg_pid)..."
kill $bg_pid # Gui SIGTERM

echo "Doi 5 giay de no ket thuc..."
wait $bg_pid
echo "Lenh sleep (co the) da ket thuc."
```

---

## 13. Xử Lý Lỗi và Mã Thoát (Error Handling & Exit Codes)

Viết script cần đáng tin cậy đòi hỏi khả năng xử lý lỗi hiệu quả.

### Mã thoát của lệnh (`$?`)

Như đã nói, `$?` chứa mã thoát của lệnh hoặc hàm cuối cùng. `0` thường biểu thị thành công, bất kỳ giá trị khác `0` nào là lỗi.

```bash
#!/bin/bash

# Lệnh thành công
ls /tmp
echo "Ma thoat cua 'ls /tmp': $?" # Output: 0 (neu thanh cong)

# Lệnh thất bại
ls /duong/dan/khong/ton/tai
echo "Ma thoat cua 'ls /duong/dan/khong/ton/tai': $?" # Output: 2 (thuong la 1 hoac 2)

# Kiểm tra mã thoát trong if
if ls /home; then
  echo "Lenh ls /home thanh cong!"
fi

if ! ls /duong/dan/khong/ton/tai; then # Su dung ! phu dinh dieu kien kiem tra ma thoat 0
  echo "Lenh ls den duong dan sai da that bai nhu du kien."
fi
```

### Thoát script với mã cụ thể (`exit`)

Lệnh `exit [ma_thoat]` dừng thực thi script ngay lập tức và trả về mã thoát được chỉ định. Mặc định là 0.

```bash
#!/bin/bash

echo "Bat dau script"

# ... code ...

# Kiểm tra một điều kiện lỗi
if [[ ! -f "required_file.txt" ]]; then
  echo "ERROR: File required_file.txt khong ton tai!" >&2 # In ra standard error
  exit 1 # Thoat script voi ma loi 1
fi

# ... code tiep neu khong co loi ...

echo "Ket thuc script thanh cong."
exit 0 # Thoat script voi ma thanh cong
```
Sử dụng `>&2` để in thông báo lỗi ra kênh lỗi chuẩn (standard error - fd 2) thay vì kênh output chuẩn (standard output - fd 1). Điều này hữu ích khi chuyển hướng output và error ra các nơi khác nhau.

### Redirect Output và Error

Đã giới thiệu trong mục [15. Chuyển Hướng I/O (Redirection) và Pipes](#15-chuyển-hướng-io-redirection-và-pipes). Kỹ thuật này quan trọng để quản lý output/error khi chạy script.

```bash
# Chuyen huong Stdout vao file (ghi de)
my_command > output.txt

# Chuyen huong Stderr vao file (ghi de)
my_command 2> error.txt

# Chuyen huong ca Stdout va Stderr vao file (ghi de)
my_command &> all_output.txt # Tuong duong my_command > all_output.txt 2>&1

# Chuyen huong Stderr vao Stdout, sau do Stdout vao file
my_command > output_and_error.txt 2>&1 # Dung cho bash cu hoac chi ro rang hon

# Chuyen huong Stdout vao file, Stderr vao file khac
my_command > output.txt 2> error.txt

# Gui output vao /dev/null de bo qua
my_command > /dev/null # Chi bo qua Stdout
my_command &> /dev/null # Bo qua ca Stdout va Stderr
```

### Sử dụng tùy chọn `set -e`

Thêm `set -e` vào đầu script (hoặc sau shebang) là một kỹ thuật xử lý lỗi mạnh mẽ. Nó khiến script tự động dừng (exit) ngay lập tức nếu có bất kỳ lệnh nào trả về mã thoát khác 0 (bị lỗi). Điều này giúp ngăn chặn script tiếp tục chạy với trạng thái không mong muốn sau một lỗi.

```bash
#!/bin/bash
set -e # Nếu bất kỳ lệnh nào sau đây bị lỗi, script sẽ dừng

echo "Bước 1: Bắt đầu"

mkdir /tmp/my_temp_dir # Thành công, mã thoát 0

echo "Bước 2: Tạo thư mục thành công"

# Giả sử file khong ton tai
rm non_existent_file.txt # Sẽ báo lỗi và có mã thoát khác 0

# Nếu khong co 'set -e', script se tiep tuc chạy đến đây:
# echo "Bước 3: Dòng này sẽ không bao giờ chạy nếu lệnh rm lỗi và có set -e"
```
Sử dụng `set -e` cùng với `set -u`, `set -o pipefail` (đề cập ở Best Practices) tạo nên các script đáng tin cậy hơn rất nhiều.

---

## 14. Regex và Các Công Cụ Văn Bản Mạnh Mẽ (grep, sed, awk)

Bash scripting thường làm việc song song với các tiện ích dòng lệnh kinh điển để xử lý văn bản dựa trên Biểu thức Chính quy (Regular Expressions - Regex).

### Giới thiệu về Regex

Regex là một chuỗi ký tự tạo thành một mẫu (pattern) dùng để so khớp, tìm kiếm và thay thế văn bản. Chúng cực kỳ mạnh mẽ nhưng cú pháp ban đầu có thể hơi khó hiểu.

Ví dụ Regex cơ bản:
*   `.`: Bất kỳ ký tự nào (trừ ký tự xuống dòng).
*   `*`: Xuất hiện 0 hoặc nhiều lần của ký tự/nhóm ký tự đứng trước.
*   `+`: Xuất hiện 1 hoặc nhiều lần.
*   `?`: Xuất hiện 0 hoặc 1 lần.
*   `{n}`: Xuất hiện đúng `n` lần.
*   `{n,}`: Xuất hiện ít nhất `n` lần.
*   `{n,m}`: Xuất hiện từ `n` đến `m` lần.
*   `^`: Khớp với điểm bắt đầu của dòng.
*   `$`: Khớp với điểm kết thúc của dòng.
*   `[abc]`: Khớp với 'a', 'b', hoặc 'c'.
*   `[^abc]`: Khớp với bất kỳ ký tự nào ngoại trừ 'a', 'b', 'c'.
*   `[a-z]`: Khớp với bất kỳ ký tự thường nào từ a đến z.
*   `\d`: Khớp với một chữ số ([0-9]).
*   `\w`: Khớp với ký tự chữ, số hoặc gạch dưới ([a-zA-Z0-9_]).
*   `\s`: Khớp với khoảng trắng.
*   `(...)`: Gom nhóm các mẫu.
*   `|`: OR logic giữa các mẫu (a|b khớp a hoặc b).

### `grep`: Tìm kiếm theo mẫu

Lệnh `grep` tìm kiếm các dòng trong file (hoặc input từ pipe) khớp với một mẫu Regex.

```bash
# Tim cac dong chua tu 'error' trong file log
grep "error" application.log

# Tim cac dong chua tu 'warning' hoac 'error' (su dung -E cho Extended Regex)
grep -E "warning|error" application.log

# Tim cac dong bat dau bang 'PID:'
grep "^PID:" system.log

# Tim cac dong KHONG chua 'info'
grep -v "info" system.log

# Tim kiem trong nhieu file
grep "failed" /var/log/*.log

# Dem so luong dong khop
grep -c "Connected" history.log

# Hien thi so dong cua ket qua
grep -n "config" configuration.txt
```
Xem thêm: `man grep`

### `sed`: Chỉnh sửa dòng (Stream Editor)

Lệnh `sed` chủ yếu dùng để tìm và thay thế văn bản trên dòng (stream) dựa trên mẫu Regex, nhưng cũng có thể dùng để xóa dòng, chèn dòng, v.v. Nó không thay đổi file gốc trừ khi bạn chuyển hướng output hoặc dùng tùy chọn `-i`.

Cú pháp thay thế phổ biến: `sed 's/mau_tim_kiem/chuoi_thay_the/options' file`.

```bash
# Thay the lan dau tien cua "error" bang "ERROR" tren moi dong
sed 's/error/ERROR/' application.log

# Thay the TAT CA cac lan cua "warning" bang "WARN" tren moi dong
sed 's/warning/WARN/g' application.log # 'g' = global

# Xoa cac dong trong
sed '/^$/d' file_with_blank_lines.txt # '^$': khop dong trong; 'd': xoa dong

# Them "LINE: " vao dau moi dong
sed 's/^/LINE: /' input.txt

# Thay the dau cach = dau phay trong file (lan dau tien)
sed 's/ /,/' data.txt

# Thay the dau cach = dau phay (tat ca)
sed 's/ /,/g' data.txt

# Luu thay doi vao file goc (dung -i)
#sed -i 's/old_text/new_text/g' my_file.conf # Can than khi dung -i!
```
Xem thêm: `man sed`

### `awk`: Xử lý văn bản theo cột và mẫu

Lệnh `awk` là một ngôn ngữ xử lý văn bản mạnh mẽ hơn, làm việc dựa trên các "record" (mặc định là dòng) và "fields" (mặc định là các cột phân tách bằng khoảng trắng). Nó cho phép thực thi các action (code) khi một pattern khớp.

Cú pháp cơ bản: `awk 'pattern { action }' file`.
Pattern có thể là Regex, điều kiện, BEGIN/END. Action là các lệnh awk.

```bash
# In toan bo file (default action: { print } )
awk '{ print }' data.txt # Tuong duong voi cat data.txt

# In cot dau tien va cot thu ba
awk '{ print $1, $3 }' data.txt

# In cac dong chua tu 'success'
awk '/success/ { print }' logfile.log # hoac don gian la awk '/success/' logfile.log

# Tinh tong cot thu 2
awk '{ sum+=$2 } END { print "Tong:", sum }' numbers.txt # BEGIN/END action

# Xu ly du lieu tu /etc/passwd
awk -F':' '{ print "User:", $1, "Home Dir:", $6 }' /etc/passwd # -F: quy dinh ky tu phan cach cot
```
Xem thêm: `man awk`

Kết hợp `grep`, `sed`, `awk` thông qua pipe (`|`) là một kỹ thuật rất mạnh mẽ trong Bash scripting.

```bash
# Liet ke file, chi lay cot quyen va ten, chi loc file bat dau bang 'my_', thay the ten = [FILE NAME]
ls -l | grep "^-rwx" | awk '{ print $1, $9 }' | sed 's/my_.*\.txt$/[FILE NAME]/g'
```

---

## 15. Chuyển Hướng I/O (Redirection) và Pipes

Mục này đã được đề cập rải rác ở trên, giờ chúng ta tổng hợp và đi sâu hơn một chút. Unix/Linux có 3 standard streams:

*   `0`: Standard Input (stdin) - nơi chương trình đọc dữ liệu đầu vào (thường là bàn phím).
*   `1`: Standard Output (stdout) - nơi chương trình ghi dữ liệu đầu ra thông thường (thường là màn hình).
*   `2`: Standard Error (stderr) - nơi chương trình ghi thông báo lỗi (thường là màn hình).

### Chuyển hướng Output

*   `command > file`: Chuyển hướng stdout của `command` vào `file`, **ghi đè** nếu file tồn tại. `1> file` tương đương.
*   `command >> file`: Chuyển hướng stdout của `command` vào `file`, **thêm vào cuối** nếu file tồn tại. `1>> file` tương đương.
*   `command 2> file`: Chuyển hướng stderr của `command` vào `file`, **ghi đè**.
*   `command 2>> file`: Chuyển hướng stderr của `command` vào `file`, **thêm vào cuối**.
*   `command &> file`: Chuyển hướng cả stdout và stderr vào `file`, **ghi đè**. Bash mới hơn.
*   `command > file 2>&1`: Chuyển hướng stdout vào `file`, sau đó chuyển hướng stderr vào cùng nơi với stdout. Cú pháp cũ nhưng phổ biến. `>& file` là cú pháp tắt tương đương `>&1 file`.

### Chuyển hướng Input

*   `command < file`: Chuyển hướng nội dung của `file` làm stdin cho `command`.

```bash
#!/bin/bash

# Tạo file thử nghiệm
echo "Dong 1" > test_io.txt
echo "Dong 2 co the bi loi" >> test_io.txt # Dung thu dong nay co the gay loi sau

# Ghi stdout vao file
echo "Ghi chu" > output_file.txt

# Ghi stderr vao file
ls /duong/dan/khong/ton/tai 2> error_file.txt

# Ghi ca hai vao cung file
cat test_io.txt my_non_exist_file.txt &> all_output.txt

# Doc input tu file
while read -r line; do
  echo "Đọc từ file: $line"
done < test_io.txt
```

### Pipes (`|`)

Pipe (`|`) dùng để "ống" output chuẩn (stdout) của lệnh bên trái làm input chuẩn (stdin) cho lệnh bên phải. Cực kỳ hữu ích để kết hợp nhiều lệnh nhỏ thành một pipeline xử lý phức tạp.

```bash
# Liet ke cac file .sh trong thu muc hien tai va sap xep
ls *.sh | sort

# Dem so luong user trong he thong
cat /etc/passwd | wc -l

# Tim kiem cac tien trinh dang chay chua 'bash'
ps aux | grep "bash" | grep -v "grep" # Loai bo chinh lenh grep ra

# Loc file, sap xep nguoc, chi lay 5 dong cuoi
cat some_file.txt | grep "keyword" | sort -r | tail -n 5
```
Lưu ý khi sử dụng `set -o pipefail`: Nếu một lệnh bất kỳ trong chuỗi pipe bị lỗi (mã thoát khác 0), toàn bộ pipe sẽ trả về mã lỗi của lệnh đó, thay vì chỉ trả về mã thoát của lệnh cuối cùng (hành vi mặc định của Bash).

---

## 16. Quản Lý Job (Job Control - Background/Foreground)

Trên môi trường tương tác, bạn có thể đưa các lệnh ra chạy nền (background) hoặc đưa chúng trở lại chạy trước (foreground). Script cũng có thể sử dụng tính năng này.

### Chạy lệnh nền (`&`)

Thêm dấu `&` vào cuối một lệnh để chạy nó ở chế độ nền, shell sẽ ngay lập tức trả về dấu nhắc lệnh và bạn có thể chạy lệnh khác.

```bash
# Chay sleep 30 giay nen
sleep 30 &

# Shell se tro lai ngay va in [job_id] pid
# Ban co the tiep tuc go lenh
echo "Lenh sleep dang chay nen voi PID $!" # $! la PID cua lenh nen gan nhat
```

### Đưa lệnh nền ra trước (`fg`)

Lệnh `fg [job_id]` đưa một job đang chạy nền trở lại foreground. Nếu không có `job_id`, nó sẽ đưa job chạy nền gần nhất (hiển thị khi dùng lệnh `jobs`) ra trước. `job_id` thường có dạng `%1`, `%2`, v.v.

```bash
# Goi lenh sleep 30 nen
sleep 30 &
# Quay lai shell

# Go lenh jobs de xem danh sach cac jobs
jobs
# [1]+ Running    sleep 30 &

# Dua job nay ra truoc
fg %1
# Bây giờ bạn sẽ bị "block" bởi lệnh sleep 30 đang chạy lại ở foreground.
# Nhấn Ctrl+C để kết thúc hoặc Ctrl+Z để tạm dừng và đưa lại ra nền.
```

### Đưa lệnh trước vào nền (`bg`)

Nếu một lệnh đang chạy ở foreground và bạn nhấn `Ctrl+Z`, nó sẽ bị tạm dừng. Lệnh `bg [job_id]` sẽ tiếp tục chạy job đã bị tạm dừng ở chế độ nền.

```bash
# Chay mot lenh lau
long_running_command # lenh dang chay o foreground

# Nhấn Ctrl+Z
# [1]+ Stopped    long_running_command

# Tiep tuc chay no o nen
bg %1
# [1]+ long_running_command &

# Bay gio no dang chay o nen
jobs
# [1]+ Running    long_running_command &
```

### Danh sách các job (`jobs`)

Lệnh `jobs` hiển thị danh sách các job đang chạy nền hoặc đang bị tạm dừng trong shell hiện tại.

```bash
sleep 10 &
sleep 20 &
jobs
# [1]- Running    sleep 10 &
# [2]+ Running    sleep 20 &
```
Số trong ngoặc vuông là `job_id`. Dấu `+` chỉ job gần nhất sẽ được `fg` hoặc `bg` mặc định. Dấu `-` chỉ job kế tiếp.

---

## 17. Tín Hiệu (Signals) và Bẫy (Trap)

Hệ điều hành gửi các tín hiệu (signals) đến các tiến trình để thông báo các sự kiện (ví dụ: interrupt - Ctrl+C, terminate - kill command, hangup - terminal closed). Tiến trình có thể xử lý (bắt) các tín hiệu này. Lệnh `trap` trong Bash cho phép script của bạn "bẫy" các tín hiệu và thực thi một đoạn code khi tín hiệu đó xảy ra.

### Giới thiệu về Signals (SIGINT, SIGTERM, SIGHUP...)

Xem danh sách đầy đủ các tín hiệu với `kill -l`. Một vài tín hiệu phổ biến:
*   `SIGINT` (2): Interrupt from keyboard (khi nhấn Ctrl+C).
*   `SIGTERM` (15): Software termination signal (mặc định của lệnh `kill`).
*   `SIGHUP` (1): Hangup (thường khi terminal đóng).
*   `SIGKILL` (9): Kill signal (không thể bị bắt hoặc bỏ qua).
*   `SIGQUIT` (3): Quit from keyboard (khi nhấn Ctrl+\).

### Sử dụng lệnh `trap` để bắt và xử lý tín hiệu

Cú pháp: `trap 'command(s)' signals`. `command(s)` là code sẽ chạy khi một trong các `signals` xảy ra. `signals` có thể là tên (ví dụ: `SIGINT`) hoặc số (ví dụ: `2`).

```bash
#!/bin/bash

# Đặt trap cho tín hiệu SIGINT (Ctrl+C)
trap 'echo -e "\nỒ! Bạn vừa nhấn Ctrl+C. Script sẽ dừng lại."; exit 1' SIGINT

echo "Script đang chạy. Nhấn Ctrl+C để dừng lại một cách an toàn."
while true; do
  echo "Đang làm gì đó... $$"
  sleep 5
done
```
Khi chạy script này và nhấn Ctrl+C, thông báo thân thiện sẽ hiện ra thay vì bị dừng đột ngột bởi tín hiệu mặc định.

Bạn cũng có thể bỏ qua tín hiệu bằng cách đặt `trap '' signal` hoặc khôi phục hành vi mặc định bằng `trap - signal`.

```bash
#!/bin/bash

echo "Bo qua tín hiệu Ctrl+C"
trap '' SIGINT # bỏ qua SIGINT

echo "Script sẽ không dừng khi nhấn Ctrl+C (bạn phải dùng Ctrl+\ hoặc kill)"
sleep 10 # Script vẫn chạy

echo "Khôi phục hành vi mặc định cho Ctrl+C"
trap - SIGINT
echo "Bây giờ Ctrl+C sẽ hoạt động bình thường."
sleep 5 # Bấm Ctrl+C ở đây để thấy tác dụng
```

### Trap EXIT cho việc dọn dẹp

Một trường hợp sử dụng `trap` rất hữu ích là xử lý tín hiệu đặc biệt `EXIT` (hoặc 0). Khối lệnh của `trap EXIT` sẽ luôn chạy khi script kết thúc, bất kể là thành công hay bị lỗi hoặc bị dừng bởi một tín hiệu khác (trừ SIGKILL). Điều này lý tưởng cho việc dọn dẹp (xóa file tạm, dừng dịch vụ, v.v.).

```bash
#!/bin/bash

# Tao file tam
TEMP_FILE="/tmp/my_temp_file_$$"
touch "$TEMP_FILE"
echo "File tạm đã tạo: $TEMP_FILE"

# Hàm dọn dẹp
clean_up() {
  echo "Đang dọn dẹp file tạm: $TEMP_FILE"
  if [[ -f "$TEMP_FILE" ]]; then
    rm "$TEMP_FILE"
    echo "Đã xóa file tạm."
  fi
}

# Đặt trap cho tín hiệu EXIT (hoặc 0)
trap 'clean_up' EXIT

echo "Script đang chạy... (Để ý trap EXIT sẽ chạy khi script kết thúc)"
sleep 5 # Simulate work

# Gioi tinh hieu khac (Ctrl+C) de thay trap EXIT van chay
trap 'echo -e "\nCtrl+C bị bắt"; exit 1' SIGINT

echo "Nhấn Ctrl+C để kiểm tra trap EXIT."
sleep 10 # Cho nguoi dung nhan Ctrl+C

echo "Script ket thuc binh thuong." # Dong nay chi chay neu khong nhan Ctrl+C hoac xay ra loi gi
```
Output khi nhấn Ctrl+C:
```
File tạm đã tạo: /tmp/my_temp_file_PID
Script đang chạy... (Để ý trap EXIT sẽ chạy khi script kết thúc)
Đang làm gì đó... PID
Đang làm gì đó... PID
Nhấn Ctrl+C để kiểm tra trap EXIT.
^C
Ctrl+C bị bắt
Đang dọn dẹp file tạm: /tmp/my_temp_file_PID
Đã xóa file tạm.
```

---

## 18. Mở Rộng Biến Nâng Cao (Advanced Parameter Expansion)

Đây là các cú pháp mạnh mẽ để thao tác với giá trị của biến mà không cần gọi lệnh phụ (nhanh hơn!).

### Mặc định giá trị, báo lỗi nếu biến rỗng/unset

| Cú pháp                 | Giải thích                                                                      | Ví dụ (`var` rỗng hoặc unset) |
| :---------------------- | :------------------------------------------------------------------------------ | :----------------------------- |
| `${var:-word}`          | Sử dụng `word` nếu `var` unset hoặc rỗng. `var` **không thay đổi**.             | `echo ${var:-default}` -> default |
| `${var:=word}`          | Sử dụng `word` nếu `var` unset hoặc rỗng. `var` **được gán giá trị `word`**.   | `echo ${var:=default}` -> default, `var` bây giờ là "default" |
| `${var:?message}`       | Nếu `var` unset hoặc rỗng, in `message` ra stderr và **thoát script**.       | `echo ${var:?variable required}` -> error and exit |
| `${var:+word}`          | Sử dụng `word` nếu `var` **đã** được set và không rỗng. Ngược lại, rỗng.      | `echo ${var:+set_value}` -> rỗng |

**Ví dụ:**

```bash
#!/bin/bash
# myvar unset

echo "Su dung :-: ${myvar:-Gia tri mac dinh}" # Output: Gia tri mac dinh
echo "myvar van chua duoc set: '$myvar'"      # Output: ''

echo "---"

echo "Su dung :=: ${myvar:=Gia tri nay se duoc gan}" # Output: Gia tri nay se duoc gan
echo "myvar da duoc set: '$myvar'"                # Output: Gia tri nay se duoc gan

echo "---"

bien_yeu_cau="Mot gia tri nao do"
echo "Bien 'bien_yeu_cau' da set: ${bien_yeu_cau:?Bien bien_yeu_cau phai duoc set}" # Khong thoat, chi in gia tri bien

# Thu voi bien_yeu_cau2 chua set
# echo "Bien 'bien_yeu_cau2' chua set: ${bien_yeu_cau2:?Bien bien_yeu_cau2 phai duoc set}" # Se in loi va thoat script!
# Dong code nay se gay dung script neu bien_yeu_cau2 chua duoc set.
```

### Loại bỏ tiền tố/hậu tố (Substring Removal)

Cực kỳ hữu ích để xử lý đường dẫn file.

*   `${var#pattern}`: Xóa phần `pattern` **ngắn nhất** khớp ở **đầu** của `var`.
*   `${var##pattern}`: Xóa phần `pattern` **dài nhất** khớp ở **đầu** của `var`.
*   `${var%pattern}`: Xóa phần `pattern` **ngắn nhất** khớp ở **cuối** của `var`.
*   `${var%%pattern}`: Xóa phần `pattern` **dài nhất** khớp ở **cuối** của `var`.

**Ví dụ:**

```bash
#!/bin/bash
duong_dan="/home/user/docs/report.2023.txt"
file_list="a.txt b.txt c.log d.txt"

# Lay ten file (xoa duong dan nhat gan nhat)
ten_file="${duong_dan##*/}" # */: khớp moi thu ket thuc bang / o dau
echo "Ten file: $ten_file" # Output: report.2023.txt

# Lay ten directory (xoa ten file nhat gan nhat)
ten_dir="${duong_dan%/*}" # /*: khớp moi thu bat dau bang / o cuoi
echo "Ten directory: $ten_dir" # Output: /home/user/docs

# Xoa phan mo rong .txt
file_goc="${ten_file%.txt}" # .txt: khop chuoi ".txt" o cuoi
echo "Ten file khong duoi .txt: $file_goc" # Output: report.2023

# Xoa phan mo rong dai nhat (vi du file.tar.gz)
archive_name="project.tar.gz"
goc_archive="${archive_name%%.*}" # .* : khớp dau . va bat ky ky tu nao theo sau
echo "Goc ten archive: $goc_archive" # Output: project

# Xoa cac file .txt trong chuoi file_list (xoa .* o cuoi nhat gan nhat)
files_no_txt="${file_list// *.txt/}" # Can than voi dau cach!
echo "File list sau khi xoa .txt (có lỗi khoảng trắng): $files_no_txt" # Output:  a b c.log d
# Cách tốt hơn: đọc từng file, kiểm tra và xử lý thay vì xử lý chuỗi
```

### Tìm và thay thế

Đã đề cập ở mục [10. Thao Tác Với Chuỗi (String Manipulation)](#10-thao-tác-với-chuỗi-string-manipulation).

### Độ dài, chỉ mục/phần tử

Đã đề cập ở mục [10. Thao Tác Với Chuỗi (String Manipulation)](#10-thao-tác-với-chuỗi-string-manipulation) và [9. Mảng (Arrays)](#9-mảng-arrays).

---

## 19. Debugging Script Bash

Script Bash có thể chứa lỗi (bug). Việc gỡ lỗi (debugging) là kỹ năng cần thiết.

### Các tùy chọn Debug

Bạn có thể bật các tùy chọn debugging cho shell hoặc một phần của script bằng lệnh `set`:

*   `set -x`: Print commands and their arguments as they are executed (in ra từng lệnh sau khi mở rộng biến trước khi chạy). Rất chi tiết.
*   `set -v`: Print shell input lines as they are read (in ra từng dòng lệnh ngay sau khi đọc, trước khi xử lý biến).
*   `set -n`: Read commands but do not execute them (Syntax Check - kiểm tra cú pháp mà không chạy code). Ít dùng trong thực tế debug logic, chủ yếu kiểm tra nhanh cú pháp.
*   `set -e`: Exit immediately if a command exits with a non-zero status (như đã nói ở mục [13](#13-xử-lý-lỗi-và-mã-thoát-error-handling--exit-codes)). Rất hữu ích cho script production.

Bạn có thể đặt các tùy chọn này ở đầu script (`set -ex`), hoặc chỉ bật/tắt cho một đoạn code:

```bash
#!/bin/bash

# Debuging ca script
# set -x # Uncomment de debug toan bo script

echo "Bắt đầu."

set -v # Bắt đầu in dòng input
echo "Đây là một dòng lệnh."
echo "Biến: $USER"
set +v # Ngừng in dòng input

echo "---"

echo "Phần này không in input"
# Chỉ debug mot đoạn code cụ thể
echo "Debug một đoạn code:"
set -x # Bắt đầu in lệnh sau mở rộng biến
file="/tmp/some_file"
ls -l "$file"
set +x # Ngừng in lệnh

echo "Kết thúc."
```
Bạn cũng có thể truyền trực tiếp các tùy chọn này khi chạy script:
`bash -x my_script.sh`

### Sử dụng các công cụ khác

*   **`echo`**: In giá trị biến ở các điểm khác nhau để theo dõi.
*   **`declare -p variable`**: Hiển thị thuộc tính và giá trị của một biến.
*   **Shellcheck**: Một công cụ tĩnh (static analysis tool) kiểm tra các vấn đề cú pháp, lỗi logic, các pattern dễ gây lỗi trong script Bash. Rất nên dùng! (https://shellcheck.net/)
*   **Trình soạn thảo**: Nhiều trình soạn thảo code hiện đại có hỗ trợ cú pháp tô sáng, kiểm tra lỗi cơ bản cho Bash.

---

## 20. Viết Script Mạnh Mẽ và Bảo Mật (Best Practices)

Để viết Bash script hiệu quả, đáng tin cậy và an toàn, hãy tuân thủ các quy tắc sau:

### Luôn sử dụng Shebang

`#!/bin/bash` hoặc `#!/usr/bin/env bash`. Cái sau linh hoạt hơn nếu Bash không nằm ở `/bin`.

### Sử dụng tùy chọn `set -euo pipefail`

Kết hợp các tùy chọn mạnh mẽ để bắt lỗi sớm:
*   `set -e`: Script dừng ngay lập tức nếu lệnh trả về mã thoát khác 0.
*   `set -u`: Script dừng nếu sử dụng một biến chưa được khai báo/set (unset variable).
*   `set -o pipefail` (hoặc `-P`): Nếu bất kỳ lệnh nào trong pipe bị lỗi, pipe sẽ trả về mã lỗi đó (thay vì mặc định là mã thoát của lệnh cuối cùng).
Kết hợp chúng lại: `set -euo pipefail`. Hãy đặt dòng này ngay sau shebang.

```bash
#!/bin/bash
set -euo pipefail

echo "Script mạnh mẽ bắt đầu"

# Vi du loi unset variable (set -u se bat)
# echo "Bien chua khai bao: $UNSET_VAR"

# Vi du loi pipefail (set -o pipefail se bat)
# echo "abc" | grep "xyz" | echo "sau pipe" # grep khong tim thay, ma thoat 1, script se thoat
```

### Đóng ngoặc kép cho biến và tham số

Luôn đóng ngoặc kép `"$variable"` hoặc `"${variable}"` khi sử dụng giá trị biến, đặc biệt là khi biến có thể chứa khoảng trắng, ký tự đặc biệt, hoặc output của lệnh. Điều này ngăn ngừa các lỗi do word splitting (tách chuỗi thành các từ dựa trên `$IFS`) và pathname expansion (globbing - mở rộng ký tự wildcard như `*`, `?`, `[`). Các trường hợp ngoại lệ chính là khi biến đang nằm trong `((...))` hoặc vế phải của gán giá trị, hoặc bạn *muốn* nó được tách từ hoặc mở rộng path (ví dụ: vòng lặp `for file in *.txt`).

```bash
#!/bin/bash
set -euo pipefail

ten_file="tap tin co khoang trang.txt"

# LOI: ten file bi tach thanh 4 phan tu
# ls $ten_file # Se loi vi ls nhan 4 tham so

# DUNG:
ls "$ten_file" # ls nhan dung 1 tham so la "tap tin co khoang trang.txt"
```

### Sử dụng hàm cho các tác vụ lặp lại

Như đã nói ở mục Hàm, giúp code dễ đọc, quản lý và tái sử dụng. Luôn dùng `local` cho các biến trong hàm.

### Kiểm tra Input đầu vào

Nếu script nhận tham số (`$1`, `$2`, ...), luôn kiểm tra xem chúng có đủ số lượng (`$#`) và có định dạng hợp lệ không trước khi sử dụng. Kết hợp với `$0`, `$?`.

```bash
#!/bin/bash
set -euo pipefail

if [[ $# -ne 1 ]]; then
  echo "ERROR: Can truyen mot tham so duy nhat (ten thu muc)." >&2
  echo "Su dung: $0 <ten_thu_muc>" >&2
  exit 1
fi

TARGET_DIR="$1"

if [[ ! -d "$TARGET_DIR" ]]; then
  echo "ERROR: Thu muc '$TARGET_DIR' khong ton tai hoac khong phai la thu muc." >&2
  exit 1
fi

echo "Xu ly thu muc: $TARGET_DIR"
# ... Xu ly cac file ben trong thu muc ...
```

### Viết code dễ đọc (thụt lề, chú thích)

Sử dụng thụt lề nhất quán cho các khối lệnh (trong `if`, `for`, `while`, `case`, functions). Viết chú thích giải thích logic phức tạp hoặc lý do của một quyết định thiết kế.

### Tránh Parse Output của `ls`

Output của `ls` (và một số lệnh khác như `ps`, `netstat`) được thiết kế cho người đọc, không phải cho script để xử lý tự động. Format có thể thay đổi giữa các phiên bản hoặc phụ thuộc vào cài đặt locale. Thay vào đó, sử dụng các phương pháp đáng tin cậy hơn:
*   Để duyệt file: dùng globbing (`*.txt`), lệnh `find`.
*   Để lấy thông tin file: dùng lệnh `stat`.
*   Để kiểm tra sự tồn tại/loại file: dùng `test` (`[`, `[[`).

```bash
#!/bin/bash

# KHONG NEN LAM: Xy ly output cua ls de tim file .conf
# ls *.conf | while read -r file; do
#  echo "Found config file (KHONG NEN LAM): $file"
# done

# NEN LAM: Dung globbing trong vong lap for
echo "Xu ly file .conf (NEN LAM):"
for conf_file in *.conf; do
  # Kiem tra xem co it nhat 1 file khop mau *.conf truoc khi xu ly
  # Neu khong co file nao khop, $conf_file se la "*.conf"
  # [[ -e "$conf_file" || -L "$conf_file" ]] can de kiem tra $conf_file co that su ton tai khong
  # Tuy chon nullglob va failglob co the giup it hon trong Bash moi

  # Cai tien (dung tuy chon Bash)
  shopt -s nullglob # Nếu không có file nào khớp, pattern mở rộng thành null (rỗng)
  shopt -u failglob # Ngược lại với nullglob, sẽ báo lỗi nếu không khớp, tranh sai sot

  for conf_file in *.conf; do
     # Neu dung nullglob, vong lap nay se KHONG chay neu khong tim thay file .conf
     echo "Found config file (cai tien): $conf_file"
     # Xu ly $conf_file o day
  done

  shopt -u nullglob # Tat lai tuy chon
  shopt -u failglob
done


# NEN LAM hon: Dung find
echo "Xu ly file .conf (NEN LAM HON):"
find . -maxdepth 1 -name "*.conf" -print0 | while IFS= read -r -d '' conf_file; do
  echo "Found config file (dung find + read -d ''): $conf_file"
  # Xu ly $conf_file o day
done
```
Sử dụng `find ... -print0 | while IFS= read -r -d '' ...` là pattern rất tin cậy để xử lý tên file có khoảng trắng hoặc ký tự đặc biệt.

---

## 21. Các Ví Dụ Thực Tế (Real-world Examples)

Áp dụng kiến thức đã học vào các tác vụ phổ biến.

### Script sao lưu file đơn giản

Sao lưu một danh sách các file/thư mục vào một thư mục backup với timestamp.

```bash
#!/bin/bash
set -euo pipefail

# Cau hinh
SOURCE_DIRS=("/home/user/documents" "/home/user/projects") # Cac thu muc can backup
BACKUP_ROOT_DIR="/backup" # Thu muc chua cac ban backup

# Tao ten ban backup kem timestamp
TIMESTAMP=$(date +"%Y%m%d_%H%M%S")
BACKUP_DIR="${BACKUP_ROOT_DIR}/backup_${TIMESTAMP}"

echo "Bat dau tao ban backup..."
echo "Nguon: ${SOURCE_DIRS[*]}"
echo "Dich: $BACKUP_DIR"

# Tao thu muc backup neu chua ton tai
if [[ ! -d "$BACKUP_ROOT_DIR" ]]; then
  mkdir -p "$BACKUP_ROOT_DIR"
  echo "Da tao thu muc goc backup: $BACKUP_ROOT_DIR"
fi

# Tao thu muc cho ban backup hien tai
mkdir "$BACKUP_DIR"
echo "Da tao thu muc ban backup: $BACKUP_DIR"

# Thuc hien sao chep
for dir in "${SOURCE_DIRS[@]}"; do
  if [[ -d "$dir" || -f "$dir" ]]; then
    echo "Sao chep '$dir'..."
    cp -rv "$dir" "$BACKUP_DIR/" # -r: recursive (ca thu muc con), -v: verbose (hien thi dang lam gi)
    # Co the thay the bang rsync de hieu qua hon khi backup lan tiep theo
    # rsync -avz "$dir" "$BACKUP_DIR/"
  else
    echo "WARNING: Nguon '$dir' khong ton tai. Bo qua." >&2
  fi
done

echo "Ket thuc qua trinh backup."
```

### Script giám sát dung lượng đĩa

Kiểm tra dung lượng trống của một phân vùng và gửi cảnh báo nếu dưới ngưỡng.

```bash
#!/bin/bash
set -euo pipefail

# Cau hinh
MONITOR_PATH="/home" # Duong dan phan vung can giam sat
THRESHOLD_PERCENT=10 # Nguong toi thieu dung luong trong (phan tram)
ALERT_EMAIL="admin@example.com" # Dia chi email gui canh bao (can configure sendmail/postfix)

# Lay thong tin dung luong bang df
# df -h /home: human-readable
# df -P /home: Portable format, đảm bảo output nhất quán cho scripting
DF_OUTPUT=$(df -P "$MONITOR_PATH")

# Su dung awk de phan tich output cua df.
# df -P co format la:
# Filesystem     1024-blocks      Used Available Capacity Mounted on
# /dev/sda1         10000000   8000000   2000000      80% /home
# Chung ta quan tam cot 4 (Available) va cot 5 (Capacity - %). Loai bo header bang tail -n +2
AVAIL_KB=$(echo "$DF_OUTPUT" | awk 'NR==2 { print $4 }') # NR==2: dong thu 2
CAPACITY_PERCENT=$(echo "$DF_OUTPUT" | awk 'NR==2 { print $5 }' | sed 's/%//') # Loai bo %

echo "Dang kiem tra '$MONITOR_PATH'..."
echo "Dung luong trong: $AVAIL_KB KB"
echo "Ty le da dung: $CAPACITY_PERCENT%"

# So sanh ty le da dung voi nguong (Nguong cua chung ta la free, can doi nguoc lai)
USED_PERCENT=$CAPACITY_PERCENT
FREE_PERCENT=$((100 - USED_PERCENT)) # Doi nguoc ty le trong tu ty le da dung

if (( FREE_PERCENT < THRESHOLD_PERCENT )); then
  echo "CANH BAO: Dung luong trong cua '$MONITOR_PATH' chi con $FREE_PERCENT% (duoi nguong $THRESHOLD_PERCENT%)" >&2
  # Gui email canh bao
  #echo "CANH BAO: Dung luong '$MONITOR_PATH' dang thap ($FREE_PERCENT%)" | mail -s "Canh bao dung luong thap: $MONITOR_PATH" "$ALERT_EMAIL"
  # Dong tren can co mutt hoac mailutils va sendmail/postfix/exim duoc cau hinh tren he thong
else
  echo "Dung luong '$MONITOR_PATH' ($FREE_PERCENT%) nam trong nguong cho phep."
fi

echo "Ket thuc kiem tra dung luong."
```

### Script xử lý hàng loạt file

Tìm các file có đuôi nhất định trong một thư mục và thực hiện một hành động (ví dụ: nén) trên từng file đó.

```bash
#!/bin/bash
set -euo pipefail

# Cau hinh
TARGET_DIR="./reports" # Thu muc can xu ly
FILE_EXTENSION="log" # Duoi file can tim (.log)
COMPRESSED_EXT=".gz" # Duoi file sau khi nen

# Tao thu muc dummy de test neu chua co
if [[ ! -d "$TARGET_DIR" ]]; then
    echo "Tao thu muc '$TARGET_DIR' cho vi du..."
    mkdir "$TARGET_DIR"
    echo "Tao mot so file dummy..."
    echo "log content 1" > "$TARGET_DIR/file1.log"
    echo "log content 2" > "$TARGET_DIR/file2.log"
    echo "text content 3" > "$TARGET_DIR/file3.txt"
fi

echo "Tim va nen cac file co duoi .$FILE_EXTENSION trong '$TARGET_DIR'..."

# Sử dụng find để tìm các file (đáng tin cậy)
# '-type f' chi file thuong, '-name "*.log"' tim file ket thuc bang .log
# '-print0' in duong dan ket thuc bang ky tu null (0)
find "$TARGET_DIR" -type f -name "*.$FILE_EXTENSION" -print0 | \
while IFS= read -r -d '' file; do # Doc tung duong dan file cach nhau boi null

  echo "Dang xu ly file: $file"

  # Kiểm tra xem file .gz đã tồn tại chưa (tranh nen lai)
  COMPRESSED_FILE="${file}${COMPRESSED_EXT}"
  if [[ -f "$COMPRESSED_FILE" ]]; then
    echo "  $COMPRESSED_FILE da ton tai, bo qua nen lai."
    continue # Bo qua vong lap hien tai
  fi

  # Tien hanh nen file (su dung gzip)
  # Lệnh gzip mac dinh se thay the file goc bang file .gz
  # neu muon giu file goc, dung 'gzip -kc' (k: keep, c: stdout) roi chuyen huong
  # gzip "$file" # nen truc tiep

  # hoac:
  echo "  Nen file..."
  if gzip -c "$file" > "$COMPRESSED_FILE"; then # Nén ra stdout rồi lưu vào file .gz mới
     echo "  Da nen thanh cong vao '$COMPRESSED_FILE'"
     rm "$file" # Xoa file goc sau khi nen thanh cong
     echo "  Da xoa file goc '$file'"
  else
     echo "  ERROR: Nen file '$file' that bai!" >&2
  fi


done # Ket thuc while loop

echo "Ket thuc xu ly hang loat file."

# Don dep (optional)
# rm -r "$TARGET_DIR" # Can than khi dung dong nay!
```
Đây là ví dụ minh họa việc kết hợp `find`, pipe, `while read`, kiểm tra file, và lệnh nén/xóa.

### Script tự động hóa tác vụ định kỳ (Cron jobs)

Lên lịch chạy script tự động bằng Cron. Bạn cần sửa crontab để thêm dòng chỉ định thời gian và lệnh chạy script.

```bash
# Luu script tren (vd: /home/user/scripts/backup_script.sh)
# Chmod +x script de dam bao co the thuc thi
# chmod +x /home/user/scripts/backup_script.sh

# Sua crontab cua user hien tai
crontab -e

# Them mot dong vao cuoi file (vi du: chay script moi ngay luc 2h sang)
# Dang cu phap Cron: phut gio ngay_trong_thang thang ngay_trong_tuan lenh
#       *     *    *             *        *        lenh
  0     2    *             *        *        /home/user/scripts/backup_script.sh

# Luu lai file crontab. Cron daemon se tu dong doc cau hinh moi.
```
Cron rất mạnh mẽ, nhưng hãy cẩn thận:
*   Đặt `PATH` và các biến môi trường cần thiết ở đầu script hoặc trong crontab vì môi trường của Cron thường rất tối giản.
*   Chuyển hướng output/error (`&> /var/log/my_script.log`) của script trong crontab để ghi log. Nếu không, Cron sẽ gửi email output (nếu có mail server).
*   Kiểm tra kỹ script với `set -euo pipefail` trước khi đưa vào Cron.

---

## 22. Kết Luận và Bước Tiếp Theo

### Tóm tắt

Chúng ta đã đi qua một hành trình thú vị, khám phá những viên ngọc quý của Bash Scripting từ biến, cấu trúc điều khiển, vòng lặp, hàm cho đến xử lý file, tín hiệu, Regex, và các kỹ thuật debugging, best practices. Bash là một ngôn ngữ scripting tuyệt vời cho việc tự động hóa và quản lý hệ thống trên Linux/Unix. Khả năng kết hợp các lệnh tiện ích thông qua pipe và xử lý văn bản mạnh mẽ làm cho nó trở thành một công cụ không thể thiếu.

### Tài nguyên học thêm

*   **Bash Hackers Wiki:** [https://wiki.bash-hackers.org/](https://wiki.bash-hackers.org/) - Tài liệu kỹ thuật sâu sắc.
*   **Bash Guide for Beginners / Advanced Bash-Scripting Guide:** Các sách online kinh điển, có thể hơi cũ nhưng nền tảng rất tốt.
*   **man bash:** Tài liệu hướng dẫn chính thức của lệnh `bash` (rất chi tiết!).
*   **shellcheck.net:** Công cụ kiểm tra tĩnh script của bạn.
*   Thực hành trên môi trường Linux/Unix của bạn.
*   Đọc source code của các script Bash phổ biến.

### Khuyến khích thực hành

Lý thuyết là quan trọng, nhưng thực hành là cách duy nhất để thực sự làm chủ Bash.
*   Hãy thử viết script để giải quyết các vấn đề nhỏ hàng ngày của bạn (ví dụ: dọn dẹp file tạm, đổi tên hàng loạt file, tổng hợp dữ liệu từ các file log).
*   Thử viết lại các lệnh dài bạn thường gõ vào terminal thành một script đơn giản.
*   Tạo các alias hoặc hàm trong file `.bashrc` hoặc `.bash_profile` để tự động hóa các tác vụ thường dùng.
