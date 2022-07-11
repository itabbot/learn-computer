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

### 4.3.10 未定义值（undefined value）

当变量未被赋值时使用的原始值 `undefined`。

### 4.3.11 未定义类型（Undefined type）

其唯一值为 “`undefined`” 值的类型。

### 4.3.12 空值（null value）

有意不包含任何对象值的原始值。

### 4.3.13 空类型（Null type）

其唯一值为 “`null`” 值的类型。

### 4.3.14 布尔值（Boolean value）

Boolean 类型的数据值。

总共只有两个布尔值：`true` 和 `false`。

### 4.3.15 布尔类型（Boolean type）

由基本值 `true` 和 `false` 组成的类型。

### 4.3.16 布尔对象（Boolean object）

标准内置 Boolean 构造函数的实例。

布尔对象可以被强制转换为布尔值。

### 4.3.17 字符串值（String value）

直观来说，字符串值是由 0 个或多个可见字符（比如字母、数字、标点符号等）组成的序列。但是严格来说，字符串值的定义应该是：由 0 个或多个 “16 位（bit）代码单元” 组成的序列。

我们可以从 `'😀'.length === 2` 表达式的值为 `true` 可以看出，上述前者的定义是错误的，而后者才是正确的。因为 ECMAScript 内部使用 UTF-16 编码来处理字符串，一个字符通常只需一个 16 位（bit）的整数来表示，而像微笑表情符号 “😀” 之类的特殊字符却占用了一个 32 位（bit）的整数，所以在字符串中占用了 2 个代码单元，于是其 length 属性值为 2。

### 4.3.18 字符串类型（String type）

所有可能的字符串值的集合。

### 4.3.19 字符串对象（String object）

标准内置构造函数 String 的实例。

### 4.3.20 数值（Number value）

对应于 IEEE 754-2008（二进制浮点数算术标准）的双精度 64 位二进制格式的原始值。

### 4.3.21 数字类型（Number type）

所有可能的数字值的集合，包括特殊的 “NaN（非数值）” 值、正无穷和负无穷。

### 4.3.22 数字对象（Number object）

标准内置构造函数 Number 的实例。

### 4.3.23 无穷（Infinity）

正无穷数的数值。

### 4.3.24 非数值（NaN）

IEEE 754-2008 标准中的特殊数值 “Not-a-Number” ，即 “非数值”。

### 4.3.25 符号值（Symbol value）

表示一个唯一的、非字符串的对象属性名的原始值。

ECMAScript 5 的对象属性名都是字符串，这容易造成属性名的冲突，ECMAScript 6 引入 Symbol 数据类型以解决这个问题。以下示例解释了这一点：

```javascript
// 直接使用字符串类型的属性名给对象的属性设置值
// 容易因不知情而覆盖原有的属性值
const obj = {
  property: 1,
};
obj.property = 2;

// 初始化对象属性时使用 Symbol 属性名以防止被覆盖
const symb = Symbol();
const obj = {
  [symb]: 1,
};
obj.property = 2;

// 添加属性时使用 Symbol 属性名以防止覆盖已有的属性值
const symb2 = Symbol();
obj[symb2] = 3;
```

### 4.3.26 符号类型（Symbol type）

所有可能的符号值的集合。

### 4.3.27 符号对象（Symbol object）

标准内置构造函数 Symbol 的实例。

需要注意的是：从 ECMAScript 6 开始不再支持使用 new 运算符创建原始数据类型的显式包装器对象，这意味着无法使用 `new Symbol()` 来创建一个 Symbol 对象。当然，为了向前兼容，现有的原始包装器对象仍可被创建，如 new Boolean、new String 以及 new Number 等。

如果真的想创建一个 Symbol 包装器对象，可以使用 Object 函数，比如：

```javascript
const sym = Symbol("foo");
const symObj = Object(sym);

// 或者
const symObj2 = Object.create(Symbol.prototype);
```

### 4.3.28 函数（function）

可以当作子程序调用的对象。

函数除了属性之外，还包含可执行的代码和状态，这些代码和状态决定函数被调用时的行为方式。

### 4.3.29 内置函数（built-in function）

内置的函数对象。比如 `parseInt` 和 `Math.exp`。

一个 “ECMAScript 实现” 可以提供与其相关但本规范中没有描述的内置函数。

### 4.3.30 属性（property）

是对象的一部分，关联一个键名和键值。

根据属性的形式，其值可以直接表示为数据值（原始值、对象或函数对象），也可以通过一对访问器函数间接表示。比如：

```javascript
// 定义一个对象
const person = {
  // 普通属性
  language: "",

  // 访问器属性
  get lang() {
    return this.language;
  },
  set lang(value) {
    this.language = value;
  },
};

// 设置属性值
person.lang = "zh-cn";

// 获取属性值
console.log(person.lang);
```

### 4.3.31 方法（method）

作为对象的属性值的函数。

当函数作为对象的方法被调用时，该对象会作为 `this` 值被传递给函数。

### 4.3.32 内置方法（built-in method）

内置对象的方法。

本规范定义了标准的内置方法，“ECMAScript 实现” 也可以指定并提供其他额外的内置方法。

### 4.3.33 特性（attribute）

定义属性（property）的某些特征的内部值。

attribute 通常也会被翻译为 “属性”，但是在此称它为 “特性” 会更加贴切一点。可回顾之前学习的 “[Property 和 Attribute](../4.2.ECMAScript-Overview#property-和-attribute)”。

### 4.3.34 自有属性（own property）

对象直接包含的属性，与 “继承属性” 相对。

### 4.3.35 继承属性（inherited property）

从对象的原型继承而来的属性，与 “自有属性” 相对。
