# The JavaScript tutorial ( Ilya Kantor )


  - **[2.1:Hello, world!](#1)**
  - **[2.2:Code structure](#2)**
  - **[2.4:Variables](#3)**
  - **[2.5:Data types](#4)**   
  
<a name="1"></a>
## 2.1:Hello, world!

Nếu chúng ta có rất nhiều mã JavaScript, chúng ta có thể đặt nó vào một tệp riêng biệt: không cần viết thằng đoạn js vào trực tiếp web, mà truyền qua 1 url 



`<script src="/path/to/script.js"></script>`

Đây /path/to/script.jslà một đường dẫn tuyệt đối đến tập tin với kịch bản (từ gốc trang web).


Cũng có thể cung cấp một đường dẫn liên quan đến trang hiện tại. Ví dụ, src="script.js"có nghĩa là một tập tin "script.js"từ thư mục hiện tại.


Chúng ta cũng có thể đưa ra một URL đầy đủ, ví dụ:


`<script src="https://cdnjs.cloudflare.com/ajax/libs/lodash.js/3.2.0/lodash.js"></script>`

Để đính kèm một số tập lệnh, sử dụng nhiều thẻ:


```
<script src="/js/script1.js"></script>

<script src="/js/script2.js"></script>
```

**note** nếu src được đặt trong thẻ <script> thì nội dung bên trong bị bỏ qua

<a name="2"></a>
## 2.2:Code structure

```
alert("All fine now");

[1, 2].forEach(alert) // kết hợp lệnh alert để in ra 1 và 2 mà ko cần viết 2 câu lệnh
```

nếu bỏ ; trong trường hợp nối 2 đoạn thì không hoạt động.


- comment trong js giống như c, 
```
// để in 1 dòng 
/* 1 đoạn*/

```

## 2.3:The modern mode, "use strict"

<a name="3"></a>
## 2.4:Variables
dùng var hoặc let để khai báo

let tạo ra một biến chỉ có thể truy cập được trong block bao quanh nó, khác với var - tạo ra một biến có phạm vi truy cập xuyên suốt function chứa nó.

Ví dụ:

Sử dụng var:

```
function foo() {
   var x = 10;
   if (true) {
      var x = 20; // x ở đây cũng là x ở trên
      console.log(x); // in ra 20
   }
   console.log(x); // vẫn là 20
}
```

```
Sử dụng let:

function foo() {
   let x = 10;
   if (true) {
      let x = 20; // x này là x khác rồi đấy
      console.log(x); // in ra 20
   }
   console.log(x); // in ra 10
}

```
```
Ngoài ra, khi ở global scope (tức là không nằm trong một function nào cả), từ khóa var tạo ra thuộc tính mới cho global object (this), còn let thì không:

var x = 'global';
let y = 'global';
console.log(this.x); // "global"
console.log(this.y); // undefined
```

Có một trường hợp dùng let rất hiệu quả đó là sử dụng callback trong một vòng lặp.

Ví dụ nếu dùng var:

```
for (var i = 0; i < 5; i++) {
   setTimeout(function(){ 
      console.log('Yo! ', i);
   }, 1000);
}
Kết quả sẽ ra gì nào?

Yo! 5
Yo! 5
Yo! 5
Yo! 5
Yo! 5
```

Giá trị của biến i bên trong hàm callback luôn là giá trị cuối cùng của i trong vòng lặp.

Để giải quyết vấn đề này, chúng ta thay var bằng let:

```
for (let i = 0; i < 5; i++) {
   setTimeout(function(){ 
      console.log('Yo! ', i);
   }, 1000);
}
Output sẽ đúng như mong đợi:

Yo!  0
Yo!  1
Yo!  2
Yo!  3
Yo!  4
```
	
- hàm const giống let nhưng ở dạng hằng số

<a name="4"></a>
## 2.5:Data types

 
Có 7 kiểu cơ bản trong JavaScript.

- `number` Cho số bất kỳ dạng nào: số nguyên hoặc số trôi nổi.

- `stringCho` dây. Một chuỗi có thể có thêm một số ký tự, không có loại ký tự đơn lẻ.

- `boolean` Cho true/ false.: lưu ý loại Backticks: ``` `hello` ```

```
Backticks là "mở rộng chức năng" báo giá. Chúng cho phép nhúng các biến và các biểu thức vào một chuỗi bằng cách gói chúng vào ${…}, ví dụ:
  let name = "John";

// embed a variable
alert( `Hello, ${name}!` ); // Hello, John!

// embed an expression

alert( `the result is ${1 + 2}` ); // the result is 3
```

- `nullCho` các giá trị không xác định - một loại độc lập có một giá trị null.

- `undefined` Cho các giá trị không được gán - một loại độc lập có một giá trị undefined.

- `object` Cho các cấu trúc dữ liệu phức tạp hơn.

- `symbol` Cho các định danh duy nhất.

## 2.7:Operators

toán tử

## 2.8  Interaction: alert, prompt, confirm

```
let age = prompt('How old are you?', 100);

alert(`You are ${age} years old!`); // You are 100 years old!
```

hàm prompt nhập vào 1 giá trị

```
let isBoss = confirm("Are you the boss?");

alert( isBoss ); // true is OK is pressed
```

Hiển thị một tin nhắn và chờ người dùng nhấn "OK" hoặc "CANCEL". Nó trả về trueOK và falsecho CANCEL / Esc.

## 2.10: Conditional operators: if, '?'

điều kiện if else , nhập giá trị thông qua prompt


# Code quality

## 3.1:Debugging in Chrome

The “sources” pane: khi vào bằng Chrome hoặc firefox( có cài fire bug) có một công cụ hỗ trợ , cho việc xem kiểm tra cấu trúc của trang web

, thực hiện bằng cách nhấn f12

<img src="http://image.prntscr.com/image/6ba4508f4651463c9e325614f5795542.png">
gồm 3 mục
- **Vùng tài nguyên** liệt kê các tệp html, javascript, css và các tệp khác bao gồm các hình ảnh được gắn vào trang. Tiện ích Chrome cũng có thể xuất hiện ở đây.

- **Khu vực nguồn** hiển thị mã nguồn.

- **Vùng thông tin** và kiểm soát là để gỡ lỗi

- **Console** tương tự như trình biên dịch của các phần mềm khác

- **Breakpoints** là một điểm của mã mà trình gỡ lỗi sẽ tự động tạm dừng việc thực hiện JavaScript. hoặc có thể dùng `debugger;` 
Một breakpoint là một điểm dừng có chủ đích trong code, dùng để hỗ trợ lập trình viên trong quá trình debug. Khi chương trình chạy đến một breakpoint, bạn có thể “bước qua” (step-through) từng dòng lệnh và kiểm tra xem mọi logic có đúng như ý đồ. Ở trạng thái dừng của breakpoint, bạn cũng có thể kiểm tra giá trị của từng biến tại thời điểm hiện tại. Điều này giúp xác định một lỗi thường gặp nhưng ít được để ý: sử dụng một biến khi chưa khởi tạo biến đó.
http://karmiphuc.com/cong-nghe/debug-javascript-de-dang-voi-chrome-dev-tools/



tham khảo : https://developers.google.com/web/tools/chrome-devtools/

## 3.3 :comment

sử dụng cmt để chú thích cho câu lệnh

- http://jshint.com/  công cụ tự động kiểm  tra style







## 3.5:Automated testing with mocha

Tại sao chúng ta cần các bài kiểm tra?

Khi viết một hàm, chúng ta thường có thể tưởng tượng nên làm gì: các tham số nào cho kết quả nào.

Trong quá trình phát triển, chúng ta có thể kiểm tra chức năng bằng cách chạy nó và so sánh kết quả với mong muốn. Ví dụ, chúng ta có thể làm điều đó trong bảng điều khiển.

Nếu có gì sai - sau đó chúng tôi sửa mã, chạy lại, kiểm tra kết quả - và cứ như vậy cho đến khi nó hoạt động.

Nhưng hướng dẫn như vậy "chạy lại" là không hoàn hảo.

Khi kiểm tra mã bằng tay chạy lại - bạn dễ dàng bỏ lỡ một cái gì đó . vì vậy tự động giúp chúng ta thực hiện ez hơn



