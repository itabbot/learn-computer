# 4.2.1 对象（Objects）

[官方在线版](https://262.ecma-international.org/6.0/#sec-objects)

## 学习理解

本章节描述了对象的创建方式、原型链、动态赋值，以及类的定义语法。

### 创建对象

ECMAScript 的对象可以通过文字表示法或构造函数来创建，不像 C++ 或 Java 等语言中的对象是基于类的。如下示例：

```javascript
// 文字表示法
let object1 = {
  property1: "haha",
};

// 构造函数法
let Constructor1 = function () {
  this.property1 = "heihei";
};
const object2 = new Constructor1();
```

### 原型链

ECMAScript 中的函数都有一个名为 “prototype” 的属性，它是一个对象，称为该函数的原型属性。当该函数被作为构造函数使用 new 表达式来构造对象时，会将其原型属性隐式地关联到所创建出来的对象中，并称之为该对象的原型。

构造函数对其原型属性是显性的引用，可以直接访问的到。而所构造的对象对其则是隐形的引用，无法直接访问，但可以使用 `Object.getPrototypeOf` 方法来获取。如下示例：

```javascript
// 使用构造函数实例化对象
let Constructor1 = function () {};
const object1 = new Constructor1();

// 显性访问构造函数的 prototype 属性
Constructor1.prototype;

// 通过 Object.getPrototypeOf 方法访问对象的隐式 prototype 引用
Object.getPrototypeOf(object1);

// 它们之间是完全相等的
// 以下表达式的值为 true
Constructor1.prototype === Object.getPrototypeOf(object1);
```

当访问对象的某个属性时，会先确认该对象是否实际拥有该属性，如果有则直接使用，如果没有，则确认其原型是否拥有该属性，如果有则也会被使用。如下示例：

```javascript
// 定义构造函数，并设置其原型的属性
let Constructor1 = function () {};
Constructor1.prototype.property1 = 1;
Constructor1.prototype.property2 = 2;

// 使用构造函数实例化对象，并设置对象的属性
const object1 = new Constructor1();
object1.property2 = 22;
object1.property3 = 33;

// 以下语句会输出：1 22 33
console.log(object1.property1, object1.property2, object1.property3);
```

对象的原型本身也是一个对象，它也可以有原型，原型的原型也可以有原型，这便组成了一条原型链。当访问对象的某个属性时，会依次上溯原型链，直到找到属性的定义，或最终到达原型链的尽头（此时该属性为 undefined）。如下示例：

```javascript
// 定义祖辈构造函数，并设置其原型的属性
let Grandparent = function () {};
Grandparent.prototype.property1 = 1;
Grandparent.prototype.property2 = 2;

// 定义父辈构造函数，并设置其原型的属性
let Parent = function () {};
Parent.prototype = new Grandparent();
Parent.prototype.property2 = 22;
Parent.prototype.property3 = 33;

// 实例化子辈，并设置其属性
const son = new Parent();
son.property3 = 333;
son.property4 = 444;
// 以下语句会输出：1 22 333 444
console.log(son.property1, son.property2, son.property3, son.property4);
```

### 动态属性

与大多数基于类的语言不同，ECMAScript 对象的属性可以通过赋值直接动态地添加。如下示例：

```javascript
// 定义一个对象
let object1 = {
  property1: 1,
};

// 动态添加属性
object1.property2 = 2;

// 以下语句输出：1 2
console.log(object1.property1, object1.property2);
```

### 类定义语法

尽管 ECMAScript 对象本身不是基于类的，但根据构造函数、原型对象和方法的公共模式可以很方便地定义类。ECMAScript 内置对象本身就遵循这样的类模式。从 ECMAScript 2015 开始，ECMAScript 语言包括了类的语法定义，允许程序员简明地使用。如下示例：

```javascript
// 定义祖类
class Grandparent {
  property1 = 1;
  property2 = 2;
}

// 定义父类
class Parent extends Grandparent {
  property2 = 22;
  property3 = 33;
}

// 实例化子辈
const son = new Parent();
son.property3 = 333;
son.property4 = 444;

// 以下语句会输出：1 22 333 444
console.log(son.property1, son.property2, son.property3, son.property4);
```
