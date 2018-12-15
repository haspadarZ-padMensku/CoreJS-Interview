# CoreJS-Interview

## Questions

#### 1. Типы данных в JS. Приведение типов
Все типы данных в JavaScript, кроме объектов, являются иммутабельными (значения не могут быть модифицированы, а только перезаписаны новым полным значением). Например, в отличии от C, где строку можно посимвольно корректировать, в JavaScript строки пересоздаются только полностью. Значения таких типов называются «примитивными значениями».

- _Булевый тип данных_

Булевый тип представляет собой результат логического выражения и принимает одно из двух значений: true (истина) или false (ложь).
```javascript
let checked = true;
checked = false;    
```
- _Null_

Этот тип данных имеет всего одно значение: null. Смотрите null и Null для получения подробностей.
```javascript
let age = null;
```
- _Undefined_

Переменная, значение которой не было присвоено, имеет значение undefined. Смотрите undefined и undefined для получения подробностей.
```javascript
let x = 123;
x = undefined;
alert( x ); // "undefined"
```
- _Числа_

В соответствии со стандартом ECMAScript, существует только один числовой тип, который представляет собой 64-битное число двойной точности согласно стандарту IEEE 754. 
Другими словами, специального типа для целых чисел в JavaScript нет. 
Это означает, что при числовых операциях вы можете получить неточное (округлённое) значение. 
В дополнение к возможности представлять числа с плавающей запятой, есть несколько символических значений: +Infinity (положительная бесконечность), -Infinity (отрицательная бесконечность), и NaN (не число).
Для получения самого большого или самого меньшего доступного значения в пределах +/-Infinity, можно использовать константы Number.MAX_VALUE или Number.MIN_VALUE. 
А начиная с ECMAScript 2015, вы также можете проверить, находится ли число в безопасном для целых чисел диапазоне, используя метод Number.isSafeInteger(), либо константы Number.MAX_SAFE_INTEGER и Number.MIN_SAFE_INTEGER. 
За пределами этого диапазона операции с целыми числами будут небезопасными, и возвращать приближённые значения.
Ноль в JavaScript имеет два представления: -0 и +0. («0» это синоним +0). На практике это имеет малозаметный эффект. Например, выражение +0 === -0 является истинным. Однако, это может проявиться при делении на ноль:
> 42 / +0
Infinity
> 42 / -0
-Infinity
```javascript
  let n = 123;
  n = 12.345;
```

Подробнее: https://learn.javascript.ru/number

- _Текстовые строки_

В JavaScript для представления текстовых данных служит тип String. 
Он представляет собой цепочку «элементов» 16-битных беззнаковых целочисленных значений. 
Каждый такой элемент занимает свою позицию в строке. Первый элемент имеет индекс 0, следующий — 1, и так далее. 
Длина строки — это количество элементов в ней.
В отличие от языков подобных C, строки в JavaScript являются иммутабельными. 
Это означает, что после того, как строковое значение создано, его нельзя модифицировать.
 Остаётся лишь создать новую строку путём совершения некой операции над исходной строкой. 
```javascript
let str = "Мама мыла раму";
str = 'Одинарные кавычки тоже подойдут';
```

Подробнее: https://learn.javascript.ru/es-string

- _Тип данных Символ (Symbol)_

Символы являются нововведением JavaScript начиная с ECMAScript 2015. 
Символ — это уникальное и иммутабельное примитивное значение, которое может быть использовано как ключ для свойства объекта. 
В некоторых языках программирования символы называются атомами. Их также можно сравнить с именованными значениями перечисления (enum) в языке C. 

Подробнее: https://learn.javascript.ru/symbol#obyavlenie

- _Объекты_

В JavaScript объект может расцениваться как набор свойств. 
Литеральная инициализация объекта задаёт определённое количество начальных свойств, и в процессе работы приложения поля могут добавляться и удаляться. 
Значения свойств могут иметь любой тип, включая другие объекты, что позволяет строить сложные, разветвлённые иерархии данных. 
Каждое свойство объекта идентифицируется ключом, в качестве которого может выступать значение с типом Строка или Символ.
Создание объекта:
```javascript
1. let a = new Object();
2. let b = {}; // пустые фигурные скобки
```

Подробнее: https://learn.javascript.ru/object

Приведение типов:

##### Строковое преобразование.
Строковое преобразование происходит, когда требуется представление чего-либо в виде строки. Например, его производит функция alert.
```javascript
 let a = true;
 alert( a ); // "true"
 ```
Можно также осуществить преобразование явным вызовом String(val):
```javascript
 alert( String(null) === "null" ); // true
 ```
Как видно из примеров выше, преобразование происходит наиболее очевидным способом, «как есть»: false становится "false", null – "null", undefined – "undefined" и т.п.
Также для явного преобразования применяется оператор "+", у которого один из аргументов строка. В этом случае он приводит к строке и другой аргумент, например:
```javascript
 alert( true + "test" ); // "truetest"
 alert( "123" + undefined ); // "123undefined"
 ```
##### Численное преобразование.
Численное преобразование происходит в математических функциях и выражениях, а также при сравнении данных различных типов (кроме сравнений ===, !==).
Для преобразования к числу в явном виде можно вызвать Number(val), либо, что короче, поставить перед выражением унарный плюс "+":
```javascript
let a = +"123"; // 123
let a = Number("123"); // 123, тот же эффект
```
##### Логическое преобразование.
Преобразование к true/false происходит в логическом контексте, таком как if(value), и при применении логических операторов.
Все значения, которые интуитивно «пусты», становятся false. Их несколько: 0, пустая строка, null, undefined и NaN.
Остальное, в том числе и любые объекты – true.

Подробнее: https://learn.javascript.ru/types-conversion

#### 2. Что такое hoisting?
Hoisting (поднятие) - это механизм в JavaScript в котором переменные и объявления функций передвигаются вверх своей области видимости перед тем, как код будет выполнен. Это происходит, т.к. компиляция кода происходит в два прохода. При первом проходе компилятор получает все объявления переменных, все идентификаторы. При этом никакой код не выполняется, методы не вызываются. При втором проходе собственно происходит выполнение.
- _var_
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
- _let_
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
- _const_
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
- _function declaration_
```javascript
display(); //"Hello Hoisting"
 
function display(){
    console.log("Hello Hoisting"); 
}
```
- _function expression_
```javascript
display(); //TypeError: display is not a function.
 
var display = function (){
    console.log("Hello Hoisting"); 
}
```
- _class declaration_ (не всплывает)
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
- _class expression_ (не всплывает)
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
- _var_
Область видимости переменной, объявленной через var, это её текущий контекст выполнения. Который может ограничиваться функцией или быть глобальным, для переменных, объявленных за пределами функции.

Подробнее: https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Statements/var

- _let_
Директива let позволяет объявить локальную переменную с областью видимости, ограниченной текущим блоком кода . В отличие от ключевого слова var, которое объявляет переменную глобально или локально во всей функции, независимо от области блока.

Подробнее: https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Statements/let

- _const_
Значение констант не может быть изменено новым присваиванием, а также не может быть переопределено. Константы (const) подчиняются области видимости уровня блока, так же как переменные объявленные с использованием ключевого слова let.

Подробнее: https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Statements/const

#### 4. Передача данных по ссылке и по значению. Примеры
- _Передача по значению_
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
- _Передача по ссылке_
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
