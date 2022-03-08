# I. Một số hàm built-in (hàm được xây dựng sẵn)
## 1. alert 

## 2. console
  - Đối tượng console
```
  console.log('') : in ra thông báo 
  console.warn('') : in ra cảnh báo
  console.error('') : in ra dấu x báo lỗi
```

## 3. confirm("messege") : yêu cầu xác nhận
    confirm("bạn đã đủ 18 tuôi?");

## 4. prompt("message") 
  - Tương tự như confirm nhưng sẽ có thêm một ô input để người dùng nhập thông tin 

## 5. setTimeout(function(){ }, delayTime, arg1, arg2, arg3, ... )
    setTimeout(function(){
        alert("thông báo")
    },1000);
- delayTime được tính bằng đơn vị ms(mili giây), trên thực tế không phải sau delayTime thì function sẽ đc thực hiện, nó lâu hơn thế(chênh lệch rất nhỏ)
- setTimeout trả về một id, là một số nguyên dương, nó sẽ được truyền vào hàm clearTimeOut() để hủy hàm setTimeout 
- các tham số arg1, arg2, arg3,  ... sẽ được sử dụng trong function của setTimeout

## 6. setInterval( )
- Tương tự như setTimeout nhưng cứ sau delayTime thì hàm lại được thực thi

## 7. Math.random()
- Tạo một số ngẫu nhiên nằm trong khoảng 0 đến 1 (số thập phân)
- Nếu muốn random ra một số nguyên, ta kết hợp với Math.floor() (Math.floor() làm tròn xuống)
```
Math.floor(Math.random() * n) : trả về một số nguyên ngẫu nhiên từ 0 đến n - 1
```

## 8. toPrecision(x)
- Hàm sẽ format một số trở thành một số có x chữ số có nghĩa 
- Theo hàm, các chữ số có nghĩa là các số từ 1 đến 9 
- Hàm sẽ tìm vị trí đầu tiên mà gặp chữ số có nghĩa, sau đó đảm bảo số sau khi format có x chữ số có nghĩa(x chữ số tính từ vị trí đầu tiên tìm đc số có nghĩa), thêm 0 để đảm bảo đủ độ dài cần có, và sẽ làm tròn nếu cần(làm tròn lên)
```
var a = 0.004 
console.log(a.toPrecision(2)) // 0.0040 -> 4 là số đầu tiên có nghĩa, thêm 0 để đủ là 2 

var a = 0.104 
console.log(a.toPrecision(2)) // 0.10

var a = 0.105 
console.log(a.toPrecision(2)) // 0.11 -> làm tròn lên
```
- Nếu như không truyền gì vào thì x = 0 
- Hàm sẽ trả về một chuỗi 

# II. Toán tử
## 1. Toán tử số học 
### Toán tử lũy thừa : **
``` 
2**3 == 8
```
### Toán tử ++ và -- 
- Khi đứng trước biến   --a / ++a : trừ đi 1/ cộng thêm 1 rồi trả về giá trị mới cho a
- Khi đứng sau biến 
```
a = 5
b = a-- => b vẫn là 5(a sẽ giảm về 4) => tương tự với a++

number = 6
calc = number++ + --number; => calc = 6 + (7-1) = 12
```
## 2. Toán tử so sánh 
- Toán tử so sánh trả về kiểu dữ liệu boolean 
```
var tmp = 1 > 2; => tmp mang giá trị false 
```
## 3. Toán tử logic
### Cách hoạt động của &&
```
var result = 1 && 2 && 3
```
#### Toán tử && kiểm tra từ trái qua phải 
- Kiểm tra 1, không phải thuộc loại falsy, chuyển sang kiểm tra 2
- 2 không phải falsy, chuyển qua 3
- 3 không phải falsy, nhưng đã hết vế để kiểm tra nên && lấy giá trị 3 gán cho result 
- Trong trường hợp kiểm tra đúng loại falsy, && sẽ gán giá trị falsy đó cho result 
  
### Cách hoạt động của ||
```
var result = 1 || 2 || 3;
```
- Toán tử || kiểm tra từ trái qua phải và khi gặp được loại truthy thì lập tức trả về giá trị đó
- Do đó trong trường hợp này result mang giá trị 1 
```
var result = null || 2 || 3; 
```
* result mang giá trị 2

## 4. Toán tử gán
## 5. Toán tử chuỗi 
- Khi 1 trong 2 toán hạng là chuỗi thì đó là phép cộng chuỗi
```
var tmp = 1 + 2 + '3'; => '33'
```
- Thực hiện từ trái qua phải, tính tổng 1 + 2 = 3, rồi cộng chuỗi '3' 
```
var tmp = '1' + 2 + 3; => '123'
```
## 6. Toán tử '+'            
- Nếu các số hạng thuộc dạng boolean, toán tử '+' sẽ convert chúng qua number với giá trị là 1 cho true và giá trị là 0 cho false

# III. Các loại dữ liệu
## Trong JS có 2 kiểu dữ liệu: primitive và complex 
### Primitive(nguyên thủy) gồm 7 loại 
- null
- boolean
- number 
- string 
- undefined 
- symbol
- bigint (ES2020)

### Complex (phức tạp - các kiểu object) gồm 3 loại
- object
- array
- function

## Dữ liệu nguyên thủy : primitive data 
### 1. number 
### 2. boolean 
- Khi khai báo biến boolean người ta thường khai báo biến có 'is' ở đầu 
```
var tmp = isNumber
```
- Cách chuyển một biến sang kiểu boolean 
```
var a = 1;
console.log(!!a); => true
```
### 3. null 
### 4. string 
- Biến có thể bao quanh bởi dấu nháy đơn hoặc nháy kép
- Khi khai báo bằng dấu nháy kép, mà trong biến có chứa dấu nháy đơn thì có thể viết trực tiếp và ngược lại 
- Còn khi muốn khai báo biến bằng dấu nháy đơn và bao gồm cả dấu nháy đơn thì ta dùng \' để thể hiện cho dấu nháy đơn đó
```
var name = 'Nguyen \'hiep\''; => Nguyen 'hiep'
```
### 5. undefined 
### 6. symbol 
```
var id = Symbol('id');
```
- Có đặc tính unique

### 7. BigInt 
 [Tài liệu tham khảo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/BigInt) 


## Dữ liệu kiểu đối tượng ( phức tạp ) : complex data
### 1. function
### 2. object
- Các bộ key-value( thuộc tính ) cách nhau bởi 1 dấu phẩy
### 3. array 
    

## IV. String - Chuỗi
### 1. Tạo chuỗi 
- Ngoài cách tạo thông thường, ta cũng có thể tạo với syntax sau 
```js 
var fullName = new String('hiep nguyen');
```

* Tạo với syntax này thì 'hiep nguyen' là một object nhưng thường ta k hay dùng cách này 
### 2. Backslash ( \\ )
- Sử dụng \\' để biểu thị dấu ' khi khai báo chuỗi bao quanh bởi ' ' và tương tự với  " " 
- Trong trường hợp khai báo bởi dấu " " thì khi có dấu ' ' trong biến thì k cần sử dụng \ và ngược lại 
- Để biểu thị dấu \ ta sử dụng \\\ 

### 3. Template string trong ES6
- Thay vì phải sử dụng dấu '+' để nối chuỗi, ta có thể thay thế bằng    
```js
console.log(`toi là : ${fullName}`)
```
- Ta sử dụng dấu \` \` để làm việc này (dấu dưới nút Esc)

### Các method làm việc với chuỗi
```js 
var myString = 'học js tại js js f8!'
```

#### 1. length : kiểm tra độ dài của chuỗi ( đếm cả dấu cách )
```js
myString.length
```
#### 2. find index 
```js
indexOf('js')  => 4 
```
* Trả về vị trí đầu tiên tìm thấy Chuỗi

#### 3. indexOf ('js', n) : tìm kiếm chuỗi con từ vị trí n 
#### 4. lastIndexOf ('js') : trả về vị trí của chuỗi con cuối cùng 
#### 5. search ('js') : tương tự indexOf('js');
* Nếu k tìm thấy hàm sẽ trả về -1
#### 6. cut string

* 6.1 slice(n,m) : cắt từ vị trí n đến vị trí m (không lấy tại vị trí m)
* 6.2 slice(n) : cắt từ vị trí n đến hết 
* 6.3 slice(-n,-m) : cắt từ vị trí m đến vị trí n nhưng tính từ bên phải sang 
```js 
var tmp = myString.slice(-2,-1); => tmp = f8
```
* 6.4 substr(n,m) : trả về một chuỗi từ vị trí n và cho đến vị trí m, hoặc đến hết chuỗi 
```js
var string = 'javascript'
string.substr(1,4) // avas
string.substr(-1,4) // pt
```
* 6.5 substring(n,m) : trả về một chuỗi từ vị trí n đến trước vị trí m hoặc đến hết chuỗi
```js
var string = 'javascript'
string.substring(1,4) // ava
string.substring(-1,4) // pt
```
* 6.6 replace 
    + replace(chuỗi 1, chuỗi 2) : thay thế chuỗi 1 đầu tiên tìm thấy bằng chuỗi 2
    + replace(/chuỗi 1/g,'chuỗi 2') : thay thế tất cả chuỗi 1  bằng chuỗi 2, /chuỗi 1/g : là biểu thức chính quy (regx)
* 6.7 uppercase : myString.toUpperCase()
* 6.8 lowercase : myString.toLowerCase()
* 6.9 trim : myString.trim( )
    + loại bỏ khoảng thừa ở đầu và cuối chuỗi
* 6.10 split : cắt chuỗi thành array
```js
var language = 'js, php, cpp, java'
var array = language.split(', ') => [js, php, cpp, java]
var array1 = language.split('')  => ["j", "s", ",", " ", "p", "h", "p", ",", " ", "c", "p", "p", ",", " ", "j", "a", "v", "a"]
```
* 6.11 get a character by index
```js
myString.charAt(n) : lấy kí tự tại vị trí n 
```
 * Nếu truyền vào index k có, hàm sẽ trả vể 1 chuỗi rỗng 

## V. Số 
### 1. Cách tạo một giá trị số : 2 cách 
```js
var num1 = 2
var num2 = new(2)
```

* Nên dùng cách 1, cách 2 sẽ rườm rà hơn và mang lại kiểu dữ liệu k mong muốn là kiểu Mảng, trong khi ta chỉ muốn khai báo kiểu number
* Khi thực hiện một phép tính không hợp lệ kết quả trả về sẽ là NaN(Not an Number) nhưng typeof vẫn là number 
* Để kiểm tra xem số đó có phải NaN hay k ta sử dụng isNaN(biến)
### 2. Làm việc với số 
#### Chuyển sang chuỗi 
```
var.toString()
```
#### Làm tròn 
```js
var.toFixed(n)
```
* Làm tròn n số sau dấu phẩy, khi truyền vào giá trị falsy thì mặc định là giá trị 0 và typeof sẽ là string 

## VI. Mảng 
* Có thể lưu tất cả các loại dữ liệu vào 1 mảng 
#### 1. Kiểm tra kiểu dữ liệu
```js
Array.isArray(tên biến)
```
   * Nếu dùng typeof nó sẽ trả về object, do đó ta k phân biệt được đâu là 1 mảng 
#### 2. Kiểm tra độ dài
```js
arr.length
```
#### 3. Kiểm tra vị trí của giá trị nào đó trong mảng
```js
arr.indexOf(giá trị)
```
#### 4. Sắp xếp 
```js
arr.sort(); == arr.sort((a,b) => a-b); sắp xếp tăng dần
arr.sort((a,b) => b-a); sắp xếp giảm dần 
```
#### 5. toString() 
* Chuyển mảng thành dạng chuỗi : trả về một chuỗi gồm các phần tử của mảng cách nhau bởi dấu phẩy
#### 6. join() 
* Nếu không truyền gì vào thi tương tự toString
* Khi truyền một chuỗi vào thi các phần tử của mảng được chuyển sang dạng chuỗi sẽ được cách nhau bởi chuỗi truyền vào hàm join 
#### 7. pop()
* Xóa phần tử cuối mảng và trả về chính phần tử đó, khi mảng đã hết phần tử thì hàm pop trả về undefined 
#### 8. push()
* Thêm các phần tử vào cuối mảng
```js 
push(ele1,ele2,elen)
```
* và trả về độ dài mới của mảng 
#### 9. shift()
* Tương tự như pop nhưng là xóa đầu mảng
#### 10. unshift()
* Tương tự push nhưng là thêm vào đầu mảng 
#### 11. splice(index start, số lượng phần tử muốn xóa,item) 
```js
splice(m,n)
```
* Xóa n phần tử từ vị trí bắt đầu là m và trả về một mảng gồm các phần tử bị xóa theo đúng thứ tự trong mảng cũ
```js
splice(n,0,item)
```
* Thêm phần tử item vào mảng tại vị trí n
```js
splice(m,n,item)
```
* Xóa n phần tử từ vị trí bắt đầu m, thay thế bằng item và trả về một mảng gồm các phần tử bị xóa theo đúng thứ tự trong mảng cũ
#### 12. concat()
* Dùng để hợp nhất 2 mảng với nhau 
```js
a1.concat(a2)
```
* Trả về một mảng mới được nối từ mảng a1 rồi đến mảng a2, mảng a1 không bị thay đổi
```js
var a = [1,2,3]
var c = [4,5,6]
var b = a.concat(c)
console.log(a) // [1,2,3]
```

#### 13.  slice(index start, index end)
* Dùng để trích xuất các thành phần của mảng, trả về 1 mảng mới và 
    không ảnh hướng đến mảng cũ, mảng trả về không bao gồm thành phần có index end
* Nếu các tham số start và end truyền vào là số âm thì hàm sẽ tính từ cuối mảng về
* Giá trị mặc định của index start là 0 và của index end là vị trí cuối cùng của mảng. Do đó nếu ta không truyền bất kì tham số nào vào đồng nghĩa với việc ta lấy tất cả các thành phần của mảng <=> copy mảng
```js
const animals = ['ant', 'bison', 'camel', 'duck', 'elephant']

console.log(animals.slice(2))
// trích xuất từ vị trí 2 đến hết mảng
// output: Array ["camel", "duck", "elephant"]
    
console.log(animals.slice(2, 4))
// trích xuất các thành phần từ vị trí 2 đến 4( không lấy thành phần có index 4)
// output: Array ["camel", "duck"]
    
console.log(animals.slice(1, 5));
// output: Array ["bison", "camel", "duck", "elephant"]
    
console.log(animals.slice(-2));
// output: Array ["duck", "elephant"]
    
console.log(animals.slice(2, -1));
//trích xuất từ index 2 đến index -1, không bao gồm thành phần có index là -1
(-1 là index của elephant(được tính từ cuối mảng))
// output: Array ["camel", "duck"]
```
#### 14. forEach()
* Lặp qua tất cả các thành phần của mảng 
* Không thể sử dụng break và cx k thể sử dụng continue trong forEach 
* Trả về undefined
```js
// Arrow function
forEach((element) => { ... } )

forEach((element, index) => { ... } )

forEach((element, index, array) => { ... } )

// Callback function
forEach(callbackFn)

forEach(callbackFn, thisArg)

// Inline callback function
forEach(function callbackFn(element) { ... })

forEach(function callbackFn(element, index) { ... })

forEach(function callbackFn(element, index, array){ ... })

forEach(function callbackFn(element, index, array) { ... }, thisArg)
```

#### 15. every( )
* Thường dùng để kiểm tra tất cả các phần tử của mảng xem có thỏa mãn điều kiện nào đó
* Trả về giá trị boolean : true khi hàm callBack truyền vào trả về giá trị truthy, false nếu hàm callBack trả về falsy 
#### 16. some( ) 
* Tương tự như every, nhưng khác ở chỗ some chỉ cần 1 trong các thành phần của mảng thỏa mãn điều kiện
    thì sẽ trả về true và kết thúc hàm tại element thỏa mãn đk 
#### 17. find( ) 
* Tìm kiếm các thành phần theo yêu cầu trong hàm callBack, nếu đã tìm thấy thì trả về và kết thúc tại đó luôn
* Nếu không thì trả về undefined
    ```js
    var course = courses.find(function(course,ind)) {
                return course.name === 'ruby';
            }
    ```
* Trả về khóa học có tên là ruby 
            giả sử thành phần phía sau cx có tên là ruby nhưng hàm sẽ kết thúc tại thành phần đầu tiên thỏa mãn
#### 18. filter( )
* Tương tự như find, nhưng nó sẽ trả về tất cả các thành phần thỏa mãn theo hàm callBack
#### 19. map() 
* Duyệt qua tất cả các ele của mảng, trả về 1 mảng mới, ele của mảng mới là giá trị trả về của hàm callBack được gọi bên trong map()
#### 20. reduce() 
[Tài liệu tham khảo](https://viblo.asia/p/tim-hieu-ve-phuong-thuc-reduce-trong-javascript-djeZ1mx8ZWz)
```js
const solve = (accumulator, currentValue, currentIndex, array) => accumulator + currentValue
```
* Ta sử dụng để có thể tính toán 1 giá trị nào đó
* Tham số: hàm callback và giá trị khởi tạo cho thành phần muốn tính toán(có thể k truyền value cho giá trị khởi tạo, nhưng nên truyền để đảm bảo sự chính xác), khi không truyền giá trị khởi tạo thì mặc định giá trị khởi tạo sẽ là thành phần đầu tiên của mảng, và currentValue sẽ là element thứ 2 của mảng
* Các tham số trong hàm callback lần lượt là
    + accumulator : là thành phần ta muốn tính toán 
    + currentValue : giá trị của ele hiện tại của mảng 
    + currentIndex : chỉ số ele hiện tại của mảng
    + array : mảng hiện tại đang gọi reduce 
    ```js
    // Truyền một initialValue cho hàm reduce( )
    a = [2,4,6,8,10]
    a.reduce(solve, 8)
    ```
* Lúc này hàm reduce sẽ nhận 8 làm giá trị khởi tạo và bắt đầu cộng cả 8 với những thành phần của mảng a
* Nếu mảng chỉ có một phần tử và ta k truyền giá trị initialValue hoặc có giá trị initialValue và mảng rỗng thì giá trị sẽ được trả về mà không cần gọi hàm callBack
* Hàm reduce sau mỗi lần lặp sẽ return một giá trị và gán cho biến tích lũy accumulator, tức là ví dụ sau lần reducing đầu tiên giá trị là
    2 + 8 = 10 sẽ được gán cho biến tích lũy accumulator để thực hiện tiếp vòng reducing thứ 2
#### 21. includes()
* Chỉ có với array và string 
* Tìm kiếm xem trong mảng /chuỗi có thành phần đó không 
    ```js
    string.includes(ele,index_start) // tìm kiếm element bất đầu từ index_start

    array.includes(ele,index_start)
    ```
* Khi không có index_start thì mặc định là bất đầu từ 0
* Nếu index_start được truyền vào nhỏ hơn 0, thì index_start sẽ được tính bằng giá trị truyền vào cộng với độ dài mảng và giá trị đó mới là index_start
* Nếu index_start mới này < 0 thì nó quy định index start là 0
* includes() sử dụng dấu so sánh === , tức là so sánh đúng khi phép so sánh là truthy, ví dụ 80 và '80' khi so sánh sẽ không return true (vi khác type)
* Đối với chuỗi, includes phân biệt chữ hoa và chữ thường
* Đối với mảng, không phải độ dài là n thì sẽ có thực sự n ele, nó có thể có những empty ele, khi ta dử dụng vòng for(var i = 0; i< arr.length; i++) nó sẽ lặp theo độ dài mảng, còn với các method của Array nó sẽ chỉ xét các ele thực mà thôi

#### 22. reverse() 
* Đảo ngược mảng và mảng nhận giá trị mới là đảo ngược của nó

* Khi ta định nghĩa ra 1 method mới(giống với việc ta từng code lại các method ở trên f8), nó sẽ được thêm vào prototype, và khi lặp nó cx sẽ được lặp tới, ta dùng hasOwnProperty để tránh nó duyệt cả những thành phần trong prototype
  

## VII. Function
```js
function nameFunction() {
    code 
}
    // định nghĩa 1 hàm

function sayHello() {
    alert('hello');
}

sayHello(); // gọi hàm
```
    
* Nếu hàm có các tham số, khi ta không truyền đủ tham số vào hàm thì tự động tham số đó sẽ là undefined

* Khi các function trùng tên : các hàm khai báo sau sẽ ghi đè các hàm trước đó

* Định nghĩa hàm trong hàm : ta có thể định nghĩa hàm trong hàm một cách bình thường, khi đó hàm được khai báo cũng là 
thành phần nội bộ, chỉ được gọi/sử dụng trong hàm

### Các loại function : 3 loại
#### 1 . Declaration function 
```js
function name(){
        // code here
}
```
* Bắt buộc phải có tên
* Có thuộc tính hoisting (có thể gọi hàm mà k cần định nghĩa trước)
* Có scope sử dụng rộng hơn Expression function

#### 2. Expression function 
```js
var fun = function(){
    // code here
}
```
* Hoặc sử dụng cú pháp es6 tạo ra một function anonymous (khai báo hàm nhưng k dùng từ khóa 'function') cũng đc gọi
    là Expression function
    ```js
    const fun = (){
        // code here
    }
    ```
* Expression function k có thuộc tính hoisting, nên chỉ được sử dụng khi đã định nghĩa

#### 3. Arrow function(học sau)
```js
const logger = (log) => console.log(log)
```
* Ta cũng có thể viết mà không cần phải có thêm ( )
    ```js
    const logger = log => console.log(log)
    ```

* Nếu như sau dấu => không phải là một khối code (khối code được thể hiện qua { }) thì hàm sẽ trả về những gì sau dấu =>
* Còn nếu muốn return một objec, hãy thêm ( ) ở ngoài 
    ```js  
    const course = courseName => ({
        name: courseName
    })
    ```

### Callback là việc gọi lại 1 hàm trong 1 hàm khác, thời điểm callback tùy thuộc vào định nghĩa của hàm và được truyền như 1 tham số cho hàm khác

## VIII. Object 
* Object miêu tả 1 đối tượng
* Gồm nhiều thuộc tính thể hiện qua các cặp key-value
* Các cách đặt tên key 
  + Ta có thể đặt tên theo quy tắc đặt tên hàm/biến
  + Trong trường hợp muốn đặt tên key có chứa cả những kí tự đặc biệt ta để key trong dấu ' '
* Tạo ra một object theo cách đơn giản nhất 
    ```js 
    var person = {
        name: 'hiep',
        age: 18,
        email: 'nguyenhiep01@gmail.com'
    }
    ```
* Cách thêm các thuộc tính
    + Đối với tên đặt theo quy tắc tên biến/hàm 
    ```js 
    object.nameKey = value
    ```
    + Khi muốn có các kí tự đặc biệt hãy để nó trong chuỗi và [ ]
    ```js
    object['nameKey'] = value
    ```
    + Thêm thuộc tính thông qua biến
    ```js
    var emailKey = 'email'
    var myInfo = {
        [emailKey] : 'hiep@gmail.com',
    }
    ```

    + Lấy các thuộc tính của object 
        + object.nameKey 
        + hoặc objcet['nameKey']
        + khi không có thuộc tính đó thì trả về undefined

    + Xóa các thuộc tính : sử dụng delete 
        ```js
        delete object.nameKey
        ví dụ : delete myInfo.email
        ```
    
* Trong 1 object ta cx có thể có các hàm, khi đó ta gọi các hàm là method(phương thức)

- Object constructor : khởi tạo 1 đối tượng
    ```js
    function User(firstName, lastName, Age, Avatar) {//ta viết hoa chữ cái đầu tiên của tên object
        this.firstName = firstName
        this.lastName = lastName
        this.Age = Age
        this.Avatar = Avata
        this.getName = function(){  
            return `${this.firstName} ${lastName}`
        }
    }
    ```
* Object prototype : khi ta muốn thêm thuộc tính/phương thức cho hàm constructor ta không thể thêm trực tiếp 
bằng cách User.nameKey = value mà ta phải thêm nó qua prototype 
    ```js
    User.prototype.name = value
    ```


* Các thuộc tính/phương thức thêm qua prototype sẽ hiện thị ở proto khi ta console.log(User)

#### Đối tượng Date()
* var date = new Date(); lúc này date là 1 object
* var date = Date(); lúc này date là 1 string 
* Hai cách khai báo trên đều trả về thời gian lúc gọi hàm 
* Ta cũng có thể lấy riêng các giá trị ngày, tháng, năm, phút, giây
* Chú ý khi gọi getMonth() nó sẽ trả về từ 0 đến 11, do đó ta cần cộng thêm 1 để được kết quả đúng

#### switch-case trong js sử dụng toán tử === để so sánh

#### Toán tử 3 ngôi (ternary operator) 
```js
var tmp = điều kiên ? tmp1 : tmp2
```
* Nếu điều kiện đúng thì gán tmp1 cho tmp, sai thì gán tmp2 cho tmp


#### Loop
* Vòng for/in lặp qua key 
    ```js
    var object = {
        name: ;
        age: ;
        address: ;
    }        
        
    for(var key in object){
        console.log(key); 
    }

    // Từng thuộc tính/method của object được gán vào key qua từng vòng lặp

    var array = [
        'java',
        'php',
        'html',
        'js',
        'css'
    ]

    for(var key in array){
        console.log(key);
    }
    // index của từng phần tử trong mảng được gán cho key qua mỗi vòng lặp
    ```

* Vòng for/of lặp qua value
    ```js
    var array = [
        'java',
        'php',
        'html'.
        'js',
        'css'
    ]

    for(var value of array){
        console.log(value);
    }
    // từng thành phần được gán vào value trong mỗi lần lặp (chuỗi cũng là 1 mảng)
    ```
    nếu muốn lấy ra cả index, ta sẽ sử dụng method entries
    ```js 
    var person = [
        {
            name: 'hiep',
            age: 18,
        },
        {
            name: 'tuan',
            age: 20,
        },
        {
            name: 'tu',
            age: 21
        }
    ]

    for(const [index, value] of Object.entries(person)){
        console.log(index, value)
    }
    // 0 {name: 'hiep', age: 18}
    // 1 {name: 'tuan', age: 20}
    // 2 {name: 'tu', age: 21}
    ```
    + Object.entries(object) : trả về một mảng, trong mảng đó chứa các mảng con [key, value] tương ứng với cặp thuộc tính - giá trị của object truyền vào 
    ```js
    var person = {
        name: 'hiep',
        age: 18,
    }


    for(const [key, value] of Object.entries(person)){
        console.log(key, value)
    }
    // name: 'hiep'
    // age: 18
    ```

* Một mảng gồm các Object
    ```js
    var person = [
        {
            name: 'hiep',
            age: 18,
        },
        {
            name: 'tuan',
            age: 20,
        },
        {
            name: 'tu',
            age: 21
        }
    ]

    for(const {name} of person){
    console.log(name)
    }
    // hiep 
    // tuan
    // tu
    ```
* Đối với 1 object, for of không thể áp dụng cho nó, ta sẽ dùng method của Object để lặp
    ```js
    var myInfo = {
        name: ;
        age: ;
        address: ;
    }        
    // Object.keys(myInfo); => trả về 1 mảng là tên thuộc tính hoặc method của đối tượng khi đó ta có thể lặp với for of 
        
    for(value of Object.keys(myInfo) ){

    }
    Object.value(myInfo)
    // trả về 1 mảng là các giá trị của đối tượng
    ```
##### Chốt lại :
    * For ... in 
        + Đối với một Object : lấy ra các thuộc tính/method ( các key )
        + Đối với array : các index chính là các key, trong trường hợp array chứa các Object, ta sử dụng {keyName1, keyName2, ...} để có thể lấy ra keyName1, keyName2 của các Object đó
    * For ... of 
        + Đối với Object : không thể lặp bằng For ... of mà phải dùng các method của Object
        + Đối với array : lấy ra các giá trị của mảng

## IX. HTML DOM (document object model)
* 1 trang web có 3 thành phần 
    + các ele
    + attributes
    + text 
* Với JS ta có thể truy cập vào DOM thông qua DOM API và từ đó có thể tùy chỉnh trang web
* Document là thành phần chứa toàn bộ trang web 

### 1. Element
#### Các phương thức Get Element
* ID, class, tag name, CSS seclector, HTML collection
    + getElementById : trả về thành phần "đầu tiên" có Id đó (trả về 1 thành phần nên Element ở số ít)
    + getElementsByClassName : trả về Nodelist(trả về 1 tập hợp nên Element ở số nhiều)
    + getElementsTagName : trả về HTML collection(trả về 1 tập hợp nên Element ở số nhiều)
    + querySelector('.test') : trả về thành phần đầu tiên có Css như đã truyền vào 
    + querySelectorAll('.test') : trả về một nodelist(truy cập như mảng)
    + document.anchors : lấy ra tất cả các thẻ a có thuộc tính name ( trả về dạng HTML collection )
* Chỉ có getElementById và querySelector là trả về trực tiếp ele
* So sánh html collection và nodelist với array 
    + chúng đều có thể truy cập qua index giống như array, có thuộc tính length để lấy độ dài 
    + chúng không có các method như của mảng(push,pop,shift,...)
* Khác nhau giữa html collection và nodelist 
    + html collection chỉ chứa các element node trong khi nodelist chứa mọi loại node(node ele, node text, node attribute) 
    + html collection có thể truy cập bằng tên, id hoặc index còn nodelist chỉ có thể truy cập bằng index 

* get element by attributes : [Tài liệu thêm](https://link-url-here.org)
    + [att~=v1] : lấy ra những element có thuộc tính là att và thuộc tính đó có value chứa v1 trong một danh sách cách nhau bởi khoảng trắng
    ```html
    <div lang="en-us en-gb en-au en-nz">Hello World!</div>

    div[lang~="en-us"] {
        color: blue;
    }
    ```
            

### 2. innerHTML và outerHTML
* innerHTML : sẽ trả về các ele con của ele đang gọi innerHTML, khi ta dùng nó để set html thì nó sẽ ghi đề tất cả các ele hiện tại có trong ele đang gọi innerHTML
* outerHTML : khi dùng để get, nó sẽ trả về thành phần gọi nó, bao gồm cả các ele con bên trong nó khi dùng để set, nó sẽ thay thế ele gọi nó(cả các ele con) bằng chính nội dung mà ta muốn set

### 3. Attribute 
#### Thêm thuộc tính cho ele
```js
ele.name_attribute = value;
ví dụ div.title = "test"
```
* Hoặc ta cũng có thể sử dụng method
    ```js
    setAttribute('name_attribute','value_attribute')
    ```
   Với cách này ta có thể thêm bất kì thuộc tính nào cho ele, kể cả ele không có thuộc tính đó hoặc thuộc tính đó là ta tự tạo ra cho ele

#### Note
* Khi thêm thuộc tính class ta sử dụng từ khóa className, vì từ khóa class trùng với keyword của JS
* Khi ta dử dụng JS để add attribute thì khi xem sourcecode ta sẽ k thấy được những j chúng ta thêm vào, vì chỉ khi JS đc chạy thì những thuộc tính đó mới đc thêm 
#### get attribute 
* Ta có thể lấy ra attribute của ele bằng cách gọi trực tiếp 
    ```js
    a.href
    ```
    Nhưng cách này chỉ dùng được với các attribute hợp lệ của ele, do đó những attribute mà ta thêm vào sẽ k thể lấy theo cách này, mà ta phải sử dụng method getAttribute
    ```js
    a.getAttribute('name_attribute')
    ```

### 4. Text : innerText và textContent 
#### get text 
* innerText : trả về những gì ta có thể nhìn thấy trên trang web 
* textContent : trả về nội dung tất cả các text node có trong trang web, các text node bao gồm cả các dấu tab, dấu xuống dòng, nội dung các thẻ ở trong sourcecode    
    ```html
    <div>inner    text</div>
    ```
    ```js
    console.log(div.innerText)  // inner text
    console.log(div.textContent) // inner    text

    // như đã thấy textContent sẽ lấy cả những khoảng trắng, còn innerText thì không 
    ```

#### set text 
* innerText : khi sử dụng inner text để thêm text, nó sẽ trả về đúng như những gì chúng ta thêm, kể cả các khoảng trắng, dấu tab,..., trong đoạn text của ta nếu như có xuống dòng thì html sẽ xuất hiện những thẻ br (thẻ xuống dòng)
* textContent : đối với textContent, nó sẽ chỉ trả về các đoạn text(có nghĩa là không có các dấu tab, dấu cách, xuống dòng)
#### classList :
* remove( ) : xóa 1 class khỏi ele
* add() : thêm 1 class vào ele
* toggle( ) : nếu có thì xóa, nếu chưa có thì thêm
* contains( ) : kiểm tra class có thuộc ele không
## X. DOM events               
* prevenDefault : hủy bỏ hành động mặc định của tag
* stopPropagation : ngăn chặn sự nổi bọt/lan truyền từ các ele con ra ele cha

### Event Listener 
```js
element.addEventListener('event',function()) 
``` 
* Các hàm callBack đc gọi lại khi event đc lắng nghe và sẽ đc gọi theo thứ tự từ trước sau
* Có thể lắng nghe nhiều lần : 
    ```js
    element.addEventListener('click',function(e){})
    element.addEventListener('dbclick',function(e){})
    element.addEventListener('keydown',function(e){})
    // có thể định nghĩa riêng function và resues trong nhiều addEventListener khác
    ```
* removeEventListener (có add thì đương nhiên có remove, ít dùng)

* JSON : JavaScript Object Notation (ký hiệu đối tượng JS)    
- Là một định dạng dữ liệu(một quy tắc chung) thể hiện dưới dạng CHUỖI, nó tuân theo một quy luật nhất định mà hầu hết các ngôn ngữ lập trình đều có thể đọc được => là tiêu chuẩn để trao đổi dữ liệu trên web
- JSON có thể mã hóa và giải mã các kiểu dữ liệu như Number, String, Boolean, Null, Object
- JSON mã hóa các kiểu dữ liệu(encode) và giải mã chúng khi cần(decode) để các ngôn ngữ có thể trao dổi dữ liệu với nhau
- Mã hóa thông qua Stringify và giải mã ta có method parse
- các đoạn code của JSON bất buộc được viết trong dấu " " , nếu ta đặt nó trong dấu nháy đơn thì đây k phải một chuỗi JSON đúng chuẩn, khi trong value có dấu "" ta có thể thêm \ để biểu thị dấu "" đó

* Cấu trúc chuỗi JSON
- Khi ta thể hiện một object ;
+ được thể hiện bằng dấu {}
+ khái niệm object trong JSON cx tương đồng trong JS, nhưng phải đảm bảo những điều sau đây
    - key : luôn phải để trong dấu " ", không được phép là biến Số
    - value : chỉ thể hiện các kiểu dữ liệu như number, string, boolean, array, object, null và không thể hiện được các dạng như function, date, undefined
    - không được để thừa dấu phẩy ở cuối
    ví dụ : var hiep = {
        "name" : "hiep",
        "age" : 18 -> kiểu số ta k cần để trong " "
    }

            var person = [{
                "name" : "hiep",
                "age" : 18
            },
            {
                "name" : "tien",
                "age" : 18
            }]
- Khi nào cần sử dụng JSON : khi ta muốn lưu trữ dữ liệu ở dạng metadata(siêu dữ liệu) ở phía server, chuỗi JSON sẽ được lưu ở database và khi cần sẽ được giải mã

* Promise 
- Synchronous(đồng bộ) và Asynchronus(bất đồng bộ) trong JS
- Sync : là xử lý đồng bộ, có nghĩa là đoạn mã nào đc viết trc sẽ thực hiện trước, từ trên xuống dưới từ trái qua phải, chỉ khi biên dịch xong dòng thứ nhất mới chuyển sang dòng thứ hai -> điều này dẫn tới trạng thái chờ
- Async : xử lý bất đồng bộ, các đoạn code có thể k thực hiện theo thứ tự được viết, ví dụ hàm setTimeout có thể thực hiện sau dù nó được viết trước
- Khi xử lí bất đồng bộ, hay đồng bộ thường ta sẽ sử dụng callback, nhưng khi đó sẽ có trường hợp có quá nhiều hàm callback lồng vào nhau(đc gọi là callback hell) =>  promise sinh ra để giải quyết chuyện đó(hạn chế callback hell)

- Khởi tạo Promise : var promise = new Promise(function(resolve, reject){
    code xử lí
    nếu xử lí thành công ta trả về resolve;
    nếu thất bại ta trả về reject;
})

- Constructor của Promise nhận một function(được gọi là executor) có 2 hàm call là resolve(thực hiện khi tác vụ bất đồng bộ được xử lí thành công) và reject(thực hiện khi tác vụ xử lí bất đồng bộ thất bại)

- Promise có 3 trạng thái 
+ Pending : trạng thái chờ, kết quả chưa được xử lí xong
+ Fullfiled : tác vụ được thực hiện thành công
+ Rejected : tác vụ không đồng bộ thất bại
  ** 2 trạng thái cuối đc gọi chung là Settled, một promise chỉ có thể chuyển từ Pending sang Settled và không có chiều ngược lại

+ promise
    .then(function{ }) : được thực hiện nếu promise trả về resolve, các hàm them có thể nối tiếp nhau, hàm sau nhận một promise của promise của hàm trước trả về(đợi promise hoàn thành) nếu hàm then trước không trả về promise thì chương trình lọt luôn vào hàm sau
    .catch(function{ }) : được thực hiện khi promise trả về reject, tương tự khi các hàm then trả về 1 promise ở trạng thái rejected thì hàm catch lập tức được gọi
    .finaly(function{ }) : luôn được thực hiện khi promise được chuyển sang trạng thái Settled(có nghĩa là promise đã trả về reject hay resolve)
* Tính chất chuỗi của Promise : ta có thể .then() nhiều lần cho cùng một promise, các .then() nối tiếp nhau
    ví dụ : var promise = new Promise(function(resolve, reject){
                                // logic
                            })

            promise
            .then(function(){
                console.log(1)
            })
            .then(function(){
                console.log(2)
            })
            .catch(function(){
                console.log('error')
            })
    các hàm .then sẽ thực hiện lần lượt theo thứ tự, nhưng giả sử một hàm .then nào đó return một Promise(), thì các hàm then/catch sau đó sẽ chờ cho đến khi Promise() mới được return đó thực hiện xong thì chúng mới thực hiện tiếp
    => đây là tính chất chuỗi của Promise

- Promise có 3 method
    + Promise.resolve() : khi ta có một promise và bt chắc chắn rằng nó sẽ thành công, ta có thể khởi tạo luôn với syntax Promise.resolve() mà không cần khởi tạo như syntax ban đầu
    + Promise.reject() : tương tự với resolve()
    + Promise.all([]) : giả sử ta có nhiều Promise(), chúng không phụ thuộc nhau, lúc này nếu xử lý từng Promise sẽ mất nhiều tgian hơn là xử lý chúng một cách song song. Method .all của Promise cho phép chúng ta xử lý các Promise một cách song song
        + tham số của method .all là một mảng, gồm các promise
        + Promise.all() cũng là một promise, do đó cx có .then và .catch
        + khi tất cả các promise trong mảng truyền vào được xử lý xong thì mới chạy vào .then/.catch
        + nếu tất cả các promise đều resolve, dữ liệu trả về của chúng sẽ được lưu vào một mảng và mảng đó chính là kết quả trả về của .all
        + nếu một trong số đó bị reject thì Promise.all() sẽ chạy .catch() như bình thường, nó sẽ trả về error của promise đầu tiên bị reject dù có một hay nhiều promise bị reject hay không
        ví dụ :
        // resolve
        var promise1 = new Promise(function(resolve) {
                                        setTimeout(function(){
                                            resolve([1,2,3])
                                        }, 1000)
                                    })
        var promise2 = new Promise(function(resolve) {
                                setTimeout(function(){
                                    resolve([1,2])
                                }, 1000)
                            })
        Promise.all([promise1, promise2])
            .then(function(result){
                console.log(result)  => output : [[1,2,3],[1,2]]
            })
        // reject
        var p1 = Promise.reject('Lỗi 1!')
        var p2 = Promise.reject('Lỗi 2!')
        var p3 = Promise.resolve(3)

        Promise.all([p1, p2, p3])
        .then(function([s1, s2,s3]){
            console.log(s1 + s2 + s3)
        })
        .catch(function(err){
            console.log(err) => output : Lỗi 1!
        })

- Một cách viết khác của .catch 
    + khi một promise bị reject, ta sẽ viết hàm catch để bắt lỗi, nhưng cx còn một cách khác tiện lợi hơn, đó là ta bắt lỗi trong hàm then
    + cụ thể : hàm then có thể có 2 tham số truyền vào, 2 tham số này đều là function callback
            ví dụ promise.then(function1(){}, function2(){})
    + khi đó function1() sẽ được gọi khi promise trả về resolve và function2() sẽ được gọi khi promise trả về reject
    https://viblo.asia/p/gioi-thieu-ve-promise-trong-javascript-mrDGMJVPezL

** API : là viết tắt của Application Programing Interface
- Nó dùng để các ứng dụng có thể giao tiếp, trao đổi data với nhau
    ví dụ : khi ta đi ăn nhà hàng, ta gọi món để nhà bếp có thể chuẩn bị và khi món ăn đã đc chuẩn bị thì cần một ai đó chuyển thức ăn đến vị trí ngồi của chúng ta. Đó chính là nhiệm vụ của nhân viên phục vụ, vai trò này tương tự như API 
- Nó sẽ xử lý yêu cầu của ta sau đó truyền về phía server và nhận dữ liệu từ phía server để render ra các data cho ta
- Data mà nó trả về có thể ở dạng JSON hoặc XML
- Theo tiêu chuẩn REST, API có các loại sau :
    CRUD
    + Create : tạo mới dữ liệu - sử dụng method Post
    + Read : lấy dữ liệu - sử dụng method Get
    + Update : cập nhật dữ liệu - sử dụng method Put / Patch
    + Delete : xóa dữ liệu - sử dụng method Delete

** Fetch 
- Được sử dụng để có thể call API
- Trả về một promise và ta sử dụng method json để có thể chuyển nó về dạng đối tượng
    ví dụ : data = fetch(apiURL).then(response => response.json())
    lúc này response là một promise thứ 2 ở dạng resolve và trả vể các dữ liệu của JS 



*** ES6 : ECMAScript 6 là phiên bản thứ 6 của ngôn ngữ JS, ra đời tháng 6 năm 2015
phiên bản ES 5 ra đời năm 2011

** var / let / const https://2ality.com/2015/02/es6-scoping.html
- var 
+ scoped : trừ phi biến được khai báo với var trong phạm vi một function thì phạm vi sử dụng của nó sẽ chỉ là hàm đó, còn không phạm vi của biến đó sẽ là global 
+ đối với vòng for, nếu biến i được khai báo với var thì nó cũng là tương tự như trên tức là trừ phi vòng for đó nằm trong một function, còn không thì biến i đó vẫn có scope là global 
+ ta có thể gán một biến được khai báo vs từ khóa var trước khi ta khái báo nó 
    ví dụ : a = 18;
            var a
            console.log(a) // 18
+ sở dĩ ta có thể làm như vậy là do khi biên dịch những biến đc khai báo là var sẽ được biên dịch là 
        var a;
        a = 18 
    => đây là đặc tính hoisting của các biến var (hoisting : hiểu là được ưu tiên lên đầu)
+ các biến là var có thể tái khởi tạo 
    var a = 18;
    var a = 3;
    console.log(a) // 3

do khi sử dụng var ta rất khó có thể kiểm soát được rằng biến đó có bị thay đổi giá trị hay không( vì var là biến global và có thể trong một đoạn code lớn ta có thể sử dụng cùng một tên biến cho nhiều biến chẳng hạn, như vậy các biến sẽ bị trùng và từ đó giá trị có thể thay đổi) nên trong phiên bản ES6 đã có sự xuất hiện của let và const để giải quyết vấn đề này 

- let
+ scoped trong khối code, không thể tái khởi tạo trong cùng một khối code, trừ phi được khai báo không thuộc phạm vi khối code hay function nào thì biến đó ms có scoped là global
    ví dụ :
    {
        let a = 4
        {
            let a = 2 
        }
        console.log(a) // 4
    }
        let a = 4
        {
            let a = 2 
            let a = 3 
            // báo lỗi
        }
        console.log(a) // 4
    }

+ let được sử dụng để khai báo biến i trong vòng for: nó sẽ tạo ra một scoped chỉ trong vòng for đó, do đó biến i khôn thể sử dụng ở ngoài vòng for 

** sự khác nhau giữa let và var với for: https://stackoverflow.com/questions/40519064/i-am-confused-with-javascript-let-and-var-in-for-loop

- const
+ scoped: chỉ trong code block, trừ phi được khai báo không thuộc phạm vi khối code hay function nào thì biến đó ms có scoped là global
+ không thể tái khởi tạo trong cùng một khối code (immutable: bất biến)
+ đối với các loại dữ liệu primitive (nguyên thủy) ta sẽ không thể gán lại giá trị cho biến const(tức là không thể dùng toán tử gán lần thứ 2)
+ đối với các kiểu dữ liệu đối tượng(array, ojbect, function) thì ta cũng không thể gán lại trực tiếp giá trị cho biến const, nhưng ta vẫn có thể gán lại giá trị cho các thuộc tính(đối vs object), cho từng thành phần cụ (đối với mảng)
        ví dụ : 
            const a = [1,2,2,3]
            a[2] = 4
            console.log(a) // 1,2,4,3

            const a = {
                name : "JS"
            }
            a.name = 'PHP'
            console.log(a.name) // PHP

** classes
- syntax :
    ví dụ : class Course {
        constructor(name, price){
            this.name = name;
            this.price = price;
        }

        // các method khác
    }

** default parameter value : giá trị mặc định cho tham số
- khi sử dụng hàm có những khi ta không truyền hết giá trị cho các tham số, khi đó ta cần một giá trị mặc định cho chúng
    syntax : function logger(log, isAlert = false){
        if(isAlert) return alert(log)
        console.log(log)
    }

    logger('mess') => có thể thấy hàm logger có 2 tham số, nhưng ta lại chỉ truyền vào đó một giá trị cho tham số log, còn isAlert thì ta không truyền, lúc này isAlert mặc định sẽ được gán cho giá trị là false như ta đã định nghĩa và output sẽ là mess 

chốt : các tham số nếu như không đc truyền giá trị hoặc được truyền undefined thì giá trị của chúng sẽ là giá trị đã đc default trước, trong ví dụ trên thì giá trị mặc định của isAlert là false

- giả sử ta khai báo 1 tham số không được default value ở phía sau 1 tham số đc default value và khi truyền ta lại chỉ truyền 1 tham số thì tham số thứ 2 kia sẽ là undefined
    ví dụ : function sum(a = 1, b){
        return a + b 
    }

    sum() // undefined( x = 1 và y = undefined)
    sum(2) // undefined(x = 2 và y = undefined)

- một vài ứng dụng/ ví dụ : 
    vd1 : 
    function append(value, array = []) {
        array.push(value)
        return array
    }

    append(1)  // [1]
    append(2)  // [2], not [1, 2]

    vd2 : 
    function callSomething(thing = something()) {
        return thing
    }

    let numberOfTimesCalled = 0
    function something() {
        numberOfTimesCalled += 1
        return numberOfTimesCalled
    }

    callSomething()  // 1
    callSomething()  // 2

** enhanced object literals : cung cấp syntax ngắn gọn hơn cho
- định nghĩa key: value cho object
    syntax : var name = 'js'
             var price = 1000

             var course = {
                name: name,
                price: price
             }

        ta có thể viết ngắn gọn như sau(trong trường hợp ta để key cx tên với biến chứa value)
             var course = {
                 name,
                 price
             }

- định nghĩa method cho object
            var course = {
                name: name,
                price: price
                getName : function (){ 
                    return this.name
                }
             }        

             tương đương vs 
             var course = {
                name: name,
                price: price
                getName() {
                    return this.name
                }
             }

- định nghĩa key của object dưới dạng biến 
            var attribute1 = 'name'
            var attribute2 = 'price'

            var course = {
                [attribute1] : 'js',
                [attribute2] : 1000

            }
    + ta cũng có thể sử dụng các biến đó để tính toán để tạo ra thuộc tính cho object 
            var course = {
                ['course' + attribute1] : 'js' // coursename : 'js'
            }

** Destructuring 
- giả sử ta có 1 mảng arr = [1,2,3], ta muốn lấy ra từng thành phần của mảng 
    + thay vì var a = arr[0]
            var b = arr[1]    
            var c = arr[2]
    thì h ta chỉ cần var [a,b,c] = arr 
    **chú ý : [a,b,c] : không phải một mảng 

    + var [a , , c] = arr // 1 3
        dấu ", ," thể hiện ta bỏ qua arr[1] mà không gọi đến nó 

    + rest parameter : 
        syntax : var [a, ...rest] = arr 
        console.log(rest) // 2 3 

    => tham số rest sẽ trả về một mảng gồm các phần tử còn lại trong arr , trừ những phần tử đã được khai báo trước đó 

- tương tự với mảng, đối với objcet ta cx có thể làm tương tự
    var course = {
        name : 'js',
        price : 1000,
        childrenCourse : {
            name : 'react'
        }
    }

    + var {name , price } = course // js 1000
        chú ý : các biến trong {} phải trùng với keyName của objcet, nếu như biến nào đó không trùng với keyName thì biến đó sẽ là undefined
    + tương tự, ta cx có thể sử dụng rest để trả về các key còn lại, và nó sẽ trả về một objcet
    + giả sử muốn lấy ra tên của objcet con trong course(ở đây là childrenCourse)
        * nếu var {name, childrenCourse : { name }}
        - ta sử dụng {} cho childrenCourse để lấy ra các keyName
        - nếu như đều dùng name để lấy giá trị thì name thứ nhất(name của course) sẽ bị ghi đè bởi name của childrenCourse
        - do đó ta cần đổi tên để có thể lấy đc giá trị của cả 2 bọn chúng
            syntax : var { name : parentName , childrenCourse : {name}} 
            ta cx có thể đổi tên name của childrenCourse, ta chỉ cần đảm bảo chúng có tên khác nhau và khi đã đổi tên thì các tên cũ sẽ không thể sử dụng 
    + trong trường hợp ta lấy ra một key mà không tồn tại trong objcet, nó sẽ được trả về là undefined
    + ta cũng có thể sử dụng default value trong trường hợp này 
        var { name , des = 'giá trị mặc định'} = course // js giá trị mặc định

** Spread(phân rã) : đúng như ý nghĩa, nó sẽ phân rã một mảng/objcet thành các thành phần của mảng/các thuộc tính của objcet, khác với ...rest
        var a = [1,2,3,4,5]

        console.log(...a) // 1 2 3 4 5 
- phân biệt vs rest 
    function logger(a , b, ...rest){ // rest
        console.log(a,b); // 1 2
        console.log(rest) [3,4,5]
    }

    logger(...a) // Spread
- dễ dàng nối các mảng với nhau 
    var b = [10,11,12]
    var c = [...b, ...a] // [10,11,12,1,2,3,4,5]
- thêm phần tử mới vào mảng : 
    a = [...a, 87] // [1,2,3,4,5,87]
- tìm min, max 
    var max = Math.max(...a) // 5 => đây cx là cách biến mảng thành một danh sách các tham Số
- gộp 2 objcet thành 1 
    var course1 = {
        name: 'js',
        des: 'cơ bản'
    }

    var course2 = {
        price: 1000
    }

    var course3 = {
        ...course1,
        ...course2
    }
    // 
    { 
        name : 'js',
        des : 'cơ bản',
        price : 1000
    }

    var course4 = {
        ...course1,
        ...course2,
        des: 'nâng cao'
    }
    //
    {
        name:'js',
        des:'nâng cao',
        price: 1000
    }

    ** chú ý : Spread sẽ tạo ra một tham chiếu mới, sau đó sao chép các giá trị của tham chiếu cũ vào tham chiếu mới. Do đó, bất cứ điều gì làm thay đổi tham chiếu cũ cx không ảnh hưởng đến tham chiếu mới(khác với phép gán sẽ làm thay đổi theo)
        var a = [1,2,3,4,5,6]
        var b = a
        var c = [...a]
        a[0] = 9
        console.log(b) // [9,2,3,4,5,6]
        console.log(c) // [1,2,3,4,5,6]

** Template literals trong ES6 
1. Khởi tạo chuỗi
- Bình thường ta có thể khởi tạo chuỗi bằng single quote('') hoặc double quote("")
- Ta cx có thể khai báo chuỗi bằng Template literals(sử dụng dấu ` `)
    ví dụ : var str = `this is a string`
    tuy nhiên theo quy ước chung, ta chỉ sử dụng Template literals khi thực sự cần đến các khả năng khác của nó và sử dụng sing quote or double quote cho các chuỗi đơn giản khác

2. Multi-line string 
- khi tạo chuỗi nếu ta sử dụng dấu \ để có thể viết chuỗi đó trên nhiều dòng, nhưng thực sự các chuỗi đó khi ở giao diện vẫn sẽ ở trên 1 dòng và chỉ cách nhau bởi các khoảng trắng
- nếu muốn thực sự các chuỗi đó sẽ ở trên nhiều dòng, ta phải sử dụng dấu \n 
- tuy nhiên vs Template literals ta không cần phải \n quá nhiều nữa, khi cần xuống dòng chỉ cần enter là đc 
    ví dụ : 
    var str = `this is 
    string`
    // 
    this is 
    string 
    *chú ý : khi sử dụng Template literals, nó sẽ thể hiện đúng như những gì chúng ta làm ở trình soạn thảo, cụ thể như ở ví dụ trên ta không thụt đầu dòng ở dòng string, nhưng nếu ta thụt vào thì khi lên giao diện nó cx sẽ thụt vào đầu dòng như những j cta đã code ở trình soạn thảo 
    var str = `this is 
            string`
    //
    this is string

3. Biểu thức nội suy 
- ta có thể truyền vào một biến khi kháo báo một chuỗi với ký tự ${}
    var course = 'js'
    var tmp = ` học ${course} để làm web`

    var age = 19 
    var cnt = `you can ${age < 21 ? 'not' : ''} view`
    console.log(cnt) // you can not view
    
điều mà khi khai báo với single quoute or double quote k thể làm đc

4. Tagged Template literals
- ví dụ : 
    function highlight(strings, ...log){
           console.log(strings) // ['học lập trình',' tại ', '!']
           console.log(log) // ['js', 'f8']
    }

    var course = 'js'
    var brand = 'f8'
    const html = highlight`học lập trình ${course} tại ${brand}!`
    
- Hàm highlight sẽ nhận vào các tham số sau 
+ một mảng đầu tiên chứa các chuỗi không phải biến nội suy(là những biến được truyền vào qua ${}), bao gồm cả các dấu cách(ví dụ như ' tại ' ở ví dụ trên)
+ mảng thứ 2 chứa các biến nội suy, chú ý nếu ta k sử dụng rest ở đây thì log sẽ chỉ nhận biến đầu tiên được lấy đó là course(có nghĩa là nếu k sử dụng ...rest tức là ta k truyền vào một mảng với rest mà khi đó ta chỉ truyền vào 1 biến)
+ cả 2 tham số truyền vào đều là mảng nên ta có thể sử dụng rest và spread một cách bình thường
    ví dụ : 
    function toHTML([first, ...rest], ...values){
        return values.reduce(
            (acc, curr) => [acc, `<span>${curr}</span>`, rest.shift()],
            [first]
        )
    }

    var course = 'js'
    var brand = 'f8'
    var html = toHTML`học lập trình ${course} tại {brand}!`
    // ['học lập trình', '<span>js</span>', ' tại ', '<span>f8</span>','!']
    // giải thích code : 
    - hàm toHTML nhận 2 tham số truyền vào là mảng ['học lập trình',' tại ', '!'] và mảng ['js', 'f8']
    - [fist, ...rest] : theo lý thuyết về rest thì first sẽ nhận giá trị là 'học lập trình', ...rest sẽ là mảng gồm các thành phần còn lại trong mảng 1
    - ...values sẽ là mảng gồm các biến nội suy
    - values.reduce : lặp qua các thành phần của mảng values
    - hàm reduce nhận 2 tham số là một callBack và giá trị khởi tạo cho acc 
    - lặp lần 1:
    + acc nhận giá trị của first => acc : 'học lập trình'
    + curr nhận giá trị đầu tiên của mảng values => curr :'js' 
    + rest.shift() : xóa và trả về thành phần đầu tiên của mảng rest => ' tại '
    + trả về một mảng ['học lập trình', '<span>js</span>', ' tại '] và mảng này lại được gán cho acc 
    - tương tự lặp lần 2 được kết quả như trên : ['học lập trình', '<span>js</span>', ' tại ', '<span>f8</span>','!']
5. String.raw()
- nó sẽ ngăn cho các kí tự đặc biệt thực hiện nhiệm vụ của mk, trừ những gì được đặt trong dấu nội suy(${})
    ví dụ : const tmp = String.raw`hi \n people` // hi \n people
        kí tự \n sẽ không thể thực hiện vc xuống dòng của mk, tương tự với những kí tự đặc biệt khác 
    var str = String.raw`hi \n${2+3}` // hi \n5
- thay vì phải \\ để biểu diễn \ thì ta có thể dùng String.raw
    const filePath = String.raw`C:\Development\profile\aboutme.html`;

    console.log(filePath) // C:\Development\profile\aboutme.html
- ví dụ khác : 
    String.raw({
        raw: ['foo', 'bar', 'baz']
        }, 2 + 3, 'Java' + 'Script'); // 'foo5barJavaScriptbaz'




