# instanceof
instanceof 运算符用于检测构造函数的 prototype 属性是否出现在某个实例对象的原型链上。  

```js
function Car(make, model, year) {
  this.make = make;
  this.model = model;
  this.year = year;
}
const auto = new Car('Honda', 'Accord', 1998);

console.log(auto instanceof Car);
// Expected output: true

console.log(auto instanceof Object);
// Expected output: true
```
手撕如下：  

```js
function myInstanceof(left, right) {
  let proto = Object.getPrototypeOf(left);
  const prototype = right.prototype;
  while (true) {
    if (!proto) return false;
    if (proto === prototype) return true;
    proto = Object.getPrototypeOf(proto);
  }
}
var handleClick = function () {
  function Car() {
    this.price = 20;
    this.size = 30;
  }
  const mycar = new Car();
  console.log(myInstanceof(mycar, Car));    // true
  console.log(myInstanceof(mycar, Object));    // true
};
```