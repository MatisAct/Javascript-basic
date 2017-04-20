#The JavaScript tutorial ( Ilya Kantor )

<ul>
  <li>**[2.1:Hello, world!](#1)</li>
  <li>Mục con 2</li>
  <li>Mục con 3</li>
  <li>Mục con 4</li>
  <li>Mục con 5</li>
</ul>

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

2.5:Data types
