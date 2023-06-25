# new
使用new关键字创建对象的过程如下：  
1. 创建一个新的空对象  
2. 将新对象的原型设置为构造函数的 prototype 对象  
3. 让构造函数的 this 指向这个新对象，执行构造函数  
4. 判断函数的返回值类型，如果是值类型，返回创建的对象，如果是引用类型，则返回引用类型的对象。  

示例代码  
```js
// 定义一个构造函数
function Person(name, age) {
  this.name = name;
  this.age = age;
}

// 使用new关键字创建一个Person对象
var person = new Person("John Doe", 30);

// 访问对象的属性
console.log(person.name); // 输出 "John Doe"
console.log(person.age); // 输出 30
```

手撕代码
```js
function myNew() {
  const constructor = Array.prototype.shift.call(arguments);
  if (typeof constructor !== "function") return;

  // 创建一个新的对象，并将其原型设置为构造函数的原型对象
  const newObj = Object.create(constructor.prototype);

  // 将构造函数的 this 指向这个新对象，并且执行构造函数
  const result = constructor.apply(newObj, arguments);

  return typeof result === "object" && result !== null ? result : newObj;
}

const handleClick = function () {
  function Car(price, size) {
    this.price = price;
    this.size = size;
  }
  const car = myNew(Car, 10, 20);
  console.log(car);

  const number = myNew(Number, 10);
  console.log(number);
};
```