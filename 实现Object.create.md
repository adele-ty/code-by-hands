# Object.create()
Object.create() 方法以一个现有对象作为原型，创建一个新对象。  

```js
function Create(obj) {
    function F() {}
    F.prototype = obj
    return new F()
}

var handleClick = function () {
  const o = { name: "jj" };
  const a = Create(o);
  a.age = 13;
  console.log(a.name, a.age);    // jj 13
};
```
