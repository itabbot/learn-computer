# 4.3 术语和定义（Terms and definitions）

[官方在线版](https://262.ecma-international.org/6.0/#sec-terms-and-definitions)

## 学习理解

本章节列举并解释了本规范中提及的一些术语和定义。

### 4.3.1 类型（type）

本规范[第六章](https://262.ecma-international.org/6.0/#sec-ecmascript-data-types-and-values)中定义的各种数据类型。

### 4.3.2 原始值（primitive value）

是[第六章](https://262.ecma-international.org/6.0/#sec-ecmascript-data-types-and-values)中的 Undefined、Null、Boolean、Number、Symbol 或 String 类型定义的值。

原始值其实是一种[值类型](../../../../术语表/值类型与引用类型.md)数据，相对于引用类型数据来说，值类型数据变量保存的是实际的数据值，而引用类型的变量保存的则是对实际值的引用地址。

### 4.3.3 对象（object）

Object 类型的数据。

对象是属性的集合，只有一个原型对象，且原型也可能是空值。

关于对象、构造函数和原型请查阅前面学习的[第 4.2.1 章节](../4.2.ECMAScript-Overview/4.2.1.Objects)。

### 4.3.4 构造函数（constructor）

用于创建和初始化对象的函数对象。

构造函数的 “prototype” 属性是一个原型对象，用来实现继承和共享属性。

### 4.3.5 原型（prototype）

为其他对象提供共享属性的对象。

- 当构造函数创建一个对象时，该对象隐式引用构造函数的原型属性。

- 可以使用 `constructor.prototype` 表达式来访问构造函数的原型属性。

- 添加到构造函数原型属性中的属性，会被共享到所有构造函数的实例对象。

- 可以使用 [Object.create](https://262.ecma-international.org/6.0/#sec-object.create) 内置方法显式地指定原型来创建一个新对象。

### 4.3.6 普通对象（ordinary object）

具有所有 “基本内部方法” “默认行为” 的对象。和 “异质对象” 相对。

“内部方法” 是指一组定义了对象在运行时行为的方法，在本规范中使用双方括号 “[[]]” 括起来的名称来标识。“基本内部方法” 是本规范定义的一组每个对象都必须拥有的内部方法。详情请查阅[第 6.1.7.2 章节](https://262.ecma-international.org/6.0/#sec-object-internal-methods-and-internal-slots)。

然而，并非所有对象都必须为这些 “基本内部方法” 使用相同的算法，即 “非默认行为”。这些不具有一个或多个 “基本内部方法” “默认行为” 的对象则是 “异质对象”。

Array 对象就是一种异质对象，比如设置 Array 对象的 length 属性可以从对象中删除属性，但是 length 属性其实只是一个普通的数据属性。这种行为是通过重写 [[DefineOwnProperty]] 内部方法来实现的。详情请参阅[第 9.4.2 章节](https://262.ecma-international.org/6.0/#sec-array-exotic-objects)。以下是示例代码：

```javascript
// 定义一个数组对象。
const arr = [0, 1, 2, 3];

// 以下语句输出：[ 0, 1, 2, 3 ]
console.log(arr);

// 设置数组的长度为 1
// 此时索引值大于等于 1 的元素均被删除
arr.length = 1;

// 以下语句输出：[ 0 ]
console.log(arr);
```

### 4.3.7 异质对象（exotic object）

不具有一个或多个 “基本内部方法” “默认行为” 的对象。

在 ECMAScript 中，对象不是普通对象就是异质对象。参阅上述 [4.3.6 章节](#436-普通对象ordinary-object)的描述。

### 4.3.8 标准对象（standard object）

其语义由本规范定义的对象。

比如浏览器中的 DOM 对象就不是标准对象。

### 4.3.9 内置对象（built-in object）

由 “ECMAScript 实现” 指定和提供的对象。

- 相对来说，用户自己定义的对象则不是内置对象。

- 所有的标准对象都是内置对象。

- “ECMAScript 实现” 可以指定并提供其他类型的内置对象，比如浏览器提供的 DOM。
