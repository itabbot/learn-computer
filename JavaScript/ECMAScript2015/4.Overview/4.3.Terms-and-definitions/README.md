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
