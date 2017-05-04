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

# Objects: the basics

## 4.1 :Objects

- mỗi Objects được tạo ra nằm trong dấu {...} , thuộc tính nằm trong "key: value" key từ khóa , value giá trị tùy người dùng đưa vào 

<img src="http://javascript.info/article/object/object.png">

- tạo 1 object trống

```
let user = new Object(); // "object constructor" syntax
let user = {};  // "object literal" syntax
```
### Literals and properties

```
let user = {     // an object
  name: "John",  // by key "name" store value "John"
  age: 30        // by key "age" store value 30
};
```


<img src="http://javascript.info/article/object/object-user.png">


- sử dụng

```
alert( user.name ); // John
alert( user.age ); // 30
```

<img src="http://image.prntscr.com/image/59d73c52f7b540279a1178ab48de88cf.png">

  - khi khai báo 1 biến ngoài Object thì thay thế dấu , bằng ngoặc vuông 

  <img src="http://image.prntscr.com/image/cbb65c40941344d08d659e845fe3d654.png">

  
  ### Property value shorthand
  
  <img src="http://image.prntscr.com/image/bc869c05bf31491086a96a313e8c4a36.png">

Thay vì name:namechúng ta chỉ có thể viết name, như thế này:

```
function makeUser(name, age) {
  return {
    name, // same as name: name
    age   // same as age: age
  };
}
```

Chúng ta có thể sử dụng cả thuộc tính bình thường và các ký tự viết tắt trong cùng một đối tượng:

```
let user = {
  name,  // same as name:name
  age: 30
};
```

- dùng `in` để kiểm tra sự tồn tại của 1 biến 

```
let user = { name: "John", age: 30 };

alert( "age" in user ); // true, user.age exists
alert( "blabla" in user ); // false, user.blabla doesn't exist
```

### The “for…in” loop

Cú pháp:

```
for(key in object) {
  // executes the body for each key among object properties
}
```
ví dụ
```
let user = {
  name: "John",
  age: 30,
  isAdmin: true
};

for(let key in user) {
  // keys
  alert( key );  // name, age, isAdmin, lấy ra các key
  // values for the keys
  alert( user[key] ); // John, 30, true lấy ra các thuộc tính của key

}
```
```
let codes = {
  "49": "Germany",
  "41": "Switzerland",
  "44": "Great Britain",// ngược mảng
  // ..,
  "1": "USA"
};

for(let code in codes) {
  alert(code); // 1, 41, 44, 49
}
```
## Copying by reference

khai báo hàm const giá trị se bị thay đổi khi tác động, thay đổi chứ không phải thay thế

```
const user = {
  name: "John"
};

user.age = 25; // (*)

alert(user.age); // 25
```

<img src="http://image.prntscr.com/image/0a455eb8acf74578a9311bd31fd415ff.png">

## Garbage collection


```
// user has a reference to the object
let user = {
  name: "John"
};
```
giả sử đây là 1 biến tên  user với thuộc tính là `name:"John"`

giờ bạn ghi đè lên user =`user = null;` lúc này thuộc tính ban đầu của nó se ko truy cập được nữa!

<img src="http://image.prntscr.com/image/197963349867489db6e86935c3b6d5cd.png">


- tiếp tiếp
```
// user has a reference to the object
let user = {
  name: "John"
};

let admin = user;
```
- giờ giả sử thêm `user = null;` lúc này biến user trở về trạng thái null, lúc này mọi truy vấn giá trị vào user bị error, nhưng chúng ta có thể truy vấn giá trị `name: "John"` thông qua biến admin.

## Symbol type

### Symbols
  `Symbol(name);` mang giá trị duy nhất
  ```
let id1 = Symbol("id");
let id2 = Symbol("id");

alert(id1 == id2); // false vì id1 và id2 khai báo bằng hàm symbol 
  ```
### “Hidden” properties
có thể ghi đè data lên mà ko bị gì cả,

```
let user = { name: "John" };
let id = Symbol("id");
//id khai báo ở let và id trong biến user là khác nhau
user[id] = "ID Value";
alert( user[id] ); // "id value"   //we can access the data using the symbol as the key
```

nhưng khi ghi đè 2 thuộc tính thì buzz! :v

```
let user = { name: "John" };

// our script uses "id" property
user.id = "ID Value";

// ...if later another script the uses "id" for its purposes...

user.id = "Their id value"
// boom! overwritten! it did not mean to harm the colleague, but did it!
``` 
### Symbols in a literal

```
let id = Symbol("id");

let user = {
  name: "John",
  [id]: 123 // not just "id: 123" khai báo , thuộc tính symbolic
};
```
[symbolic] không tham gia vòng lặp for..in

### Global symbols
  
  khi 2 biến có cùng 1 giá trị ,  nhưng tên chúng khác nhau , ta sử dụng hàm `Symbol.for(name)` khi đó 2 đứa này sẽ bằng nhau

  ```
// read from the global registry
let name = Symbol.for("name"); // if the symbol did not exist, it is created

// read it again
let nameAgain = Symbol.for("name");

// the same symbol
alert( name === nameAgain ); // true

  ```

## Object methods, "this"
đại loại là chèn 1 hàm vào 1 biến vậy :troll:

```
let user = {
  name: "John",
  age: 30
};

user.sayHi = function() {
  alert("Hello!");
};

user.sayHi(); // Hello!
```
hoặc là 
```
let user = {
  // ...
};

// first, declare
function sayHi() {
  alert("Hello!");
};

// then add as a method
user.sayHi = sayHi;

user.sayHi(); // Hello!
```
- cú pháp ngắn hơn, kiểu này bỏ qua function 
```
let user = {
  sayHi: function() {
    alert("Hello");
  }
};

// method shorthand looks better, right?
let user = {
  sayHi() { // same as "sayHi: function()"
    alert("Hello");
  }
};
```

- để truy cập đối tượng trong biến có thể dùng từ khóa `this` thay cho tên biến 
```
let user = {
  name: "John",
  age: 30,

  sayHi() {
    alert(this.name);//Ở đây trong quá trình thực hiện user.sayHi(), giá trị của thissẽ là user.
  }

};

user.sayHi(); // John
```
- Nếu chúng ta quyết định sao chép usersang một biến khác, ví dụ admin = uservà ghi userđè lên cái gì khác, thì nó sẽ truy cập vào đối tượng sai.

```
let user = {
  name: "John",
  age: 30,

  sayHi() {
    alert( user.name ); // leads to an error
  }

};


let admin = user;
user = null; // overwrite to make things obvious

admin.sayHi(); // Whoops! inside sayHi(), the old name is used! error!
```

Ví dụ, cùng một chức năng có thể có khác nhau "này" khi được gọi từ các đối tượng khác nhau:

 
```
let user = { name: "John" };
let admin = { name: "Admin" };

function sayHi() {
  alert( this.name );
}

// use the same functions in two objects
user.f = sayHi;
admin.f = sayHi;

// these calls have different this
// "this" inside the function is the object "before the dot"
user.f(); // John  (this == user)
admin.f(); // Admin  (this == admin)

admin['f'](); // Admin (dot or square brackets access the method – doesn't matter)
```
# Data types

## Methods of primitives

có 6 kiểu giá trị:` string, number, boolean, symbol, nullvà undefined.` có thể tạo ra nhiều loại với {...}

vd
```
let john = {
  name: "John",
  sayHi: function() {
    alert("Hi deo!");
  }
};

john.sayHi(); // Hi deo!
```

## number

Tất cả các số trong JavaScript được lưu trữ ở định dạng 64-bit

### More ways to write a number

```
1bn=1000000
1.2bn=1.200.000
1e9=1.000.000.000
1e-6=0.000001

```
### Hex, binary and octal numbers

Hệ thống số nhị phân và bát phân hiếm khi được sử dụng nhưng cũng được hỗ trợ sử dụng 0bvà 0otiền tố:

 ```
 let a = 0b11111111; // binary form of 255
let b = 0o377; // octal form of 255

alert( a == b ); // true, the same number 255 at both sides
```

### toString(base)

Phương thức num.toString(base)trả về một biểu diễn chuỗi numtrong hệ thống số với giá trị đã cho base.

Ví dụ:

```
 let num = 255;

alert( num.toString(16) );  // ff
alert( num.toString(2) );   // 11111111
```

Các basethể thay đổi từ 2tới 36. Theo mặc định nó 10.

Hầu hết các trường hợp sử dụng thường là:

Base = 16 được sử dụng cho các màu hex, encodings ký tự vv, chữ số có thể được 0..9hoặc A..F.

Cơ sở = 2 chủ yếu là để gỡ lỗi hoạt động bitwise, chữ số có thể được 0hoặc 1.

Cơ sở = 36 là tối đa, chữ số có thể được 0..9hoặc A..Z. Toàn bộ bảng chữ cái latin được sử dụng để biểu thị một số. Một trường hợp thú vị nhưng hữu ích 36là khi chúng ta cần phải chuyển một số nhận dạng số dài thành một cái gì đó ngắn hơn, ví dụ để tạo ra một url ngắn. Chỉ đơn giản có thể đại diện cho nó trong hệ thống số với cơ sở 36:

### Rounding


bảng tóm tắt
|Math.floor xuống|	Math.ceil lên |	Math.round	gần nhất|Math.trunc bỏ thập phân|
|----------|-------------|--------------|----------|
|3.1	|3|	4|	3|	3|
|3.6	3	|4|	4|	3|
|-1.1	|-2|	-1|	-1|	-1|
|-1.6	|-2|	-1|	-2|	-1|

`num.toFixed(sau phấy)` dùng để làm tròn số
```
let num = 12.34;
alert( num.toFixed(1) ); // "12.3"
```


### Imprecise calculations


mất độ chính xác khi so sánh hay lấy số cụ thể , nên dùng hàm toFixed để tăng độ chính xác
vd
```
alert( 0.1 + 0.2 ); // 0.30000000000000004
```
rõ ràng khi so sánh vs 0.3 sẽ false vì vậy dùng fixed về 2 đơn vị để đúng

### hàm khác

`Math.random()` tạo một mảng radom

- Math.max(a, b, c...) / Math.min(a, b, c...)
Trả lại số lớn nhất / nhỏ nhất từ ​​số lượng tùy ý của các đối số.

``` 
 alert( Math.max(3, 5, -10, 0, 1) ); // 5
alert( Math.min(1, 2 ); // 1
```

- Math.pow(n, power):lũy thừa
```
alert( Math.pow(2, 10) ); // 2 in power 10 = 1024
```

## string

### Quotes

- chuỗi đặt trong dấu '' ""  ```` 
```
function sum(a, b) {
  return a + b;
}

alert(`1 + 2 = ${sum(1, 2)}.`); // 1 + 2 = 3. dấu `` dùng khi truyền biến 
```
- hoặc kéo nhiều dòng còn đối với '' hoặc "" thì tạch nhé okey! trừ khi dùng \n
```
let guestList = `Guests:
 * John
 * Pete
 * Mary
`;

alert(guestList); // a list of guests, multiple lines
```

### String length

- đếm chiều dài chuỗi
```
alert( `My\n`.length ); // 3
```
### Accessing characters

```
let str = `Hello`;

// the first character
alert( str[0] ); // H
alert( str.charAt(0) ); // H

// the last character
alert( str[str.length - 1] ); // o
```

### Changing the case
in thường và in hoa

```
alert( 'Interface'.toUpperCase() ); // INTERFACE
alert( 'Interface'.toLowerCase() ); // interface
```
 
## Arrays
### Declaration

- cách khai báo một hàm trống 

```
let arr = new Array();
let arr = [];
```
- khai báo và lấy mảng

```
let fruits = ["Apple", "Orange", "Plum"];

alert( fruits[0] ); // Apple
alert( fruits[1] ); // Orange	
alert( fruits[2] ); // Plum
```
- có thể thay thế 1 biến trong mảng `fruits[3] = 'Lemon'; // now ["Apple", "Orange", "Plum", "Lemon"]`

- hàm length đếm số phần tử, 1 mảng có thể lưu nhiều thể loại khácnhau

```
// mix of values
let arr = [ 'Apple', { name: 'John' }, true, function() { alert('hello'); } ];

// get the object at index 1 and then show its name
alert( arr[1].name ); // John

// get the function at index 3 and run it
arr[3](); // hello
```





