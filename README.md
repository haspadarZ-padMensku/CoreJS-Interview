# CoreJS-Interview

## Questions

#### 1. Типы данных в JS. Приведение типов
#### 2. Что такое hoisting?
Hoisting (поднятие) - это механизм в JavaScript в котором переменные и объявления функций передвигаются вверх своей области видимости перед тем, как код будет выполнен. Это происходит, т.к. компиляция кода происходит в два прохода. При первом проходе компилятор получает все объявления переменных, все идентификаторы. При этом никакой код не выполняется, методы не вызываются. При втором проходе собственно происходит выполнение.
- **_var_**
```javascript
console.log(foo); //ReferenceError: foo is not defined
```
```javascript
console.log(foo); //undefined
var foo = "Tom";
```
```javascript
var c = a * b;
var a = 7;
var b = 3;
console.log(c); //NaN
```
Область видимости var заканчивается внутри функции:
```javascript
function hoist() {
  console.log(message);
  var message = 'Hoisting is all the rage!'
}
hoist(); //undefined
```
Вот как интерпретатор видит код выше:
```javascript
function hoist() {
  var message;
  console.log(message);
  message = 'Hoisting is all the rage!'
}
hoist(); // Вывод: undefined
```
- **_let_**
```javascript
console.log(hoist); //ReferenceError: hoist is not defined
let hoist = 'The variable has been hoisted.';
```
```javascript
let hoist;
console.log(hoist); //undefined
hoist = 'Hoisted'
```
Переменные объявленные как let заключены в область видимости блока, а не функции.
- **_const_**
```javascript
console.log(hoist); //ReferenceError: hoist is not defined
const hoist = 'The variable has been hoisted.';
```
```javascript
const PI;
console.log(PI); //SyntaxError: Missing initializer in const declaration
PI=3.142;
```
Переменные объявленные с let и const остаются неинициализированными в начале выполнения, в то время как переменные объявленные с var инициализируются со значением undefined.
- **_function declaration_**
```javascript
display(); //"Hello Hoisting"
 
function display(){
    console.log("Hello Hoisting"); 
}
```
- **_function expression_**
```javascript
display(); //TypeError: display is not a function.
 
var display = function (){
    console.log("Hello Hoisting"); 
}
```
- **_class declaration_** (не всплывает)
```javascript
var Frodo = new Hobbit();
Frodo.height = 100;
Frodo.weight = 300;
console.log(Frodo); //ReferenceError: Hobbit is not defined
class Hobbit {
  constructor(height, weight) {
    this.height = height;
    this.weight = weight;
  }
}
```
- **_class expression_** (не всплывает)
```javascript
var Square = new Polygon();
Square.height = 10;
Square.width = 10;
console.log(Square); //TypeError: Polygon is not a constructor
var Polygon = class Polygon {
constructor(height, width) {
    this.height = height;
    this.width = width;
  }
};
```

[read more ...](https://medium.com/@stasonmars/%D1%80%D0%B0%D0%B7%D0%B1%D0%B8%D1%80%D0%B0%D0%B5%D0%BC%D1%81%D1%8F-%D1%81-%D0%BF%D0%BE%D0%B4%D0%BD%D1%8F%D1%82%D0%B8%D0%B5%D0%BC-hoisting-%D0%B2-javascript-7d2d27bc51f1)
#### 3. Let vs var. Const
#### 4. Передача данных по ссылке и по значению. Примеры
- **_Передача по значению_**
```javascript
function change(x){
  x = 2 * x;
  console.log("x in change:", x);
}
 
let n = 10;
console.log("n before change:", n); // n before change: 10
change(n);                          // x in change: 20
console.log("n after change:", n);  // n after change: 10
```
Строки, числа, логические значения передаются в функцию по значению (передается их копия).
- **_Передача по ссылке_**
```javascript
function change(user){
  user.name = "Tom";
}
 
var bob ={ 
  name: "Bob"
};
console.log("before change:", bob.name);    // Bob
change(bob);
console.log("after change:", bob.name);     // Tom
```
Объекты и массивы передаются по ссылке. То есть функция получает сам объект или массив, а не их копию.
```javascript
function change(array){
  array[0] = 8;
}
function changeFull(array){
  array = [9, 8, 7];
}
 
var numbers = [1, 2, 3];
 
console.log("before change:", numbers);     // [1, 2, 3]
change(numbers);
console.log("after change:", numbers);      // [8, 2, 3]
changeFull(numbers);
console.log("after changeFull:", numbers);  // [8, 2, 3]
```
#### 5. {a: 10} == {a: 10}. Что вернет код?
#### 6. Что такое this?
#### 7. Apply, call, bind. Для чего используются? В чем отличия?
#### 8. Замыкание. Приведите пример.
#### 9. Sum(1)(2)
#### 10. Prototype. Отличия proto от prototype. Пример наследования
#### 11. Как создать объект без прототипа?
#### 12. Методы массива, перебирающие элементы массива
#### 13. “hello world”.repeating(3) -> hello world hello world hello world. Как реализовать?
#### 14. Браузерные события элементов. Отмена дефолтных событий браузера
#### 15. Всплытие и перехват событий
#### 16. Делегирование. Пример
#### 17. Напишите функцию F, так чтобы new F === F
#### 18. Function.prototype.bind polyfill
#### 19. Object.create polyfill
#### 20. Event loop
#### 21. Promises
