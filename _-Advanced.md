## 1. IIFE :  Immediately Invoked Function Expression (khởi tạo một hàm và thực thi ngay nó)
```js
(function(){ //theo expression function
    // code here
})()

(() => { // theo arrow function
    // code here
})()
```

### Truyền tham số cho hàm:
```js
(function(age, name){
        console.log(age, name) // 18 'hiep'
})(18, 'hiep') // tham số được truyền vào từ đây
```
    
### Viết dấu ' ; ' trước IIFE
* Bình thường khi cần gọi một hàm ta có syntax như sau: 
    nameFunction( )
* IIFE là một hàm được định nghĩa và gọi ngay lập tức, ta có thể thấy ta viết code trong một (). Do đó ta cần thêm dấu ';' trước khi viết một IIFE để tránh lỗi 
    ```js
    var name = 'apolo'
    (function(age, name){
        console.log(age, name) // 18 'hiep'
    })(18, 'hiep')
    // nếu như không có dấu ';' trước IIFE, trình biên dịch sẽ hiểu 'apolo' kia là một tên hàm và đang gọi đến hàm 'apolo' đó, do () của phần IIFE 
    ```
    code đúng
    ```js
    var name = 'apolo'
    ;(function(age, name){
        console.log(age, name) // 18 'hiep'
    })(18, 'hiep')
    ```

* Tất cả những gì thuộc về IIFE đều không thể truy cập chúng từ bên ngoài khối code IIFE đó, kể cả tên hàm và các biến 

### các trường hợp có thể sử dụng IIFE 
#### Trường hợp 1:
```js
for(var i = 0; i < 10; i++){
    setTimeout(function(){
        console.log(i); // biến i ở đây là biến i của for
    })
}
    // output: 10 (in 10 lần)
```
* setTimeout sẽ đợi cho đến khi for đc chạy xong và bắt đầu chạy, khi đó i = 10 
    điều này cũng xảy ra khi sử dụng với for in, for off, asynchronous, promise 

* Nhưng điều chúng ta mong muốn là in ra từng i với mỗi vòng lặp, lúc này IIFE sẽ phát huy tác dụng 
    ```js
    for(var i = 0; i < 10; i++){
        (function(i){
            setTimout(function(){
                console.log(i) // đây là biến i được sử dụng trong IIFE và
                                    những j thuộc về IIFE sẽ có scoped chỉ trong khối IIFE mà thôi
            })
        )(i) // biến i ở đây là biến i của for
    }
    ```

    hoặc ta có thể sử dụng từ khóa let để thay cho var, từ khóa let tạo ra scoped cho biến i là chỉ trong khối code đó mà thôi

#### Trường hợp 2:
```js
const app = (function() {
    const cars = []
    return {
        add(car) {
            cars.push(car)
        }, 
        edit(index, car){
            cars[index] = car 
        }, 
        delete(index) {
            cars.splice(index, 1)
        }
    }
)}
// cars đảm bảo sẽ không bị truy cập được từ bên ngoài, từ đó đảm bảo được tính an toàn, bảo mật, toàn vẹn dữ liệu được đảm bảo (giống vs tính đóng gói trong java)
```
[Tài liệu tham khảo](https://stackoverflow.com/questions/750486/javascript-closure-inside-loops-simple-practical-example)

## 2. Scoped ( Đọc lại về var, let, const ở trên nếu k nhớ )
* Các biến nếu được khai báo không theo từ khóa nào trong 3 từ khóa trên thì mặc định có scoped global, dù nó có được khai báo ở trong function hay code block
* Các biến được khai báo trong code block với let, const thì scoped sẽ là code block đó, nhưng vs var thì không
* Khi một hàm được gọi một phạm vi mới của riêng hàm đó sẽ được tạo ra
* Các hàm có thể truy cập vào các biến được khai báo trong phạm vi của nó và bên ngoài phạm vi của nó, nhưng đương nhiên hai hàm có cùng mức phạm vi sẽ không thể truy cập vào biến được khai báo trong hàm kia 
### Các biến được tìm kiếm và truy cập như thế nào:
```js
{
    //scoped 3
    {
        //scoped 2
        var tmp = 10
        {
            //scoped 1
            console.log(tmp) // 10
        }
    }
}
```

* Khi console.log được gọi, nó sẽ tìm kiếm biến tmp trong scoped 1, nếu không thấy nó sẽ tìm tmp ở các scoped cha(trong trường hợp này là scoped 2), giả sử scoped 2 cx k thấy nó sẽ tìm ra scoped 3
* Nếu ở scoped 3 cx có biến tmp với giá trị là 9 thì câu lệnh console.log() vẫn sẽ lấy giá trị tmp là 10, vì scoped 2 gần scoped 1 nhất 

### Khi nào một biến bị xóa khỏi bộ nhớ 
* Biến toàn cục (global) : biến sẽ bị xóa nếu chương trình kết thúc 
* Biến trong code block, trong function : bị xóa khi khối code/function đó được thực hiện xong 
* Biến trong hàm được tham chiếu bởi 1 hàm khác 
    ```js
    function control(){
        let cars = []

        return {
            get(index) {
                return cars[index]
            },
            edit(index, car){
                cars[index] = car
            },
            add(car){
                cars.push(car)
            },
            show(){
                console.log(cars)
            }
        }
    }

    var carApp = control()
    carApp.add('BMW')
    console.log(carApp.get(0)) // 'BMW'
    carApp.add('audi')
    carApp.show() // ['BMW', 'audi']
    ```

    - Ta có thể thấy biến cars được khai báo trong phạm vi của hàm control. Theo những trường hợp trước nó sẽ bị xóa khi hàm control kết thúc
    - Nhưng hàm control lại return một đối tượng cho biến carApp, trong đối tượng đó cũng có biến cars, khi đó biến cars chính là biến được tham chiếu, và carApp là một biến global, trong đó chứa biến cars, do đó biến cars cx sẽ chỉ bị xóa đi khi chương trình kết thúc
    - Thêm vào đó, tính bảo mật của code cũng đc đảm bảo, khi mà ta không thể truy cập trực tiếp vào biến cars(vì vốn dĩ hàm control không return ra biến cars mà chỉ return ra các method để chỉnh sửa) nên từ đó biến cars có tính private

## 3. Closure (tạm dịch : bao đóng)
* Một Closure là một hàm bên trong mà có thể truy cập được vào biến của một hàm bên ngoài(chứa nó) và cả các tham số của hàm bên ngoài, và đương nhiên truy cập được vào biến được định nghĩa trong chính nó và cả biến global
    ```js
    function showName (firstName, lastName) {

        var nameIntro = "Your name is ";
        
        // Đây là hàm bên trong mà có thể truy cập đến biến của hàm bên ngoài, truy cập được tham số của hàm ngoài.
        function makeFullName () {
            return nameIntro + firstName + " " + lastName;
        }
        
        return makeFullName ();
    }

    showName ("Michael", "Jackson"); // Your name is Michael Jackson    
    //  => makeFullName là một closure
    ```
* Closure lưu tham chiếu đến biến của hàm bên ngoài(có thể xem lại ví dụ cuối trong phần scoped về cars), các biến được tham chiếu sẽ không bị xóa khi hàm cha của nó kết thúc

* Closure đôi khi trở nên không như ý muốn, chính là trong ví dụ về IIFE, khi mà biến i được khai báo với từ khóa var sẽ không thể sử dụng cho từng vòng lặp và nó sẽ đợi khi for kết thúc mới tham chiếu đến biến i đó mà chạy (closure tham chiếu đến biến chứ không tham chiếu đến giá trị ), ta đã giải quyết lỗi đó bằng cách sử dụng IIFE hoặc từ khóa let 

## 4. Hoisting
* Hoisting được hiểu là đưa sự khai báo lên trên đầu của phạm vi mà biến/hàm đó 
* Nó cho phép sử dụng biến/hàm trước khi ta thực sự khai báo chúng, tuy nhiên không phải trường hợp nào code cx có thể chạy
* Các biến khi chưa được khởi tạo mà đã sử dụng sẽ gây lỗi. Đó là các biến được khai báo với let, const
* Đối với các biến khai báo với var, nó sẽ được hoisting lên đầu của scoped và được khởi tạo là undefined, do đó nó có thể sử dụng mà chưa cần khải khởi tạo
    ```js
    console.log(mess) // undefined 
    var mess = 'từ khóa var'
    console.log(mess) // 'từ khóa var'
    ```

* Khác với var, biến được khai báo với let hay const sẽ cũng được hoisting lên đầu nhưng không được khởi tạo cho giá trị nào nên sẽ gây lỗi khi sử dụng chúng trước khi khởi tạo 
    ```js
    console.log(mess) // chương trình lỗi ngay tại đây
    let mess = 'từ khóa var'
    console.log(mess) 
    ```
* Trong trường hợp các biến được khai báo nhưng không có keyword(var/let/const) nào đi kèm và thậm chí ngay cả khí chúng được gán cho một giá trị, nó sẽ không được hoisting, nên nếu sử dụng chúng trước khi khởi tạo sẽ gây lỗi

* Function 
  + Viết theo declaration: tương tự như var 
  + Viết theo expression: viết theo expression có nghĩa là gán cho một biến, trong trường hợp này, biến đó sẽ được hoisting, nhưng biểu thức hàm gán cho biến đó không đc khởi tạo do đó cx sẽ gây lỗi

* Class
  + Viết theo declaration: class này vẫn sẽ được hoisting nhưng cx sẽ k đc gán giá trị khởi tạo 
  + Viết theo expression: tương tự trường hợp của function expression

* Vậy các biến khai báo với let/const, các function expression, class expression không được sử dụng trước khi khởi tạo như vậy thì hoisting làm j. Mục đích của hoisting trong trường hợp này là để cho các đoạn code trong cùng một scoped biết rằng trong scoped này đã tồn tại chúng, và không cần phải tìm kiếm ở các scoped cao hơn 

#### Note : Hoisting không được khuyến khích để sử dụng 

## 5. Strict mode : chế độ nghiêm ngặt 
* Cách sử dụng: ta có thể để chuỗi "use strict" ở đầu một file Script hoặc ngay dưới thẻ Script nếu code trong html hay ở đầu của một function. Vị trí đặt chuỗi sẽ quyết định phạm vi mà strict mode ảnh hưởng tới

* Đối với function ở phạm vi global, nếu có sử dụng this trong hàm thì this sẽ là undefined

* Nếu this ở phạm vi global thì this chính là object window

### Những điều bạn không thể làm khi code với strict mode 
* Không thể khai báo biến mà không có keyword(var/let/const)

* Đối với những thuộc tính của đối tượng mà có writable là false, tức là không thể ghi đè, nhưng nếu code ở normal mode thì ta vẫn có thể code ghi đè chúng, nhưng đương giá trị của nó vẫn không thay đổi, nhưng chúng ta cũng sẽ không nhận lại được một lỗi từ bộ biên dịch. Với strict mode, khi chúng ta code ghi đè một thuộc tính cá writable: false thì sẽ có lỗi được báo về

- Tương tự nếu ta xóa những thứ không thể xóa thì strict mode cũng sẽ báo về cho chúng ta một lỗi 

- Các tham số của một hàm không được phép trùng nhau

- Không thể sử dụng tiền tố 0 để viết số ở hệ bát phân: bình thường nếu một số có số 0 ở đầu thì nó sẽ được hiểu là số được viết ở hệ cơ số 8, nhưng với strict mode thì điều này không được phép, h đây để viết hệ cơ số 8 chúng ta sẽ sử dụng tiền tố 0o(0o10 = 8)

- Không thể định nghĩa hàm bên trong một block hay định nghĩa một hàm c trong một hàm b, mà hàm b lại được định nghĩa trong một hàm a : với strict mode bạn chỉ có thể định nghĩa một hàm ngay trong một hàm khác hoặc ở ngoài cùng file Script, bạn sẽ không thể định nghĩa một hàm trong hàm if, for hay trong một block  

- Không thể sử dụng một vài từ vì có thể những từ này sẽ trở thành keyword trong tương lai
  + implements
  + interface
  + let
  + package
  + private
  + protected
  + public
  + static
  + yield

[Tài liệu tham khảo](https://viblo.asia/p/tim-hieu-ve-strict-mode-trong-javascript-jaqG0QQevEKw#_khong-su-dung-duoc-cach-viet-so-thuoc-he-bat-phan-voi-tien-to-la-0-9s)


## 6.Từ khóa this 
* Từ khóa this đại diện cho một đối tượng mà nó thuộc về, đối tượng đó là chủ thể của ngữ cảnh
* Một trường hợp khác khi ta khai báo các biến global và các hàm global thì chúng sẽ trở thành thuộc tính của đối tượng global, ở đây chính là đối tượng window(browser)
* Khi ở trong method của một object, this chính là object đó 
* Khi this được gọi ở phạm vi global, nó cũng đại diện cho global object(kể cả trong strict mode)
* Khi ở trong một hàm, this đại diện cho global object
* Trong strict mode, nếu this có trong một hàm thì nó là undefined
* Trong một event, this đại diện cho element nhận được event đó

### Các trường hợp dễ nhầm lẫn với this  [Tài liệu tham khảo](https://codelearn.io/sharing/con-tro-this-trong-javascript)

## 7. Bind() : ràng buộc 
```js 
const person = {
  name: 'hiep',
  age: 18,
  show() {
    console.log(this.name + this.age)
  }
}

person.show() // hiep18

const tmp = person.show 

tmp() // undefined
```
* Lí do undefined đó là do khi tmp được gán cho method show của object person, lúc này this lại chính là object window nên đương nhiên là undefined.
* Trong trường hợp ta muốn this thực sự là object person thì bind sẽ phát huy tác dụng. Bind có nghĩa là ràng buộc.
    ```js 
    const person = {
        name: 'hiep',
        age: 18,
        show(position) {
        console.log(this.name + this.age + ' ' + position)
        }
    }

    person.show('HN') // hiep18 HN

    const tmp = person.show.bind(person)

    tmp('HN') // hiep18 HN
    ```
* Bind sẽ ràng buộc tham số đầu tiên truyền vào với từ khóa this được sử dụng trong các method đó, nếu như hàm cần các đối số thì các tham số tiếp theo được truyền vào bind sẽ tương ứng với các đối số đó. Ta có thể truyền các đối số thêm đó theo như trên hoặc truyền trực tiếp cùng lúc gọi bind 
      ```js 
      const tmp = person.show.bind(person, 'HN') // kết quả vẫn như vậy
      ```
* Ta thắc mắc tại sao bind hoạt động như thế nào để this có thể ràng buộc với đối tượng được truyền vào. Thực chất bind trả về một hàm là bản sao của method sử dụng bind và từ khóa this trong method đó chính là đối tượng mà ta đã truyền vào. 

## 8. call method 
* Là phương thức trong prototype của Function constructor
* Được dùng để gọi hàm và đồng thời có thể bind this cho hàm 

* Gọi hàm 
```js 
function show(){
    console.log('hiep)
}

show() // cách thường dùng 

show.call() // điều mà JS thực sự làm 
```

* Gọi hàm và bind this 
```js
const person = {
  name: 'hiep',
  age: 18,
}

const person2 = {
  name: 'nguyen hiep',
  age: 20,
  show(position) {
    console.log(this.name + ' ' + this.age + ' ' + position)
  }
}

person2.show.call('HN') // undefined undefined undefined

person2.show.call(person, 'HN') // hiep 18 HN
```
* Khi gọi hàm **person2.show.call()** trả về undefined là vì this lúc này đã là object window
* Khi gọi hàm **person2.show.call(person)** hàm lại thực hiện được là vì lúc này ta đã bind đối tượng person với từ khóa this nên code đã chạy như ta mong muốn
* Ví dụ trên cũng thể hiện một tính chất nữa của call(), đó là **mượn hàm**. Rõ ràng person không hề có method show, nhưng vẫn có thể in ra tên và tuổi. Đó là do call đã mượn method show từ person2 và sau đó bind với person object và từ đó ta có thể thực hiện được dù không hề có method đó 


